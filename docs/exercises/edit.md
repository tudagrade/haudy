# Bearbeiten von Hausübungen mit IntelliJ

## Dateianzeige

* Am linken Rand finden Sie den Abschnitt **"Project"**. Dort befindet sich eine Übersicht der Dateihierarchie des Projektes. Mit den Pfeilen links von Ordnern/Verzeichnissen können Sie die Ansicht erweitern bzw. verkleinern.
* In dem Verzeichnis **src/main/java** schreiben Sie den eigentlich Code.
* In dem Verzeichnis **src/test/java** schreiben Sie Ihre Tests.

## Neue Dateien erstellen
* Mit einem Rechtsklick auf ein Package können Sie über **new -> Java Class** eine neue Java Datei erstellen. Geben Sie dafür den Namen an, wählen Sie aus, ob es eine Klasse, Interface, Enum oder Annotation sein soll und bestätigen Sie das Erstellen, indem Sie **Enter** drücken.
* Sie können auf dieselbe Weise auch packages erstellen. Wählen Sie dafür **"package"** anstatt **"Java Class"** aus.

# Gradle Tasks
* Um die Übersicht mit allen Gradle Task zu öffnen, drücken Sie am rechten oberen Rand auf **"Gradle"**.  
   * Alternativ können Sie sich die Gradle Ansicht auch über den Reiter **"View"** anzeigen lassen, indem Sie dann auf **"Tool Windows" -> "Gradle"** gehen.  
* Klappen Sie den Ordner, der nach dem Projekt benannt ist, sowie den darin enthaltenen Ordner **"Tasks"**. Nun sehen Sie alle Verzeichnisse, in denen Gradle Tasks enthalten sind.
* Anbei ist eine Tabelle mit allen relevanten Tasks. Die jeweiligen Tasks sind im Format **"<Verzeichnisname\>/<Taskname\>"** angegeben.
* Sie können eine Task mit einem Doppelklick auf sie ausführen.

| Gradle Task | Beschreibung |
| ----------- | ----------- |
| application/run | Führt die main Methode des Projektes aus |
| submit/prepareSubmission | Erstellt die Abgabedatei im Ordner build/libs |
| verification/test | Führt Ihre selbstgeschriebenen Tast aus |
| verification/publicTest | Führt die von uns zur Verfügung gestellten public Tests aus |
| verification/check | Führt alle Tests aus |
| build/assemble | Kompiliert das Projekt |
| build/build | Kompiliert das Projekt und führt alle checks durch |

## Code ausführen
* In IntelliJ gibt es verschiedene Methoden, wie Sie Ihren Code ausführen können. Sie können eine der folgenden Methoden benutzten:
   1. Wenn Sie eine Klasse mit einer main Methode betrachten, befindet sich bei der Zeilenangabe auf der Höhe der main Methode und der Klassendefinition ein grünes Dreieck. Wenn Sie auf dieses draufdrücken und dann auf **"Run '...'"** drücken.
   2. Machen Sie links in der Project Ansicht einen Rechtsklick auf eine Klasse mit einer main Methode und drücken Sie auf **"Run '...'"**.
   3. Führen Sie am rechten oberen Rand in der Gradle Ansicht die Task **"run"** im Ordner **"application"** aus.
   4. Drücken Sie am oberen rechten Rand auf das grüne Dreieck.
      * Beachten Sie, dass diese Methode die letzte Aktion erneut ausführt. Diese ist nicht zwangsläufig immer das Ausführen des Codes.
* Wenn Ihr Code nicht terminiert, können Sie das Programm mit dem roten Quadrat am linken Rand stoppen.

## Tests ausführen
* Sie können Ihre Tests auf dieselbe Weise ausführen, wie Ihren Code.
   * Anstelle der Gradle Test **"application/run"** müssen Sie die Task **"verification/test"** ausführen.
   * Wenn Sie in der Project Ansicht einen Rechtsklick auf einen höher liegendes Package bzw. Verzeichnis machen, können Sie alle Test, die in diesem enthalten sind, auf einmal ausführen.

## Fehler und Warnungen erkennen und beheben

* IntelliJ zeigt Ihnen Syntaxfehler in Ihrem Code rot unterstrichenen an. Diese müssen behoben werden.  
* Warnungen werden Ihnen gelb unterstrichen angezeigt. Diese müssen zwar nicht behoben werden, sollten es aber.
* Wenn Sie mit der Maus über den rot oder gelb unterstrichenen Text gehen, wird Ihnen eine Beschreibung des Problems, sowie Vorschläge, wie es automatisch behoben werden kann, angezeigt.
* Am unteren linken Rand finden Sie im Abschnitt **"Problems"** eine Übersicht mit allen Fehlern und Warnungen.

## Fehlermeldungen verstehen

* Wenn Sie Ihr Programm ausführen, öffnet sich unten automatisch eine Übersicht über den Verlauf des Programms und die Konsole. Hier werden Ihnen auch die Fehler angezeigt, die während dem Programmablauf auftreten.
* Damit Ihnen die vollständigen Fehlermeldungen angezeigt werden, wählen Sie links von der Konsole die zweite Option von oben aus.
* Eine Fehlermeldung sieht z.B. wie folgt aus:
> Exception in thread "main" java.lang.ArithmeticException: / by zero  
> at example.Divider.divide(Main.java:20)  
> at example.Main.main(Main.java:10)
* Diese Fehlermeldung sagt Ihnen Folgendes:
   * Es ist eine **ArithmeticException** aufgetreten.
   * Der Grund ist: **"/ by zero"**.
   * Der Fehler ist in der Methode **divide** der Klasse **Divider** in Zeile 20 aufgetreten.
   * Diese Methode wurde von der Methode **main** der Klasse **Main** in Zeile 10 aufgerufen.

## Beheben von möglichen Fehlern

* Stellen Sie zunächst sicher, dass Sie den richtigen Ordner importiert haben. Der oberste Ordner sollte nach der Hausübung benannt sein (z. B. **"AuD-2022-HXX-Student-master"**) und direkt die build.gradle.kts Datei enthalten sein. Wählen Sie beim Importieren **nicht** einen identisch benannten Oberordner aus.
* Beachten Sie, dass es mit Gradle zu Problemen kommen kann, wenn das Projekt auf einer externen Festplatte gespeichert wurde.
* Anbei finden Sie ein paar mögliche Fehler, welche Ihnen in der Konsole, die sich beim Ausführen der des Programmes oder einer Gradle Task automatisch öffnet, angezeigt werden:  
   

   1. > [...] finished with non-zero exit value 1

      * Diese Meldung sagt ihnen nur, dass ein Fehler aufgetreten ist. Wenn der eigentliche Fehler nicht angezeigt wird, drücken Sie links neben der Konsolenausgabe auf die zweite Option von oben. Diese sollte **":run"** oder **":<Mainclass\>:main()"**


   2. > Execution failed for task ':compileJava'.  
      > error: invalid source release: 17

      oder 

      > UnsupportedClassVersionError

      oder

      > \[...\} has been compiled by a more recent version of the Java Runtime
      
      * Es wird eine falsche Java Version benutzt. Überprüfen Sie in einem Terminal mit **"java --version"**, ob Java 17 benutzt wird (s. Anleitung zum Installieren von Java) und überprüfen Sie in IntelliJ, ob unter **"File" -> "Project Structure..." -> "Project" -> "SDK"** sowie unter **"File" -> "Settings" -> "Build, Execution, Deployment" -> "Build Tools" -> "Gradle" -> "Gradle JVM"** Java 17 als Version angegeben ist.
 

   3. > Deprecated Gradle features were used in this build, making it incompatible with Gradle 8.0.
      
      oder 

      > org.junit.platform.launcher.core.EngineDiscoveryOrchestrator lambda$logTestDescriptorExclusionReasons$7  
        INFO: 0 containers and 1 tests were Method or class mismatch

      * Sie können diese Meldung ignorieren.


   4. > Execution failed for task ':prepareSubmission'.  
      > There were some errors preparing your submission. The following required properties were not set:  
      > studentId  
      > firstName  
      > lastName  

      * Sie haben vergessen Ihre persönlichen Daten in der build.gradle.kts Datei hinzuzufügen. Siehe Schritt 1.


   5. > execution failed for task ':test'.  
      > There were failing tests.  

      * Ihre selbstgeschriebenen Tests laufen nicht erfolgreich durch. Um dies zu beheben, fixen Sie entweder den Fehler, der in Ihren Tests auftritt, oder ändern Sie in der build.gradle.kts Datei direkt unter Ihren persönlichen Daten requireTests von true auf false:
      > requireTests = false


   6. > execution failed for task ':publicTest'.  
      > There were failing tests.  

      * Die von uns zur Verfügung gestellten public-Tests laufen nicht erfolgreich durch. Um dies zu beheben, fixen Sie entweder den Fehler, den die Tessts aufzeigen, oder ändern Sie in der build.gradle.kts Datei direkt unter Ihren persönlichen Daten requirePublicTests von true auf false:
      > requirePublicTests = false


   7. > Execution failed for task ':compileJava'.  
      > Compilation failed; see the compiler error output for details.

      * Es befinden sich vermutlich noch Syntaxfehler in Ihren Code, welche Sie vor dem Abgeben beheben müssen. Sie finden unten links am Rand im Reiter **"Problems"** eine Auflistung aller Syntaxfehler.


   8. > Note: \[...\] uses unsafe or unchecked operations.

      * Dies ist nur eine Warnung und verhindert nicht die Abgabe der Hausübung. Sie sollten allerdings überprüfen, ob der entsprechende Abschnitt funktioniert.
   

   9. > failed to delete some children.
      
      * Dieser Fehler entsteht meistens dadurch, dass der Zugriff auf bestimmte Dateien durch andere Prozesse, wie z. B. den Debugger, blockiert wird. Ein Neustart von IntelliJ oder Ihrem Rechner sollte das Problem beheben.
   

* Wenn Sie Ihr Problem nicht selber beheben konnten, können Sie entweder auf unserem Discord Server im Channel **"\#import-export-gradle** oder im Moodle Forum für technische Fragen nachfragen. Fügen Sie bei beiden am besten einen Ausschnitt der Konsolenausgabe mit dem Fehler als Screenshot oder Text an.

## Den Debugger benutzten

* IntelliJ bietet Ihnen mit dem Debugger eine sehr hilfreiche Methode Fehler in Ihrem Code zu finden. Sie können den Debugger genauso starten, wie Sie Ihren Code mit den Methoden 1. 2. und 4. ausführen. Der Unterschied dabei ist, dass Sie anstatt auf das grüne Dreieck **"Run '...'"** auf den roten Käfer **"Debug '...'"** drücken müssen.
* Mit einem Linksklick direkt neben der Zeilenangabe können Sie einen Breakpoint erstellen, welcher als roter Punkt angezeigt wird.
* Wenn Sie den Debugger starten, wird er Ihren Code so lange normal ausführen, bis er an einem Breakpoint ankommt. In dem Fall wird das Programm angehalten und Ihnen wird eine Liste der Variable mit den zugehörigen Werten angezeigt.
   * Mit **F8** können Sie die momentane Zeile ausführen.
   * Mit **F7** können Sie die in die Methode, die als nächstes ausgeführt wird, hineinspringen.
   * Mit **F9** können Sie das Programm bis zum nächsten Breakpoint weiterlaufen lassen.
   * Mit **Shift + F8** können Sie das Programm weiterlaufen lassen, bis die momentane Methode verlassen wird.
   * alternativ können Sie dies auch mit den Pfeilen am oberen Rand der Debugger Anzeige machen. 

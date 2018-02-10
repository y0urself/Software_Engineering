# Software Engineering

* [Phasen der Entwicklung](#phasen-der-entwicklung)
* [Modularisierung](#modularisierung)
  * [Bindung](#bindung)
  * [Kopplung](#kopplung)
  * [Projektmanagement](#projektmanagement)
* [Brook'sches Gesetz](#brooksches-gesetz)
* [COCOMO](#cocomo)
* [Function Points](#function-points)
* [Konfigurationsmanagement](#konfigurationsmanagement)
  * [SVN](#svn)
  * [GIT](#git)
* [Buildmanagement](#buildmanagement)
  * [Make](#make)
  * [Maven](#maven)
  * [Ant](#ant)
* [Programmablaufplan, Struktogramm](#programmablaufplan-struktogramm)
* [UML](#uml)
  * [Strukturdiagramme](#strukturdiagramme)
  * [Verhaltensdiagramme](#verhaltensdiagramme)

---

| Schnittstelle| Aufgabe|
|---|---|
|Software-Entwicklungsumgebung| Bereitstellen|
|Qualitätssicherung |Anforderungen, Prüfen|
|Software-Entwicklung |Entwickeln, (Wartung, Evolution) |
|[Projektmanagement](#projektmanagement) |Planen und Kontrollieren
|Software-/[Konfigurationsmanagement](#konfigurationsmanagement) | Projektstruktur planen, Rechte und Produkte verwalten |

---

## Phasen der Entwicklung

1. **Anforderungsphase**:     Analyse des Kundenwunschs
2. **Spezifikationsphase**:   Kontrakt,
3. **Planungsphase**:         Entwurf von Projektdurchführung, Aufwand-, Zeitabschätzung
4. **Entwurfsphase**:         Hard-/Softwareentwurf, Detailentwurf
5. **Implementierungsphase**: Impl. von Programmkomponenten, Test d. Systems
6. **Integrationsphase**:     Auslieferung an Kunden
7. **Wartungsphase**:         Betrieb b. Kunde, Verbesserung, Erweiterung
8. **Rückzugsphase**:         Einstellung, Datensicherung

[nach oben](#software-engineering)

---

## Modularisierung

* Exportschnittstelle: auf welche Konstrukte (Funktionen oder Variablen) kann von außen zugegriffen werden (auch außen sichtbare Informationen über Typen)
* Importschnittstelle: welche Konstrukte werden von außen benutzt (in Sprachen teils nur implizit unterstützt)

* Tiefe/Breite der Modulstruktur sollte vernünftig sein
* Modulgröße und Modulzahl sind zueinander gegenläufige Größen

Lieber kleine Module, die genau eine Sache machen und keine Entscheidungen haben.

### Bindung
* reflexive Beziehung: Beziehung einer Klasse zu sich selbst
* Zusammenhang innerhalb des Modules
* möglichst eng, aber nicht zu eng -> z.B. _Kommunikatorisch_

####  Arten:
|zufällig|logisch| temporal| prozedual| Kommunikations-| sequenziell| funktionale Bindung|
|---| --- |---| -----| ------|----|------|
|niedrig (zerstreut)||||||hoch (eng)|

**prozedural**: Prozeduren in der Aufrufreihenfolge voneinander abhängig, muss nicht sein, dass alle und alles starr ausgeführt wird
  _Beispiel_: `Stack`

**sequenziel**: Sequenz muss vollständig ausgeführt werden, alle Methoden in einer festen Reihenfolge
  _Beispiel_: `Schalter`: erst an, dann aus (anders geht nicht)


[nach oben](#software-engineering)

---

### Kopplung

* Abhängigkeit zwischen den Modulen
* möglichst kleine Kopplung -> _Stempel-_ oder _Datenkopplung_
* am Besten **NIE** Steuerkopplung

#### Arten:
|keine|direkte|Daten-|Stempel-|Steuer-|Externe/ Common-|Inhaltskopplung|
|--- | --- |---| -----| ------|----| -----|
|niedrig | | | |             |         |hoch|

### Design by Contract:
Invariants (C4J):
* Client (Aufrufer des Modules) must ensure precondition and may assume postcondition
* Method (Modul)                may assume precondition and must ensure postcondition
-> Invariante gilt immer, außer wenn Prozeduren, Methoden, Funktionen ausgeführt werden

@Java:
`java -ea (enable assertions) -javaagent:$(lib_path)/$(lib_name)`

[nach oben](#software-engineering)

---

## Projektmanagement

### Grundlagen:

* Magisches Dreieck aus _Zeit_, _Qualität_ und _Ressourcen_ (z.B. Mitarbeitertage)
  * Leistungen (z.B. Anzahl der SW Elemente)
  * `Produktivität = (Leistungen * Qualität) / Ressourcen`
* Ressource
* Planung
* Meilenstein
* kritischer Pfad
* Projektrisiko
* Projekterfolg
* Projekttyp

* Motivationsmodell: Was Entwickler kann, muss, will und was honoriert wird ...

#### Organisationsformen:

- starke bis schwache Hierarchie

|Organisationsformen|Beschreibung|
|----|----|
|Funktionale Organisation|Abteilungen bzw. Gruppen mit Spezialisten für einzelne Aufgaben|
|Reine Projektorganisation|Temporäre Struktur(Sekundär)|
|Matrixorganisation|jeder Mitarbeiter hat einen festen Platz in der Primärunternehmensorganisation und gleichzeitig seine Rolle(n) in Projekten|

#### Teamorganisation

* kleine Teams und "Einzelkämpfer"
* anarchische Teams
* demokratische Teams
* hierarchische Teams
* Chief-programmer Teams

[nach oben](#software-engineering)

---

### Vorgangsliste

|ID|Aufgabe | Vorraussetzung | Zeit|
|---|---|---|---|
|A |Aufgabentext lesen      | |                  30 Minuten
|B| Arbeitspakete identifizieren   |  A|        10 Minuten
|C| Projektstrukturplan         |     B     |   20 Minuten
|D| Vorgangsliste erstellen    |      C    |    10 Minuten
|E| Netzplan zeichnen            |    D      |  40 Minuten
|F| Gantt-Diagramm                |   D       | 30 Minuten
|G| Organisationsformen          |    A      |  10 Minuten
|H| Fragen der Tutoren vorbereiten       ||     30 Minuten

[nach oben](#software-engineering)

---

### Projektstrukturplan

Gliederungsarten:
* Funktionsorientiert
* Objektorientiert
* Phasenorientiert
* andere Kriterien
* Mischformen


### Netzplan

* Vorgangsname und ID
* Dauer des Vorgangs
* Start und Endzeit vorwärts (VA und VE)
* Start und Endzeit rückwärts (RA und RE)
* Puffer zwischen RA und VA, kann nicht negativ sein!

#### Anordnungsbeziehungen

|Anordnungsbeziehung |Beschreibung |
|----|-----|
|Normalfolge (Ende-Anfang)| Y muss beendet sein bevor X anfangen kann|
|Endfolge(Ende-Ende)|Y muss beendet sein bevor X beendet werden kann|
|Sprungfolge (Anfang-Ende)|Y muss angefangen haben bevor X enden kann||
|Anfangsfolge (Anfang-Anfang)|Y muss angefangen haben bevor X anfangen kann||

* Vorwärts- und Rückwärtsrechnung
* kritischen Pfad bestimmen

[nach oben](#software-engineering)

---

### Gantt-Diagramm

```
10    20    30    40    50    60    70    80    90
A ##############
B               ######
C                     ############
D                     ######
E                           ########################
F                           ##############################
G               ######
H ##############
```
* Meilensteine eintragbar

[nach oben](#software-engineering)

---

### Meilenstein-Trendanalyse

* Verzögerungen sind schlecht
* Schätzzeitpunkt - was denke ich zu Schaffen?
* Berichtzeitpunkt - was ist zum angegebenen Zeitpunkt fertig?
* Diagonale ist optimal ...

## Brook'sches Gesetz

* Mitarbeiter vs. Kommunikationsaufwand

| Variable | Beschreibung | Formel |
|----|----|----|
`k` | Kommunikationsaufwand | `k = c_k * (n^2/2)` |
`a` | Entwicklungsdauer | `a = t * (1/n)` |
`n`| Anzahl Mitarbeiter | |
`c_k`| Konst. für durchschnittl. individ. Kommunikationsaufwand| |
`t` | Entwicklungsdauer des Projektes | |

#### (z.B) Angegebene Parameter:
Ein Mitarbeiter arbeitet 40 Stunden die Woche. 3 Mitarbeiter benötigen 5 Wochen. `c_k = 2`

  ```
  ... t = 40 * 3 * 5 = 600
  ... a = 600 * (1/3) = 200
  ... k = 2 * (3^2/2) = 2 * (9/2) = 9
  -> Suche nun min. Gesamtzeitaufwand pro Mitarbeiter ...
 ```
 
 [nach oben](#software-engineering)
 
 ---

## COCOMO
(Constructive Cost Model)

|Faktor |Varibale| |Beispiel|
|---|---|---|---|
|Lines of Code|`LoC`| | |
|Vorgangsdauer |`VD`| `VD = a * kLoC^b` |
|Personentage |`PM`| |
|Umrechnungsfaktor |`a`| `a = LoC/PM`| `400 LoC/PM <=> 1/0.4 PM/kLoC <=> 2.5 PM/kLoC`|
|Gewichtungsfaktor| `b`| (exponenziell ...)||
|Einflussfaktoren| `EF` |||

|Schwere| `a`|`b`|
|---|---|---|
|einfaches Softwareproblem| `2,4` |`1.05`|
|mittelschweres Softwareproblem| `3,0`| `1,12`|
|schweres Softwareproblem|`3,6` |`1,2`|

* Intermediate COCOMO ( COCOMO * EF )
* EF = (Summe aller) Einflussfaktor(en)
* Schlecht: kLoC muss man schätzen!

[nach oben](#software-engineering)

---

## Function Points

#### Beispiel:
Anforderungen -> `zuordnen + klassifizieren`

|Anforderung | Typ | Schwere |
|----|----|----|
|Anmeldung im System |Abfrage|niedrig|
|Pizza bestellen|Eingabe|mittel|
|Speiseplan verändern|Datenbestände|hoch|

* Summe der Einflussfaktoren: `15`

#### Rechnung:

* `FPu` ungewichtete Functionpoints
* `FP` gewichtete Functionpoints
* `EF` Einflussfaktor(en)

```
sum(uFP) = 3 + 4 + 15
FP       = sum(FPu) * ((0.01 * sum(EF)) + 0.65)
FP       = 22       * ((0.01 * 15)      + 0.65) = 17.6
```

* empirische Daten sammeln und über Erfahrungen mitteln
* 14 Einflussfaktoren (Wert 0-5), Summe kann zwischen `0.0` und `0.7` liegen
  * Dadurch sind die gewichteten `FP` immer zwischen `0.65 * uFP <= FP <= 1.35 * uFP`

| Element|   niedrig  |mittel  |hoch|
|----|----|----|----|
|Eingabe (external Input)    | 3  |4    |    6|
|Ausgabe (external Output)|4|5|7|
|Datenbestände (internal Logical File)|7  |      10 |      15|
|Abfrage (external Inquery)|3       |  4 |6|
|Referenzdaten (external Interface File)   |5|7|10|

---

#### Klausur:

_Erkläre Funktion Points:_
- 5 Kategorien, 3 Katogerisierungen leicht mittel schwer, 14 Einflussfaktoren
- Tabelle unwichtig
- 14 Einflussdinger (Gewichtung bis 5), 35%, Rückkopplungsprozess, ...
- Immer genauer werden, Daten sammeln, ...

_Beispiel_

... dann halt machen

[nach oben](#software-engineering)

---

## Konfigurationsmanagement

### Konfigurationselemente
* Quelltext
* Schnittstellenverträge
* Anforderungsdokumente (z.B. Use Cases)
* Architektur- und Designdokumente
* Konfigurationsmanagement-Handbuch
* Testspezifikationen und Testdaten
* [Build-Skripte](#buildmanagement)
* Meta- und Konfigurationsdaten
* Benutzerdokumentation
* Installationsanleitung, Release-Notes
* Werkzeuge (z.B.Compiler, Entwicklungsumgebungen)
* Bibliotheken
* Generierte Artefakte (z.B. HTML-Dokumente, kompilierte Quelltexte)
* Protokolle von Meetings
* Binäre Auslieferungsdateien
* Projektpläne
* Protokolle von Meetings
* Liste offener Punkte, Risikolisten, etc.

* = alle Elemente in einem Repository, die unter die Versionskontrolle fallen, (Quelldateien (Dateien, die sich schnell, häufig verändern))
* != Konstanten, Binäre Daten, ...

#### Konfiguationsmanagement-Plan
Einleitung -> Management -> Aktivitäten -> Zeitplan -> Ressourcen -> Pflege

[nach oben](#software-engineering)

---

## Versionskontrolle

#### Delta-Mechanismus
  * Reduktion von Speicherbedarf
  * Vorwärtsdelta:
    * erste Version als komplette Datei, anschließend Deltas
  * Rückwärsdelta:
    * letzte Version als kompette Datei, davor Deltas

* lock-modify-unlock
  * keine parallele Veränderung (daher lock!)
* copy-modify-merge
  * Arbeiten auf der Kopie, Konflikte mergen

### SVN:

(?)


[nach oben](#software-engineering)

---

### GIT:

* Tags
  * einfache Tags, Referenz auf Commit
  * kommentierte Tags, "Zwitter zwischen Commit & Branch"

**JAVA**
  `@` in comment: _Java-Annotationen_
  z.B. `@goal` ...
  
  [nach oben](#software-engineering)
  
  ---

## Buildmanagement:

* **Make** und **Ant** sind _imperativ_
* **Maven** ist _deklarativ_


* **Ant** und **Maven** sind XML, plattformunabhängig
* **Make** irgendwie Script, plattformabhängig

### Make:
* Regeln mit dependencies(Abhängigkeiten) und targets(Ziele)
* baut aus den Abhängigkeiten die Ziele zusammen

```makefile
# bauen wir uns ein Makefile
# einrücken :D

# variablen, aufrufen mit $()
RM = rm -rf

# file-lists
FILE = test.txt

# target
$(FILE):
touch $(FILE)

# pseudo target
all:

#  $^
#  $+ alle Abhängigkeiten, wo noch Abhängigkeiten

# intermediate target, wenn aus %.text: %.txt aufgerufen
# wildcard
# touch target "$@"
%.txt:
touch $@

# wildcard
# name der ersten abhängigkeit: &< und name des targets: &@
%.text: %.txt
cp $< $@

# target: dependencies(target)
test.text: test.txt
cp test.txt test.text

# pseudo target
# wird immer ausgeführt
clean:
$(RM) $(FILE)
rm -rf jar.jar
```

[nach oben](#software-engineering)

---

### Maven:

* `mvn archetype:generate -DgroupId=de.uos.swe -DartifactId=uebung-maven`
  * `archetype`: was soll passieren?
  * `groupID`: Paketname (erste 3 ...),
  * `artifactID`: wie soll die `jar`-Datei heißen?
    * fragt Dinge ab, welcher `build`, ...
  * `pom.xml` ist analog zum Makefile, `build.xml`
    * `<dependencies>` wenn neue `<dependency>`,
    * schaut ob maven `local` installiert`ist
    * sonst schaut er `global`, ob es auf maven liegt und läd es runter, wenn er es findet

| Befehl | Aufgabe |
|----|------|
| `mvn compile` |kompiliert den Kram|
| `mvn validate` ||
| `mvn package`| mache ein Package daraus|
| `mvn test`||
| `mvn integration test` |teste ob es integriert funktioniert|
| `mvn varify` |ist das erstelle korrekt? Prüfsumme, ...|
| `mvn install` | frimelt es aus dem Maven Repository raus|
| `mvn site` | Erstellt eine Internetseite `documentation`|
| `mvn clean`| |

[nach oben](#software-engineering)

---

#### MAVEN Mojo:

* mojo: **M**aven plain **O**ld **J**ava **O**bject
* in maven eigenes Plugin einbauen
* `getLog().info(message);` -> gib mir aktuellen Mavenlog und poste was als Info Message
  * in Javadoc: `@parameter property="message"`
* plugin einbauen

### Ant:
* von Apache
* moderner als make
* XML
  * `<tag> mehr Inhalt </tag>`
  * `<tag atribute = bla> </tag>`
  * `<tag/>`
    * `((()())())` -> "well formed"
  * nur ein Wurzelelement
  * XML-Schemadefinition:
    * wie ist die Struktur? (wird vorher festgelegt)
  * ant kann automatisch Strings einbauen
  * see build.xml

#### Klausur:

(wohl eher) Make
TAB := `->|`

[nach oben](#software-engineering)

---

## Programmablaufplan, Struktogramm
* Heron-Verfahren?
* total einfach
* Struktogram: Structorizer
* Programmablaufplan: TBBT Staffel 2 Folge 13
  * Freundschaftsalgorithmus von Sheldon
  * -> Info C?!
  * -> Start Ende Rund
  * -> Ausgabe/Eingabe Paralelogramm ...


[nach oben](#software-engineering)

---


# 08.12.2017 - Übung 07:

**Strukturierte Analyse** [DFD = Datenflussdiagramm]
* Menge von DFDs, Dateilexikon, Minispezifikationen
  * genau ein Übersicht DFD (kein Datenspeicher, ein Prozess)
  * ein- oder mehrere Verfeinerungs-DFDs (1 pro Prozess, keine Terminatoren)
    * Verfeinerungs-DFD sind konsistent zum Übersichts-DFD
  * Terminatoren und Datenspeucher nur über Prozesse verbinden
  * Datenlexikon
    * endliche Menge Datendefinitionen
      * *BEISPIEL:*
        * Aufgabenblatt = {Aufgabe}
        * Aufgabe = Text, Musterlösung, Bewertungskriterien (für Tutoren)
  * Minispezifikation
    * z.B. Pseudocode, PAP
    * formlos

* Observer beobachtet Observable, wird benachrichtig, wenn irgendwas sich ändert
  * notifyAll, notifyObservers


[nach oben](#software-engineering)

---


# UML

| Diagrammtyp | Beschreibung |
|-------------|---|
|**Strukturdiagramme**||
| Klassendiagramme | Modellierung der Einzelklasse mit _Attributen_ und _Parametern_, sowie _Beziehungen_ untereinander |
| Objektdiagramme | Ausschnitt zu gewissem Zeitpunkt von _Objekt(instanzen)_ im System und ihre Beziehungen zueinander |
| Paketdiagramme | Strukturierung des Systems nach ihren Paketen |
| Komponentendiagramm | Komponenten mit _gekapselter Funktionalität_ nach außen abgrenzen |
| Kompositionsstrukturdiagramm | Komponenten tw. durchlässig von innen nach außen ... |
| Verteilungsdiagramm | Es zeigt eine bestimmte Sicht auf die Struktur des modellierten Systems |
|**Verhaltensdiagramme**||
| Anwendungsfalldiagramm | UseCase: Beschreibung aus User-Sicht, was das System leistet |
| Aktivitätsdiagramm | ausdrucksmächtige Möglichkeit Abläufe oder Prozesse mit Flüssen zu beschreiben |
| Zustandsdiagramm | Zustände und Übergänge von Objekten innerhalb eines Systems |
| Kommunikationsdiagramme | wenig Interaktion zwischen einer (größeren) Menge von Objekten explizit dargestellt |
| Sequenzdiagramm | viel Interaktion zwischen einer (kleinen) Menge von Objekten mit festgelegter Zeitachse |
| Zeitdiagramm | Mischung aus Zustands- und Kommunikationsdiagramm mit _echter_ Zeitachse (Intervall `t`) |
| Interaktionsübersichtsdiagramm | Zusammensetzung zwischen Sequenz- und Aktivitätsdiagramm |

**Kommunikationsdiagramm, Zeitdiagramm sowie Sequenzdiagramm sind komplementär**

[nach oben](#software-engineering)

---

## Strukturdiagramme



[nach oben](#software-engineering)

---

## Verhaltensdiagramme
#### UML-Sequenzdiagramme:
* if/else, nur if (optional)
* asynchron, synchrone Antwort

#### UML-Kommunikationsdiagramm:
* (Instanzname):FieldController
* **Nummerierung**:
    *     sequenzielle Nummerierung   1, 2, 3 ..
    *     iterative Nummerierung      1 * , 1.1 * , 1.2 *
    *     geschachtelte Nummerierung  1.1, 1.1.1
    *     parallele Nummerierung      1a, 1b
    
#### UML-Objektdiagramm
  * Variable dessen Zustand ungewiss ist, werden mit ihrem Typ dargestellt
    * ansonsten ihren Wert eintragen

#### UML-Zustandsdiagramm
  * Terminationszustand

* use-case-Point Methodede

[nach oben](#software-engineering)

---

# 22.12.2017 - Übung 09:

# 19.01.2018 - Übung 10:


## Vorgehensmodell

* allgemeine Art des Vorgehens für ein Projekt

### Code & Fix:

* Phase I: Erstellt eine Version
* Phase II: Änderungsphase - so lange bis fertig
* Schlecht: Kunde ist quasi der Tester

### Wasserfall Modell:

* Phase I: System Requirements
* Phase II: Software Requirements
* Phase ..: Design
* ...
* Phase ...: Implementation


* Jede Phase bedingt die nächste Phase!
* Wasserfallmodelle werden allgemein dort vorteilhaft angewendet, wo sich Anforderungen, Leistungen und Abläufe in der Planungsphase relativ präzise beschreiben lassen.
* kann maximal eine Phase zurück springen, um zu fixen

### V-Modell
(Erst was, dann wie)
```
Anforderungsdefinition (Was?)                    <->                    Abnahmetest (durch Kunden)
    Funktionaler Systementwurf                   <->               Systemtest (Funkt. ganze System?)
        Technische Systementwurf (Wie?)          <->          Integrationstest (Zusammenschieben)
            Komponentenspezifikation (Module)    <->     Komponententest (Test einzelner Klassen)
                                            Implementation
```
__auf Konsistenz achten!__

[nach oben](#software-engineering)

---

### Rapid-Prototyping
* Explorativ (rausfinden, was die Anforderungen sind - Erkundung durch Implementation)
* Evolutionär (Baue Prototypen und verbessere immer weiter, bis fertig)
* Experimentell
    * Vertikal  (Immer Schrittweise neue Funktionalitäten hinzufügen)
      * -> Horizontaler Prototyp: Eine Schicht formuliert man aus, (GUI fertig), aber da steht nichts hinter
    * Horizontal (Erstmal alle Funktionalitäten andeuten)
      * -> Vertikaler Prototyp: Ein Feature komplett durchbauen, von GUI bis zur Datenbank
              
[nach oben](#software-engineering)

---

### Spiralmodel
(inkrementell) [Berry Böhm]

  * Risikoanalyse -> als erstes das Problem mit dem größten Risiko lösen! :)
  * Sektoren
  * Kosten und Zustimmung durch Überprüfung (an den Achsen)
  * Anforderungen -> Testen (jede Phase)
    * Starte in der Mitte

### Objektorientierte Modelle
* Makroprozess (Konzept -> Designphase -> Analyse (nach Sinn) -> Evolution (Implementation) -> Wartung (Maintaining)
  * Mikroprozess [pro Makroprozess beliebig viele Mikroprozesse] (...ces -> Identifizierung -> Semantik -> Relationship -> Implementation, Interfaces -> Ident...)
* das kleine "b"
  * [Grady Botch]
  * Unify Process (Objektmodell)

[nach oben](#software-engineering)

---

## Prozessmodelle
(erlaubt jedes Vorgehensmodell)

* zusätzlich angepasst auf das Produkt, welches Vorgehen sich anbietet und welche Organisationsmodell sich anbietet, um das Vorgehen umzusetzen

* rational Unify Process

## Agile Modelle

### Agiles Manifest


[nach oben](#software-engineering)

---

#### extreme Programming (xP)
* erstes agiles Modell?
* tailoring?
* setzt agiles Manifest um


[nach oben](#software-engineering)

---

#### Scrum
  * Product-Owner: Weiß, was er haben will
          * Product Backlog:
            * Schreibt Userstories rein
            * Tasks, die das System beschreiben
              * Sprint Backlog:
                * in jedem Sprint-Zyklus werden so und so viele Tasks aus dem Product Backlog genommen und verarbeitet
                * keine neuen Story-Points während eines Sprints
              * Sprint 1-4 Wochen 
                * in einem Sprint arbeiten die Mitarbeiter ungestört an dem Sprint Backlock
              * Daily Scrum:
                * Besprechung was getan wurde, was getan wird, gab es Probleme
                * das was ich gestern gesagt hab und was ich am nächsten Tag geschafft habe, sollten optimalerweise zusammenliegen
        * Scrum-Master: Hat die Scrum-Skillz, hält Probleme vom Team fern
          * Sprint-Retrospektive:
            * was hat gut, was nicht so gut geklappt?
          * Sprint-Review:
            * präsentiere Sprint dem Product-Owner
            * neue Features, oder eilige Sachen können nun hinzugefügt werden
        * Burndown-Chart:
          * x: Zeit, y: Story-Points
        * Definition of Done:
          * wenn der Entwickler sagt: es ist fertig

[nach oben](#software-engineering)

---

#### Kanban

(nicht wirklich Agil?)

Design  |   Implementation    |   Test|
|    ------------|--------------------|-------------------|
|            X    |                    | |

  * Pol-Prinzip (nur einer kann an einem Ticket arbeiten)
    * Man holt sich das Ticket, es wird einem nicht gegeben
  * Kaisen (Ständiger wille zur Optimierung)
    * z.B. 2 statt einem Implementationsstrang ... (besser aufteilen ...)
    * z.B. Tester überfordert - 2. Tester dazunehmen
  * Cost-of-Delay (also die Tickets priorisieren, die bei delay am teuersten sind)
    * gleichgroße Happen machen (damit man sie besser gleichzeitig machen kann)

  * Microsoft-Modell
    * bla



* evolutionäre Modelle
  * Grundsystem - dann neues System mit Änderungen - wieder neues System mit nächsten Änderungen (Immer neu)
* inkrementelle Modelle (gut geplant!)
  * Kernsystem - weitere Ausbaustufen hinzufügen
* iterative Modelle
  * arbeiten im selben System - nicht wie in evolutionär immer neu implementiert


[nach oben](#software-engineering)

---

### Klausur?

- Fehler in einem UML-Diagramm suchen?
- Aktivitätsdiagramm erstellen?
- Vergleichen inkrementell/evolutionär
- Ein Szenario einem Modell zuordnen
- Scrum/Kanban?
- Agiles Manifest auswendig lernen /sonst Klausur doof

# 09.02.2018 - Übung 11:




-> Netzplan? Vorgangsliste machen - dann einfacher.
-> Ausgabe & Abfrage: Function Points:
egal
//  -> external inquery:            Daten müssen prozessiert werden
//  -> external output:             Daten müssen verarbeitet werden


* DELTA-Mechanismus:

Hallo

(+Welt)
<-
->
(-Welt)

Hallo
Welt

* Snapshot Verfahren:


---

  

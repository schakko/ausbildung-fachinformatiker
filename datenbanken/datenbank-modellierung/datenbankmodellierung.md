# Datenbankmodellierung

### Prüfungsvorbereitung für IHK-Ausbildung zum Fachinformatiker

---

# Worum geht es?
- Was sind Entitäten, Entitätstypen und Attribute?
- Was sind Relationen und Kardinalitäten?
- Darstellungsarten von Datenbankdiagrammen
- Wie können Anforderungen auf Entitäten und Attribute gemappt werden?

---

# Fallbeispiel Netflix

"Bei Netflix können Filme virtuell ausgeliehen werden. Jeder Film gehört zu genau einer Kategorie. Filme wie *Terminator* oder *Jack Reacher* gehören zur Kategorie *Action*, Filme wie *Herr der Ringe* gehören zur Kategorie *Fantasy*. Kunden, wie z. B. Herr Maier, können Filme für einen Zeitraum von 30 Tagen ausleihen.

Modellieren Sie ein ER-Diagramm anhand dieses Texts."

---

# Entität und Entitätstyp

- Eine *Entität* ist etwas, das eine reale, konkrete oder abstrakte Idee sein kann. Es kann physikalisch vorhanden sein, muss aber nicht.
- Eine Entität kann eindeutig bestimmt werden, z. B.
	- Kunde Herr Maier
	- Video "Terminator"
	- Ausleihe des Films Terminator durch Herr Maier für 30 Tage mit Beginn am 25.05.2020

- Der Entitätstyp ist hingegen das übergeordnete Konzept, z. B. *Kunde*, *Video*, *Kategorie* oder *Ausleihe*

---

# Attribute

- Attribute beschreiben die Eigenschaften eines Entitätstyps
- Ein Entitätstyp kann beliebig viele Attribute besitzen
- Ein Attribut gilt für alle Entitäten eines Entitätstyps
- Ein Attribut gehört immer zu einer Entität und kann ohne diese nicht existieren (Aggregation)
- Attribute bestehen aus einem Namen, einem Typ und dem zugeordnetem Wert pro Entität

---

## Beispiele für Attribute

- Nummer oder E-Mail des Kunden
- Erscheinungsjahr des Videos
- Beginn der Ausleihe
- Dauer des Films

---

## Attributtyp
- Attribute haben einen Attributtyp
- Dies ist der Datentyp, den ein Attribut hat, z. B.
	- Die Nummer des Kunden ist ein Integer
	- Der Name des Kunden ist ein String
	- Die Dauer des Videos ist ein Integer
	- Der Beginn der Ausleihe ist ein Datum

---

## Attributwerte

- Der Wert eines Attributs ist immer einer Entität zugeordnet und **nicht** dem Entitätstyp
- z. B.
	- Der Name (*Attribut*) des Kunden (*Entitätstyp*) mit der Nummer 123 (*Attribut* und *Wert*) entspricht "Maier" (Wert)
- ansonsten würde jeder Kunde "Maier" heißen
- Der Wert eines Attributs muss immer innerhalb des Wertebereichs des Attributtyps liegen. 
	- z. B. Datentyp "Integer" kann nicht in den Datentyp "String" umgewandelt werden

---

## Attribute als eigene Entität
- Ein Attribut könnte auch eine eigene Entität sein (z. B. Kundennummer)
- Komplexität steigt dadurch
- Meistens nicht notwendig oder im Datenbankdesign nicht gewollt

---

# Relationen
- Eine Relation beschreibt, wie eine Entität mit einer anderen Entität in Verbindung steht. 
- Dies kann z. B. sein
	- Ein Kunde kann beliebig viele Video ausleihen (Kunde und Video)
	- Ein Video wird von mehreren Kunden ausgeliehen (Kunde und Video)
	- Ein Kunde kann während eines Zeitraums einen Film nur einmal ausleihen (Kunde, Video, Datum)
	- Ein Kunde hat eine Kundennummer

---

## Kardinalität
- Die *Kardinalität* beschreibt die Anzahl der Verbindungen, die eine Entität zu einer (oder mehreren) anderen Entitäten besitzt.

- Folgende Kardinalitäten können existieren:
	- 1:1
	- 1:n bzw. n:1
	- m:n
	- theoretisch sind auch weitere, genaue Zahlenangaben möglich (z. B. 1:2), dies wird aber so in der Datenbankmodellierung i.a.R. nicht betrachtet
- die Kardinalität spezifiziert die Relation

---

# Darstellung in Excel

Siehe `fallbeispiel.xlsx`.

---

# Vergleich zwischen Excel-Tabelle und ER-Modell 

| Excel-Tabelle | Entity-Relationship-Modell|
|---|---|
|Tabellenname|Entitätstyp|
|Spaltenüberschrift|Attribut|
|Zellinhalt (Wert)|Attributswert|
|Zellinhalt (Referenz)|Relation|
|Zeile|Entität|

---

# Darstellung mit Hilfe von ERD

- Attribute, Relationen und und Entitäten werden in einem Entity-Relationship-Diagramm (ER-Diagramm, ERD) abgebildet
- ERDs dienen dazu, einen Überblick über alle beteiligten Aktoren (Entitätstypen) in einem System (Gesamtzahl der Entitätstypen mit deren Relationen und Kardinalitäten) zu bekommen
- Bei der Einarbeitung in bestehende Projekte sind ERDs wichtig

---

## Übersetzen des Fallbeispiels in ein ERD

Siehe `fallbeispiel-erd.png`.

---

# Ableiten eines ERDs anhand von Anforderungen
Das ERD kann aus den schriftlichen Anforderungen abgeleitet werden. Regeln:
|Grammatik|Bespiel|ER-Diagramm|
|Gängiges Nomen|Kunde|Entitätstyp|
|Bekanntes Nomen|Herr Maier|Entität|
|Transitive Verben||Relation|
|Intransitive Verben||Attributtyp|

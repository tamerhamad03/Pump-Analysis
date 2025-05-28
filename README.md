# Pump-Analysis
# 💧 Pumpen-Analyse – DHBW Karlsruhe

Dieses Projekt wurde im Rahmen des Moduls *Turbomachinery* an der Dualen Hochschule Baden-Württemberg (DHBW) Karlsruhe durchgeführt. Ziel ist die Analyse des Betriebsverhaltens einer Industriewasserpumpe auf Basis realer Messdaten sowie herstellerseitiger Kennlinien.

---

## 🟦 Ausgangssituation

In einem industriellen Prozess wird eine Wasserpumpe eingesetzt, deren Leistungskennwerte (Förderhöhe, Energieverbrauch, Wirkungsgrad) untersucht werden sollen. 

Gemessen wurden:
- **Volumenströme (m³/h)** über einen Zeitraum von mehreren Stunden
- **Zeitstempel** jeder Messung

Zudem liegt ein **Datenblatt der Pumpe** vor, aus dem Förderhöhen und Wirkungsgrade in Abhängigkeit vom Volumenstrom entnommen werden können.  

Ziel ist es, mit diesen Informationen die **tatsächliche energetische Leistung** der Pumpe zu bestimmen.

---

## 🧾 Aufgabenstellung

1. **Gesamten Energieverbrauch berechnen**  
   → Wie viel elektrische Energie wurde im Messzeitraum verbraucht?

2. **Durchschnittlichen Wirkungsgrad bestimmen**  
   → Wie effizient arbeitete die Pumpe im Mittel?

3. **Nicht genutzte Energie ermitteln**  
   → Wie viel der elektrischen Energie wurde nicht in hydraulische Arbeit umgesetzt?

4. **Visualisierung der Ergebnisse**  
   → Darstellung des zeitlichen Verlaufs von Volumenstrom, Leistungen und Verlusten.

---

## ⚙️ Methodik

1. **CSV-Datei einlesen:**  
   Die Messwerte wurden als Zeitreihe im Format `.csv` aufgezeichnet.

2. **Einheitliche Umrechnung:**  
   - Volumenstrom von m³/h in m³/s
   - Leistung in Watt, Energie in kWh

3. **Interpolationen aus dem Datenblatt:**  
   - Förderhöhe (H) in Abhängigkeit des Volumenstroms
   - Wirkungsgrad (η) in Abhängigkeit des Volumenstroms

4. **Leistungs- und Energieformeln anwenden**

5. **Glättung & Visualisierung der Ergebnisse**

---

## 📐 Verwendete Formeln

### 💠 Hydraulische Leistung:
\[
P_hyd = rho * g * Q * H
\]

- \( \rho \) = Dichte der Flüssigkeit [kg/m³]  
- \( g \) = Erdbeschleunigung [m/s²]  
- \( Q \) = Volumenstrom [m³/s]  
- \( H \) = Förderhöhe [m]

---

### ⚡ Elektrische Leistung (vereinfacht):

> \[
P_{\text{el}} = \frac{P_{\text{hyd}}}{\eta}
\]

- \( \eta \) = Wirkungsgrad der Pumpe (aus Kennlinie oder fest angenommen)

---

### 🔋 Elektrische Energie:

> \[
E_{\text{el}} = P_{\text{el}} \cdot \Delta t
\]

- \( \Delta t \) = Zeitdifferenz pro Messintervall (z. B. 60 s)

---

### 💧 Hydraulische Energie:

> \[
E_{\text{hyd}} = P_{\text{hyd}} \cdot \Delta t
\]

---

### 🧾 Gesamtwirkungsgrad:

> \[
\overline{\eta} = \frac{E_{\text{hyd}}^{\text{gesamt}}}{E_{\text{el}}^{\text{gesamt}}}
\]

---

## 📊 Visualisierungen

Das Notebook erzeugt folgende Diagramme:

1. **Volumenstrom über die Zeit**  
   → Darstellung der Förderleistung im Betrieb

2. **Hydraulische vs. elektrische Leistung**  
   → Vergleich des Energieeintrags und -nutzens

3. **Verlustleistung (Energieverluste)**  
   → Darstellung der Differenz zwischen zugeführter und genutzter Energie

**Alle Diagramme** sind geglättet mittels gleitendem Mittelwert (Rolling Average) und mit Zeitachsen versehen (4-Stunden-Ticks).

---

## 🛠️ Benötigte Bibliotheken

- `pandas`
- `numpy`
- `matplotlib`
- `datetime`

---

## 📁 Projektstruktur

```bash
├── Pump_Analysis.ipynb          # Analyse-Notebook mit Berechnungen & Plots
├── volume_flow_data.csv         # Messdaten der Pumpe
├── README.md                    # Projektbeschreibung (diese Datei)

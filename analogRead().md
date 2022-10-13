---
títol: "analogRead()"
descripció: ""
categoria: "Funcions"
subcategoria: "ES Analogiques"
---

# analogRead()

### Descripció

Llig el valor del pin analògic especificat. Les plaques Arduino contenen un convertidor analògic a digital multicanal de 10 bits. Això significa que mapeará els voltatges d'entrada entre 0 i el voltatge d'operació (5V o 3.3V) en valors sencers entre 0 i 1023. En un Arduino UNO, per exemple, això produeix una resolució entre lectures de: 5 volts / 1024 unitats o , 0,0049 volts (4,9 mV) per unitat. Consulte la taula a continuació per a conéixer els pins utilitzables, el voltatge de funcionament i la resolució màxima per a algunes plaques Arduino.

El rang d'entrada es pot canviar usant `analogReference()`, mentre que la resolució es pot canviar (només per a targetes Zero, Due i MKR) usant `analogReadResolution()`.

En plaques basades en ATmega (UNO, Nano, Mini, Mega), es tarda uns 100 microsegons (0,0001 s) a llegir una entrada analògica, per la qual cosa la velocitat de lectura màxima és d'unes 10.000 vegades per segon.

Placa | Voltage de funcionament | Pins utilitzables | Max resolució
---   | ---                     | ---               | ---
Uno   | 5 Volts                 | A0 to A5          | 10 bits
Mini, Nano | 5 Volts            | A0 to A7          | 10 bits
Mega, Mega2560, MegaADK | 5 Volts | A0 to A14 | 10 bits
Micro | 5 Volts | A0 to A11* | 10 bits
Leonardo | 5 Volts | A0 to A11* | 10 bits
Zero | 3.3 Volts | A0 to A5 | 12 bits**
Due | 3.3 Volts | A0 to A11 | 12 bits**
MKR Family boards | 3.3 Volts | A0 to A6 |
12 bits**

* A0 a A5 estan etiquetats en la placa, A6 a A11 estan disponibles respectivament en els pins 4, 6, 8, 9, 10 i 12
** La resolució predeterminada d'analogRead() per a aquestes plaques és de 10 bits, per motius de compatibilitat. Ha d'usar analogReadResolution() per a canviar-ho a 12 bits.

### Sintaxi

`analogRead (pin)`

### Paràmetres

`pin`: el nom del pin d'entrada analògica per a llegir (A0 a A5 en la majoria de les plaques, A0 a A6 en les plaques MKR, A0 a A7 en Mini i Nano, A0 a A15 en Mega).

### Devolucions

La lectura analògica en el pin. Encara que està limitat a la resolució del convertidor analògic a digital (0-1023 per a 10 bits o 0-4095 per a 12 bits). Tipus de dada: int.

### Codi d'exemple

El codi llig el voltatge en analogPin i el mostra.

```
int analogPin = A3; // contacte movil del potenciòmetre (terminal central) connectat
                    //al pin analògic 3, cables exteriors a terra i +5 V
int val = 0;  // variable per a guardar el valor llegit

void setup()
{
  Serial.begin(9600);           //  configura port serie
}

void loop()
{
  val = analogRead(analogPin);  // llig el pin d’entrada
  Serial.println(val);          // mostra el valor
}
```

### Notes i Advertiments

Si el pin d'entrada analògica no està connectat a res, el valor retornat per analogRead() fluctuarà en funció d'una sèrie de factors (per exemple, els valors de les altres entrades analògiques, quines tan a prop està la seua mà del tauler, etc.).

### Veure també

LLENGUATGE [AnalogReadResolution() (en anglés) ](https://www.arduino.cc/reference/en/language/functions/zero-due-mkr-family/analogreadresolution)  
EXEMPLE [Descripció dels pins d'entrada analògica (en anglés)](http://arduino.cc/en/Tutorial/AnalogInputPins)  
LLENGUATGE [Funcions](../../Funcions.md)

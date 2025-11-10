# **LunarDuino - ATmega328P Development Board**

## 1. **Project Overview**

This project is an **Arduino-style development board** built around the **ATmega328P-PU microcontroller**, providing a compact and easy-to-use platform for embedded development, prototyping, and hardware experimentation.

The board is inspired by the Arduino UNO but designed to be minimalistic, modular, and cost-effective. It integrates a crystal oscillator, reset circuitry, onboard LED indicators, GPIO breakout headers, and polarity protection.

Its pin headers expose **digital I/O, PWM, analog inputs, SPI, and UART**, enabling easy interfacing with sensors, actuators, communication modules, displays, and shields.

---

## 2. **Key Features**

* ATmega328P microcontroller
* 16 MHz crystal oscillator
* Reset button + pull-up resistor
* Onboard user LED + power LED
* Polarity protection on power input
* Break-out headers for:

  * Digital I/O
  * Analog input
  * Power rails
* Easy integration with Arduino toolchains
* Compact single-board design

---

## 3. **Applications**

* Embedded systems development
* Arduino learner platform
* Rapid prototyping
* Robotics and automation
* Research/academic labs
* IoT development
* Hobby electronics

---

## 4. **Expanded Theory of Operation**

The ATmega328P is an 8-bit AVR microcontroller widely used in Arduino UNO boards.
This development board provides the minimum supporting circuitry required for ATmega operation, including:

* Clock source
* Reset circuit
* Power distribution
* GPIO breakout

### 4.1 Core Microcontroller

ATmega328P features:

* 32 KB Flash
* 2 KB SRAM
* 1 KB EEPROM
* 6 PWM channels
* 10-bit ADC (6 channels)
* SPI / I2C / UART

These hardware modules allow versatile use in low-power digital systems.

### 4.2 Clock System

A **16 MHz crystal oscillator** (X1) with 22 pF capacitors (C1, C2) provides stable timing.

### 4.3 Reset Circuit

A push button and pull-up resistor reset the device manually.

### 4.4 Power Section

The board is powered via **+5 V input**.
Polarity protection is included to prevent incorrect power connection.

Decoupling capacitors (e.g., 100 nF) suppress noise for improved analog performance.

### 4.5 Indicators

* **Power LED**
* **User LED (LED_BUILTIN)**

These allow quick feedback during prototyping.

### 4.6 GPIO Breakout

All 28 pins of the ATmega328P are accessible via labeled headers, grouped by:

* Digital pins
* Analog pins
* Power pins

This allows easy external module interfacing.

---

## 5. **System Block Diagram**

```
            +-------------------+
            |   ATmega328P MCU  |
            |                   |
     XTAL --| Oscillator        |
   RESET <--| Reset Circuit     |
            |                   |
            | UART / SPI / I2C  |
            | PWM / ADC         |
            +-------------------+
                |          |
            GPIO Breakout  Status LEDs
```

---

## 6. **Hardware Architecture**

| Block               | Description             |
| ------------------- | ----------------------- |
| MCU (ATmega328P)    | Core processor          |
| Crystal + Caps      | Provides clock          |
| Reset switch        | Manual reset            |
| Polarity protection | Prevents reverse supply |
| LED indicators      | User + power LED        |
| GPIO Headers        | Digital + Analog        |
| Decoupling caps     | Noise filtering         |
| UART breakout       | Programming/debug       |

---

## 7. **Component Specifications**

### **ATmega328P-PU – Microcontroller**

| Parameter         | Value          |
| ----------------- | -------------- |
| Flash             | 32 KB          |
| SRAM              | 2 KB           |
| EEPROM            | 1 KB           |
| Clock             | 16 MHz         |
| Operating voltage | 1.8–5.5 V      |
| GPIO pins         | 23             |
| ADC               | 6-ch, 10-bit   |
| PWM               | 6 channels     |
| Interfaces        | UART, SPI, I2C |

---

### **Crystal Oscillator**

| Value | 16 MHz |
Provides system clock timing.

22 pF capacitors (C1, C2) ensure stable oscillation.

---

### **Reset Network**

* Momentary push-button
* 10 kΩ pull-up resistor

---

### **LEDs**

* Power indicator
* Built-in activity LED (digital pin)

---

### **Polarity Protection**

Protects from incorrect power input.

---

### **Decoupling Capacitors**

100 nF placed near Vcc pins to reduce noise.

---

## 8. **Electrical Specifications**

| Parameter        | Specification       |
| ---------------- | ------------------- |
| Supply voltage   | 5 V DC              |
| Clock Frequency  | 16 MHz              |
| Max current draw | ~20–30 mA (no load) |
| GPIO max current | 20 mA per pin       |
| ADC resolution   | 10 bit              |
| Operating temp   | –40 to +85 °C       |

---

## 9. **Installation & Usage Guide**

### 9.1 Requirements

| Item       | Notes                 |
| ---------- | --------------------- |
| Programmer | USB-Serial or ISP     |
| 5 V Input  | Regulated             |
| Software   | Arduino IDE / AVRDude |

---

### 9.2 Getting Started

1. Supply +5 V power
2. Connect programmer to UART or ISP pins
3. Upload firmware using Arduino IDE
4. Use GPIOs to interface hardware as required

---

### 9.3 Programming Options

* UART via bootloader
* Direct ISP (recommended for development)

---

## 10. **Pinout Overview**

```
   +------------------------------+
   |     ATmega328P DIP-28        |
   |                              |
   | PC6   1   28 PC5 (SCL/ADC5)  |
   | PD0   2   27 PC4 (SDA/ADC4)  |
   | PD1   3   26 PC3 (ADC3)      |
   | PD2   4   25 PC2 (ADC2)      |
   | PD3   5   24 PC1 (ADC1)      |
   | PD4   6   23 PC0 (ADC0)      |
   | VCC   7   22 GND             |
   | PB6   8   21 AREF            |
   | PB7   9   20 AVCC            |
   | PD5   10  19 PB5 (SCK)       |
   | PD6   11  18 PB4 (MISO)      |
   | PD7   12  17 PB3 (MOSI)      |
   | PB0   13  16 PB2 (SS)        |
   | PB1   14  15 PB1 (OC1A)      |
   +------------------------------+
```

Breakout headers expose all important pins for:

* Digital / PWM
* Analog
* SPI
* UART
* Power

---

## 11. **PCB Features**

* Simple UNO-like form factor
* Standalone +5 V powered
* Reset + LED included
* UART header for programming
* Digital + Analog labeled breakouts
* Minimal component count
* Clear silkscreen labeling

---

## 12. **Bill of Materials (BOM)**

| Item | Qty | Ref     | Description         |
| ---: | :-: | ------- | ------------------- |
|    1 |  1  | U1      | ATmega328P-PU       |
|    2 |  1  | X1      | 16 MHz crystal      |
|    3 |  2  | C1, C2  | 22 pF capacitors    |
|    4 |  1  | SW1     | Reset switch        |
|    5 |  1  | R (10k) | Reset pull-up       |
|    6 |  1  | R (1k)  | LED current-limit   |
|    7 |  2  | LED     | Power + built-in    |
|    8 |  1  | U9      | 100 nF decoupling   |
|    9 |  1  | Diode   | Polarity protection |
|   10 |  —  | Headers | GPIO breakout       |

---

## 13. **Advantages**

* Arduino IDE compatible
* Minimal cost
* Easy to solder
* Full IO exposure
* Debug-friendly headers
* Low-power MCU
* Compact layout

---

## 14. **Suggested Improvements**

| Improvement            | Benefit            |
| ---------------------- | ------------------ |
| USB-serial module      | Direct programming |
| Onboard regulator      | Wide input range   |
| SWD header             | Easier debugging   |
| Multiple power domains | Better isolation   |
| Onboard FTDI           | Plug-and-play use  |

---

## 15. **Conclusion**

This ATmega328P development board is a compact, reliable, and Arduino-compatible microcontroller platform ideal for education, prototyping, and embedded experimentation.
With GPIO headers, crystal timing, reset circuitry, and onboard LEDs, it provides all required foundation electronics to begin programming and hardware integration quickly.

Whether used for robotics, sensors, automation, or general microcontroller exploration, the board offers simplicity, flexibility, and a smooth learning curve.

---

## 16. **LICENSE**
See the LICENSE file.

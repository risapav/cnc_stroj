# cnc_stroj
návrh CNC gravírovacieho stroja

Ak si chceš zkonštruovať vlastnú 3D tlačiareň, veľmi pekný návrh je na [stránke](http://www.juce.sk/index.php/elektronika/3d-tlac/13-stavba-3d-tlaciarne?showall=1).

## RAMPS 1.6

Odkaz na Web stránku [RAMPS 1.6](https://reprap.org/wiki/RAMPS_1.6)

Software bežiaci pod týmto HW je potrebné naklonovať z [Github](https://github.com/MarlinFirmware/Marlin)

ubuntu:
```sh
cd ~ 
git clone https://github.com/MarlinFirmware/Marlin

```

Následne postupuj podľa inštrukcií popísaných v [Instalation](http://marlinfw.org/docs/basics/install.html).

Aby bolo jednoduché downloadovať SW do arduina, je potrebné mať nainštalované prostredie Vscode alebo Atom a v ňom mať pripravené extension PlatformIO

Potom je potrebné sprístupniť USB port, kde je pripojené Arduino. Napr: /dev/ttyUSB0. Inak budeš mať hlášku: "Cannot open /dev/ttyUSB0: Permission denied"

použi na to príkaz:
sudo usermod -a -G tty yourname

ubuntu:
```sh
example: sudo usermod -a -G tty palo
```

manjaro archlinux:
```sh
example: sudo usermod -a -G uucp palo
```

potom neyabudni na: After the sudo usermod -a -G tty yourname you have to logout/login to get group addition happens.

## Komponenty pre pohyb

* T8 Pitch 2mm Lead 2/ 8mm Rod Stainless Lead Screw Linear Rail Bar Shaft +T8 Nut
* 10x GT2 Aluminium Timing Pulley 20 Tooth Bore 5mm For 3D Printer Width 6mm Belt 
* 4pcs GT2 20T 5mm Bore 6mm Width Pulley+4M GT2 Timing Belt CNC 3D Printer Reprap
* remeň, šírka 6mm, počet zubov na 1cm je 6
* motory ACT 17HS4417 Stepper motor, 4 pole, 1.8 °, 2.55 V DC

## Nastavenie firmware Marlin

Keď je úspešne pripravené IDE a jeho časť PlatformIO, potom je potrebné nastaviť parametre CNC stroja. Vykoná sa to nastavením v súbore Configuration.h

moje nastavenia boli nasledovné:
* zmena ***BAUDRATE 115200***
* nastaviť MOTHERBOARD na hodnotu ***MOTHERBOARD BOARD_RAMPS_14_EFB***
* nastaviť POWER_SUPPLY na hodnotu ***POWER_SUPPLY 0***
* nastaviť ***USE_XMIN_PLUG***
* nastaviť ***USE_YMIN_PLUG***
* nastaviť ***USE_ZMIN_PLUG***
* nastaviť ***X_DRIVER_TYPE  DRV8825***
* nastaviť ***Y_DRIVER_TYPE  DRV8825***
* nastaviť ***Z_DRIVER_TYPE  DRV8825***
* nastavit ***DEFAULT_AXIS_STEPS_PER_UNIT   { 25, 50, 50, 500 }***
* nastavit ***DEFAULT_MAX_FEEDRATE          { 150, 300, 300, 25 }***
* nastavit ***DEFAULT_MAX_ACCELERATION      { 3000, 3000, 3000, 10000 }***
* nastavenie [displeja](https://reprap.org/wiki/RepRapDiscount_Full_Graphic_Smart_Controller) ***REPRAP_DISCOUNT_FULL_GRAPHIC_SMART_CONTROLLER***


Na nastavenie motorov je potrebne urobiť niektoré prepočty. Ak používaš ozubený remeň, 

Odkaz na [kalkulačku](https://blog.prusaprinters.org/calculator/)


pokus
git commit -a -m 'made a change'

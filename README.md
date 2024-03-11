# STK600 Arduino Programmer

This information allows you to use the [STK600](https://ww1.microchip.com/downloads/aemDocuments/documents/MCU08/ProductDocuments/UserGuides/STK600-AVR-Flash-MCU-Starter-Kit-Users-Guide-DS40001904.pdf) development system as an ISP programmer within the Arduino IDE.
<p align="center"><img src=/images/STK600.webp></p>

# Linux rules

Download the Linux udev [rules](rules/90-atmel-stk600.rules) and copy the file to /etc/udev/rules.d/ 

you can use the following commands:

```
wget https://github.com/zarpli/STK600/blob/main/rules/90-atmel-stk600.rules
sudo cp 90-atmel-stk600.rules /etc/udev/rules.d/
```

after this file is installed, physically unplug and reconnect STK600.

# Windows Driver

Replace the STK600 USB driver with the generic [LibusbK](https://libusbk.sourceforge.net/UsbK3/) driver, you can use the [Zadig](https://zadig.akeo.ie/) automatic tool.

<p align="center"><img src=/images/device_manager.png></p>

# Complement the Arduino IDE

Add the following parameters in the "programmers.txt" file.

```
stk600.name=Atmel STK600 development board
stk600.communication=usb
stk600.protocol=stk600
stk600.program.protocol=stk600
stk600.program.tool=avrdude
stk600.program.tool.default=avrdude
stk600.program.extra_params=
```

The location of "programmers.txt" file depends on your operating system, for example for Linux and Windows respectively:

```~/.arduino15/packages/arduino/hardware/avr/<platform version>/programmers.txt```

```C:\Users\<user name>\AppData\Local\Arduino15\packages\arduino\hardware\avr\<platform version>\programmers.txt```

# Upload program

use Upload Using Programmer in Sketch tab (Ctrl+Shift+U)

<p align="center"><img src=/images/upload.png></p>

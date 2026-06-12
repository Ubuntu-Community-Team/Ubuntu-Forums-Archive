---
title: "Multiple-monitor Set Up Makes Mouse-pointer Jump About in 20.04"
date: 2020-06-19
forum: New to Ubuntu
---

### Post by charlesb2t on 2020-06-19
I  have recently loaded Ubuntu 20.04 to dual-boot on a Packard Bell with  Windows 10 Home 64-bit already installed. The mouse-pointer moves and  clicks perfectly when the PC has a single-monitor. However, for work as a  developer, I should like to use a dual-monitor setup.
 The problem I have is, if I plug in to the PC tower a second monitor  and follow the steps to Connect Another Monitor To My Computer ([https://help.ubuntu.com/stable/ubuntu-help/display-dual-monitors.html](https://help.ubuntu.com/stable/ubuntu-help/display-dual-monitors.html)),  and after I confirm "join Display", the mouse-pointer jumps about and a  second stationary mouse-pointer appears in the bottom right of my  primary screen. This behaviour stops immediately I confirm "Single  Display", but now the second screen is now turned blank.

 $ xinput
&#9121; Virtual core pointer                      id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Wired Keyboard Consumer Control       id=12   [slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                  id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                     id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; USB Wired Keyboard                        id=10   [slave  keyboard (3)]
    &#8627; USB Wired Keyboard System Control         id=11   [slave  keyboard (3)]
    &#8627; USB Wired Keyboard Consumer Control       id=14   [slave  keyboard (3)]

 $ sudo dmidecode -t 1
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.
 Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Packard Bell
    Product Name: iMedia S2984
    Version:
    Serial Number: DTU96EK00360103D0F3000
    UUID: 84edd4a2-b457-11e5-9b1f-98eecb2ca5dd
    Wake-up Type: Power Switch
    SKU Number:
    Family: Packard Bell Desktop

 $ lsb_release -a; uname -a; lsusb
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:   focal
Linux charlesb2t-iMedia-S2984 5.4.0-37-generic #41-Ubuntu SMP Wed Jun 3 18:57:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0153 Realtek Semiconductor Corp. 3-in-1 (SD/SDHC/SDXC) Card Reader
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 0461:4e6f Primax Electronics, Ltd Acer Wired Keyboard Model KBAY211
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

 Should I report this as a bug, or is there something I can do?

 Any help will be appreciated. Otherwise, to carry on my work it looks as though I need to go back to Windows 10

 :(

---

### Post by howefield on 2020-06-19
Duplicate thread closed.

---


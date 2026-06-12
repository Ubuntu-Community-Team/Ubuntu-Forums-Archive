---
title: "Mouse Pointer Jumping About on Ubuntu 20.04 (dual-boot with Windows 10)"
date: 2020-06-11
forum: New to Ubuntu
---

### Post by charlesb2t on 2020-06-11
Now that I have loaded Ubuntu 20.04 to dual-boot on a Packard Bell with  Windows 10 Home 64-bit, I am unable to stop the mouse pointer from  jumping around and leaving a trail of flickering pointers wherever the  pointer has gone. When I hover over a button, the pointer jumps around  so much, clicking on a button becomes very much a hit and miss affair.  Meanwhile, an unmoving pointer sits at the bottom right of the screen,  while I am moving a second pointer around the screen. How do I fix this  please? Is it a mouse driver compatibility issue?
My xinput is as follows:
[INDENT]Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; USB Wired Keyboard Consumer Control         id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB Wired Keyboard                          id=11    [slave  keyboard (3)]
    &#8627; USB Wired Keyboard System Control           id=12    [slave  keyboard (3)]
    &#8627; USB Wired Keyboard Consumer Control         id=14    [slave  keyboard (3)]

$ lsb_release -a; uname -a; lsusb
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
Linux charlesb2t-iMedia-S2984 5.4.0-37-generic #41-Ubuntu SMP Wed Jun 3 18:57:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0153 Realtek Semiconductor Corp. 3-in-1 (SD/SDHC/SDXC) Card Reader
Bus 001 Device 007: ID 0461:4e6f Primax Electronics, Ltd Acer Wired Keyboard Model KBAY211
Bus 001 Device 008: ID 0461:4e70 Primax Electronics, Ltd USB Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/INDENT]

I'm shooting in the dark here. I've unplugged the USB mouse and, after plugging it back in, there was no change. I have unplugged the mouse from a USB 3 and plugged it into a USB 2 with no effect. 
There is more detail about what I have tried to achieve [here.]("https://askubuntu.com/questions/1248844/mouse-pointer-jumps-about-in-ubuntu-20-04-dual-boot-with-windows-10")

Thank you for any help.

---

### Post by dino99 on 2020-06-11
I do have such jumping issues when scrolling browser page or details inside a dialog box. i suspect a kernel module bug but have not yet found which one. Many users already have warn about that.

---

### Post by ActionParsnip on 2020-06-11
What is the output of:

sudo dmidecode -t 1

Thanks

---

### Post by charlesb2t on 2020-06-11
The output of:

sudo dmidecode -t 1

is:

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

---

### Post by charlesb2t on 2020-06-16
As my **4e70 USB Optical Mouse** is not listed, in the [Linux USB IDs List]("http://www.linux-usb.org/usb.ids"), but the [Kensington]("https://www.kensington.com/en-gb/p/products/control/mice/mouse-in-a-box-wired/") **4d03 Mouse-in-a-box** is, I'm going to try and get my hands on one of those.

---

### Post by charlesb2t on 2020-06-18
So, I've now plugged in a "Kensington Mouse-in-a-Box" Wired Optical USB Mouse and the PC has identified it as a **093a:2510 Pixart Imaging, Inc. Optical Mouse** (not 4d03 Mouse-in-a-box), but the mouse is on the Linux USB IDs List. However, this different mouse is still showing the same behaviour of jumping the mouse-pointer about; leaving a trail of flickering mouse-pointers wherever one has passed the mouse-pointer; and then there's still another stationary mouse-pointer at the bottom-right of the screen. So, what now?

---

### Post by charlesb2t on 2020-06-19
The issue seems to be that I have two  monitors plugged in to my tower. If I have only one monitor plugged in, the  mouse-pointer performs perfectly. However, I need two screens / monitors  for my work. :(

---

### Post by charlesb2t on 2020-06-19
So, all I've solved here is:

1. It's not down to a dual-boot setup with Windows 10 and Ubuntu 20.04
2. It's not down to an incompatible mouse driver

However, the problem of the jumping mouse-pointer occurs as soon as I [connect another monitor to my PC]("https://help.ubuntu.com/stable/ubuntu-help/display-dual-monitors.html").

---

### Post by charlesb2t on 2020-06-22
So, the problem I now have is, if I plug in to the PC tower a second monitor, and follow the steps to Connect Another Monitor To My Computer ([https://help.ubuntu.com/stable/ubunt...-monitors.html]("https://help.ubuntu.com/stable/ubuntu-help/display-dual-monitors.html")),   and after I confirm "join Display", the mouse-pointer jumps about and a   second stationary mouse-pointer appears in the bottom right of my   primary screen. This behaviour stops immediately I confirm "Single   Display", but now the second screen is now turned blank.

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

 Should I report this as a bug on Launchpad, or is there something I can do?

 Any help will be appreciated. Otherwise, to carry on my work it looks as though I need to go back to Windows 10

:confused:

---


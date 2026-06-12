---
title: "Can't install ubuntu on my laptop"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by wariso on 2013-03-15
Hello, I have installed ubuntu in many computers but Im having trouble with a laptop, it is a toshiba satellite C845D-SP4216SL, that came with windows 7, when I boot from cd and try to install the computer just freezes, Im sure that my ubuntu CD is ok, because I checked it after I downloaded it and also I used it for another installation; I started investigating in some forums and they said "Turn ACPI off and installation will run ok" but this did not solved the problem, after turning ACPI off, I got some kind of "initframs" error, and I don't know what to do,
I would appreciate any help you could bring.

---

### Post by coldraven on 2013-03-15
It could be that the CD drive is faulty or the lens needs cleaning.
I just use an old 1GB SD card for my installs. Use "Startup Disc Creator" or Unetbootin and set the BIOS to boot from USB.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

That saves burning a disc, is faster to load and no CD drive noises.
Edit: unplug any other USB drives when trying to boot from a card or stick

---

### Post by sudodus on 2013-03-15
You have tried one boot option, ***acpi=off***. I suggest that you try the others too. Start with ***nomodeset***

If still no go, try according to *coldraven*'s advice. Boot via USB, either a flash card or a USB pendrive. ***Unetbootin*** is good, and there are versions for Ubuntu as well as Windows.

---

### Post by wariso on 2013-03-15
Already tried nomodeset and botting up from usb drive 
another thing it's the fact that none operative system based in linux can be installed on this machine
Machine specs:
AMD e300 1.3Ghz
2gb RAM
AMD Radeon HD 6310 integrated graphics
500gb HDD

---

### Post by sudodus on 2013-03-15
Try with Knoppix! It is known to be good at recognizing and co-operating with most hardware. See these links[URL="http://www.knopper.net/index-en.html"]

[/URL][http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)

[http://www.knopper.net/knoppix-info/index-en.html](http://www.knopper.net/knoppix-info/index-en.html)

---

### Post by wariso on 2013-03-15
No

---

### Post by sudodus on 2013-03-16
> **wariso said:**
> No

0. Does this mean that you don't want to try Knoppix, or that you have tried but it does not boot?

1. Do you have BIOS or UEFI? Could it be, that the vendor has tried to lock the system to only use Windows?

2. Or is it a problem with the graphics chip?

What happens if you select the boot option ***text*** when you boot Ubuntu? Then it should boot into a proper text mode, if the problem was that it wouldn't run in any graphics mode.

---

### Post by wariso on 2013-03-16
0. Don't want to try it
1. I have BIOS but i think that the vendor has tried to lock it..
2. How do I know if the problem it's my graphics chip??

---

### Post by sudodus on 2013-03-16
> **wariso said:**
> 0. Don't want to try it
OK> 
1. I have BIOS but i think that the vendor has tried to lock it..
Try to find some bios menu item, where it could be unlocked!> 
2. How do I know if the problem it's my graphics chip??

If you can get it running in text mode, not only a primitive mode with a mini-shell, but with the full bash with all the text mode commands. This can be tested with the option ***text***.

---

### Post by wariso on 2013-03-16
OK guys, I managed to solve the freeze problem, but now, the installation starts good but  the part when I must choose partitions, nothing it's displayed, and if I try to search, it just displays "ubuntu has encountered an error" and reboots
My hdd is configured in ACHI mode

---

### Post by sudodus on 2013-03-16
> **wariso said:**
> OK guys, I managed to solve the freeze problem, but now, the installation starts good but  the part when I must choose partitions, nothing it's displayed, and if I try to search, it just displays "ubuntu has encountered an error" and reboots
My hdd is configured in ACHI mode
I'm glad it is running live now :-)

If you have problems with the graphical installer, try the alternate iso files for Ubuntu
[[COLOR=#ff0000]http://www.ubuntu.com/download/desktop/alternative-downloads[/COLOR]]("http://www.ubuntu.com/download/desktop/alternative-downloads")
for Lubuntu[COLOR=#ff0000]
[/COLOR][[COLOR=#ff0000]https://help.ubuntu.com/community/Lubuntu/Alternate_ISO[/COLOR]]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")[COLOR=#ff0000]
[/COLOR]for Xubuntu
[[COLOR=#ff0000]http://xubuntu.org/getxubuntu/[/COLOR]]("http://xubuntu.org/getxubuntu/")

After installation you need to install the same boot options as you were using in the live session. This is described in this link
[[COLOR=#ff0000]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")
and this is a general help text about the grub boot system
[[COLOR=#ff0000]https://help.ubuntu.com/community/Grub2[/COLOR]]("https://help.ubuntu.com/community/Grub2")

[COLOR=#ff0000]


[/COLOR]

---


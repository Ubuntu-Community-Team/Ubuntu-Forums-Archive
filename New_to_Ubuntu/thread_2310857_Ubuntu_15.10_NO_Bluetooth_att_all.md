---
title: "Ubuntu 15.10 NO Bluetooth att all"
date: 2016-01-22
forum: New to Ubuntu
---

### Post by MatsN on 2016-01-22
None of my BT (Bluetooth) are not to be found. They are stopped working. It works on Windows 7 but not on Ubuntu .15.10
Everything is updated!
I had before my Smartphone, speaker, laptop, headset, keyboard, mouse but NOTHING WORKS ANYMORE!!

But now they are all stone dead!

I've tried a lot of solutions in this forum but nothing works!

Is there someone in here that can give me a clue how to solve this problem ):P

---

### Post by QDR06VV9 on 2016-01-22
> **MatsN said:**
> None of my BT (Bluetooth) are not to be found. They are stopped working. It works on Windows 7 but not on Ubuntu .15.10
Everything is updated!
I had before my Smartphone, speaker, laptop, headset, keyboard, mouse but NOTHING WORKS ANYMORE!!

But now they are all stone dead!

I've tried a lot of solutions in this forum but nothing works!

Is there someone in here that can give me a clue how to solve this problem ):P
This is a bug reported here...[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1478799](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1478799)
There were a couple of hack jobs there mentioned also.
> [COLOR=#333333][FONT=monospace]Kernel 3.19: Bluetooth is running[/FONT][/COLOR]
Regards

---

### Post by MatsN on 2016-01-22
ThankYou for this info.
I tried the so called hack. BUT it did not work at all...

CLIP:

```
nimda@LINUX:~$ sudo apt-get purge pulseaudio-module-bluetooth
[sudo] password for nimda: 
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  linux-headers-4.2.0-16 linux-headers-4.2.0-16-generic linux-headers-4.2.0-17
  linux-headers-4.2.0-17-generic linux-headers-4.2.0-18
  linux-headers-4.2.0-18-generic linux-headers-4.2.0-19
  linux-headers-4.2.0-19-generic linux-image-4.2.0-16-generic
  linux-image-4.2.0-17-generic linux-image-4.2.0-18-generic
  linux-image-4.2.0-19-generic linux-image-extra-4.2.0-16-generic
  linux-image-extra-4.2.0-17-generic linux-image-extra-4.2.0-18-generic
  linux-image-extra-4.2.0-19-generic
Use 'apt-get autoremove' to remove them.
Följande paket kommer att TAS BORT:
  pulseaudio-module-bluetooth*
0 att uppgradera, 0 att nyinstallera, 1 att ta bort och 0 att inte uppgradera.
Efter denna åtgärd kommer 271 kB att frigöras på disken.
Vill du fortsätta? [J/n] j
(Läser databasen ... 520520 filer och kataloger installerade.)
Tar bort pulseaudio-module-bluetooth (1:6.0-0ubuntu13) ...
nimda@LINUX:~$ sudo apt-get install pulseaudio-module-bluetooth
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  linux-headers-4.2.0-16 linux-headers-4.2.0-16-generic linux-headers-4.2.0-17
  linux-headers-4.2.0-17-generic linux-headers-4.2.0-18
  linux-headers-4.2.0-18-generic linux-headers-4.2.0-19
  linux-headers-4.2.0-19-generic linux-image-4.2.0-16-generic
  linux-image-4.2.0-17-generic linux-image-4.2.0-18-generic
  linux-image-4.2.0-19-generic linux-image-extra-4.2.0-16-generic
  linux-image-extra-4.2.0-17-generic linux-image-extra-4.2.0-18-generic
  linux-image-extra-4.2.0-19-generic
Use 'apt-get autoremove' to remove them.
Följande NYA paket kommer att installeras:
  pulseaudio-module-bluetooth
0 att uppgradera, 1 att nyinstallera, 0 att ta bort och 0 att inte uppgradera.
Behöver hämta 52,3 kB arkiv.
Efter denna åtgärd kommer ytterligare 271 kB utrymme användas på disken.
Läs:1 [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) wily/main pulseaudio-module-bluetooth amd64 1:6.0-0ubuntu13 [52,3 kB]
Hämtade 52,3 kB på 0s (153 kB/s)                     
Väljer tidigare ej valt paket pulseaudio-module-bluetooth.
(Läser databasen ... 520510 filer och kataloger installerade.)
Förbereder att packa upp .../pulseaudio-module-bluetooth_1%3a6.0-0ubuntu13_amd64.deb ...
Packar upp pulseaudio-module-bluetooth (1:6.0-0ubuntu13) ...
Ställer in pulseaudio-module-bluetooth (1:6.0-0ubuntu13) ...
nimda@LINUX:~$ sudo apt-get install pavucontrol
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
pavucontrol är redan den senaste versionen.
pavucontrol är satt till manuellt installerad.
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  linux-headers-4.2.0-16 linux-headers-4.2.0-16-generic linux-headers-4.2.0-17
  linux-headers-4.2.0-17-generic linux-headers-4.2.0-18
  linux-headers-4.2.0-18-generic linux-headers-4.2.0-19
  linux-headers-4.2.0-19-generic linux-image-4.2.0-16-generic
  linux-image-4.2.0-17-generic linux-image-4.2.0-18-generic
  linux-image-4.2.0-19-generic linux-image-extra-4.2.0-16-generic
  linux-image-extra-4.2.0-17-generic linux-image-extra-4.2.0-18-generic
  linux-image-extra-4.2.0-19-generic
Use 'apt-get autoremove' to remove them.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 0 att inte uppgradera.
nimda@LINUX:~$ pactl load-module module-bluetooth-discover
**Misslyckande: Misslyckades med att starta modul [COLOR=#ff0000]FAIL!![/COLOR]**
nimda@LINUX:~$
```

 END CLIP:

Buah.... :mad::(:confused:
Now I cant use Ubuntu anymore.... To bad beacuse it is very nice to use.... [-o<

---

### Post by QDR06VV9 on 2016-01-22
Yes that is why I called them Hack Jobs instead of "fix" or "work around's"
3 had mentioned they got bluetooth working under the kernel I Quoted above ..[COLOR=#333333][FONT=monospace][I]Kernel 3.19


[/I][/FONT][/COLOR]

---

### Post by Geoffrey_Arndt on 2016-01-22
Perhaps it's worth a try to run 16.04 beta (can test it via usb-flashstick) . . . or 14.04 LTS (and then upgrade to 16.04 in April or later).

---

### Post by MatsN on 2016-01-22
Okay I will try my older Kernels and see what happens...
I have now running [COLOR=#ff0000]4.2.0.25[/COLOR] down to[COLOR=#000080] [/COLOR][COLOR=#0000cd]3.19.0.31

[/COLOR]We have to see what happen after a couple of minutes..[COLOR=#0000cd]. [/COLOR]:guitar::rolleyes:

I just tested 3.19.0.31.

No go!!!

BT is still not working here. On my other machines, Amiga, Apple, Windows 7, but not here.... Buuaaahhh  :neutral: (crying)

Whats Going On....  ( [https://www.youtube.com/watch?v=6NXnxTNIWkc](https://www.youtube.com/watch?v=6NXnxTNIWkc) )

---

### Post by Geoffrey_Arndt on 2016-01-23
Hate to say this, but from what I've read on the blog below . . bluetooth working OOTB (out of the box) on Fedora 22:

Running Gnome, Fedora is similar in appearance and functionality with Unity (not identical though).   Plus a bit more work to set up proprietary binaries.

[https://ftbeowulf.wordpress.com/2015/09/24/ubuntu-15-10-bluetooth-still-not-working/](https://ftbeowulf.wordpress.com/2015/09/24/ubuntu-15-10-bluetooth-still-not-working/)

---

### Post by MatsN on 2016-01-23
Thank You "Geoffrey_Arndt"

I tried all the solutions, but no go...

So, since I can't do my normal work any more with mouse, keyboard, sound and stuff I have to leave Linux/Ubuntu for the time being.

Goodbye Ubuntu - for a while!! [-(

Well....[B] a kind of solved!
[/B]
I bought a Bluetooth mini adapter at Clas Ohlson here in Sweden.[B]

[http://www.clasohlson.com/se/Mini-Bluetooth-adapter-v-4.0/38-5934](http://www.clasohlson.com/se/Mini-Bluetooth-adapter-v-4.0/38-5934)

[/B]Mine has the name: bluetooth USB dongle 38-3355 GUBTCR42|, Made in China, Imported by clas ohlson.

I also installed a program blueman-manager 2.0

Inserting my nano USB adapter i started to blink.

Went to the menu and selected Adapters. There I can select 2 adapters, Linux-0 and **Linux#2**.I selected[B] Always visible.

[/B]I started my Bluetooth things and hold an behold.[B]

They all started to work!

[/B]The computer inbuilt bluetooth are still not working.

So.... I prefer to call this a [COLOR=#0000ff]**kind of SOLVED!**[/COLOR]

I am happy now!! :popcorn: :D

---

### Post by jeremy31 on 2016-03-15
Post ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by MatsN on 2016-03-15
Hello Jeremy31...

I do not know why You wrote this text. But I run it and here is the result:


$ lsusb; dmesg | egrep -i 'blue|firm'
Bus 002 Device 004: ID 064e:f203 Suyin Corp. 
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 03f0:231d Hewlett-Packard Broadcom 2070 Bluetooth Combo
Bus 001 Device 003: ID 062a:4102 Creative Labs 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.256490] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   15.076602] Bluetooth: Core ver 2.20
[   15.076645] Bluetooth: HCI device and connection manager initialized
[   15.077890] Bluetooth: HCI socket layer initialized
[   15.077896] Bluetooth: L2CAP socket layer initialized
[   15.077907] Bluetooth: SCO socket layer initialized
               Loading firmware rtlwifi/rtl8192sefw.bin
[   35.211397] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.211402] Bluetooth: BNEP filters: protocol multicast
[   35.211408] Bluetooth: BNEP socket layer initialized
[   59.672371] Bluetooth: RFCOMM TTY layer initialized
[   59.672393] Bluetooth: RFCOMM socket layer initialized
[   59.672400] Bluetooth: RFCOMM ver 1.11

---

### Post by jeremy31 on 2016-03-15
There was an active bug report but it was spammed by others, so it was never addressed

Sometimes a non working bluetooth module can interfere with a working one.  If that happens do
```
echo '"SUBSYSTEM=="usb", ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="231d", ATTR{authorized}="0"' | sudo tee /etc/udev/rules.d/81-bluetooth-hci.rules
```
reboot

---

### Post by MatsN on 2016-03-15
I have never ever had some other thing that "interfere with a working one"
My own BT never worked since Ubuntu 15... It worked nicely before.
I will try Your last text and see what happens. Before that  I will remove my nano USB BT.
Hold on...

:guitar:

I just tried Your text after removing my xtra nano BT USB stick.

First try: noting happened:

@LINUX:~$         echo '"SUBSYSTEM=="usb", ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="231d", ATTR{authorized}="0"' | sudo tee /etc/udev/rules.d/81-bluetooth-hci.rules[sudo] password for xxxxx: 
aSorry, try again.
[sudo] password for xxxxx: 
"SUBSYSTEM=="usb", ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="231d", ATTR{authorized}="0"
xxxx@LINUX:~$ 

Second try: Computer rebooted by it self...



The inbuilt BT still not working :-(
But my extra BT still working.

---

### Post by jeremy31 on 2016-03-15
The inbuilt shouldn't show in rfkill list all or hciconfig -a

Fixing the inbuilt would take a kernel patch that may or may not work

---

### Post by MatsN on 2016-03-15
Well, well.... I hope that the programmers can fix this issue because so many really need a working OS.
Soo... My, so called "fix" or "solved" solution will make many others users hopefully happy for the time being.

My so called fix is working perfectly for me...

Thanks a lot for Your help in this issue..

Take care!

---

### Post by jeremy31 on 2016-03-15
The inbuilt shouldn't show in rfkill list all or hciconfig -a

Fixing the inbuilt would take a kernel patch that may or may not work

Actually the command had a typo, I got it from [http://askubuntu.com/a/626104/300665](http://askubuntu.com/a/626104/300665)

Command should be

```
echo 'SUBSYSTEM=="usb", ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="231d", ATTR{authorized}="0"' | sudo tee /etc/udev/rules.d/81-bluetooth-hci.rules
```

Reboot

I have encountered the interference issue before on the forums, one case was a year and a half ago.  The poster had a RTL8723BE wifi card with bluetooth that wasn't fully supported by the kernel then.  I wish I would have known about this command then rather than patch the kernel module so that it ignored his inbuilt

You can help get it working by filing a bug report and following through with it.  Start here [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)  I would file against linux as it is an issue with the kernel.  You might want to remove the USB dongle and remove the udev rule before filing the bug ```
sudo rm /etc/udev/rules.d/81-bluetooth-hci.rules
```

---

### Post by MatsN on 2016-03-15
Thank You for Your help.
I ran these text and this is the answer I got:

nimda@LINUX:~$ echo 'SUBSYSTEM=="usb", ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="231d", ATTR{authorized}="0"' | sudo tee /etc/udev/rules.d/81-bluetooth-hci.rules
[sudo] password for nimda: 
SUBSYSTEM=="usb", ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="231d", ATTR{authorized}="0"


nimda@LINUX:~$ sudo rm /etc/udev/rules.d/81-bluetooth-hci.rules
nimda@LINUX:~$ 

I will report this to the Ubuntu people...

---


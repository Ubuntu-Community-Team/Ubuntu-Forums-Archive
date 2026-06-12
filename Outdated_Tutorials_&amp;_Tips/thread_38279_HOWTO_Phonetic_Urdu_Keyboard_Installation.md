---
title: "HOWTO: Phonetic Urdu Keyboard Installation"
date: 2005-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by mohaham on 2005-05-30
This HOWTO will guide you through the installation of Phonetic Urdu(language) keyboard on Hoary.

**step#1** Download the Phonetic Urdu Keyboard from [www.crulp.org](www.crulp.org)
wget -c [http://www.crulp.org/Downloads/ur](http://www.crulp.org/Downloads/ur) 

**step#2** Copy this file to  /etc/X11/xkb/symbols and /etc/X11/xkb/symbols/pc  folders.
sudo cp ur /etc/X11/xkb/symbols
sudo cp ur /etc/X11/xkb/symbols/pc


**step#3** Edit “xorg.lst” found in folder /etc/X11/xkb/rules
 and add  “ur Urdu Pakistan” under the  ! layout section :
sudo gedit /etc/X11/xkb/rules/xorg.lst
add the following line under ! layout section:
ur Urdu Pakistan

**step#4** Update /etc/X11/xkb/symbol.dir by this command:
cd /etc/X11/xkb
xkbcomp -lhlpR '*' -o ./symbols.dir

**step#5** To add the Urdu keyboard goto Applications->System Tools->Configuration Editor->desktop->gnome->peripherals->keyboard->kbd->edit layouts and add "ur"
(without the quotes)

**step#6** Add Keyboard Indicator Applet to the Panel to switsh between different languages.

**step#7** Installation is complete.

For help with installation on Kubuntu refer to:
[http://www.crulp.org/Downloads/Installation%20Guide.pdf](http://www.crulp.org/Downloads/Installation%20Guide.pdf)

For detailed instructions on the installation refer to:
[http://www.sovereign-renditions.info/urduwiki/UbuntuLinux](http://www.sovereign-renditions.info/urduwiki/UbuntuLinux)

---

### Post by Quest-Master on 2005-05-31
Awesome. I'll try to link this to some of my relatives. :D

---

### Post by aflatun on 2006-02-17
I am a recent convert to Ubuntu and I followed these instructions to the dot. But for some reason it seems that some of the characters are missing. Anyone else having similar problems?

---

### Post by wisesabre on 2006-08-28
I have tried the above Instruction and get [this error]("http://ur.wikipedia.org/wiki/%D8%AA%D8%B5%D9%88%DB%8C%D8%B1:Screenshot.png")

how to resolve it?

plus is there anything like TaskManager in Windows?

Thanks

---

### Post by wisesabre on 2006-08-28
This problem is with Ubuntu 5.10 "Breezy Badger" - Release amd64

---

### Post by Rayaz on 2008-06-03
> **aflatun said:**
> I am a recent convert to Ubuntu and I followed these instructions to the dot. But for some reason it seems that some of the characters are missing. Anyone else having similar problems?

Same problem here, any solutions?

---


---
title: "NEED HELP: dual booting windows 10 and ubuntu 15.04."
date: 2015-07-31
forum: New to Ubuntu
---

### Post by HIMAL__LIMBU on 2015-07-31
so i have installed ubuntu 15.04 alongside windows 10...it went all fine until...boot repair screen. 

[http://paste.ubuntu.com/11976707/](http://paste.ubuntu.com/11976707/)

this is what i have.

Any help will be greatly appreciated.

---

### Post by oldfred on 2015-07-31
So what is the problem?

Boot-Repair looks normal for dual boot.
 
Grub2's os-prober did not yet add a Windows boot entry. 
Did you try from terminal in Ubuntu:
sudo update-grub

Or did you leave Windows fast startup on? If so you cannot boot it from grub. You may have to temporarily restore Windows boot loader to directly boot Windows and turn off fast startup. Boot-Repair or your Windows repair flash drive booted into repair console can restore a Windows boot loader. Then use Boot-Repair to restore grub.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---


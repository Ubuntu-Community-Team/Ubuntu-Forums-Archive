---
title: "2 Questions: Ubuntu version AND need dual-boot guide Ubuntu First"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by AaronCW on 2008-10-01
hello all.

can anyone tell me the easiest way to discover if i am running 64bit ubuntu or 32bit? i did install 'sysinfo' but it doesnt seem to tell me (in beginner speak) what flavor i have.

also, i did install ubuntu using my whole hard disk (wiping out vista in the process. go me!) but i also want to make it dual bootable for certain things. but im going to try it with xp home instead of vista. anyway, is there a guide to tell me how to dual boot after ive already got ubuntu on here? 

tia
aaron

---

### Post by phidia on 2008-10-01
Open a terminal and enter > uname -a that should tell you.

[Dual boot guide]("https://help.ubuntu.com/community/WindowsDualBoot") from the Ubuntu wiki.

---

### Post by AaronCW on 2008-10-01
okay uname works but what am i looking for to tell me its 64bit? it does say i686, does that mean 64bit? 

the link you posted to the guide works but at first glance appears to be windows first guide, ive already got ubuntu loaded... using the whole disk.

thx
aaron

---

### Post by o.besner on 2008-10-01
Probaly one of the easiest way you can tell which architecture you're running is to try and install Flash. If it's only flash, it's 32 bit. If it's Flash, nspluginwrapper and a bunch of 32-bit libraries, then it's 64 bit. You can also download a 32 bit .deb and see if you can install it. 

With uname -a you'll also see it. If it says "x86_64" then you're running a 64-bit install.

Windows operating systems are like men : they like to be on top. Which means they like to be installed before any other operating system, and if you install windows first ubuntu will detect it and modify your bootloader so you'll have both choices. 

If you don't want to format, you can resize your partition using Gparted. Once you've freed some space for Windows, install it. Then add the good entry in your bootloader ( sudo nano /boot/grub/menu.lst) There is an example there, just adapt it to your need.

I have a dual boot system, but I never installed Ubuntu first ( I was told not to). I'm not sure it's gonna work. Someone more knowledgeable might help you more with that.

---

### Post by AaronCW on 2008-10-01
i think system information is one thing that most new people, like me, refer to on a regular basis... when im talking to another newbie we say things like: "yeah i have 2ghz of ram and a 4gb mother processor" and then i look at my system information screen to back me up. thats one thing that windows has nailed, would be a nice feature in ubuntu... graphical system information screen. ubuntu version / processor type / maybe filesystem, hdd size, ram amount, etc.

---

### Post by kansasnoob on 2008-10-01
i686 is 32 bit.

I like this dual boot guide for simplicity:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by kansasnoob on 2008-10-01
> **AaronCW said:**
> i think system information is one thing that most new people, like me, refer to on a regular basis... when im talking to another newbie we say things like: "yeah i have 2ghz of ram and a 4gb mother processor" and then i look at my system information screen to back me up. thats one thing that windows has nailed, would be a nice feature in ubuntu... graphical system information screen. ubuntu version / processor type / maybe filesystem, hdd size, ram amount, etc.

You can install sysinfo from the repos or:

```
sudo apt-get install sysinfo
```

It'll then show up in System Tools.

---


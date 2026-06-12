---
title: "Do not Finish Avast Virus protected in Ubutnu 12.04LTS"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by agerpark on 2013-12-13
Hi all, 

My laptop info and ubuntu ver.
CPU : Inter i5 M520
Memory : 8G
Platform : x86_64
Operation system : ubutnu desktop 12.04 LTS
Desktop : cairo-Dock


First install, 
[FONT=Courier New][B]wget [http://files.avast.com/files/linux/avast4workstation_1.0.6-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.0.6-2_i386.deb)
sudo dpkg -i avast4workstation_1.0.6-2_i386.deb[/B][/FONT]

i have installed Avast Virus Protected but do not running at avast. Why don't start avast ?
anyway, i found avast solutions via google search. 
[FONT=Courier New][FONT=arial]Second install[/FONT][B]
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install

[/B][FONT=arial]but i steel don't running avast antivirus[FONT=Courier New][FONT=arial] and referance,Ubuntu 10.04LTS is running.[/FONT][/FONT]
Please let me know how to run avast or any idea.
 [/FONT]
Thanks.[/FONT]

---

### Post by nerdtron on 2013-12-13
May I know why would you like avast?
If you need antivirus protection ClamAV is in the repository and is very easy to install.

---

### Post by Frogs Hair on 2013-12-13
From what I Have found , Avast must be registered in order to work and there are some instructions for updating definitions due to the size. Clam may be a better solution for Ubuntu. [http://ubuntuforums.org/showthread.php?t=2098622](http://ubuntuforums.org/showthread.php?t=2098622)
[http://howtoubuntu.org/how-to-install-and-update-avast-antivirus-in-ubuntu#fix](http://howtoubuntu.org/how-to-install-and-update-avast-antivirus-in-ubuntu#fix)

---

### Post by oldos2er on 2013-12-13
Moved to Absolute Beginners.

---

### Post by Mark de J on 2013-12-13
You need to activate, also the free version of Avast need it by email. Do you get an error when you start it or something?

---


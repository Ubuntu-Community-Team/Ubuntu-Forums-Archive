---
title: "boot loader.............."
date: 2008-07-05
forum: New to Ubuntu
---

### Post by ettercap on 2008-07-05
boot loader..........
hello every 1
i have dual-booted xp sp 2 + ubuntu 8.04 both in seperate drives
with LILO bootloader installed.
The problem is i donot get a menu wherein i can select my desired os . The boot loader waits for 1 or 2 seconds (prompts to press any key..... )and directly starts ubuntu......

can i change this timing .....

and also if any 1 could tell me how make windows boot first if possible....coz i hardly use ubuntu in my pc ." dont get angry "

i use ubuntu as my main os in my laptop .......

---

### Post by sayakb on 2008-07-05
Sure it's LILO? By default, Ubuntu uses the GRUB bootloader.
In ubuntu, install the program startup manager. At a terminal:
```
sudo apt-get install startupmanager
```
Then goto System->Administration->Startup-manager.
Change **Timeout** and **Default Operating System** there.

---

### Post by sharks on 2008-07-05
gedit /boot/grub/menu.lst in terminal and look out for this:
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

and change the timeout

BE SURE TO MAKE A COPY OF UR MENU.lst file
by sudo cp /boot/grub/menu.lst /the-place/where-u-want-to-paste

---

### Post by jmfa59 on 2008-07-05
LinuxIsInnovation Thanks that is very helpfull

---

### Post by ettercap on 2008-07-05
thank u every 1

---


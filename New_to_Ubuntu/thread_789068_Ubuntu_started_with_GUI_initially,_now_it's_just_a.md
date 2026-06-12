---
title: "Ubuntu started with GUI initially, now it's just a text-based interface"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Edulon1111 on 2008-05-10
Okay. I had installed Ubuntu and was fascinated with the piecing together I had to do to make it a fully functional system. I got flash and sound to work after a monstrous mission. However, when I had to restart due to some updates... It went back to "Terminal" except this terminal didn't recognize some commands like sudo, apt get, and other oddities. I felt defeated, especially after so much work on Ubuntu to find all the drivers and things I needed. Can anyone help me restore Ubuntu back to its GUI?

Also,
if I want to use wine on an ubuntu OS, [for gaming] and I want to make music and make videos, etc= {Very artsy stuff] Which one would you guys recommend? As of now, I have ubuntu. I have heard of other ""ubuntus, but don't know the difference.

---

### Post by kwacka on 2008-05-10
Does this help?```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by joshsmith on 2008-05-10
its difficult to diagnose unless we have more info. give us as much as possible

also, are you sure you are looking a terminal, and not a login window in a terminal

run the command 
ls
if it does take that, and output a list of files, you have screwed something up pretty badly

unless you are very motivated, take the easy way out and install ubuntu from scratch, it will certainly be the least time consuming method,
20 minutes to reinstall. This sounds like such a diffficult thing to diagnose, although maybe a trivial problem, that reinstalling just seems quicker

if you are motivated:
if you are looking at a root teminal, it wont take the command sudo, as you are already sudo.
if you start in recovery mode (choose that at the grub (the place where you choose which operating system you want to use) you will get straight to a root terminal
the commmand 
/etc/init.d/gdm start
or
startx
should get you back into graphical mode.

but do consider a reinstall


ps, for sound and flash to work, you just need to install the package libflashsupport

for your version of ubuntu, just stick with ubuntu

---

### Post by Edulon1111 on 2008-05-10
Hey guys, I went to go put in that command... But ubuntu decided to digress into its GUIness. Thanks anyway, and sorry for the bother.

---

### Post by barbedsaber on 2008-05-10
thats fine

---


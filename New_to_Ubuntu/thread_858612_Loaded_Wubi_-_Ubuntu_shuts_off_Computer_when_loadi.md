---
title: "Loaded Wubi - Ubuntu shuts off Computer when loading"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by hshawjr on 2008-07-13
Loaded Wubi 8.04.1 and everything seemed but everytime I go to load Ubuntu it cycles and then shuts off laptop??? Ideas anyone?  I have a HP Pavilion tx2510us TABLET PC running Vist SP1  Thanks Harold

---

### Post by n7bek on 2008-09-11
YEAH SAME PROBLEM HERE BUT, I FOUND THAT WHEN THE BLACK SCREEN APPEARS AKA GRUB TO SELECT UBUNTU
THEN YOU PRESS "E"
YOU WILL GET TO A SECOND MENU 
THEN SELECT THE SECOND LINE THAT HAS KERNEL IN THE BEGINNING
THEN PRESS "E" AGAIN AND AT THE END OF THE LINE ADD "acpi=off"
press enter
you will go back the previous menu and press "b" to boot into ubuntu

if you dont want to do this all the time you have to edit the menu.lst

hope that would help

until now i have no sound and wifi I'm still looking into it & this is my first day to have it installed i'll keep looking to see how i can get this sweet babe to fully fly on ubuntu

---

### Post by samin90 on 2008-10-22
I have the exact same problem, (I'm using an HP tx2514ca by the way) except it doesn't install. During the installation it loads just like windows would and the under the logo after the loader meter thingy stops it would say "please remove the disk and close the tray, then press enter to continue" (the C.D. tray pops open at the same time). I press enter and the computer shuts down. I successfully installed it later while I was on Windows Vista after I extended C: (left 60 GB un-allocated for Ubuntu), when i restarted my p.c. windows selector popped up with the options of Windows Vista and Ubuntu. I chose Ubuntu and it loaded up like last time, but unlike last time it didn't ask me to take out the C.D., it just shut-down.

Grub didn't appear at all, maybe it has something to do with HP tablets?

---

### Post by gali98 on 2008-10-22
Here is what you should do...
When it boots up select "ubuntu"
Immediatly after you select it, start hitting esc.
A menu should pop up.
press e
press -> until you get to the end then type a space and add this:
acpi=off
then press e
then press b
This should boot it up and install.
to get a lot of stuff working, you should then see here:
[http://ubuntuforums.org/showthread.php?t=873188](http://ubuntuforums.org/showthread.php?t=873188)
Kory

---

### Post by prematurebaby on 2008-10-22
So I take it you've never booted properly. I have an hp laptop as well but maybe mine is different. I think the kernel hates your computer.

---

### Post by gali98 on 2008-10-22
The problem is with overheating. Intrepid fixes this. If you want to wait for a couple of weeks. This fix will also work.
Kory

---


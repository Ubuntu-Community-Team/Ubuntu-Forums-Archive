---
title: "Desperate please, Want to completely uninstall Ubuntu!"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by jimsonweed on 2008-10-13
i want to redo my whole partitions and everything on another pc. I only have ubunut 7.4 installed on it. Thing is only thing I can access is the failsafe terminal. I dont really want to lose all the files on there -importantly pictures-, but the system is useless the way it is. It doesnt boot window or ubuntu cds it just loads ubuntu. its just that nothing loads !! This all happened trying to get my second hd to work :mad:

---

### Post by Keen101 on 2008-10-13
you can't even boot an ubuntu live-cd to backup your data??

you should still be able to boot live-cd's. Maybe you accidentally changed something in your BIOS. Check please.

we'll I have a solution to erase partitions, but you will need to use a Live-CD though.

I recommend the Gparted Live-CD for partition editing. It provides a nice GUI partition editor. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by jimsonweed on 2008-10-13
well I have an ubuntu 8.04 install cd, but It wont start the cd when I boot up.

---

### Post by fooman on 2008-10-13
to boot from a cd,  you may have to make a change in the bios.  usually pressing the "delete", "f1", or "f2" during boot will get you into the bios...check the screen as it starts to boot and it should tell you what key to press to enter the bios or setup.

once there,  look for a "boot" or "start" section and you should see "first boot device" or something similar...change it to cdrom, save settings,  insert cd into drawer and reboot.

hope that helps.

---

### Post by master5o1 on 2008-10-13
Considering that it doesn't boot from cds, you should try and access the bios [on boot, press either delete, f2 or f12] and switch the boot order to: 1: CD; 2: Hard Disk. etc.

Then try using a live cd to access the gnome session so you can be comfortable in a gui.
If you need access to your hard disk (permissions) then you can use `chroot` in terminal using the live cd.




Why do you want to get rid of Ubuntu?

---

### Post by jimsonweed on 2008-10-13
I dont want to get rid of it completely I just want to reinstall and start from scratch. Some how I got locked out of windows2k and I screwed ubuntu up trying to get my second hd to work. I would really like to backup the pictures if possible?

---

### Post by Keen101 on 2008-10-13
again... please try checking your BIOS so we can help you.

---

### Post by lisati on 2008-10-13
Jim: A lot of us here at the forum can probably appreciate the frustration you're feeling. One or two of us might even be thinking of puns about your handle......

It's ok to sit down, take a deep breath, and relax for a little while.
 
When you turn your computer on (or restart it), take a look for a message that says something about "Press F2 to enter setup" - pressing whichever key it says will let you take a look at the settings that your computer's BIOS uses to get started, and change them to tell your computer to start up from CD. Don't forget to save your changes after doing whatever is needed.

---

### Post by jimsonweed on 2008-10-13
im sorry, it does nothing when i press any of those. it starts up as if it dual booting. List ubuntu and windows which the partition for windows was deleted. It wont let me do what you are asking.

---

### Post by lisati on 2008-10-13
(Thinks for a moment) What make/model computer do you have? Perhaps someone here will know which key to press  on it when starting up to help check for loading from CD

---

### Post by Keen101 on 2008-10-13
> **jimsonweed said:**
> im sorry, it does nothing when i press any of those. it starts up as if it dual booting. List ubuntu and windows which the partition for windows was deleted. It wont let me do what you are asking.

what type of system do you have? This info may help us figure out the key to get into your BIOS. Try the DEL key.

---

### Post by jimsonweed on 2008-10-13
Dell Dimension L933r

---

### Post by lisati on 2008-10-13
Just looking at this thread (and [here]("http://ubuntuforums.org/showthread.php?t=946219") as well). A couple of questions:

1) When you recorded your LiveCD, did you remember to burn it as a disk image?
2) are you able to boot into Windows?

---

### Post by jimsonweed on 2008-10-13
1)I got the cd from a distributor. 
2)No im not able to boot into windows at all, the partition was deleted
I know what it is you guys want me to do but, . . . it just wont let me for some reason.

---

### Post by Keen101 on 2008-10-13
> **jimsonweed said:**
> Dell Dimension L933r

Try to press the f12 key repeatedly at startup.

or you can try pressing the DEL key repeatedly on startup.


[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by jimsonweed on 2008-10-13
^didnt work either. Well I tried getting there through the memory test-only other thing i can select on boot-, didnt work. Well its running memory test atm.

---

### Post by crjackson on 2008-10-13
> **jimsonweed said:**
> ^didnt work either. Well I tried getting there through the memory test-only other thing i can select on boot-, didnt work. Well its running memory test atm.

On mine f11 gives me a menu to select which device to boot from. Try f11

---

### Post by handydan918 on 2008-10-13
acoording to the Dell support site, the DEL key is the correct key for BIOS access. As soo as you hit the power button, start tapping the DEL key 1-2 times per second. That should get you into the bios.

---


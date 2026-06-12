---
title: "[SOLVED] Making XP boot by default"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by DawnDisciple on 2008-05-12
I have installed XP on one drive and Ubuntu on my second drive.  Xp first and then Ubuntu.  Ubuntu has made me a nice boot menu but the problem is that it boots Ubuntu by default and I wanted XP to boot by default. How do I change this?

---

### Post by zenwalker on 2008-05-12
Edit /boot/grub/menu.lst file of Ubuntu and then edit the default section value. 

As of now, the default value would be 1 if the ubuntu entry is second in the grub menu. Change it to 0 to boot Xp as default.

---

### Post by aysiu on 2008-05-12
Instructions here:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by DawnDisciple on 2008-05-12
Thanks, seems straight forward (touches wood)I will give it a go.

---

### Post by DawnDisciple on 2008-05-12
It wont let me do anything keeps telling me I am not the owner. I own the computer the copy of Ubuntu and the house that shelters it, what more does it want?

---

### Post by aeiah on 2008-05-12
you have to be the root user to make important changes. ubuntu doesnt let you do it without providing a password and such. open a terminal and type ```
sudo gedit /boot/grub/menu.lst
```

this will open the file with gedit, the text editor. sudo roughly stands for 'super user do'. it gives you temporary root privilages.

---

### Post by bruce2000 on 2008-05-12
Hi,

It needs sudo to edit the menu.lst file:

> 
gksudo gedit /boot/grub/menu.lst


It might be worth making a backup beforehand, should something go wrong:

> 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak


---

### Post by rahimveron on 2008-05-12
Since you are dual booting XP entry would be in the 5th Line in Grub Menu. So change the deafult value to 4 (Grub counts the line from 0)

---

### Post by mister_pink on 2008-05-12
There's also a new GUI way of doing these things. I get the impression its will be standard in future versions but isn't quite ready yet, but it seems to work well enough.

Go to Applications-> Add remove and search for "start up" (make sure it says show all available next to the search box). Tick Start up Manager then apply changes. When its installed it will be in your System -> Admin menu.

---

### Post by Fly135s on 2008-05-12
Yup, StartUp-Manager in the System -> Admin menu is how I did it (after adding it via Applications-> Add remove).  Works like a charm!

---

### Post by DawnDisciple on 2008-05-12
Yes!! done it using start up manager as described, easier than remembering code " I know I'm lazy"
Thanks again. I'm liking this new Ubuntu.

I have started to learn the code, I have 3 commands now that I understand - sudo = super user do - gedit = open text editor - sudo cp = copy

---


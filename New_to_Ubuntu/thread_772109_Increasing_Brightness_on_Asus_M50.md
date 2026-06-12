---
title: "Increasing Brightness on Asus M50"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Iago1989 on 2008-04-28
Okay I'm not the biggest computer noob out there, I know I have Ubuntu 8.04, that my laptop is an ASUS M50sv, and that Vista is the worst operating system I've ever seen. Anyway, I've got the brightness applet on my panel, I drag the little thingy up and down and it changes nothing. Right now my brightness is pretty dark...way darker than on Vista, and the function keys aren't working either. I have no idea (with the code provided in Hardy's function key howto thingy) where code should go, he just says "add" and "replace" though I dont really know where...so make sure when you say "replace" or "add" some code...tell me where and if it's somewhere weird that I can't find easily, tell me how to see it.

I already did the NVIDIA graphics driver installation, *pats self on back*. But the darkness of my screen strains my eyes and almost makes me a little nauseous! Don't know why. Anyway, thanks for reading and I hope you can help!

---

### Post by Iago1989 on 2008-04-28
bump?

---

### Post by zecritter on 2008-04-28
Having the same problem, Kubuntu 8.04 & asus m50sv. With or without NVIDIA driver installed. While loading, at some moment brightness visually drop down and never come back.
> almost makes me a little nauseous!
+1. It's just impossible to work.
Any ideas?

---

### Post by Iago1989 on 2008-04-28
I found a solution! I went on #ubuntu on IRC and I got an answer! Go to applications, add/remove, make sure you're searching for ALL applications, find "Displaycalibrater" and tada! You have gamma correction?

---

### Post by Iago1989 on 2008-04-29
Nevermind, it didn't work, it just was dark in my room and felt better. The gamma correction doesn't really fix it. I've tried the "HOWTO" in the tutorial and it doesn't work because my fn keys are mapped differently. He has a program made for up and down, and ALL of my fn keys work except for my brightness keys, and my up/down are stop/playpause.

my brightness keys are f5 and f6

---

### Post by Iago1989 on 2008-04-29
bump!

---

### Post by zecritter on 2008-05-11
solution for hardy ([http://www.linlap.com/wiki/Asus+M50SV):](http://www.linlap.com/wiki/Asus+M50SV):)

$ sudo -s
# echo 0 > /sys/devices/platform/asus_laptop/ls_switch

---

### Post by hotweiss on 2009-01-10
> **zecritter said:**
> solution for hardy ([http://www.linlap.com/wiki/Asus+M50SV):](http://www.linlap.com/wiki/Asus+M50SV):)

$ sudo -s
# echo 0 > /sys/devices/platform/asus_laptop/ls_switch

This is how to make it permanent:

A) Open Terminal (Menu->Accessories), and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

---

### Post by maxitenerife on 2009-10-08
There is an error over there ...

Bad One: echo 0 > /sys/devices/platform/asus-laptop/ls_switch

Good One: echo 0 > /sys/devices/platform/asus_laptop/ls_switch

Over "asus-laptop" you must replace with "asus_laptop"

Only for doin' it permanent in the archive for init.d

Hay un error por ahi ...

El malo: echo 0 > /sys/devices/platform/asus-laptop/ls_switch

El bueno: echo 0 > /sys/devices/platform/asus_laptop/ls_switch

Se debe reemplazar el "asus-laptop" por "asus_laptop" 

El error esta solo en la explicación para hacer los cambios permanentes en init.d

Max

---

### Post by tbedolla on 2010-08-06
> **hotweiss said:**
> This is how to make it permanent:

A) Open Terminal (Menu->Accessories), and type the following:
sudo nano brightness

B) Now paste the following in the Terminal window:
#!/bin/sh
echo 0 > /sys/devices/platform/asus-laptop/ls_switch

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
sudo mv brightness /etc/init.d
and then
sudo chmod 755 /etc/init.d/brightness
and then
sudo update-rc.d brightness defaults 90

E) Reboot, and you will have regained control of your brightness level.

Has anyone had any success with something like this for the ASUS_UL50V? The previously mentioned brightness key fix didn't work for this machine.

Thanks in advance!

---


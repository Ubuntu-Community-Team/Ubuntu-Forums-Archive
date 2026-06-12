---
title: "signal out of ranch change settings 1440x900 , why?"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by oliver74 on 2013-02-10
i have installed Ubuntu and i notice, when i start the computer, always it says signal out of range, change settings 1440x900

i have a desktop pc from hp 2 gb ram and an nvida 6150 on board card. What can i do so that stops? 

thank you):P

---

### Post by kc1di on 2013-02-10
Hello oliver74,

I have a very similar machine and get a very similar error message 
it is caused by grub 2 not being able to use non standard resolutions you can sort of fix it at least you can stop the message from coming up. here how to do it.

open a terminal and type ```
sudo gedit
```
when Gedit come up open /etc/default/grub

scroll down until you find the line that looks like this:
```
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
```

remove the # sign from infront of that line and change the resolution to 1024x768 for now
so it looks like this :
```

GRUB_GFXMODE=1024x768
```

save the file and exit gedit.
Then in a terminal type
```
sudo update-grub
```
when that's done reboot see if the warning is gone.

---

### Post by wildmanne39 on 2013-02-10
+1 for kc1di answer, I had the same issue, it took a long time to find the answer at the time it was a new issue.

---

### Post by kc1di on 2013-02-10
Thanks Wild Man :)

you live in beautiful country there , many moons ago I was stationed an Ft. Bliss in ElPaso ;)

---

### Post by oliver74 on 2013-02-10
can i instead of writing 1024x768 , write in the 1440x900 ? And would it be done too, when i instead install a older grafic driver?

---

### Post by kc1di on 2013-02-10
> **oliver74 said:**
> can i instead of writing 1024x768 , write in the 1440x900 ? And would it be done too, when i instead install a older grafic driver?

no grub will not recognize 1440x900 as it is not in it's list of standard resolutions.  here is a list of resolution grub 2 will recognize.

```
1600x1200,1280x1024,1024x768,800x600,640x480
```

you can select anyone of those, you can also put the word **auto** after the equal sign and grub will select the highest resolution that will work.  Sometimes auto does not work well though. 

What ever resolution you select for grub does not affect the resolution ubuntu will use once booted. it only is use during boot for the grubs screen. 

good luck ;)

---

### Post by oliver74 on 2013-02-11
kc1di, i did sudo gedit and then came that, a warning.


(gedit:2167): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.local/share/recently-used.xbel

what means that?

---

### Post by kc1di on 2013-02-11
Which version of ubuntu are you using?

---

### Post by oliver74 on 2013-02-11
12.04 lts, i was reading in an forum that says ,when you put sudo in front of gedit, then you get that message.

---

### Post by kc1di on 2013-02-11
Never had that happen here but try ```
gksu gedit
``` instead

---

### Post by Mark Phelps on 2013-02-11
If you don't want to struggle with command entries, then install Grub-Customizer.  It will provide screens and menus for doing essentially the same thing.

---

### Post by oliver74 on 2013-02-21
thanks mark

---


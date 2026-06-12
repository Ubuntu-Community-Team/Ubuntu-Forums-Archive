---
title: "[SOLVED] HUGE login text size!"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Anathallo on 2008-08-26
Hi, on a fresh install of Hardy the login text is Massive!
 I found this thread on it, unfortunately I have no idea how to do any of this since I am new to Linux [http://ubuntuforums.org/showthread.php?t=867601&highlight=huge+font]("http://ubuntuforums.org/showthread.php?t=867601&highlight=huge+font")

Help is greatly appreciated.

---

### Post by halitech on 2008-08-26
open a terminal (Applications - Accessories - Terminal) and type in
```
gksu gedit /etc/gdm/gdm.conf
```
then look for the section that says
```
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0

```
after the -audit 0, add
```
-dpi 96
```

reboot and see how that looks

---

### Post by Anathallo on 2008-08-26
Thanks, but that didn't work :(
 Still totally illegible.

---

### Post by halitech on 2008-08-26
did it make any change at all? might just need to up the number or lower it to make a difference

---

### Post by halitech on 2008-08-26
I checked that thread and it linked to another thread that has some ideas. try checking here
[http://ubuntuforums.org/showthread.php?t=786963&highlight=96+dpi](http://ubuntuforums.org/showthread.php?t=786963&highlight=96+dpi)

---

### Post by alienexplorers on 2008-08-26
You could try loading startup manager and using that to set boot text height.

---

### Post by Anathallo on 2008-08-28
> **alienexplorers said:**
> You could try loading startup manager and using that to set boot text height.
How do I do this?


Bumping this topic as I have tried everything in this thread [http://ubuntuforums.org/showthread.p...ghlight=96+dpi](http://ubuntuforums.org/showthread.p...ghlight=96+dpi) and nothing has worked yet. :( Still massive text in login box.

---

### Post by Anathallo on 2008-08-28
Bump :<

---

### Post by halitech on 2008-08-28
look for it Synaptic, I dont use it so not sure exactly what it is called

---

### Post by philinux on 2008-08-28
It's called startupmanager.

Either install via synaptic, the menu item ends up in system>admin

or

sudo apt-get install startupmanager 

from the terminal.

It sets boot up screen res and can modify grub. Excellent little gui.

---

### Post by Anathallo on 2008-08-28
Ok, I installed it. But I am unsure of what setting to change to modify the font.

---

### Post by anotherdisciple on 2008-08-28
This worked for me...

Open a terminal and type:

```
sudo gedit /etc/X11/xorg.conf
```

in Section "Device" add this...

	
```
Option  "DDC" "No"
```

save and log back in

---

### Post by anotherdisciple on 2008-08-28
PS- your terminal is under

Applications--> Accessories--> Terminal

---

### Post by philinux on 2008-08-28
> **Anathallo said:**
> Ok, I installed it. But I am unsure of what setting to change to modify the font.


Look at the Display Resolution setting it's on the first tab that opens when you run SUM.

---

### Post by eggdeng on 2008-08-28
I had this problem on a fresh install using the ati driver. The solution in my case was simply to install the restricted driver.

---

### Post by Anathallo on 2008-08-28
:D I tried both of your ideas so I am not sure which one worked, so thank you both :)

---

### Post by philinux on 2008-08-28
> **Anathallo said:**
> :D I tried both of your ideas so I am not sure which one worked, so thank you both :)

Interesting to know what the display resolution was and what you changed it to.

---

### Post by Danjoh on 2008-08-30
Can't answer for him, but my laptop is 15.4" with resolution 1280x800

What solved it for me was this post:
> **nick_h said:**
> In your /etc/gdm/gdm.conf file you will see a section like the following:
```
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 **-dpi 96**
```

You can add a dpi option here (96 dpi in my example).

That worked for me, so never tried the DDC thingy.
And while looking for a sulution, I've found people who have had the opposite problem (huge screens, and font text of 1 or 2 pixels).

Hope this helps, since this is something wich in my opinion should work correctly on a clean install =)

---


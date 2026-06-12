---
title: "Screen Resolution won't stick"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by orrymr on 2012-04-13
My Ubuntu was working fine up until a few days ago, when it decided to change the screen resolution.
I sort of ignored the problem and just used Windows for a while, but now I need to do some stuff on this partition. I can change the resolution to the correct one for my screen, via NVidia x-server settings, but even if I then go "save to X configuration file", after I log out then log back in, I'm back to the crappy resolution and have to change it again.

Is there any way I can get it to remember what the correct resolution is?

---

### Post by mhgsys on 2012-04-13
I've seen this "problem" way way way before!

[http://ubuntuforums.org/showthread.php?t=1192754](http://ubuntuforums.org/showthread.php?t=1192754)

I bet the same solution still works...

post #2 btw..in that link above

---

### Post by orrymr on 2012-04-13
well, I'm using Unity, so from the dash I just launched "displays", but it doesn't ask me:
It appears that your graphics driver does not support the necessary  extensions to use this tool.  Do you want to use your graphics driver  vendor's tool instead?

Still, no luck

---

### Post by mhgsys on 2012-04-13
hmz, 

does it use a xorg.conf? made by nvidia-settings perhaps?

```
nano /etc/X11/xorg.conf
```

if so you can try to change the resolution there..

you will have to use sudo nano (or any editor you like) to write the file.
and perhaps it would be safest to make a backup of the original /etc/X11/xorg.conf first...
f.e ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorgworking.conf.bak
```

This is the old way of doing this though, atm I'm on 10.04... so I cannot test it before suggesting..
(although this is the way I do it on my 10.04! using 2 screens on nvidia96)

---

### Post by mhgsys on 2012-04-13
Silly oldschool me,

You could also just use 
```
gksudo nvidia-settings
``` and save the config file
so you don't have to edit xorg.conf manually

---

### Post by orrymr on 2012-04-13
Awesome, the gksudo method worked!

I did try it earlier as well, but I made the (really) stupid mistake of leaving the display resolution on auto, rather than the preferred setting before I saved it lol

anyway, thanks for the help, that was becoming quite irritating :)

---

### Post by mhgsys on 2012-04-13
so it's solved now?

---

### Post by orrymr on 2012-04-13
Yes; just marked it as such now :)

---


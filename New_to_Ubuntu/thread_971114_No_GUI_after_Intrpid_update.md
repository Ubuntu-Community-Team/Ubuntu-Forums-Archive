---
title: "No GUI after Intrpid update"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Phoenix CMXIV on 2008-11-04
A few days ago i was running Hardy. every thing fine, and i just updated to Ibex. but, i dont have any GUI. i have tried several things such as:

sudo apt-get update == that downloaded many thing, but no change
sudo envyng -t == couldnt find it or something like that


there are more things ive tried but i just cant remember any of them.

I currently have a Nvidia GeForce 5500, and a 9600GT.

what can i do? thx

---

### Post by Paqman on 2008-11-04
What happens when you run:
```

startx

```

---

### Post by bwhite82 on 2008-11-04
For now use vesa to at least boot into a desktop, then enable your driver in System>Administration>Hardware Drivers.
> 
sudo dpkg-reconfigure xserver-xorg and choose 'vesa' as your video card driver.

---

### Post by Elfy on 2008-11-04
> **Soldierboy said:**
> For now use vesa to at least boot into a desktop, then enable your driver in System>Administration>Hardware Drivers.
 and choose 'vesa' as your video card driver.

Doesn't work anymore, only appears to do keyboard/mouse - progress apparently.

You have to boot to recovery mode and do xfix from the root menu

---

### Post by bwhite82 on 2008-11-04
> **forestpixie said:**
> Doesn't work anymore, only appears to do keyboard/mouse - progress apparently.

You have to boot to recovery mode and do xfix from the root menu

Darn, have been distributing old advice. Thanks for the update.

---

### Post by Phoenix CMXIV on 2008-11-04
> do xfix from the root menu

srry noob here.. please explain?

---

### Post by Elfy on 2008-11-04
lol changed for Hardy afaik :)

---

### Post by Elfy on 2008-11-04
Boot your pc - in your menu list you will have a recovery option - underneath your normal boot option - use that

Load of text will pass and you will end up at a small menu - go down to the xfix option, then when it's finished you can resume from the same menu

It will set the system to use the basic vesa driver.

Better to try paqman's ```
startx
``` first, if it gives you an error - write it down and let us see it.

---

### Post by Phoenix CMXIV on 2008-11-06
Frost Pixie, after i do everyting you said i get:

```
Fatal Error:
No screens Found
Giving up
Connection Refused (errno 111)  unable to connect to X server
No such process (errno 3): Server error
error in locking authority file /home/***/.Xauthority
```

i get thes when i say startx

---

### Post by Phoenix CMXIV on 2008-11-12
Bump

---

### Post by Newbie23 on 2008-11-12
Same problem for me....
Please help....

---


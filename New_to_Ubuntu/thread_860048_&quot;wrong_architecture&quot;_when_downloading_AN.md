---
title: "&quot;wrong architecture&quot; when downloading ANY .deb file"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-07-15
this happens with any deb file I get (I do remember getting around it once but I have NO idea how i did it before) the package manager comes up and says wrong architecture and cant install. This happens with every deb file I find.

If it helps, im following this tutorial on animated backgrounds: [http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/)

im using ubuntu 8.04 ? At least thats what it says when I open firefox.

---

### Post by Elfy on 2008-07-15
Have you got 32bit or 64bit installed.

---

### Post by lazyart on 2008-07-15
yep, it sounds like to you are trying to install a 64 bit package onto a 32 bit system, or vice versa.

Post the output of```
uname -o
``` as well as a link to the .deb you are tryin to install.  Also, have you tried to install this program from Synaptic?  Synaptic will always get the right version for you, and keep it updated...

---

### Post by sharks on 2008-07-15
i think u r trying to install 64 bit on 32 bit system.

---

### Post by Canis familiaris on 2008-07-15
> **lazyart said:**
> yep, it sounds like to you are trying to install a 64 bit package onto a 32 bit system, or vice versa.

Post the output of```
uname -o
``` as well as a link to the .deb you are tryin to install.  Also, have you tried to install this program from Synaptic?  Synaptic will always get the right version for you, and keep it updated...

Shouldn't it be:
uname -m

---

### Post by WinterMadness on 2008-07-15
well i tried downloading quite a bit of different programs, including older ones like air crack to test my wireless security (until i found out how it worked and realized its not so useful in my situation)


unless i manage to somehow find 64 bit versions of everything i dont know. but I tried running that deb file on my other machine with ubuntu and it worked. maybe my package manager is corrupt?

---

### Post by Canis familiaris on 2008-07-15
Could you post the output of:
```
uname -a
```

---


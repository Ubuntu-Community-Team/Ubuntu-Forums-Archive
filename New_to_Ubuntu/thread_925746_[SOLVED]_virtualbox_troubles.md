---
title: "[SOLVED] virtualbox troubles"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-09-21
i installed virtualbox from here
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

i then installed  windows xp onto the virtualbox

but i have a few problems

1. i inserted my usb flash drive thinking it would automatically mount but nothing happend
(do i even have usb support in the virtualbox?)

2. i cant connect to the internet in the virtualbox
(at first i figured it was because i dont have wireless drivers installed, but i even tried just plugging in the ethernet cord and i still cannot connect) 

how does that work anyway? 
(can i use my wirelesss card in ubuntu and the virtualbox at the same time?)


will the virtualbox show up as a seperate machine on my router?

3. i can't get the right resolution settings in the virtualbox
 (i figure because i dont have the graphics driver installed yet)
 
but can i even utilize my graphics card at all from in the virtualbox?

---

### Post by wolfen69 on 2008-09-21
you need to go into the settings and enable usb support. check the network settings in VB also. 

since xp is "borrowing" from your video card, it is pointless to install video drivers.(no 3D)

---

### Post by Therion on 2008-09-21
See if [this tutorial](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html) helps.  It's the one I've used several times and it's always given me a good install.  Maybe it'll help give you some direction... 

Or you might try doing a clean install using the latest version of VB.  The version in the repo (the OSE verison) is not only an older version, it's also the version that does NOT have USB support built in; you want the binary version.  Download [this version](http://www.virtualbox.org/wiki/Downloads) (latest binary)  if you want to go the reinstall route.  Huge update and, since it's the binary version, includes USB device support.

---

### Post by tjwoosta on 2008-09-21
ok i just noticed that there were settings for network and usb in the virtual box manager settings

so i got it all working now except for the resolution


does anybody know how i can get 1280x800 resolution on windows xp in virtualbox?

(im trying to make it so when virtualbox is in fullscreen mode it will take up one full side of my compiz cube)

but it turns out 1280x800 is not even one of the options in the windows xp appearance settings

normally it would just be a matter of drivers but since this is virtualbox i cant figure it out

---


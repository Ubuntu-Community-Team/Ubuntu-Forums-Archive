---
title: "&quot;no signal&quot; after grub"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by robbietea on 2012-04-30
I did a clean install of ubuntu 12.04 on my PC, when I get to the grub and select ubuntu my moniter says no input. Windows still works fine and 11.10 was working fine a few days ago, I guess the problem is drivers for my 6870 GPU, but how can I install them if my monitor wont turn on?

---

### Post by ubudog on 2012-04-30
Hi there, are you able to access the "recovery" option?

---

### Post by robbietea on 2012-04-30
I will just check brb

---

### Post by robbietea on 2012-04-30
*in ubuntu 12.04* 

It worked! Thanks alot, does recovery mode download the drivers automatically, or do I still have to do that?

---

### Post by ubudog on 2012-04-30
Cool -- you'll still have to download the drivers.

Assuming you cannot get to the graphical interface, boot into recovery once more and select the "drop to root shell" option.

Type: 
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.firstbak
```
This will backup your xorg.conf file, in case we mess it up later on.

-- ^^ Do not continue if this fails ^^ --

Then: 
```
apt-get install fglrx
```
This *should* install your graphics drivers.

Once that is completed, type: 
```
reboot
```

And boot normally, into the normal Ubuntu install (not recovery).

Best of luck,
ubudog

---

### Post by robbietea on 2012-04-30
I did all that and it seems to work, but now after grub it says

"input 2 out of range
resolution > 1024 X 768"

I can hear ubuntu loading but I cant see anything

edit I can still use recovery mode

---

### Post by ubudog on 2012-04-30
Weird.

Did you get any errors/warnings upon installing fglrx?

---

### Post by ibbill on 2012-04-30
I had a out of rage on mine also and followed this thread seem to do the trick for me.

[HERE]("http://ubuntuforums.org/showthread.php?t=1969868")

---


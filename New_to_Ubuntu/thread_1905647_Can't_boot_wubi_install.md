---
title: "Can't boot wubi install"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by swatisri on 2012-01-07
i hav installed ubuntu 10.10 on ny windows 7 hp laptop.i have installed ubuntu using wubi.exe . it is installed but my laptop cannot boot ubuntu only a purple screen appears with no icon.I am a new learner plz help me out!!:confused::(

---

### Post by oldos2er on 2012-01-07
Post moved to its own thread.

---

### Post by asifnaz on 2012-01-07
> **swatisri said:**
> i hav installed ubuntu 10.10 on ny windows 7 hp laptop.i have installed ubuntu using wubi.exe . it is installed but my laptop cannot boot ubuntu only a purple screen appears with no icon.I am a new learner plz help me out!!:confused::(

Your specs..? and can you run Live CD..?

---

### Post by swatisri on 2012-01-08
spec:


manufacture: hp
model: HPG62 notebook PC
processor: Intel(R) Core(TM)i3 CPU M380 @ 2.53GHz 
RAM: 3 GB
System type: 64-bit  OS
 

no.i cannot run live CD either..:( :(

---

### Post by oldfred on 2012-01-09
Often a video issue. start with nomodeset, but it may be others:

boot from the cd, press any key at accessibility circle and keyboard (first startup), press F6 and then select the nomodeset option.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---


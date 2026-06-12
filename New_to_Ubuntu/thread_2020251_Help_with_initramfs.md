---
title: "Help with initramfs"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by NTHam on 2012-07-07
Hi All
 
Am new to linux programming/faultfinding so be gentle.
 
When I boot up my 'puter I get "initramfs" and nothing I doo seems to get it to reboot.
 
I have BusyBox v1.13.3 waiting to be used as it asked for help to get a list of commands.
 
Also the kernel is paniced and has kille ini file?
 
SO HELP me before I shoot it (jus kiddn)
 
NTHam

---

### Post by Crafty Kisses on 2012-07-08
Hello,

Try the following 
```
dpkg-reconfigure -phigh -a
```

What kernel are you using?

---

### Post by NTHam on 2012-07-21
Hi 
Sorry for the late reply have put on the back burner till I have some time.
 
OK typed in what you said and I get : dpkg-reconfigure: not found
 
I'm not sure what kenel I'm using but I am using ubuntu 10.4

---


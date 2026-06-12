---
title: "[SOLVED] how to install an .inf file?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by eatingganesh on 2008-10-24
I'm trying to get my wireless to work. The directions have gotten me to the point where I have extracted the inf and sys files from the original windows exe install. The instructions now say: > Install with lswlusb.inf. I just have absolutely no idea how to do this.... I have the lswlusb file on my desktop, but just don't know what to do next. Any guidance would be very much appreciated!

---

### Post by marko_4454 on 2008-10-24
You need to use ndiswrapper. 
Follow this link: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing%20Windows%20driver](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing%20Windows%20driver)

---

### Post by Crandom on 2008-10-24
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Assuming you already installed ndiswrapper, type this into the commandline:
```
sudo ndiswrapper -i lswlusb.inf
sudo depmod -a
sudo modprobe ndiswrapper
```

---

### Post by eatingganesh on 2008-10-24
Now I get this :

sudo ndiswrapper -i netusb.inf
couldn't open netusb.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

ps. turns out the correct driver version for my setup is netusb, rather than lswlusb...

---

### Post by Duck2006 on 2008-10-24
Did you cd to where the file is?
ie cd ~/Desktop

---

### Post by eatingganesh on 2008-10-24
thanks! I finally got it to load up and recognize the wireless through ndiswrapper and that handy ndgtk gui. Still could not get the wireless to work however. I'll have to try on another day when I have several hours to kill.

---


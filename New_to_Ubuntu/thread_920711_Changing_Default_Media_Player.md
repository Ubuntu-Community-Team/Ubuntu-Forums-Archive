---
title: "Changing Default Media Player"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by WilhelmGGW on 2008-09-15
I have looked and looked for a solution that works for me. Let me try asking here.

I watch a lot of movies on DVD. When I put in a disk, the Totem Movie Player loads and tries to play it. I don't want to use this as my default media player.  I want LinDVD -- also loaded on my machine -- to start to play the DVD.  By default.

How do I change my settings to make this happen?  Thanks.

---

### Post by drs305 on 2008-09-15
System, Preferences, Preferred Applications, Multimedia should do it. Totem is the default there but you should be able to switch it to your preferred application.

---

### Post by philinux on 2008-09-15
Should is the word. Not so easy in Hardy I'm afraid. Lets hope this "bug" gets fixed in Intrepid.
One way..
[http://ph.ubuntuforums.com/showthread.php?p=4813975](http://ph.ubuntuforums.com/showthread.php?p=4813975)

---

### Post by Jake90 on 2008-09-15
> **drs305 said:**
> System, Preferences, Preferred Applications, Multimedia should do it. Totem is the default there but you should be able to switch it to your preferred application.

true, but you have to click custom and enter the command to linDVD when prompted, a command which I do not know. Although it is very possibly linDVD

---

### Post by WilhelmGGW on 2008-09-15
> **philinux said:**
> Should is the word. Not so easy in Hardy I'm afraid. Lets hope this "bug" gets fixed in Intrepid.
One way..
[http://ph.ubuntuforums.com/showthread.php?p=4813975](http://ph.ubuntuforums.com/showthread.php?p=4813975)

With this, I don't want to use VLC. Rather LinDVD. Do I just replace "vlc" with "lindvd" in the instructions here?

---

### Post by philinux on 2008-09-15
Yes.

---

### Post by promodus on 2008-10-05
This worked for me

```
sudo apt-get install vlc
```

```
sudo dpkg --purge totem-plugins totem-mozilla totem-gstreamer totem-common totem
```

---


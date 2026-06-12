---
title: "Password appears as big, filled circles"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by dmaitra on 2008-05-03
I upgraded from Feisty (7.04) to Hardy (8.04) recently. Suddenly I find that whenever I type my password somewhere (login screen or inside Firefox), every letter appears as big, black circles. This is not really a problem, but the old stars/asterisks (*) were more aesthetically pleasing to me. Is there a way I can change how the password letters appear ? :(

Thanks,
dmaitra

---

### Post by drsox1899 on 2008-05-03
X

---

### Post by dmaitra on 2008-05-03
> **drsox1899 said:**
> X

???

---

### Post by raydeen on 2008-05-03
> **dmaitra said:**
> ???

That's usually a video driver/resolution problem. Gnome has done that to me a few times as well. Check out your screen and or monitor resolutions when you get onto the desktop. I've solved the problem in the past by going into /etc/X11/ and looking at the different xorg-conf files and checking their dates. If you can remember about when it happened, you can try copying an old xorg-conf file (one from before the start of the video issue) over top of your existing one, or editing your existing file to match the old. It's a good idea to back the file up first

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back-20080503 
```

You can call the backup file whatever you want as long as it's meaningful to you. That way if modifying/copying really borks things, you can copy it back.

```
 sudo cp /etc/X11/xorg.conf.back-20080503 /etc/X11/xorg.conf 
```

---

### Post by lazyart on 2008-05-03
ubuntu has a setting in System>Login Window that lets you choose circles or asterisks.  Poke around and you might see something similar for KDE.

---

### Post by mlentink on 2008-05-03
You might want to look at this: [http://ubuntuforums.org/showthread.php?p=3609621](http://ubuntuforums.org/showthread.php?p=3609621)

---


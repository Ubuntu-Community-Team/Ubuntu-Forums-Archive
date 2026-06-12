---
title: "Adding screen resolutions"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by mglover3177 on 2008-06-18
Hello,

Im a new Ubuntu user and I am accessing an Ubuntu system through VNC. There is no montor attached to it and now it only gives me the 800 x 600 screen resolution. I need to add more but I honestly do not know where to begin or to look. I was hoping to be able to do this through Terminal as that is how I want to learn more about the software. I hope some one can help. 

regards,
Matthew

---

### Post by mglover3177 on 2008-06-18
Bump

---

### Post by OldTimeTech on 2008-06-18
Check this out....should have your answers:

[http://ubuntuforums.org/showthread.php?t=832000&highlight=screen+resolutions](http://ubuntuforums.org/showthread.php?t=832000&highlight=screen+resolutions)

---

### Post by BDNiner on 2008-06-18
```

sudo dpkg-reconfigure xserver-xorg 

```

will reconfigure your graphics card and monitor so that the correct defaults are properly detected.

---

### Post by mglover3177 on 2008-06-18
Sorry I might not have been to clear. I am using VNC to connect to the Ubuntu so there is no monitor directly connected. But I am trying to add the resolutions. That information was great btw but there was a lot of it that was invalid for what I am doing. There is no subSection Display, and I can not edit the /ect/X11/xorg.conf file for some reason...I am the admin on the box so I do not see why I can not. I tried through both Term and GUI.

---

### Post by azurepancake on 2008-06-18
> **mglover3177 said:**
> Sorry I might not have been to clear. I am using VNC to connect to the Ubuntu so there is no monitor directly connected. But I am trying to add the resolutions. That information was great btw but there was a lot of it that was invalid for what I am doing. There is no subSection Display, and I can not edit the /ect/X11/xorg.conf file for some reason...I am the admin on the box so I do not see why I can not. I tried through both Term and GUI.

In terminal, you'll have to use the "sudo" command, which gives you "super user" rights. Since your not logged in as root, you normally cannot edit files owned by root. So to edit your xorg.conf file, type the following into a terminal session:

```

sudo gedit /etc/X11/xorg.conf

```

You will be prompted for your password, Gedit should appear with the xorg.conf file loaded. Add the changes then save and exit.

---


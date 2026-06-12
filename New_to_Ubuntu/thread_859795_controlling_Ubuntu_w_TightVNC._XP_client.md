---
title: "controlling Ubuntu w TightVNC. XP client"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by blmjr on 2008-07-14
I have an XP machine that I'd like to use to control my brand new Ubuntu machine via TightVNC.

I have TightVNC installed on both machines, but don't know where to go from here. The TightVNC website has some very short instructions on how to get TVNC server running, which I believe I've done, but the XP machine can't see it.

Does anyone know of a simple step by step guide (that leaves no small step out) that could guide me through this process? 

Many, many thanks,

blmjr

---

### Post by jbrown96 on 2008-07-15
the most likely problem is that the port that tightVNC uses is closed on the Ubuntu box. If you know the port number you can fix it with ```
sudo ufw allow tcp port#
```. VNC uses ports in the 59xx range. I'm not sure exactly how it works, but I believe the first connection that is established uses 5900, then 5901, etc. Try opening 5900 and see if that works

You can also test it with ```
sudo ufw disable
``` but you should have a firewall enabled, so that should only be for testing purposes.

---

### Post by juanoleso on 2008-07-15
I used this tutorial to setup an SSH tunnel to my home computer through my firewall and then use tightVNC to control the desktop:

[[COLOR="Blue"]HOWTO: VNC over SSH using Public/Private keys From Windows[/COLOR]]("http://ubuntuforums.org/showthread.php?t=383053")

Its not exactly a tutorial about just TightVNC, but it might help to get you where you are going.

---

### Post by cariboo on 2008-07-15
Tightvnc will work with the builtin remote desktop software already installed in Hardy. Go to System-->Preferences-->Remote Desktop and enable the remote server. Select what options you need and you are set. I'm not near any computers with hardy installed at the moment, but try using the ip address of your Ubuntu computer. Tightvnc may need the port number, it normaly uses port 5901 to listen for a vnc connection.

Jim

---

### Post by blmjr on 2008-07-18
Thank you so much for the kind advice. I'm a novice in Ubuntu and see things from an XP perspective. 

Very good to learn new things. 

Thanks for the help!

b

---


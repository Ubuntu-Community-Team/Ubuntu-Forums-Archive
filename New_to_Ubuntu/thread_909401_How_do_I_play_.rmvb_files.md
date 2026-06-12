---
title: "How do I play .rmvb files?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by zzzonked on 2008-09-03
How do I play .rmvb media files? And do I get the program from add/remove or synaptic? Thanks.

---

### Post by jerome1232 on 2008-09-03
Try real player? since those are real player formats.

I stumbled on this maybe it'll help
[http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)

---

### Post by wolfen69 on 2008-09-03
[www.real.com/linux](www.real.com/linux)

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

  ```
chmod 770 RealPlayer11GOLD.bin
```
  ```
sudo ./RealPlayer11GOLD.bin
```
  

Use the following default installation directory during the installation:

  /opt/real/RealPlayer

The installer will copy the files and create menu shortcuts. Then run the following commands.

  ```
cd /usr/lib/firefox-addons/plugins
```
  ```
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
```
  ```
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
```
  ```
sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.

```
Open Firefox and type about:plugins in the address bar. Scroll down and look for the following entry.

  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
  File name: /opt/real/RealPlayer/mozilla/nphelix.so
  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

---

### Post by Ryadt on 2008-09-03
I'm pretty sure GNOME mplayer plays them.
Just follow this guide on how to play them with mplayer:
[http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)

---

### Post by lakris61 on 2008-09-03
Hi, 
I think **xine** would do the trick. I've messed about with trying to get mplayer and others to work with this and other formats, and RealPlayer is a real PITA. Xine even does mp4 better than QuickTime. I warmly recommend **xine**.

/Lakris

---


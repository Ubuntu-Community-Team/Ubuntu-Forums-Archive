---
title: "Mouse trouble in xubuntu 12.04, xfce DE"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by mlnease on 2013-12-26
Hello,  I was tinkering with my xfce desktop settings (on another partition) and found that it wasn't correctly recognizing my mouse (which was, however, working, though not perfectly).  In mouse settings, I unwisely unchecked the box reading 'Enable this device'--and, hey presto!  No cursor, no mouse.  Tried rebooting and rebooting in recovery mode, still no mouse.  Can anyone please tell me how I can re-enable the mouse without being able to use the mouse?    
Thanks in advance.    

By the way--if anyone's wondering, xubuntu 12.04 with xfce is brilliant, in my opinion.  Thanks, devs!

I'm assuming that there's a configuration file I can access from my other partition/OS and edit with gedit.  Can someone tell me how to locate that file?  Thanks again in advance.

---

### Post by Toz on 2013-12-26
Before you login in, go to the first console (Ctrl+Alt+F1) and log in to the text console. The file you are looking for is ~/.config/xfce4/xfconf/xfce-perchannel-xml/pointers.xml. You can either delete the file (it will be recreated on login and all mouse/touchpad settings reset to default) or edit the file:
```
nano ~/.config/xfce4/xfconf/xfce-perchannel-xml/pointers.xml
```
...and change the "Device Enabled" value (if one exists).

Ctrl+Alt+F7 to return to the gui console.

---

### Post by mlnease on 2013-12-27
Thanks, Toz--exactly what I needed.

---


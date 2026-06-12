---
title: "White screen after logging in"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2008-10-11
Hello - 
I just installed Ubuntu on my desktop pc.  I ran the automatic updater and then selected the ATI graphics driver (I've had Ubuntu on this computer in the past and this driver has worked for me).  When I rebooted, the login screen showed up but after logging in all I have is a white screen with a cursor.

Any ideas what is causing this?  Fixes?  Thanks

---

### Post by jbrown96 on 2008-10-11
Could you give some info on the specific graphics card? What version of Ubuntu(8.10 is not supported by ATI yet)? Try to get back to a working X session by doing the following.
1. Restart and don't login.
2. Press Ctrl+Alt+F1
3. You should now be at a console login. Login
4. Backup your xorg.conf file ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```
5. Edit the file, using your preferred text editor. You should check out some manuals because they can be daunting. I will provide some directions for Vi. Open the file ```
sudo vi /etc/X11.xorg.conf
``` Use the cursor to find a section about your graphics card; the line should be "driver "fglrx"". You need to change "fglrx" to "vesa". Move the cursor to the f and press x until there are it looks like this > driver    "". Move the cursor to the second quote, and press i. Type mesa and make sure that it is inside the quotes. Press Esc and then :x The program should exit and save. Type exit to logout and Crtl+Alt+F7 to go back to graphics. Press Crtl+Alt+Bkspace to reastart X, and try logging in. I would recommend using the drivers from Ati's website. You can download them, and just run it in a terminal with Sudo before and you should be fine.

---


---
title: "Howto Kubuntu-Lite"
date: 2006-10-10
forum: Outdated Tutorials &amp; Tips
---

### Post by duality on 2006-10-10
Heres what it looks like:
[http://img296.imageshack.us/my.php?image=snapshotba0.png](http://img296.imageshack.us/my.php?image=snapshotba0.png)

Boot process:
*normal boot
*terminal login
*startx on successfull login


Heres how to do it:
1.(K)ubuntu server installation (only need the base system)
1.5. update, fix network, install graphics driver, etc..
2. Apt-get these packages: xserver-xorg xfonts-base kwin konsole kdesktop
3. Create a file called "xinitrc" : sudo nano ~/.xinitrc
paste this into it:
------------------------------------------------
#!/bin/sh

kdesktop &
kwin &
xclock -geometry 50x50-1+1 &
konsole -geometry 800x400-280+500 &
konsole -geometry 800x400-280+20
------------------------------------------------

(Note) this layout if for 1280x1024, you might want to play around with the geometry to make it look nice on other display resolutions.

4. Open ".bash_profile" (located in your home directory) with nano or your favorite editor, and insert this at the end of the file.
------------------------------------------------
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
startx
fi
------------------------------------------------
5. Now it's complete, just reboot and start installing software,, you can now start everything from the command line and/or create desktop shortcuts.




n0n4m3-

---


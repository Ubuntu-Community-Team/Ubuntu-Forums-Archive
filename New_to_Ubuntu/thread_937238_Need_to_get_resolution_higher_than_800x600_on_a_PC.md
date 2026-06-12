---
title: "Need to get resolution higher than 800x600 on a PC that has no monitor"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by diablo75 on 2008-10-03
I am currently working on a PC via VNC.  It does not have a monitor attached right now, so running "sudo dpkg-reconfigure xserver-xorg" only gets it up to 800x600.

This computer will be going to someone else, and it's hard to say exactly what kind of monitor he is going to attach to the computer or what resolution it will be capable of displaying.  My main concern is:  Do I need to bother setting this to a higher resolution manually, or will it be able to detect the monitor and add in the appropriate resolutions automatically?

---

### Post by Kellemora on 2008-10-03
Hi Diablo

I use a KVM switch with a different monitor thats not even listed anywhere.

But by checking that the video card was correct in Screens & Graphics, and selecting Plug n Play before pulling the plug and hooking up the KVM, all has gone well with all of these wierd old monitors I have around here.

If you don't see Screens & Graphics under Applications tab, Other, right click on Applications and select Edit Menu's to add it to your drop down list.

TTUL
Gary

---

### Post by Jose Catre-Vandis on 2008-10-03
Alternately, connect up a decent monitor then reconfigure to get higher resolutions. You can then set a better resolution in your vnc parameters

---


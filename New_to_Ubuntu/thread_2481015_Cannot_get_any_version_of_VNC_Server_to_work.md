---
title: "Cannot get any version of VNC Server to work"
date: 2022-11-16
forum: New to Ubuntu
---

### Post by e298f622 on 2022-11-16
Trying to get a server going.  I cant get any version of VNC to work.  ive reinstalled Linux 5 times today.

Working on a fresh download of Linux from this website.  Version 20.04 LTS.

I cant get any version of a VNC server to work.  Ive tried tightvnc, tigervnc, openvnc, realvnc, and I am sure others.  None work.

I need someone that is willing to walk a non-idiot through how to get -any- VNC server working so I can run this machine headless.

Please help me work out a solution.

---

### Post by Skaperen on 2022-11-16
will a text console suffice or do you need graphical?

---

### Post by e298f622 on 2022-11-16
Graphical will be required.  I am the most savvy with these types of things and I am struggling.  This machine will be rarely reconfigured, but when it needs it I need to give everyone all the help they can get.

Everytime I do fresh install of ubuntu ive noticed that the gui version of x11vnc works (slowly) until I try to do something like schedule it to start on its own then I cannot get anything going.

Feel free to point me to a tutorial that will work (it wont) but atleast then when I have problems maybe I can get some help?

---

### Post by TheFu on 2022-11-16
I stopped using VNC about a decade ago after discovering NX.  

'x2go' is the best F/LOSS implementation I've found. Last time I checked, it was 2-3x faster than VNC.  It uses the same ssh connection we already need for 99% of remote stuff, so no extra security or ports are needed.  Existing ssh-keys will be used.

No remote destkop works well (at all?) with Gnome 3+ or KDE.  Use a lighter DE.

---


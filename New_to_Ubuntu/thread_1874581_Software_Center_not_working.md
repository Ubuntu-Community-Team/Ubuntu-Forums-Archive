---
title: "Software Center not working"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by TravCurrie on 2011-11-03
Hi 
  
I’m recently new to Ubuntu and I am running Ubuntu 11.04. 

I installed Sweet Home 3D from the software center, when I tried to run Sweet Home 3D it would not start up. Upon investigating this I found I needed to install sun-java6-bin which I did via the Software Center. Sweet Home 3D would then run, but it would crash when I tried to add walls or rooms to a drawing. I found that I needed to setup my graphics card properly. I followed instructions #2 through to #4 on this post [http://ubuntuforums.org/showthread.php?t=1724456](http://ubuntuforums.org/showthread.php?t=1724456) and restarted my laptop. Sweet Home 3D is now running perfectly, but Software Center no longer starts and I get a NO_PUBKEY error: NO_PUBKEY 4F191A5A8844C542
  
Please could someone help me with this.

---

### Post by Frogs Hair on 2011-11-03
Hello and Welcome

Open software sources > authentication and the PUB KEY can be added  . When I searched for information about this key , which came up many times it was associated with older releases and different programs .

I could not find out if the key was still valid and it does not appear on my 11.10 key list .

---

### Post by TravCurrie on 2011-11-04
Thanks for the help, I managed to get the key it was a network access problem on our network. After I got the key I did the following:

sudo apt-get update
sudo apt-get dist-upgrade

and then I restarted my computer, but Software Center still does not start up :(

---

### Post by Frogs Hair on 2011-11-04
Do a forum search because this problem has come up before . I know if the software center is having problems getting a good internet connection it won't open . It is possible to change the down load server in Update Manager > Settings > Download From .

---

### Post by themissinglinka on 2011-11-04
hey, im new too. i've put the new plazma kde on and am trying to install kdenlive from the software centre and i think i've struck the same problem. i cant install updates either. i took yr advise frog dude and checked my server and authentication certs. I dont think i could find the one needed. where do i get that PUB key from. i was downloading from sourceforge (raz) but im too green and dont think i can call myself a SUDO yet. is it a problem on the other end with ubuntus server:mrgreen:?

---

### Post by Frogs Hair on 2011-11-04
Try starting the software center from the terminal and check for errors that may help in discovering the problem .```
software-center
```

---

### Post by themissinglinka on 2011-11-04
jbone@jbone-cq60:~$ software-center
2011-11-05 13:35:23,030 - softwarecenter.ui.gtk3.em - INFO - EM's: 18 14 21
2011-11-05 13:35:25,435 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-11-05 13:35:25,611 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for raleigh Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2011-11-05 13:35:41,325 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0

(software-center:2970): Gdk-WARNING **: /build/buildd/gtk+3.0-3.2.0/./gdk/x11/gdkwindow-x11.c:4766 drawable is not a native X11 window

(software-center:2970): Gdk-WARNING **: /build/buildd/gtk+3.0-3.2.0/./gdk/x11/gdkwindow-x11.c:4766 drawable is not a native X11 window

(software-center:2970): Gdk-WARNING **: /build/buildd/gtk+3.0-3.2.0/./gdk/x11/gdkwindow-x11.c:4766 drawable is not a native X11 window
2011-11-05 13:36:09,111 - softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.56'}): org.debian.apt.install-or-remove-packages

im thinking kde isnt letting x11(the new kubuntu) open up compatable windows to walk me through the install?:mrgreen:

---

### Post by TravCurrie on 2011-11-05
I get this when I try run Software center from the terminal

travisc@Travis:~$ software-center
Segmentation fault

I'm doing some investigating on it now.

---

### Post by TravCurrie on 2011-11-07
I found a work around to the segmentation error here:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219)

The work around is not working for me. Below is the code and output I get when I use the work around. 

travisc@Travis:~$ LD_PRELOAD=/usr/lib/libstdc++.so.6 software-center
ERROR: ld.so: object '/usr/lib/libstdc++.so.6' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libstdc++.so.6' from LD_PRELOAD cannot be preloaded: ignored.
Segmentation fault

---

### Post by themissinglinka on 2011-11-08
hey guys, i did a complete re-install, and downloaded the updates etc afterwards, ill install KDE abit later and see if i get the same result. thanks for the intel

---


---
title: "[SOLVED] The panel encountered a problem"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by wawadave on 2008-09-12
The panel encountered a problem while loading
OAFIID:Gnome mixerapplet

do you want to delete the applet from your configuration?

got this while loading amarok.

what the best thing to do with this?
amorok loaded and worked any how.
i still have that message popup

---

### Post by wolfen69 on 2008-09-12
completely remove gnome-applets. then:
```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
```then reinstall gnome-applets.

---

### Post by wawadave on 2008-09-12
i did the above:
 sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswfdec-0.6-90 libboost-thread1.34.1 libaccess-bridge-java
  libboost-date-time1.34.1 libdvbpsi4 libxosd2 libvlc0 vlc-nox tzdata-java
  libiso9660-5 vlc rhino vlc-plugin-pulse libtar libvcdinfo0
The following packages will be REMOVED:
  libaccess-bridge-java libboost-date-time1.34.1 libboost-thread1.34.1
  libdvbpsi4 libiso9660-5 libswfdec-0.6-90 libtar libvcdinfo0 libvlc0 libxosd2
  rhino tzdata-java vlc vlc-nox vlc-plugin-pulse
0 upgraded, 0 newly installed, 15 to remove and 0 not upgraded.
After this operation, 24.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 304108 files and directories currently installed.)
Removing libaccess-bridge-java ...
Removing libboost-date-time1.34.1 ...
Removing libboost-thread1.34.1 ...
Removing vlc ...
Removing vlc-plugin-pulse ...
Removing vlc-nox ...
Removing libvlc0 ...
Removing libdvbpsi4 ...
Removing libvcdinfo0 ...
Removing libiso9660-5 ...
Removing libswfdec-0.6-90 ...
Removing libtar ...
Removing libxosd2 ...
Removing rhino ...
Removing tzdata-java ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

i hope i was not still needing those?




gnome-applets  ok how and where do i reinstall that?

looked in synaptic and see gnome-applets listed that as installed.

---

### Post by wawadave on 2008-09-12
ok i remove the gnome-applet from synaptic. restarted amarok the mesage did not come up. just hope nothing else broke doing this.

---

### Post by SunnyRabbiera on 2008-09-12
> **wawadave said:**
> ok i remove the gnome-applet from synaptic. restarted amarok the mesage did not come up. just hope nothing else broke doing this.

actually the advise wolfen69 was a bad call, you could have simply just told it not to reload.
but thats command line guru's for you, some of them would use a bulldozer to find a china cup.

---

### Post by wawadave on 2008-09-12
ok thanks for that.
 i try not to use sledge hammer for thumb tacks.

but it did get it solved.

odd thing is this allso solve my problem i had viewing youtue!!!

---


---
title: "Problem installing Pidgin on Langolier"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by Perkyandproud on 2012-12-08
Hello, I'm very new to this!

I recently upgraded my preinstalled Linux to Release 12.04 (precise) 32-bit, Kernel Linux 3.2.0-34-generic, GNOME 3.4.2

In the previous three versions I used Pidgin and loved it.  Unlike most of my other programs however it did not follow me this time.  When I went to install it from my Ubuntu Software Center, I got the following message:

Package dependencies cannot be resolved
The following packages have unmet dependencies:

pidgin: Depends: perlapi-5.14.2 but it is a virtual package

Your help would be much appreciated!

---

### Post by LADmaticCA on 2012-12-08
Try running in a terminal 

```
sudo apt-get install -f
```

to resolve the dependencies.

---

### Post by Perkyandproud on 2012-12-08
> **LADmaticCA said:**
> Try running in a terminal 

```
sudo apt-get install -f
```to resolve the dependencies.

I tried that and got the following:

oem@freekbox:~$ sudo apt-get install -f
[sudo] password for oem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  freegeek-logo libunity6 libglew1.5 libglewmx1.5 pidgin-data
  telepathy-indicator libtelepathy-farstream2 libdee-1.0-1 telepathy-logger
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
oem@freekbox:~$ 

Tried to install Pidgin again, got the same error.

---

### Post by Perkyandproud on 2012-12-13
> **Perkyandproud said:**
> Hello, I'm very new to this!

I recently upgraded my preinstalled Linux to Release 12.04 (precise) 32-bit, Kernel Linux 3.2.0-34-generic, GNOME 3.4.2

In the previous three versions I used Pidgin and loved it.  Unlike most of my other programs however it did not follow me this time.  When I went to install it from my Ubuntu Software Center, I got the following message:

Package dependencies cannot be resolved
The following packages have unmet dependencies:

pidgin: Depends: perlapi-5.14.2 but it is a virtual package

Your help would be much appreciated!

This has not yet been resolved.  Any other suggestions?

---

### Post by Perkyandproud on 2012-12-13
> **LADmaticCA said:**
> Try running in a terminal 

```
sudo apt-get install -f
```to resolve the dependencies.

Tried it again, got:

oem@freekbox:~$ sudo apt-get install -f
[sudo] password for oem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ubuntuone-control-panel ubuntuone-control-panel-common
  ubuntuone-control-panel-gtk freegeek-logo libunity6 libgtkspell-3-0
  python-dirspec libraw5 gir1.2-ubuntuoneui-3.0 libglew1.5 libgexiv2-1
  python-ubuntuone-control-panel libglewmx1.5 libvncserver0
  ubuntuone-control-panel-qt pidgin-data telepathy-indicator libgtk-vnc-2.0-0
  duplicity libgwibber-gtk2 telepathy-haze libubuntuoneui-3.0-1 libgwibber2
  libtelepathy-farstream2 libfreerdp-plugins-standard libdee-1.0-1
  telepathy-logger gir1.2-gnomebluetooth-1.0 libfreerdp1 librsync1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
oem@freekbox:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by mastablasta on 2012-12-13
so what happens when you try to install pidgin (output)?

---

### Post by Perkyandproud on 2012-12-14
> **mastablasta said:**
> so what happens when you try to install pidgin (output)?

Same exact message when I tried it again.

...then I updated to 12.10, hoping that would solve the problem.  Except apparently my graphics card is too slow and my computer is unusable.  My CD/DVD drive isn't working and I can't even boot from a USB in order to go back to 11.10 which is the last update that worked right.  :(

---

### Post by mastablasta on 2012-12-14
booting form USB has nothing to do with operating system as boot is handled by BIOS not OS.
 
anyway the porpper action would be to purge the previous pidgin install and then try to install it again. not sure why it has not "followed you", but it should.

---

### Post by Perkyandproud on 2012-12-14
> **mastablasta said:**
> booting form USB has nothing to do with operating system as boot is handled by BIOS not OS.
 
anyway the porpper action would be to purge the previous pidgin install and then try to install it again. not sure why it has not "followed you", but it should.

Really?  How does one purge an install? 

I'm really new, so I've been using Update Manager to do my updates and upgrades.

---


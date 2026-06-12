---
title: "Removing gwibber"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by vasa1 on 2011-11-22
```
aes@aes-Inspiron-1545:~$ sudo apt-get purge gwibber
[sudo] password for aes: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gstreamer-0.10 libgtkspell3-0 libseed-gtk3-0 libgwibber-gtk2 libgwibber2 gnome-js-common libglademm-2.4-1c2a
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gwibber* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1,315 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
aes@aes-Inspiron-1545:~$
```

I don't need blogging software so I thought I'd remove gwibber but I backed off when I saw **ubuntu-desktop** listed to be "REMOVED". How do I learn what the function of ubuntu-desktop is? And why is it tied to gwibber?

---

### Post by audiomick on 2011-11-22
This is what synaptic package manager says about it
> This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.I believe it is what is called a meta  package. It contains nothing of itself, but has dependancies to everything that is included in the desktop environment (or whatever the meta-package in question pertains to).

There are some things that are very difficult or even impossible to remove, as they are so bound up in the desktop environment. It is possible that gwibber is on of these, though I can't say this for sure.

Easiest thing would be to just forget it is there. I don't think it leaving it on the computer will cause you any grief.

---

### Post by vasa1 on 2011-11-22
> **audiomick said:**
> ...
Easiest thing would be to just forget it is there. I don't think it leaving it on the computer will cause you any grief.

Thanks, mick. My thoughts as well. Will mark this as [Solved]

---

### Post by vasa1 on 2012-07-17
A belated follow-up ... Uninstalling gwibber in 12.04 doesn't threaten to take down ubuntu-desktop as well.

---


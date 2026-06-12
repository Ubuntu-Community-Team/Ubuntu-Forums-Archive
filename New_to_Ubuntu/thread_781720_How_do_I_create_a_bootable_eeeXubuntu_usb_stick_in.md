---
title: "How do I create a bootable eeeXubuntu usb stick in windows?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by wolvish on 2008-05-04
Hi, I'm fairly new to linux, in the sense that I've used ubuntu for a while, but am mainly familiar with the GUI aspect, and have not delved very far into the filesystem and advance config settings, however, using a friends Kubuntu PC I managed to create a bootable usb drive to install eeeXubuntu on my eeePC (701). However, I then decided to upgrade to Hardy and go on to switch to KDE4. Installed via synaptic, went on to perform 

```
dpkg-reconfigure kdm-kde4
```

to switch from gdm, assuming that that would provide added performance. When kde4 booted, wifi was unavailable. Went on to attempt install of  kdebase-workspace-dbg as that was offered as a solution on a wiki. This promptly filled my little 4GB drive, leaving absolutely no space. This had previously forced me to go on a widespread cleanup mission in order to install a different package, and caused no end of irritation, so I went about that again right away. In the process, uninstalled a package which apparently had some dependencies. (also attempted to modify several files within /etc/X11/). Decided to use aptitude to uninstall/reinstall both kdm-kde4 and all associated files, along with xserver-xorg. Now, as far as my abilities are concerned, eeePC is bricked. Long story short, I'm in a house with my eeePC, 2 Windows machines, no blank CD's to create a live cd, and several flash drives, sizes are sufficient as I used one of them before (reformatted later...) So, if someone can tell me either how to create a new bootable flash drive using only windows, or how to reverse the damage done to my eeePC, either of those would help.

(yes, I know, each and every one of these steps was most likely the wrong one.)

---

### Post by TheBulgarian on 2008-05-05
[Click here ]("http://www.pendrivelinux.com/category/new-usb-linux-tutorials/")
Also u can try to WUBI and then make bootable USB stick.Link to wubi [: Click Here]("http://wubi-installer.org/")

---


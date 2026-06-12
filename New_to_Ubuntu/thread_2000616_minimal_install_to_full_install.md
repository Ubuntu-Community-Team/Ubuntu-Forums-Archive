---
title: "minimal install to full install"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by killer62491 on 2012-06-09
is there a way to get from a minimal install to a full GUI enabled one? i finally got my laptop to boot my minimal install USB and set it up, but now I can't figure out how to install/enable the GUI stuff as is normal... it will let me run all the normal commands, but when i have no 'net connection, it wont let me boot into the linux partition fully, it keeps saying "waiting for network configuration". help is, as always, much appreciated! 
Regards, 
<::ALPHA::HECTOR::SIERRA::>

---

### Post by killer62491 on 2012-06-09
now that i think about it, should this be moved to installation/upgrades section? just wondering...

---

### Post by Paqman on 2012-06-09
Are you trying to connect via wifi? If so you may need to install a proprietary driver to get it up first.

The quickest and easiest solution may be to simply plug straight into your router. Once you've got a wired connection it is possible to get your wifi driver installed from the command line using [jockey-text]("http://askubuntu.com/questions/6521/how-can-i-reconfigure-the-nvidia-proprietary-drivers-from-the-command-line-ssh").

To get the GUI desktop install the package [ubuntu-desktop]("apt:ubuntu-desktop") and reboot.

---

### Post by killer62491 on 2012-06-09
i'm already using a wired connection, so i guess i just need to install ubuntu-desktop, and just found same thing in a different post, but thanks, and it was you who said to do this action in the other post, only it was lubuntu-desktop involved in it :P i didnt think i'd get a reply this fast though, so thanks

---

### Post by Paqman on 2012-06-09
No, you don't need to install any of the desktop metapackages just to get a connection. Are you sure the network adapter is switched on (check BIOS and/or hotkeys)?

Can you post the output of these commands:
```
lspci
```
```
ifconfig
```

---

### Post by killer62491 on 2012-06-09
what i meant is that it only lets me do stuff when its connected after boot, my bad. i worded that wrong. haha, it's been a long day for me... sorry. installing ubuntu-desktop as i type this, with my laptop in my lap and my desktop in front of me as it were :P thanks though. its just finished dl'ing the stuff, now unpacking/installing them :D

---

### Post by killer62491 on 2012-06-09
ok uhhhhhh... it finished installing the ubuntu-desktop metapackage, then apparently crashed..... i have no clue why, it just shut off on me, no error message displayed before it did though. any idea as to why it would do this? also, i booted it back up, it let me log in via text only mode, and now X is only showing a black screen with a terminal section/a mouse indicator, which does move when i use the mousepad...
[edit:] i think i got it figured out, i must have somehow broken dpkg.... i tried to install firefox and i got a message saying to reconfigure it, then try again. i forget what exactly the message was though.
 
[edit:] now its saying my whole hdd is a read only filesystem after i ran the mentioned reconfigure command from the message. i tried to remove this attribute of the filesystem, no luck. ill try again in the morning. im too tired right now...

---

### Post by killer62491 on 2012-06-10
ok i'm back, and still no luk with getting my laptop fixed (again) after what happened last night... my hard drive is now in a read-onlty state. if theres a way to fix this from text-based interface, please inform me of how to do so! 
<::ALPHA::HECTOR::SIERRA::>

---

### Post by fslezak on 2012-06-10
Get the latest Ubuntu ISO and burn it to a CD. Then, plug that into your minimal, and then install the packages (I don't know the location, can anyone help?).  If that doesn't work, just re-install Ubuntu from the disk that you burnt earlier.

---


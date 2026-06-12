---
title: "Can't login into Ubuntu 14.04 and Boot Repair"
date: 2014-11-15
forum: New to Ubuntu
---

### Post by Richiegs on 2014-11-15
I was using Vista and Ubuntu 14.04 in my PC. After I finished an update in my Windows Vista, I could not login  into my Ubnutu account. Thus, I tried to install Boot Repair, but Boot Repair failed to work as  expected.
Here are the messages from the Terminal while I was trying to install Boot Repair: 

Setting up pastebinit (1.4-3)
ubuntu@ubuntu:~$ /usr/share/boot-sav/gui-g2slaunch.sh: line 33: hash: gksudo: not found
/usr/share/boot-sav/gui-g2slaunch.sh: line 35: hash: gksu: not found

It is really frustrating because I have all my files in Ubuntu. I appreciate anyone who offers help to me.

---

### Post by kc1di on 2014-11-15
download and burn boot-repair to  a CD/DVD - and run it from there. 

Alternately you can reinstall grub2 from a live Ubuntu DVD also.
More info[ here: ]("https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal")

---


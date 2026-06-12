---
title: "problems"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by ifdsgtrculdtalk on 2012-01-27
hi,m totally new to linux,i have a problm days ago i updated some
programs through update manager afterwards when i tried to uninstall programs or install the progrmas thorough synaptic package manager it shows the following letters 

    E: linux-image-2.6.32-32-386: subprocess installed post-installation script returned error exit status 127
 and also in power button it turns to red and says restart required,m trying to solve this
plz anyone if have some ideas to deal this ill be thankfull

---

### Post by ptsubin on 2012-01-28
Open synaptic package manager if you have it installed. If there is an issue, it would help you by giving direct commands to copy and paste in a terminal..

---

### Post by ifdsgtrculdtalk on 2012-01-31
> **ptsubin said:**
> Open synaptic package manager if you have it installed. If there is an issue, it would help you by giving direct commands to copy and paste in a terminal..


well, it shows errors were encountered while processing linux image 2.6.32-32.386 and i didnt find any direct commands to copy,thanks for the reply and quote:)

---

### Post by Bucky Ball on 2012-01-31
Reboot and drop to the previous kernel on the list. Should be third down after the latest kernel's recover kernel.

You could also try in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

This will upgrade packages NOT the release. ;)

---

### Post by ifdsgtrculdtalk on 2012-02-01
hmm well i did exactly what youve told to but it show the following error in the terminal

errors were encountered while processing linux-image-2.6.32-32-386 grub-pc
e:sub-process/usr/bin/dpkg returned an error code (1)

SO NOW WHAT TO DO.HELP EXPECTING

---

### Post by cortman on 2012-02-01
> **ifdsgtrculdtalk said:**
> hmm well i did exactly what youve told to but it show the following error in the terminal

errors were encountered while processing linux-image-2.6.32-32-386 grub-pc
e:sub-process/usr/bin/dpkg returned an error code (1)

SO NOW WHAT TO DO.HELP EXPECTING

You're still booting with the same kernel. Look closely at the kernel versions in the GRUB menu. Your current one is 2.6.32-32-386. Look for one with an earlier release number, and boot into that.

---


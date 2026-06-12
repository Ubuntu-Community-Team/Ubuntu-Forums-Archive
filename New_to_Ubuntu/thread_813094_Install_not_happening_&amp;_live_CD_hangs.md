---
title: "Install not happening &amp; live CD hangs"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by eekamuffy on 2008-05-30
I'm really excited to get started in linux, but I'm stuck and unable to get xubuntu (Hardy Heron) installed. The live CD gets stuck loading, so I've been trying the "install xubuntu" selection when it boots up to the CD. By the way, the vaio has an external PCMCIA CDROM. There isn't anything else installed (no Windows!) on the 9GB hard drive and 256Mb RAM, so it should work, right? So, the live CD hangs, and the "install xubuntu" runs all kinds of text on the screen, but eventually ends in busybox with the (initramfs) prompt. I've read a little, but can't get it past this point. Any suggestions?

---

### Post by cristo-father on 2008-05-30
might want to try 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by eekamuffy on 2008-05-30
that's a great idea! but, i stayed away from ubuntu cause ubuntu.com says it requires at least 256 MB of RAM to run the desktop install CD. 256Mb is all i've got and i can't upgrade any further. do you know anything about an xubuntu minimal cd?

---

### Post by james_vanb on 2008-05-30
I had to use the Alternate Install cd to load Xubuntu on a lower spec laptop.  Live cd would hang.  Give the Alternate a try.

---

### Post by cristo-father on 2008-05-30
> **eekamuffy said:**
> that's a great idea! but, i stayed away from ubuntu cause ubuntu.com says it requires at least 256 MB of RAM to run the desktop install CD. 256Mb is all i've got and i can't upgrade any further. do you know anything about an xubuntu minimal cd?
The page in the bottom says it can be installed to computers with less than 128 ram.
This installs ubuntu not gnome-desktop, so from there you can install xubuntu from apt-get by typing in the terminal: 
> sudo apt-get install xubuntu-desktop 
you should mix that with the following link
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
The desktop i would recommend would be lxde here is a link to a useful topic
[http://ubuntuforums.org/showthread.php?t=812721&page=2](http://ubuntuforums.org/showthread.php?t=812721&page=2)

---

### Post by eekamuffy on 2008-05-30
well, it looks like the minimal cd image did the trick, but is the boot supposed to look like dos? and what do i do after logging in when all it gives is a prompt?!

---

### Post by avtolle on 2008-05-30
> **eekamuffy said:**
> well, it looks like the minimal cd image did the trick, but is the boot supposed to look like dos? and what do i do after logging in when all it gives is a prompt?!
Yes, it is supposed to look like "dos" (or CP/M, for those old enough to recall. :-) ) From the command line, as this is where you are, you should follow the advice earlier given to install the GUI.

---

### Post by WRDN on 2008-05-30
> **eekamuffy said:**
> well, it looks like the minimal cd image did the trick, but is the boot supposed to look like dos? and what do i do after logging in when all it gives is a prompt?!

You need to install gnome or KDE to get the GUI, by typing:

```
sudo apt-get install [package_name]
```

I think you can just type "sudo apt-get install gnome" for the gnome packages, but someone else will need to confirm that.

 For this to work, you will need an active internet connection.

---

### Post by james_vanb on 2008-05-30
Just try the Alternate CD - Minimal will require you to build the OS from ground up.

---

### Post by eekamuffy on 2008-06-03
that minimal cd finally did the trick! i can't believe it! i just installed over and over and over again from several different iso images and then, bang!, the last one took and i'm a happy new linux convert! The install was so unstable on my sony vaio pcg-z505js that i'd encourage anyone having problems with the installer to try it over and over again. Eventually, the installer will work like it's supposed to!

---


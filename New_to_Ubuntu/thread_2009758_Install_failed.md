---
title: "Install failed"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by dasphinx on 2012-06-24
I am trying to install Ubuntu 64 bit desktop in a VMware Player. The install from the ISO file I downloaded to a CD-ROM goes fine until a message "apt configuration problem: an attempt to configure apt to install additional packages from the CD failed." At this point the window says "Easy Install is installing Ubuntu 64 bit" but in fact it is hung up. I have tried it twice with the same result. Please advise waht to do, I am a newbie to both Ubuntu and VMware Player - thanks ;)

---

### Post by nipunshakya on 2012-06-24
Have you tried to use the steps mentioned down there:
[http://www.howtogeek.com/howto/11287/how-to-run-ubuntu-in-windows-7-with-vmware-player/](http://www.howtogeek.com/howto/11287/how-to-run-ubuntu-in-windows-7-with-vmware-player/)
Maybe you downloaded a corrupt iso of ubuntu as well...have you checked it?

---

### Post by dasphinx on 2012-06-25
Yes, that was what I was using to learn how to install. I downloaded the file to a CD-ROM directly from the Ubuntu site, choosing the 64 bit version since my computer is 64 bit.

---

### Post by nipunshakya on 2012-06-25
your error pretty much says that the ubuntu installation is trying to install packages from the cd but its failing... .. has your ubuntu installation completed? or does the error appear during halfway of the installation?

---

### Post by dasphinx on 2012-06-25
I don't know and don't know how to tell. The VMware screen says Easy Install is installing Ubuntu 64 bit but it definitely has not completed because the Ubuntu screen is not displaying. I clicked on Virtual Machine --> Install VMware Tools, but get an error message saying it can't do that while Ubuntu is still installing (which is has been doing for hours now).

---

### Post by nipunshakya on 2012-06-25
Have you tried to install ubuntu from a different .iso file too by creating a new virtual machine?

---

### Post by dasphinx on 2012-06-25
I wonder whether the problem is the the Ubuntu site offers a 64bit amd iso file, whereas I am running an Intel processor (64bit)? I don't see a non-amd 64bit file offered. So I think I will try the 32bit desktop and see if it works, unless you can point me to the proper iso file for Intel.

---

### Post by nipunshakya on 2012-06-25
There is nothing as such particularly driven for intel or amd... 64 bit means it is applicable to all 64 bit capable processors buddy... even im running amd64 bit on my intel dual core processor... anyways, try what u can and post back if u make a progress or run to problem...

---

### Post by Cheesemill on 2012-06-25
The problem is you are trying to use Easy Install which doesn't have support for 12.04 yet.

Just do a manual installation and it works without any problems.

---


---
title: "[SOLVED] Suggestions for a light USB distro run in QEMU"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Berean on 2008-05-17
Hi, I've been with Ubuntu for approximately a year and love it!  I want to run a light distro within Windows (at work) from a USB that's very similar to Ubuntu.  I've used Puppy - didn't like it - DSL, but I wasn't convinced, and PClinuxOS which I'm using at the moment.  Can anyone recommend a distro that I can run on QEMU in Windows from a USB, that's light, please?  I've considered Wolvix, KolibriOS, Fluxbuntu and Xubuntu but am I right in thinking only the latter is similar to ubuntu?  Many thanks for your advice.  Regards,

---

### Post by Xiong Chiamiov on 2008-05-17
What is it you're looking for, similarity-wise?  Do you want GNOME, or just like how apt works?

---

### Post by Berean on 2008-05-17
I hadn't thought that explicitly, but as I'm not going to be downloading that much - simply using a browser, and a word editor - perhaps something akin to Gnome?  Regards,

---

### Post by bodhi.zazen on 2008-05-17
Install JEOS

JEOS is optimized for running in virtualized environments, but it is command line only.

After the install build up the apps you want.

See these links :

[https://help.ubuntu.com/community/JeOS](https://help.ubuntu.com/community/JeOS)

[http://cdimage.ubuntu.com/jeos/releases/8.04/release/](http://cdimage.ubuntu.com/jeos/releases/8.04/release/)

ISO file on that second link ^^ go for the i386 version.

Then post-install:

[http://ubuntuforums.org/showthread.php?t=298835](http://ubuntuforums.org/showthread.php?t=298835)

[http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/](http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/)

The idea here is to start small and add only what you want / need from the Ubuntu repositories.

The other advantage is you can install into an encrypted file system, very nice IMO for portable machines.

My JEOS install is just under 500 Mb (no X , but I have no need for X on the machine and prefer it that way).

You may want to look at downloading QEMU manager as that will give you some additional options for booting, inlcuding internet access and port forwarding in "userland" ie you do not need to run aas an administrative user to obtain internet access.

[http://www.davereyn.co.uk/download.htm](http://www.davereyn.co.uk/download.htm)

---


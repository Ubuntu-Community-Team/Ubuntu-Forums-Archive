---
title: "Wifi Bug Workaround Help"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by dangerous123 on 2011-12-30
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/876147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/876147)

So I have an Asus laptop U56E-BBL5.  I have tried a few things to get my wireless up and running with 11.10, like installing a new network manager, typing commands that I don't understand from old threads.  So far nothing has worked (I see network connections but can't connect).  Now I am trying to install an older kernel...  I got and installed the files from here ( [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38.8-natty/")) and rebooted... with no success.  I didn't see the grub menu- is there something I am supposed to do to boot the older kernel that I am missing?


Any other suggestions for this problem?  



Thank you for any help.

---

### Post by anewguy on 2011-12-30
I believe that once you've installed the kernel, you still need to run sudo update-grub in order to update the grub menu - it's not dynamic.


Dave ;)

---

### Post by dangerous123 on 2011-12-30
all right, got it to boot to Kernel 2.6! :) However, this time, I get wireless disabled.  (lshw -C network... network disabled).  I do not believe there is a wireless switch on the computer...  i did rfkill unblock all (there were soft blocks on wifi and wimax) but it still showed wireless disabled.  Is there a way around this?

---

### Post by dangerous123 on 2011-12-30
All right got it to work!  by unblocking wifi and changing the network manager file.  Thank you.!!!

---

### Post by anewguy on 2011-12-31
Glad it's working for you.  Please also take a second and use the "Thread Tools" option above the first post to mark this thread as solved.  It helps people searching with a similar problem.

Dave ;)

---

### Post by ieShae5d on 2012-01-13
Anyone figure out how to get this to work with Joli OS (based on Ubuntu 10.04)? My ASUS U56E-BBL5 won't connect to the Internet -- either with a tested patch cable connected to the Ethernet port on the laptop or with the built-in wireless card -- to log into Joli OS. I should note that I have Windows 7 set up as my primary operating system. Joli OS lives on either another partition or "frugally" with Windows 7, however the [automatic installer]("http://www.jolicloud.com/download/jolicloud-iso/thank-you") from the Jolicloud site sets it up.

I had previously installed Joli OS (Ubuntu 10.04) by itself on my Dell Optiplex GX280 Small Mini-Tower. I could connect to the Internet with the Ethernet cable and, later, after modifying the driver files of my Linksys by Cisco AE1000 Wireless-N adapter as per the instructions [here]("http://ubuntuforums.org/showthread.php?t=1630358&highlight=Linksys+AE1000").

Maybe Joli OS just won't work with this laptop. :( Any ideas?

---


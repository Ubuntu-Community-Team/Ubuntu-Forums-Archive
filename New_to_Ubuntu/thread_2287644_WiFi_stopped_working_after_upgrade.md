---
title: "WiFi stopped working after upgrade"
date: 2015-07-21
forum: New to Ubuntu
---

### Post by Mehul_Chirania on 2015-07-21
Running a 14.10 LTS on HP 15 R - 007 TX. Dual boot with windows 10 Tech preview. 
Ubuntu was working fine until I tried to upgrade the version using these following simple commands: 
"sudo apt-get update" and  "sudo apt-get upgrade".
After the upgrade process was finished I am still at the same version of Ubuntu, my wallpaper has become black and doesn't change and Wifi doesn't show anything. No option to enable wireless connections. Please help. TIA.

---

### Post by Vladlenin5000 on 2015-07-21
apt-get update + apt-get upgrade and even + apt-get dist-upgrade does NOT upgrade your Ubuntu version, it updates the packages already installed. So, what happened to you has nothing to do with your idea of a "failed upgrade".

Both issues suggest you had proprietary drivers for your graphics card and your WiFi installed in a non "orthodox" way for Ubuntu. Thos e are expected to break whenever the kernel changes (and it was updated recently).
So, start by explaining exactly that: What have you installed for graphics and WiFi before? And, of course, your hardware specs...


PS - ... Or you can ignore it like you did in your first thread... I always wonder why people open threads they don't intend to follow up, not even with a "thank you"... :-k

---

### Post by newb85 on 2015-07-21
First observation: 14.10 is not LTS.  In fact, it should be hitting EOL about now, which means you need to upgrade to a newer release (or roll back to 14.04, which is LTS and won't hit EOL until April 2019).  You may want to consider doing a fresh install, given the problems you're having.

That said, my best guess is that your last update included a kernel upgrade that isn't playing well with your hardware.  If you restart the machine, you should see the Grub screen (since it's dual-boot).  If you select the "More Ubuntu options" (or something like that), it should list the available kernels.  Go with the second newest.  See if things go back to the way they were.

Otherwise, my next inclination would be hardware issues...

*Edit: Vladlenin's response is from a more knowledgeable standpoint than mine.  I have little experience with unorthodox drivers.*

---


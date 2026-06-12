---
title: "Installing xserver directly from live cd"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by amajewicz on 2012-06-27
Hello, 

I'm just wondering if there is any possible way to install xserver-xorg from the liveCD. I had some issues after installing a proprietary ATI driver which lead to black screens in both normal and recovery mode. I was able to get it at least to boot up to the command line in recovery mode with hints from this link:

[http://askubuntu.com/questions/104799/after-uninstalling-ati-fglrx-drivers-ubuntu-11-10-wont-boot](http://askubuntu.com/questions/104799/after-uninstalling-ati-fglrx-drivers-ubuntu-11-10-wont-boot)

But it didn't work completely. So I stupidly decided to uninstall xserver and reinstall, but because I have an old kernel the reinstall isn't working and I get the error "Failed to fetch http://ppa/launchpad.net....." It recommends to run apt-get update, but I can't update my kernel because I have comedi libraries installed which would mess up controlling some hardware which is also a bit of a nightmare to get up and running. 

Is there any possible way to just reinstall xserver directly from the live CD?

Thanks!

---

### Post by amajewicz on 2012-06-27
As a follow up, I wanted to check out the launchpad ppa's to see if I could just get a .deb file to copy directly to my computer, but I couldn't access any of the lucid ppa's. Got a timeout error. Similar to this thread, but they were able to fix the issue. I can't turn off and on my router since I'm on a school network. Any thoughts?
[http://ubuntuforums.org/showthread.php?t=1997739](http://ubuntuforums.org/showthread.php?t=1997739)

---

### Post by amajewicz on 2012-06-28
I was able to solve the problem by getting off campus - I guess there was some odd issue with our campus firewall and launchpad. Was able to reinstall xserver.

---


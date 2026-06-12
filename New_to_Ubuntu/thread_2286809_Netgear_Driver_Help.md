---
title: "Netgear Driver Help"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by zander2 on 2015-07-14
I setup Ubuntu 15.04 today on a partition on my desktop, as I wanted to use Linux for some of my work and to play the 64-bit version of KSP. :D

Unfortunately, I can do neither of those things because I can not connect to the internet. I do not have a wired connection on my desktop, and I use a Netgear Wireless-N Dual Band USB internet adapter instead. While it works fine on Windows, Ubuntu doesn't even seem to pick it up, as I couldn't find its entry on typing *lspci** -**vvnn *into the terminal (a command which I ran because a help article [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_Windows_driver_using_ndisgtk_.28ndiswrapper_graphical_interface.29") told me to). I tried following that tutorial, but it hasn't worked out. I tried installing the packages the tutorial uses using apt-get, but I am not connected to the internet. Trying to install the packages from the liveCD, as described in section 2.1.3, didn't work, as I never got a request to install packages from the disk, couldn't find the Administrator menu in the System Settings app, and the link to help in that section is broken. I ended up using my laptop to download the required packages, and the driver in [this thread]("http://ubuntuforums.org/showthread.php?t=1830237"), and then used a flash drive to transfer them to my desktop and install them in the Ubuntu Software Center. 

I'm not sure where I went wrong, but *ndiswrapper* wasn't able to install the drivers. I did not fully work through the article, as I was not sure how to do many of the things it requests, and I was never sure which instructions were applicable to my problem. :\

All of this assumes there is a driver issue, but I am not even sure how to check for that: I don't know what the Ubuntu equivalent of the Windows Device Manager is.

Any help would be appreciated.

Thanks,
Zander

---

### Post by Geoffrey_Arndt on 2015-07-14
See post #6 in this thread for alternate wireless adapters that work with Linux "out of the box" - - in other words, plug & play . . no driver install or compiles needed.   There are also many other such devices, you just have to search for them on Amazon or New Egg, etc.   I've had especially good luck with Panda devices, but Airlink 101, TP-Link 722n, and others work great also.  These units vary in price with a range of $10 to $30 usd - - well worth avoiding the hassles of non-compatible devices.

[http://ubuntuforums.org/showthread.php?t=2286519](http://ubuntuforums.org/showthread.php?t=2286519)

---

### Post by zander2 on 2015-07-18
Thanks! I appreciate that! :D

I'll try to pick one up ASAP, as I haven't had any luck so far with what I currently have.

Thanks for the help!

---


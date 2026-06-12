---
title: "Broadcom wireless adapter"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by dustysnakes on 2011-10-22
Hi guys,
Brand new to linux and this forum so bare with me.  I just took the plunge last night and wiped my windows machine to install a brand new copy of ubuntu.  Everything went wonderfully it works beautifully couldn't be happier.  Except, I can not get it to recognize my wireless adapter.  I looked through some other posts and found this is a common problem with the broadcom.   I even tried some of that dos like coding ubuntu has to try to fix it (thats a learning curve by the way)but to no avail.  Could any of you perhaps give me some sort of walkthrough for this?  Please keep in mind that I have no idea what I am doing with this new OS.  I haven't even figured out where files are stored yet so be gentle on me.
thanks in advance.

---

### Post by westie457 on 2011-10-22
> **dustysnakes said:**
> Hi guys,
Brand new to linux and this forum so bare with me.  I just took the plunge last night and wiped my windows machine to install a brand new copy of ubuntu.  Everything went wonderfully it works beautifully couldn't be happier.  Except, I can not get it to recognize my wireless adapter.  I looked through some other posts and found this is a common problem with the broadcom.   I even tried some of that dos like coding ubuntu has to try to fix it (thats a learning curve by the way)but to no avail.  Could any of you perhaps give me some sort of walkthrough for this?  Please keep in mind that I have no idea what I am doing with this new OS.  I haven't even figured out where files are stored yet so be gentle on me.
thanks in advance.

Hi welcome to the Forum.

Take a look at _[this]("http://wireless.kernel.org/en/users/Drivers/b43")_ and _[this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")_ for guidance. 
Any problems or questions come back here and ask or say what the problems are. 

Give details of any errors that might happen. All information is helpful.

Thank you.

---

### Post by dustysnakes on 2011-10-22
Thanks for the reply.  I just went through both of those links and according to the terminal everything was installed properly.  I still however, can not get anything out of it.  When I pull up the additional drivers window it shows Broadcom STA wireless driver as being activated.  I was under the impression that I should be seeing the B43 driver there.  Am I wrong in that assumption?  The PCI - ID shows 14e4:4311 and the model number as a BCM4311.  I have run the update as well as bcm-kernel-source and both are showing up to date. I do not get anything more than a blank look from my terminal when I run the modprobe however.  Thanks for your help in advance.

---

### Post by masgeeks on 2011-10-22
Good luck to you, my friend - I went through hell with BCM4328 a while back... lots of tweaking on 10.04, I think it was...  One of the freaky things with mine was I had to make sure my SSID was set to visible in order to connect with WPA2 personal.  I always hide my station ID...  I also had to grab drivers from an older version of Ubuntu in order to get it to recognize my adapter at all.  Was a nightmare...  :(

---

### Post by dustysnakes on 2011-10-22
OK so I was wrong in that last post
I typed
 sudo modprobe -r b43 ssb wl
[sudo] password for dusty: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist.save line 1: ignoring bad line starting with 'DRIVERS'
WARNING: /etc/modprobe.d/blacklist.save line 2: ignoring bad line starting with 'X'
WARNING: /etc/modprobe.d/blacklist.save line 3: ignoring bad line starting with 'x'
then
sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist.save line 1: ignoring bad line starting with 'DRIVERS'
WARNING: /etc/modprobe.d/blacklist.save line 2: ignoring bad line starting with 'X'
WARNING: /etc/modprobe.d/blacklist.save line 3: ignoring bad line starting with 'x'
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist.save line 1: ignoring bad line starting with 'DRIVERS'
WARNING: /etc/modprobe.d/blacklist.save line 2: ignoring bad line starting with 'X'
WARNING: /etc/modprobe.d/blacklist.save line 3: ignoring bad line starting with 'x'

so I am now assuming this is a blacklist issue.  I somehow blacklisted my good driver?  Sorry I don't understand the terminal commands very well yet.

---

### Post by gandaran on 2011-10-22
> **dustysnakes said:**
> Thanks for the reply.  I just went through both of those links and according to the terminal everything was installed properly.  I still however, can not get anything out of it.  When I pull up the additional drivers window it shows Broadcom STA wireless driver as being activated.  I was under the impression that I should be seeing the B43 driver there.  Am I wrong in that assumption?  The PCI - ID shows 14e4:4311 and the model number as a BCM4311.  I have run the update as well as bcm-kernel-source and both are showing up to date. I do not get anything more than a blank look from my terminal when I run the modprobe however.  Thanks for your help in advance.
for the BCM4311 chipset try this guide, its for pci card but should work for usb adapter with same chip
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by anewguy on 2011-10-22
I think before you get in any deeper trying other suggestions, there are a couple of things you should do first:

- you mentioned using a bunch of DOS like gobblygook.  I can only assume from that that you followed an old, outdated post and tried ndiswrapper and had to type such things as sudo ndiswrapper -i xxxxxx.  If so, it's very important that before moving on to another try, you completely back out what you did that didn't work.  This would include editing the /etc/modprobe.d/blacklist.conf file to back out any additional blacklisting you did - this may have been an echo statement with tail and /etc/modprobe.d/blacklist.conf in the statement you typed.  Remove ndiswrapper from /etc/modules.  Then finally remove ndiswrapper via synaptic package manager.  If you have any questions on this, post back a link to what you have done so far so we can try to help.

- if you have tried additional things you need to also back those out.  If you aren't sure how, please just post back with what you did.

The very first important thing here is no matter what you try, back it out before you go on to the next.

The second most important thing here is that there are a LOT of OUTDATED and frankly incorrect posts for using ndiswrapper.  Before using such a tool always post first with the instructions you intend to follow and ask if they are still valid.

Similary, the bcm-kernel-source isn't needed very often.

If you tried modprobing your driver and you say the terminal just stared at you, try it again, wait a few seconds, then try lsmod to see if the module got loaded.

I believe with this adapter you need to install the firmware cutter and also the "all" firmware package.

However, before we try anything else, please be sure to back out everything you've done so far, then post the outputs of:

- lspsci

- lsusb

- iwconfig

- ifconfig

We can try again once you've done that.

Dave ;)

---

### Post by computerandu on 2011-10-22
This post has helped a lot many people ...may help you as well...

[http://www.computerandyou.net/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://www.computerandyou.net/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

### Post by SkyeFerret on 2011-10-22
I had the same exact problem. I got rid of pretty much every Broadcom package I could find in Synaptic, reinstalled b43-fwcutter and firmware-b43-installer (and I think bcm-kernel-source), then rebooted. Everything worked fine after that.

computerandu's post is very helpful, though; that's what helped me get through this. c:

---

### Post by NattyLight on 2011-10-22
What worked for me was downloading the STA broadcom driver... after this the wireless button finally turned blue but I still couldnt get online? So I then hooked the ethernet cable to my laptop so I could get the Synaptic package and then within the SPM I searched for B43... I marked b43 firmware installer lyyphy and I believe the cutter as well. After doing that I was finally able to connect wirelessly!

My Broadcom is 4312 though so I am not sure if that will work for you? It is worth a try though!

---


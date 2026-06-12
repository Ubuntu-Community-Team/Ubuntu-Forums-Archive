---
title: "Is the new kernel 3.2.0-33 stable?"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by 577 Jersey on 2012-11-15
I probably should have checked first,,because while Im typing this,,the new kernel is downloading onto my 12.04 Ubuntu,,just wanted to make sure its a stable kernel with no problems?



 Thanks ahead!!

 Tommy:guitar:

Update..well all is good so far with the 3.2.0-33 kernel.Can I just go into synaptic and remove/uninstall everything that has a green box for the 3.2.0-32 to get rid of my old kernel?

 Thanks again!!

---

### Post by mastablasta on 2012-11-16
> **577 Jersey said:**
> I probably should have checked first,,because while Im typing this,,the new kernel is downloading onto my 12.04 Ubuntu,,just wanted to make sure its a stable kernel with no problems?
 
Yes. all 3.2 versions are stable kernel. these are usually security patches and bug fixes.
i think ver 3.5 is development but i am not sure.
 
>  
Update..well all is good so far with the 3.2.0-33 kernel.Can I just go into synaptic and remove/uninstall everything that has a green box for the 3.2.0-32 to get rid of my old kernel?

That would possibly be a bad idea.
 
 i used computor janitor to clean the old kernels. i think Ubuntu tweak tool laso does it (not sure though). however you should keep the old kernel (at least one) in case something goes wrong or you accidentally break something, then you can always fallback to old version and fix it form there.

---

### Post by Y^2om&amp;#7sgP on 2012-11-16
I' currently running 3.2.0-33 (on a desktop[ and a laptop)and it appears to be stable.

I follow the procedure here and have no issues removing old kernels

[http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)

Although written for 10.04, works fine on 12.04

---

### Post by mastablasta on 2012-11-16
well that procedure purges them not just unistall. which is ok. you wouldn't want residual traces left behind i think.

---

### Post by 577 Jersey on 2012-11-16
Thanks for the info guys,,
 Ive been running 12.04 for a week or so,,like it way better than that windows propaganda crap!

Im still new to all of this,,and kinda scared of the terminal at the moment,,so was looking for the easiest way possible to remove old kernels,,thanks for the tips!!

 Tommy:popcorn:

---

### Post by 577 Jersey on 2012-11-16
> **hattpa said:**
> I' currently running 3.2.0-33 (on a desktop[ and a laptop)and it appears to be stable.

I follow the procedure here and have no issues removing old kernels

[http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)

Although written for 10.04, works fine on 12.04Just a quick question,,I looked at the procedure and it looks very strait forward,,my question is,,after the kernels come up,,do you have to choose one at a time to remove,,or does it give the option to choose multiple kernels to remove/purge?

Im taking it as,,each command I type in will remove a single kernel(the one I choose),,and I would have to reapeat the command for each one I choose?

 Thanks!

---

### Post by 577 Jersey on 2012-11-16
> **mastablasta said:**
> Yes. all 3.2 versions are stable kernel. these are usually security patches and bug fixes.
i think ver 3.5 is development but i am not sure.
 

That would possibly be a bad idea.
 
 i used computor janitor to clean the old kernels. i think Ubuntu tweak tool laso does it (not sure though). however you should keep the old kernel (at least one) in case something goes wrong or you accidentally break something, then you can always fallback to old version and fix it form there.This is what I found,,how come the older kernel still shows up after using computer janitor to remove,,am I missing something here?

 I also tried to delete the older kernel 3.2.0-29 using the purge and they said it was not installed,,why did it show up in computer janitor then,,now Im really confused.

tom@tom-OptiPlex-745:~$ uname -r
3.2.0-33-generic-pae
tom@tom-OptiPlex-745:~$ dpkg  --list | grep linux-image
ii  linux-image-3.2.0-29-generic-pae       3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic-pae       3.2.0-32.51                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic-pae       3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                3.2.0.33.36                             Generic Linux kernel image
tom@tom-OptiPlex-745:~$

---

### Post by Y^2om&amp;#7sgP on 2012-11-16
Yes, you have to repeat the command for each kernel...just make sure that you don't remove the one listed when you run uname -r.

Not sure why it still appears in Janitor, I don't use it.

Did you remember the last line of the procedure to update grub?  could be it picks it up from there.

---

### Post by snowpine on 2012-11-16
There is no benefit to uninstall the old kernels unless you are running VERY low on hard disk space.

There is also no reason to guess "what is this new kernel update?" because Ubuntu development is "open source" and transparent. Here is the changelog listing the exact changes:

[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.2.0.33.36/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.2.0.33.36/changelog)

If you need more info you can join the devel mailing lists or maybe become a developer yourself one day!

---

### Post by 577 Jersey on 2012-11-16
> **hattpa said:**
> Yes, you have to repeat the command for each kernel...just make sure that you don't remove the one listed when you run uname -r.

Not sure why it still appears in Janitor, I don't use it.

Did you remember the last line of the procedure to update grub?  could be it picks it up from there.

I dont think I did the last line in the prcedure,,thanks!!

Got it now!!

---

### Post by wheeze on 2012-11-16
I got the new kernel upgrade and had a little issue. I run two VMs on a Toshiba laptop, one with Ubu 12.04 and one with Mint 13 MATE. On the Ubuntu VM when I rebooted after the kernel update, the resolution went to 1024x768. In the Displays setting it did not even show an option to switch back to 1366x768.

On the Mint VM it worked just fine, no change in the display resolution upon reboot and just to make sure, I checked the Display settings and there was the 1366x768 setting.

I'm thinking maybe has something to do with Unity/Compiz on the Ubuntu VM?

---

### Post by snowpine on 2012-11-16
> **wheeze said:**
> I got the new kernel upgrade and had a little issue. I run two VMs on a Toshiba laptop, one with Ubu 12.04 and one with Mint 13 MATE. On the Ubuntu VM when I rebooted after the kernel update, the resolution went to 1024x768. In the Displays setting it did not even show an option to switch back to 1366x768.

On the Mint VM it worked just fine, no change in the display resolution upon reboot and just to make sure, I checked the Display settings and there was the 1366x768 setting.

I'm thinking maybe has something to do with Unity/Compiz on the Ubuntu VM?

You can test your theory by booting with the old kernel. If it works fine with the old kernel, but doesn't work with the new kernel, that supports your theory that the problem is kernel-related.

If you haven't done so already, you may wish to install **dkms** as this will automate the process of rebuilding the virtualbox module each time you upgrade the kernel.

---

### Post by wheeze on 2012-11-16
> **snowpine said:**
> You can test your theory by booting with the old kernel. If it works fine with the old kernel, but doesn't work with the new kernel, that supports your theory that the problem is kernel-related.

If you haven't done so already, you may wish to install **dkms** as this will automate the process of rebuilding the virtualbox module each time you upgrade the kernel.

Already did both of those. :)

Runs fine with the previous kernel, no 1366 resolution with the new kernel.

dkms is standard in my world!

---

### Post by write2kerry on 2012-11-18
I am running 12.04 and run a couple of kvm virtuals that access the internet via a bridge.  After the update to 33 my virtuals COULD access the internet (a 12.04 virtual had not yet had the kernel update) and my host could access the router but COULD NOT get past that.  I checked the default route etc and the config files that I had used to setup the bridge and all seemed well.  Probleem persisted several reboots.  Once I booted the host into 32 all was fine.  Maybe just a coincidence but suffice it to say I will wait till I have more time to play with it before booting into 33 agian.

---

### Post by 577 Jersey on 2012-11-18
> **write2kerry said:**
> I am running 12.04 and run a couple of kvm virtuals that access the internet via a bridge.  After the update to 33 my virtuals COULD access the internet (a 12.04 virtual had not yet had the kernel update) and my host could access the router but COULD NOT get past that.  I checked the default route etc and the config files that I had used to setup the bridge and all seemed well.  Probleem persisted several reboots.  Once I booted the host into 32 all was fine.  Maybe just a coincidence but suffice it to say I will wait till I have more time to play with it before booting into 33 agian.
I hear that,,good to know,,I have had a few strage things happen after the 33 update,,but only while my audio recording intereface was plugged in,,using audacity,screen went to a visitor screen or something,,not quite sure,,but after a reboot,,it has been running solid,,I have not plugged the interface in again yet;)

---


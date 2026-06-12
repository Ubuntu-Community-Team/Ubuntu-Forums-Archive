---
title: "How to update to latest stable kernel Ubuntu 10.04"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by aem0512 on 2012-04-10
Just wondering how to update to the latest stable kernel in Ubuntu 10.04. Currently I have 2.6.32 and am experiencing a screen flicker common to this kernel and Intel Mobile graphics.

Also how do I uninstall the other two kernels (yes there are two on here already) after testing out the new one?

---

### Post by CharlesA on 2012-04-10
As far as I know 10.04 is frozen at 2.6.32.x kernels.

---

### Post by jacob.david on 2012-04-10
To uninstall old kernels,
    Use the following command to search for installed kernels
       sudo aptitude search linux-image | grep -E "^i"
    Above command will provide the list of installed kernels. Unwanted/old kernels can be removed with the following command. 
       sudo aptitude purge <kernel name from the above list>
    Finally the boot menu can be updated with the following command
       sudo update-grub

---

### Post by CharlesA on 2012-04-10
An easier way is to run this:

```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1)
```

It does the same thing as above but removes kernels automatically.

---

### Post by aem0512 on 2012-04-10
I know it's possible to update a newer kernel on 10.04...what would be the negative ramifications of putting the newest stable kernel for 11.10 on 10.04?

---

### Post by CharlesA on 2012-04-10
> **aem0512 said:**
> I know it's possible to update a newer kernel on 10.04...what would be the negative ramifications of putting the newest stable kernel for 11.10 on 10.04?
Besides having to install them manually and the chance of something breaking?

I'd suggest waiting another couple weeks and bumping up to 12.04.

---

### Post by aem0512 on 2012-04-11
Does the long term support of 10.04 refer to the kernel itself or to something within the distribution? 

If I update to the latest stable kernel, will I receive the security updates for it through the update manager or what?

I don't want to install 12.04 yet, I want to keep Gnome 2.

---

### Post by cottfcfan on 2012-04-11
If you want to try out the latest kernel you can download it from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.14-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.14-precise/)
The 3 files you want are:
Linux Headers - all.deb
Linux headers - i386.deb/amd64.deb
Linux image - ...
Last 2 obviously depend on your architecture.
They need to be installed in the order listed above.
Don't delete your previous kernels though, until you have thoroughly tested the latest one.
It's not guaranteed to work properly for everyone.
If it doesn't work just boot back into a previous kernel & delete this one.

---

### Post by mastablasta on 2012-04-11
> **aem0512 said:**
> Just wondering how to update to the latest stable kernel in Ubuntu 10.04. Currently I have 2.6.32 and am experiencing a screen flicker common to this kernel and Intel Mobile graphics.
 

 
if you think it is the graphics card, you can update drivers only using xorg edgers PPA. 
 
>  
I don't want to install 12.04 yet, I want to keep Gnome 2. 

 
Why? 12.04 has fallback mode if you prefer the gnome 2 look.
if Unity doesn't work fast enough there is always Unity 2D if oyu prefer to see Unity at work. and then there is XFCE....
 
 
LTS are only stabel in that they know the bugs. nohting else. if it all work there is no reason to upgrade, but if it doesn't then upgrading to a version where it all works is a good thing.

---

### Post by ld114 on 2012-04-11
The 2.6.38 kernel can be added to lucid in a terminal as follows:

[I]sudo apt-get update
[/I]
*sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty*

If there are issues booting, hold down the shift key when booting and you will see the grub menu - choose an older kernel. This is a good reason to hold on to an older kernel for a while.

You may have to update drivers for your system with the 2.6.38 kernel. There were also some security issues discovered so after the above also run:

*sudo apt-get update*
[I]
sudo apt-get dist-upgrade[/I]

This will ensure that you actually have the latest secure version (though you may have got that anyway through the natty backport - I am not sure).

I am running kernel 2.6.38-14-generic on my lucid installation (to get newer intel video drivers), but as you say LTS 12.04 will be fine when it arrives in a couple of weeks. I have been looking at it on my netbook and if you like gnome 2, you can install 'gnome-panel' and log in with 'gnome classic - no effects' and it is pretty much the full gnome 2 experience (though Unity is actually pretty slick on 12.04).

---

### Post by ld114 on 2012-04-11
On my previous post I forgot to mention that I had added two PPAs before running the backport installation:

*sudo add-apt-repository ppa:glasen/intel-driver*

*sudo add-apt-repository ppa:kernel-ppa/ppa*

Will probably be essential. (I discovered this backport option somewhere in these forums but I didn't make a note of where - I guess if you search around you will find it)

---

### Post by bogan on 2012-04-11
Hi!.**aem**.

The latest update for 10.04 LTS is 2.6.32-40 or 2.6.32-4 according to lsb-release.

On my experience I would strongly advise not to try installing 11.10 or 12.04 on top of 10.04.

I tried it installing 11.10 3.0.0-13 on top of 10.10, using dkgp with the three .deb files mentioned above, and it made a complete turd splat of the whole system. 

After  a couple of weeks of support from these Forums trying to sort it out, I was forced to format the whole partition and do a clean install of 11.10.10 and 385 updates.

Chao!, **bogan.**

---

### Post by bogan on 2012-04-11
> **jacob.david said:**
> To uninstall old kernels,
    Use the following command to search for installed kernels
       sudo aptitude search linux-image | grep -E "^i"
    Above command will provide the list of installed kernels. Unwanted/old kernels can be removed with the following command. 
       sudo aptitude purge <kernel name from the above list>
    Finally the boot menu can be updated with the following command
       sudo update-grubI was surprised to find that your:```
sudo aptitude search linux-image | grep -E "^i"
``` only found the previous versions of linux-image in the current partition; it did not find the 15 or so older versions in an other partiton.

Chao!, **bogan.**

---

### Post by CharlesA on 2012-04-11
> **bogan said:**
> I was surprised to find that your:```
sudo aptitude search linux-image | grep -E "^i"
``` only found the previous versions of linux-image in the current partition; it did not find the 15 or so older versions in an other partiton.

Chao!, **bogan.**
It would only find kernels that were installed on the OS that is currently running. If you have a dual boot system, it wouldn't touch those.

---


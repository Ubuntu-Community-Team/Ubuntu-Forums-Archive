---
title: "How do I patch my ubuntu?"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by m12lrpv on 2013-02-07
It seems my xbmcbuntu installation has this bug (or a variation of it)
[https://bugzilla.kernel.org/show_bug.cgi?id=25732](https://bugzilla.kernel.org/show_bug.cgi?id=25732)
which links to fixes for it here: [http://cgit.freedesktop.org/~danvet/drm-intel/](http://cgit.freedesktop.org/~danvet/drm-intel/)

My question is... how to I apply this patch?

---

### Post by mastablasta on 2013-02-07
download the archived file and then extract it after download. there should be install instructions inside.

---

### Post by m12lrpv on 2013-02-07
Unfortunately there is a readme which is far too generic to be of any use to a newcomer.

It mainly talks about kernel builds which naturally I have no intention of doing. I just want to install fixed versions of the buggy drivers.

The documentation folder talks about merging source and is therefore not relevant.

I am of course expecting this to be as easy as linux is talked up to be. I feel that I am probably expecting too much though :(

---

### Post by mastablasta on 2013-02-07
in linux drivers are (mostly) built into kernel so if you want to get the latest driver option you either need to patch the kernel or use a newer kernel. there are a couple of PPA's you could add for newer kernel. PPA's are added into software soruces in software center and then the update is run. simple enough?
 
 
oh yeah and patching the kernel is probably  means rebuilding it.
 
btw the instructions in the bugzilla are for older kernel. 
 
there is also an imporatnt info in the end: 
A patch referencing this bug report has been merged in Linux v3.7-rc4:

you could try installing this kernel version if you really thinnk that you have been hit by this bug.

---

### Post by m12lrpv on 2013-02-07
Thanks for the info. Much appreciated.

Unfortunately I've seen too many posts of people upgrading kernel versions only to find that their systems end up broken.

My machine is a NAS first and a media PC second. The NAS is too important for me to risk with kernel upgrades.

I've therefore decided that the linux media center PC is a no go.

---

### Post by Tony Flury on 2013-02-07
> **m12lrpv said:**
> Thanks for the info. Much appreciated.

Unfortunately I've seen too many posts of people upgrading kernel versions only to find that their systems end up broken.

My machine is a NAS first and a media PC second. The NAS is too important for me to risk with kernel upgrades.


If you look at the regular updates, kernel updates are not that uncommon, and not at all risky, as they will be throughly tested.

The nice thing on linux, is that a kernel is just another file which gets loaded when you boot and it wont overwrite your current kernel. And if you find that the update doesn't work, you can always reboot and choose an older kernel from your grub menu, and use synaptic to de-install the newer kernel.

I have never had a kernel update fail on me - I have been using Ubuntu for nearly 5 years - there are other with much more experience of it on here who are likely to say the same.

---

### Post by mastablasta on 2013-02-07
i had sound drivers fail to load after kernel update. i've found a workarround, but i could have use the old kernel by selecting it on boot and everything would still work fine.

---


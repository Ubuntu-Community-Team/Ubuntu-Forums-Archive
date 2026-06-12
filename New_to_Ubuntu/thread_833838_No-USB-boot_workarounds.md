---
title: "No-USB-boot workarounds?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Angus77 on 2008-06-19
Does anyone know how to get around the fact that some older computers aren't capable of USB boots?  They're mostly older computers--the ones that are most painful when using a liveCD (too slow!)

I'm thinking along the lines of having a separate CD or floppy boot disc, while having the actual system on a USB (which would be accessible once the kernel is booted, right?).

Is that unrealistic?  I'm certainly no expert on this type of thing.

**I particularly want to be able to do this on a PC I use at a class I've been attending.  We've been using various liveCDs, but I'd just like to use Ubuntu rather that Puppy or DSL or something.  But the Ubuntu liveCD is just too freaking slow on that machine!

---

### Post by sdennie on 2008-06-19
You might be able to do it with a CD and USB stick as you've suggested by changing the kernel boot parameters to use the usb stick as the root disk.  That should work fine as long as the initrd image on the LiveCD has the usb ide kernel modules (which, it probably does).  However, it might take some guess work to figure out what the usb disk is called and it may change from system to system (you might be able to use the UUID of the usb stick but, that's a lot to remember).  

This is all in theory though.  I have no way to actually try it.  ;)

---

### Post by mikeyphi on 2008-06-19
> **Angus77 said:**
> Does anyone know how to get around the fact that some older computers aren't capable of USB boots?  They're mostly older computers--the ones that are most painful when using a liveCD (too slow!)

I'm thinking along the lines of having a separate CD or floppy boot disc, while having the actual system on a USB (which would be accessible once the kernel is booted, right?).

Is that unrealistic?  I'm certainly no expert on this type of thing.

**I particularly want to be able to do this on a PC I use at a class I've been attending.  We've been using various liveCDs, but I'd just like to use Ubuntu rather that Puppy or DSL or something.  But the Ubuntu liveCD is just too freaking slow on that machine!

Have a look at this: 
[https://help.ubuntu.com/community/Installation/FromCDwithBootFloppy?](https://help.ubuntu.com/community/Installation/FromCDwithBootFloppy?)

It's for installation but you should be able to use the idea to run off a USB drive.

---


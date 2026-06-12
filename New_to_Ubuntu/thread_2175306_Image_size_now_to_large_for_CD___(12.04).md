---
title: "Image size now to large for CD ?  (12.04)"
date: 2013-09-18
forum: New to Ubuntu
---

### Post by richard_h2 on 2013-09-18
My image burner is complaining that the image size is too large for a CD.  707mb when the CD is only 702mb.  Are the new ones only for DVD?  Or is something wrong with my burner (I though CDs were 800mb...)

---

### Post by Impavidus on 2013-09-18
Indeed, now they're too large for a cd, you need a dvd. Alternatively, if the target computer boots from USB you can use a usb pendrive.

---

### Post by richard_h2 on 2013-09-18
Pen drives are usually at least 4G these days -- sufficient for many different versions.  If you can set them up with multiple partitions and a different linux image on each ... plus a boot loader to select which to boot from.  are there some easy to follow instructions for this kind of configuration?

---

### Post by Impavidus on 2013-09-18
You can start here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by whitesmith on 2013-09-18
12.04 (alternate) fits on a CD. See [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by richard_h2 on 2013-09-18
> **whitesmith said:**
> 12.04 (alternate) fits on a CD. See [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Thank you.  It struck me as odd that the primary release was only a few meg too big for a CD ...

---

### Post by mastablasta on 2013-09-18
> **richard_h2 said:**
> Thank you.  It struck me as odd that the primary release was only a few meg too big for a CD ...

that's because i believe 12.04 fits on CD but 12.04.1 x.x.2 x.x.3 may not. because they added a few things.

i also think that if you go DVD then do it 4.2GB or whatever fits onto DVD. 

and another thing - USB memorry stick - saves the day and not only that it can easilly be reused, made live OS persistant etc..

---

### Post by Frogs Hair on 2013-09-18
The initial 12.04 release did fit on cd as stated above.

---

### Post by richard_h2 on 2013-09-23
> **richard_h2 said:**
> Pen drives are usually at least 4G these days -- sufficient for many different versions.  If you can set them up with multiple partitions and a different linux image on each ... plus a boot loader to select which to boot from.  are there some easy to follow instructions for this kind of configuration?


Actually ... given that there is a limit to the number of partitions in the standard device partition table (and a rather low one at that) ... perhaps a more flexible method of stuffing multiple bootable ISO images on a memory stick would be possible?  I was thinking of a bootstrap system.  Probably a small linux, which mounts a selected ISO image and then transfers the boot to that?  There would be no lmiit (except memory stick size) to the number of bootable images you could store on a single stick.  Has anybody ever attempted this sort of configuration?  Is it even possible?

---


---
title: "New partition on primary HDD?"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by dvdhudson33 on 2013-06-06
Is it possible to create a new partition in unused space on my netbook's HDD, without interfering with the existing Ubuntu 13.04 installation?  I need Windows 7 in order to flash-update the netbook's BIOS, and putting a second disk in this tiny PC isn't an option.

I've looked at the menu options in 13.04's 'Disks' app, but I don't see anything in there.

If the answer is no ... is installing Win7 onto an external/USB HDD an alternative?

Muchos gracias.

---

### Post by carl4926 on 2013-06-06
Let us see the partition layout in Gparted
You may have to install it
Then take a screen and  post here, it sounds unlikely but lets see....

---

### Post by dvdhudson33 on 2013-06-06
Okey dokey ...

[[IMG]http://www1.picturepush.com/photo/a/13242894/640/13242894.png[/IMG]](http://picturepush.com/public/13242894)

---

### Post by fantab on 2013-06-06
With only 54GB there is very little scope for you, however it is possible.
I would think that 30GB should be enough for Windows.

You can resize the /dev/sda1 and leave yourself about 30GB 'unallocated space'. Then from that space create an NTFS partition.
When installing Windows to it make sure you reformat it again to NTFS.

After Windows install Ubuntu will not boot. You will have to reinstall GRUB. To do this run Ubuntu DVD/USB and use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair").

EDIT: It may be possible to update BIOS without Windows, from a CD or USB... check to see if such an option is available.

---

### Post by newb85 on 2013-06-06
I've never added Windows, but I recall reading somewhere that Windows needs to be at the beginning of the drive, before Ubuntu.  No idea how accurate that is.  Maybe someone else can confirm.

---

### Post by Squalo71 on 2013-06-06
I think this is an issue of older versions of windows.
However updating bios is a task that can be performed, in most cases, using dos bootable usb stick, or cdr (maybe better cdrw).
Try documenting on website of the producer.

Cheers

---

### Post by Mark Phelps on 2013-06-06
Win7 does not need to be the first partition on the drive, however, fantab's remark about REFORMATTING the NTFS partition using the Windows installer is important -- it needs to be reformatted in order to work well with Win7.

---


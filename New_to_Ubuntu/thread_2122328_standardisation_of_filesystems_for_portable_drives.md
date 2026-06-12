---
title: "standardisation of filesystems for portable drives"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by xycris on 2013-03-04
hi, i know this is an ubuntu forum but i don't know where to put this topic:
is there a move to standardise a filesystem to format a portable drives that can be read across any devices?

i know everyone is aware that portable drives nowadays are going beyond 32 GB and FAT32 is already at its limits and also outdated. i can see that NTFS is highly supported in multiple OSs but it is proprietary. Is there an alternative that even small gadgets that support USB drive and flash card media read/write can understand that has greater support and safety measures than what FAT32 can offer?

we can't format our drives as NTFS for digital cameras can't read them or MP3/ MP4/ AVI/ MKV players on our vehicles can't read them. formatting them as FAT32 makes them readable but the limit is there in the read/write of the media. this is quite a dilemma nowadays because everyone is going mobile and sharing huge files through the network (Internet) simply won't do. we are limited as to what one device can read and the other cannot. furthermore, the availability of full HD recording in many media has presented the dire need for drives bigger than 32 GB and maybe in the future will be at TB capacities!

(just an idea though i am not sure how useful it is for the rest of the world.)

---

### Post by Cheesemill on 2013-03-05
I believe that the move to exFAT is already underway, I have several devices that use this format for their flash cards.

---

### Post by xycris on 2013-03-05
> I believe that the move to exFAT is already underway, I have several devices that use this format for their flash cards. 

i like the concept and capability of exFat but isn't it proprietary?

---

### Post by Cheesemill on 2013-03-05
Yes, it is.

There are Linux drivers for exFAT, you just have to install them yourself as they won't ever be allowed to be built into the kernel.
```
sudo apt-add-repository ppa:relan/exfat
sudo apt-get update && sudo apt-get install fuse-exfat
```


exFAT is actually part of the SDXC specification, so any devices that use these cards will understand the format.

---


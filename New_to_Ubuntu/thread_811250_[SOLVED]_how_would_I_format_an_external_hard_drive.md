---
title: "[SOLVED] how would I format an external hard drive"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-28
I have a usb external hard drive, sdc1 mounted at /media/seagate on my desktop machine. 

I want to reformat it from vfat to ext3 and then re setup an archiving system for my data on it. 

I have booted into the live cd and using gparted can see the drive mounted at /media/disk/media/seagate but the op[tions to do anything with it in gparted are all greyed out. 

Can I use the command line to somehow format the drive directly to ext3?

---

### Post by cdtech on 2008-05-29
Sure.

sudo mkfs.ext3 /dev/sdc1

And you can label it with:
sudo e2label /dev/sdc1 usb-drive (or whatever)

Hope this helps.......

---

### Post by Can+~ on 2008-05-29
[FONT="Courier New"]umount[/FONT] it first. Also, as a tip, you can open gparted targeting the exact device(s) (if you want to do it the GUI-way).

```
gparted /dev/something
```

---

### Post by tropdoug on 2008-05-29
thanks that looks easy, just the second command line is it e2 or e3 for the label bit? (does that relate to the filesystem type?)

---

### Post by sam_delta on 2008-05-29
e2label is the program used to change the name, it dosnt have anything to do with ext3 or ext2
sam

---

### Post by tropdoug on 2008-05-29
Thanks sam, thought I might take a break from the other problem for a few minutes. encouragingly I am now well on my way to dumping windows for ever. Sam you seem to have a great knowledge, for a newbie like me, rather than upgrade right now to 8.04 do you think it is safer to stick with gutsy for a couple more months cos I read some hairy stuff about the new release.

[B]EDIT

Magnificent stuff, thank you guys, I only have half a drive to go now, and I will be 100% linux. the external drive is now formatted correctly. beauty!
[/B]

---

### Post by sam_delta on 2008-05-29
hey trop, well i know a bit about ubuntu, because ive been in the average trouble before, and ive learned from fixing things and alot of reading (forums are a good source of info). but im not as knowledgeble as some other people here, 

about hardy, i think its up to you, i use hardy and i feel very confortable with it. i see nothing wrong with it. most of the poeple ive seen that complain/have trouble with hardy usually installed hardy via upgrade, so if you can, fresh install is always better.(not saying that the upgrade wont work, ive seen many people upgrading succesfully) you can try hardy live cd, and if you dont feel safe, then stay with gutsy few weeks/months

sam

edit, i always though that you were using hardy xDD

---

### Post by cdtech on 2008-05-29
I agree tropdoug if you go with Hardy do a fresh install, you should be ok.

Good luck, and remember to tip your staff. :popcorn:

---


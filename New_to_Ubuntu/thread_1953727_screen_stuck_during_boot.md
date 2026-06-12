---
title: "screen stuck during boot"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-04-06
I booted up in the recovery mode since my system will not load normally. The picture attached shows where it is at; after clicking yes it did fsck form util-linux 2.20.1    then moved onto the next line

/dev/sda1: clean, 124380/2411920 files, 766892/9649152 blocks

What do I type or do now to complete the boot process??

---

### Post by Dreamer Fithp Apprentice on 2012-04-06
I'm far from an fscking expert but from the picture it looks to me like it just needs time to finish. Sometimes things like that take a long time.

---

### Post by theducksfan2010 on 2012-04-06
I chose update grub loader and got this screen, almost instantly. The grub is set off of sda, but the OS is on sda1. I typed startx and it did nothing. What do you recommend I do, just continue to sit and wait??

---

### Post by theducksfan2010 on 2012-04-06
I got it to load up a maintenance shell. did:

fdisk -l but it told me that was a bad idea, because it was mounted and **WILL** cause **SEVERE** damage. 

so I did startx and now I just have a completely black screen, and I can hear the computer running, but that is all.

---

### Post by theducksfan2010 on 2012-04-07
bump

---

### Post by Dreamer Fithp Apprentice on 2012-04-09
You never said how long you let it run after fscking. I'm no expert, but since no one else has responded I'll give it a go. If you have data that is important on the same drive I'd boot from something else and back it up to an external drive or removable media if you haven't already.

Then I'd boot in recovery mode, choose fsck again, and leave it alone until it reported something more than it did the first time. If a disk is badly corrupted it can take hours.  Personally I wouldn't conclude it was stuck until I let it run 24 hours. I could be wrong, but if you've backed up your data, the worst it could do is invoke the program which will initiate changing physical constants resulting in the immediate destruction of the universe and all life in it. In which case you can sue me.

---

### Post by theducksfan2010 on 2012-04-09
> **Dreamer Fithp Apprentice said:**
> You never said how long you let it run after fscking. I'm no expert, but since no one else has responded I'll give it a go. If you have data that is important on the same drive I'd boot from something else and back it up to an external drive or removable media if you haven't already.

Then I'd boot in recovery mode, choose fsck again, and leave it alone until it reported something more than it did the first time. If a disk is badly corrupted it can take hours.  Personally I wouldn't conclude it was stuck until I let it run 24 hours. I could be wrong, but if you've backed up your data, the worst it could do is invoke the program which will initiate changing physical constants resulting in the immediate destruction of the universe and all life in it. In which case you can sue me.

I let it sit for a few hours before rebooting it

---


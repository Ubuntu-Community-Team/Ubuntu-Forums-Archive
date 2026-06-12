---
title: "USB flash disk as HDD cache space - Where should I start?"
date: 2006-09-12
forum: Programming Talk
---

### Post by tribaal on 2006-09-12
Hi folks!

I think I heard somewhere that Windows Vista would be able to "use usb flash disks as ram". This is sort of weird, but it gave me the idea to use a USB flash disk as cache space for your regular disk.

Indeed, flash memory is of course much faster than HDDs, and could provide a pretty cheap way to increase performance for disk-intensive operations.

Of course, flash memory "wears" after a while, so for this to work, there has to be "bad sector" checking at some point...

Is there an easy way to tell Ubuntu to use a particular memory space as disk cache?


Otherwise, I will do it myself, but I have a few linux-programming related questions (hence the sub-forum choice):

- Where to I intercept HDD read/write events? I'd guess this is at kernel level, but where, more specifically? In theory I'd guess this would be just above the driver, correct?

- What do you suggest I should use as a filesystem for the cache space? Ideally, it should be a filesystem designed for error-prone memory (since flash wears out after a while)... I have very little understanding of filesystem internals: is a "bad sector checking" algorithm a common thing in filesystems? 
Is it reasonable (ressources wise) to do it every read and write access (in ubuntu I believe filesystem checking is only done once every 30 mounts)? I mean a partial check of course, not a full scan of the whole disk cache, like a way to check if the data you retrieve from the cache is corrupted or not. ;)

- Do you think the disk access speed gain would be interesting, in regard of the ressources needed for filesystem maintenance?

Thanks a lot for your input all!

- trib'

---

### Post by Andrew12106 on 2006-09-12
generally, hard drives are faster than flash drives. in fact, they are faster than most memory cards out there too. just because its solid state memory dosent make it fast.

---

### Post by Kurt` on 2006-09-13
Also, after being overwritten a few million (billion? I forget) times, flash memory will crap out.

Probably not a good idea, just like the guide on "Speeding up Windows XP by using your USB thumbdrive as extra swap space".

Interesting, regardless.

---


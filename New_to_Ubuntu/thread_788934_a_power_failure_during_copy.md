---
title: "a power failure during copy"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by MadKAT on 2008-05-10
hello:

I am in the process of copying 150 gigabyte of data from one usb drive to another (it's a whole heirarchy of folders and subfolders). Now the power went out on me, and now that it's back on I resumed by doing a "cp -R -u" (update) instead of drag-and-dropping in nautilus. Now, I am not sure if there was a file that didn't get copied completely or got corrupted when the power went out. How do I find out if there was one?? There are lots of files here, I can't check them manually one at a time.

Thanks!

---

### Post by warbread on 2008-05-10
You could run fsck from a live boot, but I think you'll be alright.  This is the sort of thing that journaling helps with, and assuming you were writing to and copying from a journaled filesystem, you should be alright.

---

### Post by MadKAT on 2008-05-10
ahmm... yes, I'm writing to an ext3 filesystem, but I'm copying from a FAT32. Will that be a problem?

Thanks for the reply! :)

---

### Post by warbread on 2008-05-10
It's possible, but I doubt it.  The filesystem you're writing to has a journal to keep track of errors, so as long as you weren't deleting the source data during the copy, you should have all the right bits and bytes intact.  My words come with no guarantee at all, but I'd be willing to be money on them.

---

### Post by MadKAT on 2008-05-10
Ok, I understand. No, I'm not deleting anything, I was just copying from the FAT32 drive, so I guess I'd be ok.  Thank you very much!!!

---

### Post by hyper_ch on 2008-05-10
you could try rsync to make sure all is right

---

### Post by MadKAT on 2008-05-10
darn, probably what I should've used in the first place :oops: :D
Thanks!

---


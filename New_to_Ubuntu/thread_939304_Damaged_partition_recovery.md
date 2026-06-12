---
title: "Damaged partition recovery"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by willthebold on 2008-10-05
I accidentally started to format a partition's file system and stopped in the middle. Is there a way to access this partition now? The HD doesn't show up anymore, and I can't boot to it. How can I get the data back?

---

### Post by R15I23D05D14Y on 2008-10-05
There aren't any guarantees for recovering formatted data. Try the testdisk terminal program (after backing up any data still easily accessible on the disk) It might get a few files back.
Personally I'd use any program that deals with partitioning from a livecd, just to take mounting & unmounting diskd out of the equation.

---

### Post by willthebold on 2008-10-05
I can't get to anything on there right now. I've got testdisk, but I can't seem to do anything with it. I assume if I just tried to change the file system back to ext3 it would erase everything?

---

### Post by R15I23D05D14Y on 2008-10-05
If you ran testdisk, and it gave you an option of changing the partition to ext3, then it thinks it has found a partition and is trying to help recover it (including whatever files it may find).

If you change the file system to ext3 using a partition editor (eg, gparted), then it will definitely erase everything.

---

### Post by willthebold on 2008-10-05
I wasn't sure how to make testdisk make it an ext3 partition. It didn't seem to be changing anything.

---

### Post by R15I23D05D14Y on 2008-10-05
Here are some instructions for using testdisk: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you have already been following those then I can't offer any help or hope for your files. *Edit* Apart from quickly pointing at photorec, by the same people as testdisk. Might be worth looking into as well.

---

### Post by caljohnsmith on 2008-10-05
If you stopped the formatting in the middle, most likely testdisk won't be able to recover your partition. But a really great program for recovering files off the HDD is called "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")", which I've used before with good success. It comes as part of the "testdisk" package. Just run it with:
```
sudo photorec
```
And go through all the prompts. Let me know how it goes or if you need specific help with it.

---


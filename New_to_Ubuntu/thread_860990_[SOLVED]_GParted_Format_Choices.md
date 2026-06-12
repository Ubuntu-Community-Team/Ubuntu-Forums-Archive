---
title: "[SOLVED] GParted Format Choices"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2008-07-16
I want to format my second hdd to install another linux OS (Puppy).  I was offered a choice of 'ext2, ext3, fat16, fat32, linux-swap or reiserfs,'
What does anyone recommend to use?

---

### Post by Canis familiaris on 2008-07-16
Ext3.

---

### Post by bumanie on 2008-07-16
+1 for ext3

---

### Post by Dumpy Dumpster on 2008-07-16
Many thanks Anurag_panda for your quick reply.
As a matter of learning more about Linux, do you know what the othere are for?

---

### Post by t0p on 2008-07-16
Yeah, could you explain why ext3 is "better" than reiserfs?

---

### Post by arkara on 2008-07-16
I recomend using the xfs file system if it is supported on puppy linux.

---

### Post by Canis familiaris on 2008-07-16
> **Dumpy Dumpster said:**
> Many thanks Anurag_panda for your quick reply.
As a matter of learning more about Linux, do you know what the othere are for?

Ext3 is the default filesystem for most Linux distributions. It is known for the fact that is really reliable, rarely fragments, and has good speed.
ReiserFS is more known for its speed but most users do not really find appreciable difference.
SWAP is the filesystem for Virtual Memory i.e. using your hard disk as memory when RAM runs out. Also when you hibernate data from RAM is flushed to SWAP so that you could resume from where you left off. SWAP is essential for most Linux distributions. Since I'm assuming you already have one Linux distro installed you may already have SWAP. If you dont already have one, you have to create a seperate SWAP as well.
FAT/FAT32 ar frankly legacy file systems. Use them only if you share files b/w Windows 9x and Linux. FAT/FAT32 are commonly used in USB FLash drives as well.

Wikipedia is your friend:
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)
[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)
[http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)

---

### Post by Canis familiaris on 2008-07-16
> **arkara said:**
> I recomend using the xfs file system if it is supported on puppy linux.
What are advantages of XFS? (just in interest)

---

### Post by Jim! on 2008-07-16
I'll also chuck Ext3 out there, Its the most widely used linux file system so your probably better off using it. It's also quite a good file system. Not perfect, but good;)

---

### Post by Barrucadu on 2008-07-16
XFS is very good with large files - however benchmarks have shown it slower with small files. I prefer JFS myself, good with big and small files, low CPU usage, very fast fsck if something goes wrong, and fairly reliable. The only problem with XFS/JFS is that you cannot shrink them, so if you want to shuffle your partitions around a bit there is a good chance you'll have to delete the partition and remake it at the smaller size (after backing up your data, of course).

---

### Post by Canis familiaris on 2008-07-16
> **t0p said:**
> Yeah, could you explain why ext3 is "better" than reiserfs?
Not better! Both are on equal footing IMO. I use both of them.
But EXT3 has  more support and no disadvantage as such so I recommended EXT3.

---

### Post by arkara on 2008-07-16
> **Anurag_panda said:**
> What are advantages of XFS? (just in interest)

I would say that the ext 3 files ystem is actually the file system of the stone age. It is so old.
it takes for example a very long time to delete a large file

xfs is not so good with small files, like small text files, but no real difference from ext 3

also ext 3 reserves 5% of your disk for journal and de-fragmentation.
which it does every 30 mounts.
you can of course adjust that.

---

### Post by t0p on 2008-07-16
> **arkara said:**
> ext 3 reserves 5% of your disk for journal

Is this just in the data=journal mode? I know that in the default data=ordered mode, ext3 journals metadata - but surely that doesn't take up 5% of the disk?!

---

### Post by arkara on 2008-07-16
> **t0p said:**
> Is this just in the data=journal mode? I know that in the default data=ordered mode, ext3 journals metadata - but surely that doesn't take up 5% of the disk?!

i am not sure but yes ti must be journal mode, which is the default on every distribution

---

### Post by Barrucadu on 2008-07-16
Ext3 reserves 5% of the disk for root, that is so you can't fill the disk up completely and break things by not being able to write any more.

---

### Post by Dumpy Dumpster on 2008-07-16
Thanks one and all - very interesting.  I have bookmarked for bit-by-bit digestion!

---


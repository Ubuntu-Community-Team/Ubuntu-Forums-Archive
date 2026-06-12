---
title: "[SOLVED] ext2 vs ext3"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Sitting Duck on 2008-12-01
Hello!

I have three questions about filesystems.

1) What are the differences between an ext2 and an ext3 filesystems?
2) When is it best to use an ext2 filesystem?
3) When is it best to use an ext3 filesystem?

Thanks for any answer.  My apologies if this has already been covered elsewhere already.

---

### Post by ncanna1 on 2008-12-01
I would generally always use an ext3 system.  ext3 has file system journaling, so that fsck isn't really a necessity anymore.  You don't have to sit through the entire fsck when booting from an ext3 system.  Also, I believe that there is a slight file transfer speed difference between the two, with ext3 being a bit faster.

---

### Post by Dj Melik on 2008-12-01
The main difference is ext3 supports journalism and ext2 doesn't; with that said ext2 is slightly faster than ext3.

Not really sure, I myself use ext3. It doesn't really make a REALLY big difference; just slightly safer I guess. I suggest using ext3.

---

### Post by SunnyRabbiera on 2008-12-01
Both are quite good, however ext3 is more recent and more powerful.
Its time for some homework:
[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

For your main install use ext3, but maybe you can use ext2 for external drives depending on how big they are.
Ext2 is still used by many, its a dated FS though made back in 92 while ext3 was made in 2002.
Support might drop off for ext2 once ext4 comes out though

---

### Post by Sitting Duck on 2008-12-01
Thanks everyone, much appreciated!

---

### Post by SunnyRabbiera on 2008-12-01
> **Sitting Duck said:**
> Thanks everyone, much appreciated!

If you elect to use ext2 you should be fine, but it does need defragging and checkups more often then ext3.
But both are lightyears ahead of ntfs in terms of stability in my experience.
Really its your option, but I suggest using ext3 as ext4 is right around the corner, it might be the standard FS for Ubuntu Jaunty the next Ubuntu release.

---

### Post by theozzlives on 2008-12-01
What about reiserfs???

---


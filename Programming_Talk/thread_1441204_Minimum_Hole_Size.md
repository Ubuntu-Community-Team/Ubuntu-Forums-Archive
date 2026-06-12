---
title: "Minimum Hole Size"
date: 2010-03-28
forum: Programming Talk
---

### Post by snag49ers on 2010-03-28
Does anyone know how to find the minimum size of a hole in Ubuntu?

---

### Post by tom4everitt on 2010-03-28
Exactly what sort of hole? :P (hole=opening, cavity or what?)

---

### Post by snag49ers on 2010-03-28
The hole that occurs when you use lseek() and you set the offset to be > than the filesize and then you write to it and a hole is created in the file.  Trying to figure out how big of a hole do you have to create to see the difference between the space actually used on the disk and the size the file displays.

---

### Post by mbsullivan on 2010-03-28
> Does anyone know how to find the minimum size of a hole in Ubuntu?

Yeah, what exactly are you talking about?

I'm intrigued. :)

Mike

---

### Post by mbsullivan on 2010-03-28
> 
The hole that occurs when you use lseek() and you set the offset to be > than the filesize and then you write to it and a hole is created in the file. Trying to figure out how big of a hole do you have to create to see the difference between the space actually used on the disk and the size the file displays.

Oh, okay! This thread would probably be better in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forum.

Mike

---

### Post by snag49ers on 2010-03-28
Does anyone know how to find the minimum size of a hole in Ubuntu? The hole that occurs when you use lseek() and you set the offset to be > than the filesize and then you write to it and a hole is created in the file. Trying to figure out how big of a hole do you have to create to see the difference between the space actually used on the disk and the size the file displays.

---

### Post by falconindy on 2010-03-28
This is called a sparse file. The resultant versus actual size of the file depends on how your filesystem handles it.

---

### Post by Sef on 2010-03-28
> This thread would probably be better in the [Programming  Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forum.

So moved.

---

### Post by gmargo on 2010-03-28
> **snag49ers said:**
> The hole that occurs when you use lseek() and you set the offset to be > than the filesize and then you write to it and a hole is created in the file.  Trying to figure out how big of a hole do you have to create to see the difference between the space actually used on the disk and the size the file displays.

I would guess that you'd need to get to a block size boundary, then go one more block size.  So if you seek past the end by 2 times the block size, you should see a difference.  Block size (sudo tune2fs -l /dev/sd1 | grep "Block size") on my system is 4096, so try 8192.

---

### Post by gmargo on 2010-03-28
Duplicate thread: see [http://ubuntuforums.org/showthread.php?t=1441204](http://ubuntuforums.org/showthread.php?t=1441204)

---

### Post by cariboo on 2010-03-28
Please don't create multiple threads on the same subject, I have merged your two threads.

---


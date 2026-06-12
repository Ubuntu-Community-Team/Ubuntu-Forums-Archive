---
title: "external USB drive read only"
date: 2015-09-10
forum: New to Ubuntu
---

### Post by campanella-alex on 2015-09-10
I want to use my external hard drive, now I have 1.5 TB free because the Chinese guy in the apple store deleted everything.
Of course I am in China and I don't speak Chinese...I just wanted to turn off journalling...

Anyway, I have 1 partition in FAT32, works fine.
This other one...

I have tried re formatting and deleting and creating new partitions...
FAT, NTFS, LINUX file types, it does not matter.
every time I try, it says this partition is read only.
The other partition is FAT32 and works no problem!

I have already tried changing permissions in nautilus, it does not let me!
even with gksu nautilus!
Also using the terminal, remount -0,rw and -default settings no luck.

I have already had to borrow my roommate's computer to re format my thumb drive because apparently
usb drives are not meant to be actually used after formatted in Ubuntu.


uname -a
Linux campy-TP550LA 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by yancek on 2015-09-10
> I want to use my external hard drive, now I have 1.5 TB free because the Chinese guy in the apple store deleted everything.

Why did you take your computer to the Apple store and why did he delete everything?  What was the problem?

What is the FAT32 partition?  Is that a data partition?  What software are you using to re-format?  You might do a filesystem check with fsck from a Live DVD.

---

### Post by Bucky Ball on 2015-09-10
If you are using Ubuntu, open a terminal and:

```
gksudo nautilus
```

ONLY navigate to where the partitions are mounted (probably /mnt or /media), right click, permissions, change 'em. CLOSE the Nautilus window. 

When you log in with gksudo you are root, so ONLY do the instructions above and don't change anything else. :) NTFS if you are sharing with Windows, EXT4 if you never will.

---

### Post by campanella-alex on 2015-09-10
To clarify for the first poster, yancek:
I did not bring my computer to the Apple Store; the computer is fine it's just me seagate external I'm having trouble with. I read that linux has problems with hfs+ drives that have journalling enabled, so I figured I'd turn that off. 

For the second poster, buckyball? Sorry I'm on iPhone can't read previous comments on this page. 
I already tried exactly this. 
When I am in the permissions area, I go to Others and I choose read and write from the drop down, but as soon as I click on it, the drop down list closes and reverts back to read only. So I can see and choose that option, but it never sticks into place. 

Thank you for your responses. After a good night sleep I am no longer feeling like a murderous bastard and that's good.

---

### Post by campanella-alex on 2015-09-10
Actually I did "gksu nautilus" not "gksudo nautilus" probably no difference but I will try that in a few hours when I get back

---

### Post by campanella-alex on 2015-09-10
SO, I just got back started up my computer, and I can now write onto this partition...I guess it was a bug?
Just to make sure I deleted the partition, and created a new one in the same place, still works fine! ...

I also tried gksudo nautilus, and even with that, I still cannot change permissions.  But it looks like it does not matter...on the other partition that I know works with windows PCs, it says under Group and Others, the access is set to None.

So it looks like this problems solved itself.

Thanks again...spooky stuff though right...I've been working at this for days, updating all the time, and now all of a sudden it decided to work...

---

### Post by Bucky Ball on 2015-09-11
Quite bizarre. Please see the first link in my signature. It won't close the thread, but it will help others. 

Weird, though. :-k

---


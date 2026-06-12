---
title: "the best format"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by theRightNee on 2008-05-07
hey all,
going to format my hard drive so that ubuntu can write to it (currently NTFS, and i am using diskmounter to automount because manually editing is not working out for me) and i thought why stick to FAT? i am sure one of the other alternatives are better, but i have no experience in this area, so i am bringing it up. 

which is the best format? (let the debate begin)

:lolflag:

---

### Post by HotShotDJ on 2008-05-07
> **theRightNee said:**
> which is the best format?[LIST]
[*]General Purpose: ext3
[*]A boot partition: ext2
[*]A home partition (usually lots of small files): reiserfs
[*]A large partion for file storage: xfs
[*]A small USB drive: FAT32
[*]A large USB drive (that you will use with Linux and Windows): NTFS
[/LIST]

---

### Post by Monicker on 2008-05-07
Is the drive going to be accessed by Windows also?  If so, NTFS is your best bet.  It handles problems, such as an ungraceful shutdown, much better than FAT32.

---

### Post by JustinJS on 2008-05-07
to be able to write to your ntfs just go to ur terminal type in ```
sudo gedit /etc/fstab
``` and delete the ro, after it say NTFS on the drive your auto mounting

---

### Post by Xiong Chiamiov on 2008-05-07
HotShotDJ pretty much got it.  If it's Linux only, the general choice is ext3.  Not only is it journalled (a little complicated to understand, but it writes all changes to a "journal" before making the hard drive commits, so it recovers from crashes better), but FAT32 has a filesize limit of, what, 4 gigs, which can be annoying sometimes if you're not expecting it.

---

### Post by theRightNee on 2008-05-07
sorry i wasn't too clear before, but this is only for a ubuntu machine, i virtualize windows now =]

o and i cannot write to the NTFS drive because i am using a diskmounter script, which being written at the time of Dapper Drake, has limtied NTFS write capabilities. i would rather not use it, but i cannot seem to automount the hard drive without it...and i need to do some spring cleaning anyway...what better than with a newly formatted hard drive?

---

### Post by HotShotDJ on 2008-05-07
> **theRightNee said:**
> sorry i wasn't too clear before, but this is only for a ubuntu machine, i virtualize windows now =]Ok.  But what do you plan to use this harddrive for?  Small, frequently accessed and changed files (such as your home folder)?  Storing large files that don't change much (such as a music or video collection)?  Just general purpose stuff?  A combination of all of the above and other things I didn't think of (or don't WANT to think of ;) )

---

### Post by Monicker on 2008-05-07
> **Xiong Chiamiov said:**
> HotShotDJ pretty much got it.  If it's Linux only, the general choice is ext3.  Not only is it journalled (a little complicated to understand, but it writes all changes to a "journal" before making the hard drive commits, so it recovers from crashes better), but FAT32 has a filesize limit of, what, 4 gigs, which can be annoying sometimes if you're not expecting it.

Disregard previous. I was thinking of partition size, and not file size.  :)

---

### Post by theRightNee on 2008-05-07
> **HotShotDJ said:**
> Ok.  But what do you plan to use this harddrive for?  Small, frequently accessed and changed files (such as your home folder)?  Storing large files that don't change much (such as a music or video collection)?  Just general purpose stuff?  A combination of all of the above and other things I didn't think of (or don't WANT to think of ;) )

lol...i could only imagine what you do not want to think of...

anyway, no its just more of an annoyance that I have to move my files from one hard drive to another just to edit them...for example, i cannot put my virtual windows folder on my second drive because i cannot write to it...and so its a bother to move it...want to prevent this in the foreseeable future

---

### Post by HotShotDJ on 2008-05-07
> **theRightNee said:**
> anyway, no its just more of an annoyance that I have to move my files from one hard drive to another just to edit themOk.  Sound almost like you want it to serve as an extension of your home directory.  My preference would be reiserfs (don't mess with version 4... stick with the standard, tried and true, version 3).  Ext3 would also be an appropriate choice.

---


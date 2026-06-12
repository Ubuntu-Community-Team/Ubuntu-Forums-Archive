---
title: "[SOLVED] Can't copy DVD iso to flash drive"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Preturbed on 2008-10-07
Is there a max file size for what I can put on a flash drive? I'm trying to copy a 4.3 gig iso to it and it stops a 4.0

---

### Post by talsemgeest on 2008-10-07
If the flash drive is formatted as fat32, then I believe the physical limit is 4GB for a single file. If you want to fit more on, you can either put the file into a 2 part archive, or format the flash drive as something like ext3, or maybe ntfs.

---

### Post by jrothwell97 on 2008-10-07
I'm assuming the flash drive is more than 4.3gB?

---

### Post by rg_stephens on 2008-10-07
> **talsemgeest said:**
> If the flash drive is formatted as fat32, then I believe the physical limit is 4GB for a single file. If you want to fit more on, you can either put the file into a 2 part archive, or format the flash drive as something like ext3, or maybe ntfs.

This is exactly right. EXT3 will work better than FAT32, and you won't have the 4GB limit, but you'll have install a driver on your Windows machines to be able to read it, such as EXT2IFS.

---

### Post by jerome1232 on 2008-10-07
Another work around would be the split the iso file into two pieces as has been stated a few times fat file system can't hold fat files. (It wasn't a very good pun I know)

to find out more about split you can check it's man page, you would use cat to put the file back together.
```
man split
```

If you want to go the formating route to a different file system and you require portability between Linux and Windows I would actually recommend NTFS, since most modern Linux distro's now have native read/write support for it. (Windows doesn't have a clue about Linux file systems without 3rd party drivers)

---

### Post by Preturbed on 2008-10-08
> **jrothwell97 said:**
> I'm assuming the flash drive is more than 4.3gB?

16 gigs, actually. Thanks everyone for the info. :-)

Oh, and this flash drive came with something called U3... if I take the stuff that came on it and put it on my hard drive while I format, will u3 still work properly? Should I even worry about it?

---

### Post by talsemgeest on 2008-10-08
It should work, unless it only supports fat32. If that is the case, all you need to do is reformat it back to fat32 when you want to put it back on.

---

### Post by jerome1232 on 2008-10-08
U3 is probably some stupid program they had already sitting in there, if you haven't used it I doubt you will miss it.

edit: can you give any more detail on what U3 is before you format.

---

### Post by Preturbed on 2008-10-08
Actually it's kind of nifty. Can install a variety of programs onto the drive including Firefox/Thunderbird and keeps settings so the user can run them anywhere.

---

### Post by talsemgeest on 2008-10-08
I think portable apps might be even better...

[http://portableapps.com/](http://portableapps.com/)

---

### Post by Preturbed on 2008-10-08
Well then I wont worry about it :-D

---


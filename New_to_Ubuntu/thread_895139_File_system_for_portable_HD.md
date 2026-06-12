---
title: "File system for portable HD"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-08-19
So I just bought an enclosure for an old 80GB hard drive I had kicking around and now I'm left with the question...what should I format it to? I'd like to be able to plug it into Windows PCs and heck, why not be able to use it on a Mac as well...so my question is, what file system should I format it to? FAT32 seems to be the most compatible though I've heard it's horribly inefficient, as in, I won't be able to use the full 80GB or something... (as you can guess, I'm an idiot when it comes to file systems...truth is, I didn't even know there were different kinds until I started using Linux) 

Thanks.

---

### Post by halitech on 2008-08-19
any file syste will use some of the space to keep system files in. FAT32 looks like the easiest but from what they say here: [http://blog.adamnash.com/2007/05/25/how-to-mount-ntfs-drives-on-mac-os-x-with-readwrite-access/](http://blog.adamnash.com/2007/05/25/how-to-mount-ntfs-drives-on-mac-os-x-with-readwrite-access/)  MAC can read NTFS with a little work

---

### Post by shatteredmindofbob on 2008-08-19
> **halitech said:**
> any file syste will use some of the space to keep system files in. FAT32 looks like the easiest but from what they say here: [http://blog.adamnash.com/2007/05/25/how-to-mount-ntfs-drives-on-mac-os-x-with-readwrite-access/](http://blog.adamnash.com/2007/05/25/how-to-mount-ntfs-drives-on-mac-os-x-with-readwrite-access/)  MAC can read NTFS with a little work

Yeah, but odds are if I need to access my files from someone's Mac, they won't exactly want me doing "a little work" hence why loading ext3 drivers into Windows is also out. 

Thanks for clarifying the space thing, though. Looks like FAT32 it is.

---

### Post by halitech on 2008-08-19
glad to help out :)

---


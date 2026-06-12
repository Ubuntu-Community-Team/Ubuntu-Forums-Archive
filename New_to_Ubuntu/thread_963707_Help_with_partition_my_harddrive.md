---
title: "Help with partition my harddrive"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-10-30
Hello

I'm about to install ubuntu but have a question regarding how to set up my harddrive, I got 160 GiB harddrive and I got some files that I rarley use and simply want to store them somewhere. I wonder what is the best way to set it up.

Alt1.
one partition + swap

Alt2.
following partitions
/ (10GiB or so)
/home (140 GiB)
/swap

Alt3
following partitions
/ (10GiB or so)
/home (50 GiB)
/Storage (100 Gib) 
/swap

Would alt3. have a less tare on the harddrive then 1 and/or 2 ?

---

### Post by mapes12 on 2008-10-30
I would go for alt3 and use GParted to set the partitions up. Making sure the partitions are formatted withe the correct filesystem, particularly "storage" which may need to be Fat32 or NTFS depending on what files you want to keep.

---

### Post by Het Irv on 2008-10-30
I don't think one option is better over another in terms of wear and tear, but Alt2 is probably going to be the best in the long run.  With Alt2 it is much easier to upgrade your computer or reinstall if need be.  If you have little used files, it might just be easier to make a seperate folder in your Home partition labeled, "Little Used Files" or something like that.

---

### Post by cdtech on 2008-10-30
Separating partitions is the best in my opinion. If you ever need to reinstall, you wont loose your personal settings or storage using "alt 3". Formatting the storage to an NTFS will also allow you to share the partition with a dual boot setup as well.

---


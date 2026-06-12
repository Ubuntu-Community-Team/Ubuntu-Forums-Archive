---
title: "How can I copy files from old pc to new but retain datestamp"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by philinux on 2008-05-06
of original file. These are photo's and I'm using a usb stick to copy.

---

### Post by ro314 on 2008-05-06
I would say something like:
cp -pR /media/mystick/music /home/user/

The "R" tells the copy command to copy directories recursively,
the "p" tells the copy command to preserve mode, ownership and timestamps.

See also: 
man cp

greetings, robert

---

### Post by philinux on 2008-05-06
Ah right but I only want the time stamp and it's going via usb so I gues I'll have to format the usb stick to ext3. It's vfat just now.

---

### Post by ro314 on 2008-05-06
When I try with my vfat-usb-stick the timestamp is preserved.

---

### Post by philinux on 2008-05-06
All th pics copied off the usb to new pc have 3/5/08 as there modified date which is when I did the copy.

[edit]

cp -R --preserve=timestamp folder1  folder2 works a treat.

---

### Post by timcredible on 2008-05-06
tar the files, then all file permissions, timestamps, etc. are preserved, no matter what the target filesystem.

example:

to tar up file: tar -cvf <tarfile> <directory to tar>
to untar them: tar -xvf <tarfile> <directory where you want files to go>

This is standard unix/linux stuff.  you can also use ark if you prefer a gui (runs the same command).  ark is available via synaptic

---

### Post by philinux on 2008-05-07
> **timcredible said:**
> tar the files, then all file permissions, timestamps, etc. are preserved, no matter what the target filesystem.

example:

to tar up file: tar -cvf <tarfile> <directory to tar>
to untar them: tar -xvf <tarfile> <directory where you want files to go>

This is standard unix/linux stuff.  you can also use ark if you prefer a gui (runs the same command).  ark is available via synaptic

I marked this as solved as I did not need permissions etc only timestamp. The cp worked fine.

---


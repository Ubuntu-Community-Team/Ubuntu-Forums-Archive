---
title: "ntfsclone syntax"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by Gary Nored on 2013-06-12
I have ubuntu laptop (12.04.2) with 2 ntfs drives connected: sdg1 (a backup drive for windows) and sdb1 (a non-booting win 7 drive). Ultimately I'm hoping to move sdb1 to a new hard drive and use win rescue to repair anything that's broken (miracles happen ... I'm sure of it ... I think ...)

I want to clone sdb1 onto sdg1 possibly using rescue option. I've read the man page, and other pages but I just can't figure out the syntax for what I want to do. Since the target drive is my backup drive, I really don't want to hurt it! 

Here's my best guess. Am I right?   

     ntfsclone -s --rescue /dev/sdg1 /dev/sdb1

Many thanks.

---


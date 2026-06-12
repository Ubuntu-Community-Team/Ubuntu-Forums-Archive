---
title: "Solaris 10 gives incorrect size of hard drive"
date: 2007-10-23
forum: Other OS Talk
---

### Post by rudeboyskunk on 2007-10-23
I would have posted this on the solarisforums site, but that site is worthless because there are about 0 members (give or take 0) that answer questions.

Why does Solaris 10 say that my 80gig hard drive is 78gigs?  PCBSD and Ubuntu both say it's 80gigs.

---

### Post by Gen2ly on 2007-10-23
Are you using the same tool to measure both?

fdisk -l will give you an accurate value in both.

---

### Post by rudeboyskunk on 2007-10-23
I wasn't, and the command "df" doesn't really help much in Solaris.

I got the Solaris value from the install of Solaris (before I partitioned the hard drive).  But when I get home I'll give that command a shot.  Thanks.

---

### Post by D-EJ915 on 2007-10-24
Well, for one thing, different file systems will format disks to different usable sizes, that could be what is causing it.  Solaris uses UFS

---

### Post by Quadcore on 2007-10-26
df -h

I hate solaris a lot..

---


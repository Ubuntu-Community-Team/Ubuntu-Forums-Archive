---
title: "Missing hard drive space in ubuntu 8.04"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by KameZero on 2008-06-28
This is incredibly odd.

I have 2 hard drives, a 20 gig and a 180 gig.

The 20 gig has 2 partitions, a 729 MiB swap partition and a 17.93 GiB partition. The problem is that according to GParted there is 15.04 GiB used and 2.90 GiB free. Every other program on the computer however only sees 2.0 gig free. While .9 gig isn't much my 180 gig drive has the same problem.

GParted reports 149.05 gig total, 112.00 GiB used and 37.05 GiB unused, while everything else only sees 29.6 GiB of unused space, almost 9 GiB of missing space.

I can't think of anything that could be causing this, any help would be much appreciated.

---

### Post by Bakon Jarser on 2008-06-28
Could it be that one is reporting sizes in GB (1GB = 1024MB = 1024KB) and the other is reporting sizes in GiB (1GiB = 1000MiB = 1000KiB)?  I'm too lazy to do math right now but you might want to check the calculations and see if it works out.

---

### Post by KameZero on 2008-06-28
Well, according to [Google,]("http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=Kj7&q=2.9+gigabits+to+gigabytes&btnG=Search") 2.9 Gigabytes would only be .3625 gigabytes rather than 2... so I'm guessing that's not it.

---

### Post by Bakon Jarser on 2008-06-28
Wrong calculator.  1byte = 8 bits.  We're talking gigabytes versus gibibytes.

---

### Post by jw5801 on 2008-06-28
> **KameZero said:**
> This is incredibly odd.

I have 2 hard drives, a 20 gig and a 180 gig.

The 20 gig has 2 partitions, a 729 MiB swap partition and a 17.93 GiB partition. The problem is that according to GParted there is 15.04 GiB used and 2.90 GiB free. Every other program on the computer however only sees 2.0 gig free. While .9 gig isn't much my 180 gig drive has the same problem.

GParted reports 149.05 gig total, 112.00 GiB used and 37.05 GiB unused, while everything else only sees 29.6 GiB of unused space, almost 9 GiB of missing space.

I can't think of anything that could be causing this, any help would be much appreciated.

This is because GParted looks low level to the actual content on the disk itself. Whilst everything else adds up the sizes of all the files reported by the filesystem. Therefore anything that is hard-linked will be counted twice. The 2.9GB would be the correct value, does it really make much difference if things report less free space than is really present? Filling a file-system to the absolute maximum is not really advisable anyway.

---

### Post by KameZero on 2008-06-28
Yeah, but I'm losing almost nine gig on the second drive... which is more than I really want to be losing. the .9 gig I'm missing doesn't even really matter.

Oh well, thanks for the information.

---

### Post by jw5801 on 2008-06-28
Well, you're not 'losing' 9GB, it's just being reported as having less free space than it really does. I would assume you can still use that disk space.

---

### Post by KameZero on 2008-06-28
No, once the 2 gig on the first hard drive is used up, the system reports that there is no free space, even though I should have .9 gig free (according to GParted). And things that require free space to run (open office for example) won't work.

---

### Post by Bakon Jarser on 2008-06-28
I might be wrong, but if I remember right doesn't the file system itself take up some space?

---

### Post by jw5801 on 2008-06-28
Ok, then the assumption that GParted is reporting it correctly is probably wrong. File a bug a launchpad bug against GParted if it's worrying you lots. The folks who'll reply to that will know much more about it than me. :)

---


---
title: "Missing Storage space ?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by nnjond on 2008-07-01
Hi,

My sdb is a 250gb HDD, So why does Gparted claim its  size is only 233gb ?

---

### Post by wrtpeeps on 2008-07-01
> **nnjond said:**
> Hi,

My sdb is a 250gb HDD, So why does Gparted claim its  size is only 233gb ?

You on a laptop that came with windows installed?

---

### Post by avtolle on 2008-07-01
Simplest answer is that the system reserves approximately 5% so that there is a bit of room there to work with when the disk is essentially full, to avoid crashes. There's a way to reduce the amount of space reserved, but I am not familiar with it.

---

### Post by chrisccoulson on 2008-07-01
It is related to the way hard disk manufacturers report disk space. When they say 250GB, what they actually mean is 250000000000 bytes. Because 1kB = 1024 bytes, 1MB = 1024kB and 1GB = 1024MB, then your hard disk size is actually equal to (250000000000/(1024^3))GB = 232.83GB ~ 233GB

---

### Post by nnjond on 2008-07-01
My sdb is just used for data in my desktop pc. I understood I had fat 32d the all 250gb, but it shows up as 233 in gparted

---

### Post by hyper_ch on 2008-07-01
250 GB != 250 GB ^^

see chrisccoulson's post

---

### Post by Canis familiaris on 2008-07-01
It is because manufacturers use the factor of 1000 instead of 1024.
So you have:
(250  * 1000 * 1000 * 1000)/(1024 * 1024 * 1024) = 232.830643654 => 233 GB

---


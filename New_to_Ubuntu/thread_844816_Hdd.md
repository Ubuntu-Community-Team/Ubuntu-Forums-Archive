---
title: "Hdd"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by davarse on 2008-06-29
hi evryone,
i have acer aspire 5920G laptop and i have 250G hdd. when i check i much space that i have when i copy a video suprisingly it shows i only have 255,3 Gb hdd over all. anyway, i still have lots of space to save in my hdd. but i just wondering where is the rest of the memory?
i looked at the system monitor too, and it says i just have 225,3 Gb hdd 
i used gusty before, and i install hardy with the live cd. and i chose for the entire disk...

my question is how can i used my entire disk? or even just to maximized the disk?

maybe some of the memory used for gusty? i don't know.

and also i have a look on the system requirement to install hardy at just 4Gb..

i really appreciate the answer for it.

cheers'

---

### Post by phidia on 2008-06-29
OK, if I'm understanding you you are asking what happen to about 25GB from the stated hard drive capacity of 250GB.
After formatting all hard drives have less actual space than the claimed maximum size.
So what you are seeing is normal.

---

### Post by Inxsible on 2008-06-29
1) 1 kilobyte = 1024 bytes. However, the manufacturers often use 1 KB = 1000 byte, to catch customers attention thereby resulting in hyped up numbers. So the capacity of the drive is always less than declared by the manufacturer

2) Any filesystem that you install on it, like EXT3 or NTFS or FAT32 takes up some space as well. 


So you often see less space than what is advertised on your drive

---

### Post by ercferret18 on 2008-06-29
yeah, formatting a hard drive makes some of the space taken up, this is normal.

---

### Post by logos34 on 2008-06-30
I've often wondered how drive manufacturers can get away with advertising capacity with the formula '1 GB = 1,000,000,000 bytes, when all OSs see GB in binary form, 2^30, or 1 GB = 1,073,741,824.

---

### Post by davarse on 2008-06-30
thanks guys... i understand bit more now

---

### Post by kuja on 2008-06-30
1000 * 1000 * 1000 / (1024 * 1024 * 1024) = ~0.93
250GB * 0.93 = ~232.83GiB

---

### Post by phidia on 2008-06-30
> **logos34 said:**
> I've often wondered how drive manufacturers can get away with advertising capacity with the formula '1 GB = 1,000,000,000 bytes, when all OSs see GB in binary form, 2^30, or 1 GB = 1,073,741,824.

This is in the same category as advertising the diagonal dimension of a monitor or TV screen-rather than the height & width which would would be two smaller figures. Bigger is better it seems in the consumer's mind so business gives us what we want-although with hard drive capacity they've actually "converted" from binary to decimal.

---


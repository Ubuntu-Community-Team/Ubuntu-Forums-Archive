---
title: "no hard drives"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by eddiemec on 2008-10-17
I am running ubuntu from the live cd and want to install it on a hard drive. I have three hard drives installed on my computer; the installer only recognizes one. How do I get to see all of my partitions on all the drives?

---

### Post by Orange_and_Green on 2008-10-17
Hello :) That looks like a very bizarre behaviour, doesn't it...

Are all three of them on the same bus (IDE? SATA? SCSI?) Or are they on separate ones? 

If you're using IDE and the two failing drives are on the same channel (like both on primary or both on secondary), try moving one to the other channel (I once had a defective controller that would only see the secondary channel :))

Also, if you are using SATA, try plugging the drives into different sockets and see if anything changes (another direct experience of mine... One time I had to work on one motherboard where two out of six SATA bus sockets wouldn't work...)

Also, if the missing drives have NTFS partitions, they might have been shut down improperly, so you might need to mount them manually the first time with the "-o force" option.

Keep us posted, good luck:KS

---

### Post by eddiemec on 2008-10-17
two are ide; one primary the other secondary. The drive the installer recognizes is a scsi with a cd-rom with it

---

### Post by Orange_and_Green on 2008-10-18
What happens if you move them to the same channel?

---


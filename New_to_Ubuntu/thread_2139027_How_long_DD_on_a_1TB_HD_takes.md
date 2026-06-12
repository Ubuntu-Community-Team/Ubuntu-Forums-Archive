---
title: "How long DD on a 1TB HD takes?"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by Juniorr on 2013-04-25
Hello.


I bought a 1TB drive and I'm planning on doing DD on it. It's a WD, so I guess using a Seagate disk to wipe is not recommended.


What does it take? (what commands), How long? Does doing it very often hurts the drive? (my old 320GB drive had +4000 reallocated sectors)


All I'm used to do is:


* Erase the partition table with $sudo dd if=/dev/urandom of=/dev/sda count=1


* Create random size partitions with random file systems


* Delete all partitions


* Erase the partition table again and then create the partitions I needed.


Are those above enough, let's say, in a virus case, a bootloader virus or a MBR virus? WHY and in what cases are DD needed besides selling the drive? How is data recoverable? Can the FBI recover it? :P


Currently my partitions are:


- 320GB for Windows, used ONLY for games, nothing pirated
- 40GB for /
- 571GB for /home, encrypted.


Thanks in advance.

---

### Post by deadflowr on 2013-04-26
When running dd to wipe a disk, what you are doing is going byte by byte and overwriting the information that is on there.
You're using the random character method, I would assume others would use the zero method, where by they'd overwrite the disk with zeros.
It moves fast, but remember it is literally going from one byte to next, so it'll take a while.
If you really wanted to totally make sure it wiped everything out for sure, use dd twice, maybe once with random string and once with zeroes.
That's my opinion on it though, others will have theirs.

---

### Post by Irihapeti on 2013-04-26
One pass of dd seems to be enough to erase data. See [http://computer-forensics.sans.org/blog/2009/01/15/overwriting-hard-drive-data/](http://computer-forensics.sans.org/blog/2009/01/15/overwriting-hard-drive-data/) for more detail.

---

### Post by Bashing-om on 2013-04-26
Juniorr; Hi !

My experience with the dd time to write -> 1 hour per gig; as in 500 GB drive == 5 hours, 1 TB then is about 10 hours .

See:
```
man dd
``` for a work-about-it to monitor the progress of dd's status.[INDENT=2]
hope this helps

[/INDENT]

---

### Post by Paqman on 2013-04-26
> **Juniorr said:**
> 
* Erase the partition table with $sudo dd if=/dev/urandom of=/dev/sda count=1


Using random data will take longer than simply filling the drive with zeros, and isn't any better at overwriting the contents. I'd use /dev/zero instead of /dev/random

> 
* Create random size partitions with random file systems


* Delete all partitions


This step is completely unnecessary. Zeroing the whole drive will have got rid of anything and everything on it.

---

### Post by sudodus on 2013-04-26
I suggest that you use ***hdparm***, which uses low level firmware of the HDD, and it is much faster than dd, and it is also considered more secure, because

1. It also clears hidden areas (not available directly from the operating system, but used to replace bad sectors automatically)
2. It changes the encoding how physical addresses are tied to logical addresses.

The method is described and discussed in the following thread.

[[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2124829[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2124829")

An alternative is ***DBAN***.

---


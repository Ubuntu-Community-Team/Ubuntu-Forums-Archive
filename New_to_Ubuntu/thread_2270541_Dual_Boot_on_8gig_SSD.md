---
title: "Dual Boot on 8gig SSD"
date: 2015-03-23
forum: New to Ubuntu
---

### Post by Dan_Dunagan on 2015-03-23
I just purchased a Lenovo Y 70 and one of the things I like about it is the OS (Windows 8.1) is on a 8gig SSD and then there is a 1tera. HDD. I want to be able to install Ubuntu on the SSD along with Windows but I can't seem to find anything on how to do this. Any help would be greatly appreciated.

---

### Post by bardo2 on 2015-03-23
doesn't sound like a realistic goal to me:
Ubuntu partition alone > 15 GB
Windows OS > 25 GB

So how to put both on 8 GB?
The speedup from SSD is worth buying a bigger one IMHO. Or to think about more specific uses.
I heard, some HD vendors nowadays sell combination products, where SSD basically acts as cache for the HD. I have no experience, but would be critical towards marketing fluff.

---

### Post by v3.xx on 2015-03-24
The way I read the specs, it has 1TB HDD and 8G of ram.

---

### Post by Bucky Ball on 2015-03-24
Welcome. Is this a 'hybrid' drive? An SSD and HDD married together in the one unit? As bardo2 implies, Windows 8 would no way fit on an 8Gb any-drive let alone installing Ubuntu alongside it on that 8Gb drive. :-k

---

### Post by DuckHook on 2015-03-24
> **Bucky Ball said:**
> Welcome. Is this a 'hybrid' drive? An SSD and HDD married together in the one unit?That's exactly what it is&#8213;one of those loopy drives where the SSD is supposed to act as cache so that the manufacturer can pair it to a putrid HDD and supposedly get the best of both worlds. In practice, they tend to deliver the worst of both worlds as per [this]("http://www.notebookcheck.net/Lenovo-Y70-Notebook-Review.128841.0.html") review. Moreover, they require special drivers that, last I heard, are only available in Windows. If the SSD could truly act independently of the HDD, then in theory, one could install Ubuntu on the SSD with /home, /tmp, /var, and swap on the HDD and be off to the races. But my understanding is that the SSD is hard baked to the HDD and cannot be treated as a separate disk drive.

If anyone knows differently, I would love to know how to split them.

OP's machine is supposed to be quite the race car. It's a shame when manufacturers choose to pair a brute of an engine to a lousy transmission.

---

### Post by oldfred on 2015-03-24
In most cases it is just using the SSD as cache, particularly for fast booting. It is to make you think Window 8 is better than Windows 7.

Some have larger SSD of 32GB and only the 8GB is used. I have seen where then they had enough unused space to install / (root) only on the SSD and made Ubuntu fast. But  8GB by itself is too small unless just a very minimal install or perhaps server without gui. The / will fit but you will run out of room quickly. And then you do not have the cache for Windows "fast" boot.

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

---


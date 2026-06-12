---
title: "Steps to Triple Boot Ubuntu and Windows 7 and Windows Developer preview"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by BLUEWAFFLE23 on 2012-03-03
Anyone able to give steps to install Ubuntu 11.10 on my computer starting at formating my Flash Drive? Im very confused.:confused:
 
When done id like Ubuntu added to my choice of Operating Systems to boot when i start my computer up. (Allready have Windows 7 and Windows Developer Preview)
 
 
Acer Aspire 5517
250 Gb HDD
14.94 Gb Ultra Speed USB Flash Drive
 
In Photo Attachement:
C: = Windows 7
W: = Windows 8 Dev Preview
U: = Where I want Ubuntu (17.60 Gb NTFS)
G: = USB Flash Drive im using to install Ubuntu (14.94 Gb NTFS)
[ATTACH]213637[/ATTACH]

---

### Post by Mark Phelps on 2012-03-03
Installing to "U" (NTFS) requires that you use Wubi -- and I believe that does NOT work with Win8 -- DP or CP.

---

### Post by oldfred on 2012-03-03
You have installed Win8 to a logical partition. All of the boot files will be in the active partition or boot flagged partition. 

Unless using wubi as Mark Phelps mentions, you need Linux partitions ext3 or ext4 for Ubuntu. The minimum partitions are / (root) and swap, but we often suggest /home and/or a shared NTFS partition just for data to be used by all systems. 

The root partition needs to be 10 to 20GB, Swap can be 2GB or up to the size of RAM in GiB (not GB) so it can be used for hibernation. It may need to be larger if you edit video files or do some extremely intensive memory programs. Normal use now with most system does not need much swap.

Some discussion of other choice on swap.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)
I prefer sleep and shutdown to hibernate.
'Dynamic Swap Space Manager' from the Ubuntu Software Center

---


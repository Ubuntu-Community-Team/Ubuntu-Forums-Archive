---
title: "Swap Partition Lost in Windows 8"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by RaheelFarooq on 2013-05-14
Hi,
I was much eager to install Ubuntu on my PC before I realized that it may need some programming skills to be operated properly. I further came to know that my family, and even I myself, had troubles familiarizing ourselves with the interface and features.
When I was installing Ubuntu on my system, there came some error and I just blindly made one of my most valuable drives a "swap" to install Ubuntu. I didn't even know what "swap" actually meant, and still don't. But I did it. And the partition never appeared again, neither in Ubuntu nor in Windows 8 now.
I had very important data in the partition. Now that I have turned back to Windows 8, all I want is to retrieve the data and undo the "swap" to regain regular access to my drive from "My Computer." Is there anyone who could help me please?

---

### Post by oldfred on 2013-05-14
Welcome to the Forums.

STOP using system and do not boot with liveCD as that uses swap and will overwrite data.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
    
Swap is RAM memory overflow when you use more applications at once than you have room for in RAM. If you have a newer system with 4GB or more of RAM you may not have used swap or much of it and your data or most of it may still be there. Swap is just unformatted space so it is not really used until you need it.
But many Live installers like Ubuntu use swap to speed up booting & running from a slow CD, you need a Linux repair CD that does not use swap. 
I think parted magic, gparted or Knoppix do not use swap but am not 100% sure. 
Do not reformat the partition, but change its partition type back to what it was. If it was NTFS then it was 07.

 [http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

It looks like default boot includes the noswap parameter which you really want.
[http://gparted.sourceforge.net/livehd.php](http://gparted.sourceforge.net/livehd.php)

---


---
title: "Partition Plan"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by EPrips on 2008-11-07
Hi everyone. I'm a Windows user currently looking into Ubuntu, as I feel some odd need for change. I'm pretty sure I want to Dual-Boot, as opposed to using VirtualBox. Looking at PyschoCat's guide, my options appear to be Wubi, or a normal Dual-Boot. I'm trying to figure out what the downside to using Wubi is, so if anyone can help me out there that'd be great. I'm also trying to determine what partition plan to go with should I decide not to use Wubi. Pyschocat's favorite ([http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) - 5th one down) looks good, although I'd need to read up on /home. 

What would you recommend for a brand new Ubuntu user? 

P.S. What precautions do I need to take while partitioning to make sure that I don't lost any of my current data? Is it just a matter of looking at how much of my HD is currently being used and making sure I partition more than that amount to Windows?

Edit: I've also got an external HD, but I'm not sure how to use it to partition.

---

### Post by asgard_command on 2008-11-07
I can't comment on wubi never used it but I can tell you how I set up the partitions for my duel boot laptop.
I leave 40GB for windows leaving 60GB for linux. Of the 60 I set 15GB for the root partition and use the rest as my home partition, with 1GB for linux swap.
Personally I would use the external drive for extra data storage and backup.

---

### Post by Karilex on 2008-11-07
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://ubuntuforums.org/showthread.php?t=973924](http://ubuntuforums.org/showthread.php?t=973924)

Good luck and if I were you I would probably back up my home folder or any important files on an external hard drive or some other storage medium.

---

### Post by EPrips on 2008-11-07
Alright thanks guys. One last question. If I'm currently using 156GB of my C drive, do I have to partition that amount to Windows to avoid losing data?

---

### Post by BGFG on 2008-11-07
The Ubuntu install easily recognises partitions made in windows so you can create the partition in windows, boot into the liveCD and when the install comes to the disk partitioning part you'll see the new empty partition that you created for ubuntu. 
As for the partition setup. The first time i installed Ubuntu, i let the installer set me up so i had /, /home and /swap on the same partition.

Second time around in Intrepid I used the 'Manual' option in the installer to set up /, /Home and /Swap on separate partitions. Makes life easier for future upgrades.
My signature has a link to a partitioning guide screencast which should give you a good idea of what to do.

---

### Post by Karilex on 2008-11-07
Yes but if you want to move these files into a common partition for ubuntu and windows i would suggest saving all your files on a separate disc making a fat32 partition then moving everything into that so you can read it with ubuntu and windows

---

### Post by EPrips on 2008-11-07
Alright, I guess I'll just back up everything to be safe. Thanks guys.

---


---
title: "[SOLVED] How to reduce the swap partition"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by ellalan on 2008-09-09
Hi
I suspect my swap partition is too big and thinking of reducing the size to an acceptable level for a smooth operation.
I have recently re-installed Ubuntu 8.04 and noticed my swap partition had gone from 2.5 GB to 5.4GB. I have an extended partition of 5.4GB as well and I am not sure what this extended partition is.
My system specs are:
Memory:2GB
HDD: 160GB
OS: Hardy Heron 8.04
I would very much appreciate your help and suggestions.

---

### Post by Rocket2DMn on 2008-09-09
You can resize your partition from the LiveCD.  Boot from it, then open GParted: System->Administration->Partition Editor
Right click the swap partition area and Unmount it (I think the LiveCD mounts swap automatically).  You can then shrink the size of the swap and extended partition and grow the root partition to use the empty space.
You really won't be saving that much space, and might just find this process to not be worth your trouble.  You need to keep at least 2GB of swap, though I usually recommend 1.5x your RAM size (so 3GB).

As always, please backup your important data before fiddling with partitions - there is always a small chance that something could go wrong, or even more likely, that you do something wrong.

If you don't have a LiveCD handy, you can use the GParted LiveCD instead (it is much smaller than downloading a full Ubuntu LiveCD, and swap won't automount on it). [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

---

### Post by jemate18 on 2008-09-09
> **ellalan said:**
> Hi
I suspect my swap partition is too big and thinking of reducing the size to an acceptable level for a smooth operation.
I have recently re-installed Ubuntu 8.04 and noticed my swap partition had gone from 2.5 GB to 5.4GB. I have an extended partition of 5.4GB as well and I am not sure what this extended partition is.
My system specs are:
Memory:2GB
HDD: 160GB
OS: Hardy Heron 8.04
I would very much appreciate your help and suggestions.

Per your screen shot, you have two partitions, 1 (/dev/sda1)primary partition containing your root(/) partition and 1 (/dev/sda2)extended partition of 5.43GB containing 1(/dev/sda5) logical partition of 5.43GB as SWAP.

For the x86_64 architecture, you are only allowed for 4 primary partitions. to be able to have many, one of these four partitions should be extended partition. this extended partition may HOUSE arbitrary number of logical partitions starting with #5 (that's why you have /dev/sda5) Since your extended partition is 5.43GB and your swap is 5.43GB, therefore your extended partition is FULL already.. 

To be able to re size your swap, you have to partition your /dev/sda2(EXTENDED) to contain your swap (reduced)

You may use gparted or the liveCD Installer

---

### Post by ellalan on 2008-09-09
Thank you  Rocket2DMn and jemate18 for the quick response with a detailed explanation of the procedure.

---


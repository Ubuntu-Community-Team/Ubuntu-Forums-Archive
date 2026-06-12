---
title: "Broken partition?"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by BlueScientist on 2012-10-22
Hi,
After finishing a full reinstall where I changed the partioning on my hard drive, I find Gparted not recognising my swap space. 

The partition is shown as an unknown file system and is, according to Gparted, not mounted after start-up, however when I want to format it to a linux-swap, Gparted wil fail and return that the partition is busy. 

The partition is logical and hosed in the same extended partition as my /home partition, which seems to be working fine.

For safety I have made a temporary swapspace in a primary partition since I had 5gb of unallocated space and not filled all my 4 primes

How can I get Gparted to format this partition to linux-swap? Or am I thinking wrong here?

---

### Post by kc1di on 2012-10-22
> **BlueScientist said:**
> Hi,
After finishing a full reinstall where I changed the partioning on my hard drive, I find Gparted not recognising my swap space. 

The partition is shown as an unknown file system and is, according to Gparted, not mounted after start-up, however when I want to format it to a linux-swap, Gparted wil fail and return that the partition is busy. 

The partition is logical and hosed in the same extended partition as my /home partition, which seems to be working fine.

For safety I have made a temporary swapspace in a primary partition since I had 5gb of unallocated space and not filled all my 4 primes

How can I get Gparted to format this partition to linux-swap? Or am I thinking wrong here?

you have to make sure it's not mounted. and not in use when trying to format it. 
If your using gparted from the ubuntu installer , you may want to download and try buring gparted by itself on a sepreate cd and try with that. or try parted magic you can find it [here.]("http://distrowatch.com/index.php?distribution=partedmagic&month=all&year=all")

---

### Post by ajgreeny on 2012-10-22
Using your ubuntu installation's terminal, what is the output of ```
free -m
```It should be something like```
             total       used       free     shared    buffers     cached
Mem:          2012       1465        547          0        119        839
-/+ buffers/cache:        506       1505
Swap:         2047          0       2047
```The bottom line shows the size and use of swap.  If yours is all zeros, your swap is not working as it should so we need to delete it and start again with a new swap partition or figure out what is wrong with it.

If it is within an extended partition along with your other ubuntu partitions gparted can not edit it while other ubuntu partitions are in use.  You will need to use a live CD/USB.

---

### Post by BlueScientist on 2012-10-22
Hmm... I am sure that the unknown partition was unmounted, at least that was what the info pop-up said in Gparted.

However it seemed like the swap partition was broken. I tried to boot from the live USB that I did the previous installation from, but could only preform a full reinstall from it. (Is that normal? Am I not supposed to have the 'try without installing' option?) Since I still had to do all my own configurations on the system, I figured it would be easier to just reinstall. So I tried that and created a prime partitions solely for swap on the location the broken swap used to be.

Now it seems to be working fine.

Thanks for the tricks!

---

### Post by BlueScientist on 2012-10-22
This is very strange. I did an update (a series of 10) and after this update Gparted marks the partition as unknown...
Is there something wrong with Gparted? Or did the update scramble it up?

free -m
shows a 1429 MB of Swap. That is the size I intended it to have.

---

### Post by NikTh on 2012-10-22
Hi , 

probably is an encrypted swap partition. Give the results of 

```
cat /etc/fstab
```If it is an encrypted swap partition , then gparted cannot handle it. You have no problem and leave it as it is. 

After all is only a swap partition, you can delete it and recreate it easy.. :)

Thanks

---

### Post by BlueScientist on 2012-10-22
The command returns:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b9c05cc8-ebb7-4cf7-9142-7c9ea7b30dc9 /               ext2    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=e7642956-89c4-48b7-bfa9-ce308566dc4d /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
#UUID=e2a002db-e728-415f-8d10-7883eea47fb3 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

So if it where to be encrypted, would it still work or would this slow down the swap process so significantly that you would advice to change it?

---

### Post by NikTh on 2012-10-22
> **BlueScientist said:**
> The command returns:
```
/dev/mapper/cryptswap1 none swap sw 0 0
```

Its a cryptswap .. as I said , encrypted swap partition. You have no problem. Gparted cannot handle such partitions (encrypted) and display them as Unknown. 

Thanks

---

### Post by BlueScientist on 2012-10-22
Thank you all.

---


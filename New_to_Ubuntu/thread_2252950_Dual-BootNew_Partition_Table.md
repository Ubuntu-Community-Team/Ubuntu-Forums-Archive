---
title: "Dual-Boot:New Partition Table"
date: 2014-11-16
forum: New to Ubuntu
---

### Post by avis2 on 2014-11-16
I am panicking. I tried the dual boot option when installing Ubuntu. First I disabled fast boot on Windows 8. My Windows 8 was on legacy mode so I didn't do the part about disabling secure boot. 

Then I put Ubuntu in a pendrive and proceeded to instll Ubuntu but got stuck at the partition part. (I clicked 'something else' because it couldn't recognize my Windows 8). I read several articles about partitioning. My partition table had until sda4 and a row of free space. I couldn't partition any of the sda, just the free space. 

In frustration, i clicked 'new partition table' and made a 40GB ext4 partition with the label (/), one for SWAP and one 'boot' efi partition size 40MB. 

After that, I finished installation and successfully got into ubuntu. But now i don't know where the files in my D drive in Windows are, and I don't even know where my Windows is. How do I get back into Windows? I tried restarting and pressing exit, but there was no option of getting into Windows. I'm trying to use GParted's recovery option but it just hangs after I click okay. Please help. Are the files in my D drive still there?

---

### Post by ajgreeny on 2014-11-16
Oh dear!

You have wiped the whole disk including your windows partitions when you made a new partition table.

Stop using the computer straight away and clone the hard disk if you can, then at the very least you may be able to get back your files using something like testdisk.

I can't help more than this as I have never needed testdisk, nor had to recover partitions, so wait for others to come along with help for you.

---

### Post by avis2 on 2014-11-16
Ohgod.
Okay thank you so much for replying. I'm taking my laptop to the shop tomorrow. I don't think i'll be tinkering with technical things I don't understand anytime soon.

---


---
title: "couple of questions about partitioning"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by Oxyris on 2011-11-27
Which do I trust windows 7 or ubuntu? I went into disk management and it showed that the new ubuntu partitions (swap and /) were two separate primary partitions. However I just checked disk utility (in ubuntu obvs) and it shows swap and / as being under an extended partition. I ask this because I'm still a bit confused about how partitioning works. You're only allowed four partitions right? I wanted to reduce / partition and create a new partition (or I could just leave it as unallocated space as I currently have no plans for this section but you know, I may in the future) but I can't because then there would be 5 partitions..?

---

### Post by Paddy Landau on 2011-11-27
For historical reasons, a hard drive may have no more than four partitions. These are called *primary* partitions.

Too late, it was realised that people need more than four partitions. So, the powers that be invented something called *extended* partitions.

An extended partition may contain any number of *logical* partitions.

So now, a hard drive may have no more than four primary or extended partitions (in any order).

Older versions of Windows could boot only from primary partitions, but newer versions can boot from primary or logical partitions, as can Linux.

You will find that Ubuntu installed itself by creating an extended partition, within which it created two logical partitions. One logical partition contains swap, and the other root.

Therefore, both Windows 7 and Ubuntu are correct!

---

### Post by Rex Bouwense on 2011-11-27
Any information that I would give you would be based on assumptions so if you have GParted, post a screen shot of your hard drive.  I would guess without any further information that you have four primary partitions, three NTFS (Windows) and one Ex4 with / and swap on it.  We will see when you post back.

---

### Post by Oxyris on 2011-11-27
> **Rex Bouwense said:**
> Any information that I would give you would be based on assumptions so if you have GParted, post a screen shot of your hard drive.  I would guess without any further information that you have four primary partitions, three NTFS (Windows) and one Ex4 with / and swap on it.  We will see when you post back.

Here ya go. Like I said windows shows me four primary partitions: recovery, windows os, ubuntu and swap. If it turns out linux and swap are together under one extended partition like gparted shows then I'll just go ahead and make another logical partition. If not then I'll move swap into the / partition (I assume this is possible).


P.S. added windows screenshot

---

### Post by oldfred on 2011-11-27
Windows has been know to incorrectly write partition table info. It does not really understand logical partitions correctly it seems. It just calls all those as basic. 
Do not ever let Windows create more partitions as it converts to dynamic which is somewhat like LVM in Linux and not compatible with anything.

You should be fine creating additional logical partitions.

---

### Post by Paddy Landau on 2011-11-28
> **Oxyris said:**
> Here ya go. Like I said windows shows me four primary partitions: recovery, windows os, ubuntu and swap.
Thanks for the screen shots. I've just looked at my Windows partition, and it does the same as you! Well, I learn something every day. Windows incorrectly reports extended and logical partitions as primary.

> **oldfred said:**
> Do not ever let Windows create more partitions as it converts to dynamic which is somewhat like LVM in Linux and not compatible with anything.
Thank you for that warning. Duly noted.

---

### Post by haqking on 2011-11-28
> **Paddy Landau said:**
> For historical reasons, a hard drive may have no more than four partitions. These are called *primary* partitions.

Too late, it was realised that people need more than four partitions. So, the powers that be invented something called *extended* partitions.

An extended partition may contain any number of *logical* partitions.

So now, a hard drive may have no more than four primary or extended partitions (in any order).



Just a point to note, i know not applicable to the OP, however for clarity and education to the OP.

A hard drive is not limited to this any longer, it only applies to MBR based HDD, GPT is becoming more prolific and now and that changes the way we partitions disks and the 4 primary partitions are no longer a limitation.

---

### Post by Paddy Landau on 2011-11-28
@haqking: Thank you for that information. I heard the term GPT earlier today for the first time, so I think I shall have to learn more about it.

---

### Post by haqking on 2011-11-28
> **Paddy Landau said:**
> @haqking: Thank you for that information. I heard the term GPT earlier today for the first time, so I think I shall have to learn more about it.

NO worries you are welcome.

here are some informative articles.

[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

[http://msdn.microsoft.com/en-us/windows/hardware/gg463524.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463524.aspx)

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by Paddy Landau on 2011-11-28
@haqking: Thank you, those articles were informative.

---

### Post by Oxyris on 2011-11-28
> **oldfred said:**
> Windows has been know to incorrectly write partition table info. It does not really understand logical partitions correctly it seems. It just calls all those as basic. 
Do not ever let Windows create more partitions as it converts to dynamic which is somewhat like LVM in Linux and not compatible with anything.

You should be fine creating additional logical partitions.
So as long as I make the partition under ubuntu it should work? Would windows be able to read this partition too? I guess the point of making the partition would be to store music and documents that both OSes could see.

---

### Post by oldfred on 2011-11-28
Windows has to boot from a primary partition but will read logical partitions just fine. Of course it will not read Linux partitions so best to use NTFS for any data you want to read from both systems.

---

### Post by stracky on 2011-11-28
Windows can "see" all the partitions on the drive, but it can't access partitions that use Linux based filesystems. (ext3, swap,) it can only access Windows Filesystems (fat, ntfs)

Linux can access all partitions, so sharing should work out fine, as long as you use Windows-based filesystems for the shared partition.

If you ever need to modify partitions, use GParted or some other Linux-based partition manager.  The Windows ones never work for me when dealing with Linux filesystems.

---

### Post by Oxyris on 2011-11-28
> **stracky said:**
> Windows can "see" all the partitions on the drive, but it can't access partitions that use Linux based filesystems. (ext3, swap,) it can only access Windows Filesystems (fat, ntfs)

Linux can access all partitions, so sharing should work out fine, as long as you use Windows-based filesystems for the shared partition.

If you ever need to modify partitions, use GParted or some other Linux-based partition manager.  The Windows ones never work for me when dealing with Linux filesystems.

Thanks. I'll go ahead and make my partition.

---


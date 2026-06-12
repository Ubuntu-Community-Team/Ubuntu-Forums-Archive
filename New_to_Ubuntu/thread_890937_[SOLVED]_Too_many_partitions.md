---
title: "[SOLVED] Too many partitions?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by redandgreen on 2008-08-15
I have a dual-boot setup, XP and ubuntu, and I'm getting confused about the partitions. I know that the XP is on one, and ubuntu on another, and there's something called a swap file - so why do I have seven partitions, total? 

> Number  Start   End     Size    Type      File system  Flags
 
 1      32.3kB  98.7MB  98.7MB  primary   fat16             
 2      98.7MB  98.8GB  98.7GB  primary   ntfs         boot 
 3      98.8GB  156GB   57.7GB  extended               lba  
 6      98.8GB  152GB   53.2GB  logical   ext3              
 7      152GB   154GB   2319MB  logical   linux-swap        
 5      154GB   156GB   2147MB  logical   fat32             
 4      156GB   160GB   3545MB  primary   fat32   

XP is #2 and ubuntu is #3, but what are #1, #6, #5 and #4? 

I tried out a couple of live CDs for fun - Puppy, Slax and Knoppix. I didn't install any of them, but could they have made partitions just to run? I'm twitchy - I'm sure I've heard somewhere that too many partitions is a Bad Thing. Help?

confused,

redandgreen

---

### Post by drs305 on 2008-08-15
> **redandgreen said:**
> I have a dual-boot setup, XP and ubuntu, and I'm getting confused about the partitions. I know that the XP is on one, and ubuntu on another, and there's something called a swap file - so why do I have seven partitions, total? 

XP is #2 and ubuntu is #3, but what are #1, #6, #5 and #4? 

I tried out a couple of live CDs for fun - Puppy, Slax and Knoppix. I didn't install any of them, but could they have made partitions just to run? I'm twitchy - I'm sure I've heard somewhere that too many partitions is a Bad Thing. Help?

confused,

redandgreen

1 may be a recovery or system partition
2 is your windows partition
3 is an extended partition - it is a holder for partitions 5-7
4 is a fat32 primary partition that you probably aren't using (but check the contents)
5 is a fat32 logical partition that you probably aren't using (but check the contents)
6 is your linux partition
7 is your linux swap

You probably aren't using partitions 4 and 5. There aren't really problems with having a lot of partitions if you use them, but 4 and 5 are probably not being used. Since 4 is a primary partition and 5 is an extended logical partition, they cannot be combined. 

If you wanted to get rid of 4 and 5, the easiest would be to add 4 to 2. Since you would be workig with your windows OS partition, I would recommend using a windows partitioning program. Combining 5 and 6 would be a bit more problematic since you would be combining your existing root partition with the free space to the 'left' in partition 5. 

The tool you would use in linux is gparted but if you decide to delete or combine any partitions be sure to back them up first.

---

### Post by drubin on 2008-08-15
> **redandgreen said:**
> I have a dual-boot setup, XP and ubuntu, and I'm getting confused about the partitions. I know that the XP is on one, and ubuntu on another, and there's something called a swap file 

Dont worry about the Swap file, it is a standard linux partion. It is used much in the same way as the Paging file on windows. 

So when you do not have enough ram that acts as an extender...(very simplified).

I would not *stress* about having the partions as much as not knowing what they are for.

Are you missing any large chucks of spare from the hard drives that you have?

---

### Post by indytim on 2008-08-15
To expand on what drs305 said, I would suggest mounting #4 & #5 and check out the content before deleting.  

Don't worry about the number of partitions, you're doing fine (I've got 12 partitions on my primary h/d) and room for more :).

IndyTim

---

### Post by bobnutfield on 2008-08-15
It is only possible to have four primary partitions on a disk.  Yours has three and an extended partition.  An extended partition can have many logical partition within it, thereby allowing you to have many more than the four partition limit.  Partions 4 could be a windows recovery partion (or partition 5), both four and five are windows partitions.  Six and seven are your linux partition.  By default, the first logical partition inside an extended partition is labled as (by linux) /dev/sda5, and that is a fat32 partition on your disk.  Therefore, /dev/sda6 is your Ubuntu partition and /dev/sda7 is your swap partition.

It all looks normal for a disk that has had windows preninstalled when you got your computer.

---

### Post by kansasnoob on 2008-08-15
DRS305 is exactly right. What you might do to better understand what you have is install gparted:

```
sudo apt-get install gparted
```

You'll then find it by going to System > Administration > Partition Editor and you get a neat gui like this:

[ATTACH]81660[/ATTACH]

You see mine shows one primary with XP and an extended with two linux OS's and a shared swap.

The reason for extended partitions is that they can "contain" many "logical" partitions which allows many more than the physical hard drive limit of 4 primary partitions.

---

### Post by redandgreen on 2008-08-15
Okay, you've reassured me that my laptop isn't going to explode into a fiery ball of doom, and I've even learned a few things - thanks, everyone :) 

Now, to investigate #4 and #5..


no longer so confused,

redandgreen

---

### Post by redandgreen on 2008-08-15
Huh. sda5 turns out to be Dell Mediadirect, some media suite installed on a 'hidden' partition. [_This guy_]("http://forums.techguy.org/unix-linux/569616-vista-ubuntu-linux-dule-boot.html") had the idea of installing a linux OS to it instead, so you choose which to boot with the power/media buttons instead of a grub menu. Kinda superfluous, I guess, but sounds fun :)

Sda4 was a dell backup partition. Think I'll leave it be.

Thanks again :D you guys are brilliant!

---


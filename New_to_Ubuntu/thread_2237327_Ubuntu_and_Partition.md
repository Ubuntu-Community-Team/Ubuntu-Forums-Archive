---
title: "Ubuntu and Partition"
date: 2014-08-01
forum: New to Ubuntu
---

### Post by tom125 on 2014-08-01
Hello, i have some experiance with ubuntu now but still one question. 

Does ubuntu really needs 3 different partitions, root, swap and home? I want to get a new ssd and less partition will increase the lifetime of a ssd. Maybe root is needed for ubuntu and it wont need many save cycles but a swap partition? Could i make something like a swapfile in my home partition, like the swapfile in windows?

Thank you for your help,

Tom

---

### Post by kc1di on 2014-08-01
Hi tom125  and welcome to Ubuntu,

the only partition you really need is the root prartion "/"  and the standard install usually only gives you the root partition and a Swap partition.

Swap is only needed if your machine has low ram 1GB or less or if you plan on using Hibernate or suspend (on a Laptop say). 

That being said , many of us like to store important files and documents in a separate /home partition so if we need to re-install or want to upgrade we don't loose all of our data.  /other prefer a separate /data partition that separates data files from the /home so system config files stay separate.  
but the only partition that is critical so to speak is the "/' (root) partition.  The others are personal choice.   
good Luck with your new ssd.

---

### Post by mastablasta on 2014-08-01
swap is not necessary if you do not hibernate and have enough ram. you can also put swap on another disk. or you can reduce swapiness (to use ram more and swap less). more here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

separate home is not necessary. home is sort of like my documents in windows or maybe now windows user folder.

---

### Post by oldrocker99 on 2014-08-01
I set up a separate /home partition on my laptop, and dedicated a separate hard disk on my deskotp box for /home. The biggest advantage is, that when/if you install a new version (or, as sometimes happens, you hose the / folder:oops:)

---

### Post by oldfred on 2014-08-01
Partitions should have nothing to do with life of a drive. It still is number of writes and how you partition would not change that unless you put /home or /mnt/data partition on rotating hard drive so that data is not on SSD.
You also change settings to reduce writes on SSD.

But many now say the new SSD have lives comparable to rotating hard drives. No hard drive lasts forever and it does depend on use.

Will you just have SSD or also a rotating hard drive with your system?

If you have 4GB or more of RAM you may not use swap so it becomes a moot point on whether it is on SSD or not. If not used it cannot wear out an SSD. I have SSD and swap on hard drive but with 4GB of RAM never use swap with my use of system. If memory is limited, it would be better to buy more RAM as swap even on SSD is orders of magnitude slower than RAM.

 SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)

---

### Post by oldrocker99 on 2014-08-01
I set up a separate /home partition on my laptop, and dedicated a separate hard disk on my deskotp box for /home. The biggest advantage is, that when/if you install a new version (or, as sometimes happens, you hose the / folder:oops:), once you have installed, you have all your documents, media files, **and program settings** right there and ready to use. When I did not use a separate partition, reinstallation required me to restore a backup of /home to my new installation.

A / folder doesn't need to be very big (I've gotten by with 64 GB, and never filled it more than ~50%, and that's a **lot** of programs installed), and you can, at installation, ser up a smallish / partition, and use the rest for a nice, big /home directory.

---

### Post by whitesmith on 2014-08-01
> **tom125 said:**
> Could i make something like a swapfile in my home partition, like the swapfile in windows?

No, swap in Linux is not a file; it's a **partition**, which, as others have noted, is unnecessary if you have adequate RAM.

---

### Post by coffeecat on 2014-08-01
> **tom125 said:**
> Could i make something like a swapfile in my home partition, like the swapfile in windows?

Yes, you can have a swap file instead of a swap partition, but I don't think you'd want to put it in your home. I've not done this myself so I can't confirm the validity of this howto:

[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)

(Scroll down to "Four-step Process to Add Swap File"). But since it's on the community wiki and hasn't been altered, I'd guess it is probably OK. If you google for how to create a swap file, you'll find the wiki method differs from most in that others create a swapfile called /swapfile by means of dd, but the principles appear to be the same.

But I must question a point that oldfred raises. Why do you think that fewer partitions will increases the life of the drive?

---

### Post by tom125 on 2014-08-01
Thanks for your replys. 
SSDs have only, don't know the exact number, of writes for one block. The SSD controler tries to write the data on different blocks. Blocks on small partition will get more write cycles then the rest of the SSD and the lifetime will be lower. A hugh partition should lower the write cycles for a blow.
I guess i will try the swapfile on my computer. This shouldn't be slower then a swap partition.
I found something else in the net, only one /root for everything. More folders will be needed but this should work too. And a good backup disk :)

---

### Post by oldfred on 2014-08-01
What is important is that the partitions be aligned. When SSD & 4K drives first came out drives were not aligned and you did get the issue of extra writes on blocks. But now all partition tools align the partition.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by whitesmith on 2014-08-01
> **tom125 said:**
> Thanks for your replys.

I'm not trying to get the last word on this--only to set the facts straight. Please check the SwapFaq at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) before making changes to your system.

---

### Post by tom125 on 2014-08-02
I am still on my old HDD with Ubuntu, nice to try something. I am on a swapfile and low swappiness now, everything still works, same speed, no crashes. I guess i will keep this.

---

### Post by 3rdalbum on 2014-08-02
> **tom125 said:**
> Thanks for your replys. 
SSDs have only, don't know the exact number, of writes for one block. The SSD controler tries to write the data on different blocks. Blocks on small partition will get more write cycles then the rest of the SSD and the lifetime will be lower. A hugh partition should lower the write cycles for a blow.
I guess i will try the swapfile on my computer. This shouldn't be slower then a swap partition.
I found something else in the net, only one /root for everything. More folders will be needed but this should work too. And a good backup disk :)

It seems my reply yesterday was eaten by the gremlins.

SSDs do not say "This chunk of memory is for Partition 1, the next chunk is for Partition 2" etc. SSDs internally have no concept of partitions. If they are given something to store, they store it wherever is best for the SSD's circuits. If you had a swap partition on an SSD, it would basically be interspersed with all your other data. Every time you started your computer, the swap partition would be sitting in a completely different set of memory cells than it was yesterday.

Modern SSDs make it IMPOSSIBLE to wear out small patches of memory. You understand SSDs have wear-levelling, but you just didn't realise how effective it really is!

However... don't bother with swap unless you're really doing some heavy-duty tasks. 2 GB of RAM or more is enough to avoid needing any swap, at least for normal home use. This isn't Windows Vista.

It's probably important at this point that we correct your technical terms too. /root is the Root user's home directory, not the place where the operating system is installed. The operating system is installed to the / partition. Don't create a partition for /root, it'll generally only be a couple of megabytes (MB) in size.

On Linux, there is a tiny chance of losing data due to filesystem corruption. Much tinier than Windows or Mac OS. Having a partition for / and a partition for /home will further reduce the odds of losing data. Other than that, there's no real benefit to having different partitions for them.

Somebody earlier said that, if you do a clean install or upgrade of Ubuntu and you don't have a /home partition, you lose all your documents and settings. That might have been true in 2008, but it's not true anymore. If you do the clean install or upgrade with the "Something Else" partitioning screen in the installer, and you tell it not to format your / partition, you will not lose the data from /home.

I hope this helps. So, in short:

1. It's safe to put multiple partitions, and even a swan partition, on an SSD
2. You probably don't need swap anyway if you have 2 GB of RAM or more and your needs are modest
3. You can install Ubuntu with only one partition ("/") and still do clean installs or upgrades in the future without data loss.

---

### Post by tom125 on 2014-08-02
Looks like i had wrong informations. Your last post is very helpfull. I learned a lot of new things. I will install Ubuntu in the old way and there are still many things to try out.

---


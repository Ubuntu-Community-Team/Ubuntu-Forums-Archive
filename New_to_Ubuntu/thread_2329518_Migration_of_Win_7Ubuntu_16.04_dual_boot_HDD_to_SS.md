---
title: "Migration of Win 7/Ubuntu 16.04 dual boot HDD to SSD"
date: 2016-07-02
forum: New to Ubuntu
---

### Post by steve262 on 2016-07-02
Moving from Windows 7 to Ubuntu 16.04 was amazingly easy\\:D/  Moving to an SSD was amazingly difficult ](*,)

I started with a 1TB HDD and partitions for "SYSTEM", "OS" (win7), "Ubuntu", and "Swap".  My SSD is only half the size of the HDD, so some pruning and reorganization was necessary.  Moving things around became very difficult and time consuming though.  I had to do many, many searches for information and never found everything I needed, nor all in one place.  Conflicting goals got me into more trouble than was necessary, maybe describing this will help someone...

My win7 partition was originally the entire drive barring the system partition (whose purpose I still don't understand) and the HP Recovery partition that I eventually deleted.  Getting to Ubuntu dual boot meant defragging win7 and shrinking it to create Ubuntu and swap partitions.  This was unfortunate because I ended up needing to shrink win7 further and my ubuntu install was in the wrong place.  That took me to "MovingLinuxPartition" at [https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition) which gives excellent steps for fixing that problem.  However, the -d argument to grub-install seems incorrect so I used --boot-directory and my volume's boot directory instead.  Later, I used this resource again to get my SSD copy of Ubuntu running.  Managing the partition stuff was the worst nightmare in this whole ordeal.

So, my problem ended up being that my win7 partition was still too big to get the SSD properly configured.  I created a new data partition and moved all the personal files I cared about from the win7 partition to that and then backed it up a couple times.  However, I found out that was too many partitions leading to the extended partition problem and having to fix my bootup on the HDD.  At this point, my win7 partition was 600+GB but only 200+BG in use.  I was hoping that at least one tool could cope with that and give me a 300GB bootable partition of win7 on my SSD.  No such luck.

I tried:


[LIST]
[*]Acronis - only seems able to exactly duplicate all the source partitions to the target which didn't work for me because I needed different partition layouts.  Excluding everything from a partition does NOT exclude the partition. 
[*]MiniTool Partition Wizard 9 - was happy to create an extended partition for me and then Ubuntu didn't boot, wants money for SSD migration but that may have been worth it, I don't know.  Generally it wasn't doing what I thought I needed, YMMV. 
[*]Windows DiskPart - helpful info, but dead end 
[*]Windows Disk Manager - helpful info only 
[*]Clonezilla - tried to do the large to small clone but it got mysterious errors and didn't copy anything at all 
[*]EaseUs - like Acronis, not helpful here 
[*]GParted - won't offer the paste if the copy has a bigger partition size than the target space, regardless of the in use amount 
[/LIST]

I'll skip all the gory details of false paths I took and go direct to what worked.  


[LIST=1]
[*]Another round of defragging did not allow me to shrink the win7 partition much at all from the Windows side, nothing like getting to less than 300GB as I needed 
[*]Ubuntu GParted was able to resize it for me.  I left extra room at the end "just in case" and that seems to have been OK.  However, subsequently booting the HDD win7 caused it to go into repair mode and it spent a LOT of time determining that nothing was actually wrong and then booted. 
[*]Ubuntu GParted was now able to copy/paste win7 onto my SSD and then copy/paste Ubuntu onto my SSD because they both fit at this point 
[*]I created a linux-swap partition on the SSD 
[*]"MovingLinuxPartition" (linked above) allowed me to boot the SSD Ubuntu where I did the rest of what worked.  I also configured the swap from the prior step at the same time. 
[*]Install GParted on Ubuntu, it's not there by default 
[*]Unplug the HDD and reboot into the Win7 Repair Disk and let it clean things up on the SSD.  Reboot and it doesn't work, back to repair, it does different stuff, reboot, it was fixed.  I couldn't yet boot into it though, my grub stuff was all messed up. 
[*]install boot-repair and run it.  Work through all its steps of removing the old grub and installing the new one 
[*]grub-update?  I don't remember if I did this again after boot-repair, but it probably can't hurt 
[*]Testing showed everything worked! 
[*]GParted then helped me add a "HDD" prefix to all the HDD partition names so I can tell what's what 
[*]Awesome improvement!!  From wakeup button-press to resumption of suspended instance is only a few seconds on Ubuntu!  Even Win7 is tolerable now :P 
[/LIST]

I'm no expert in these areas, so please also do your own research if you want to follow this path.  The main take-aways for me are these:


[LIST=1]
[*]Get your HDD environment ready before you do anything else!  Shrink your Windows install partition to exactly the size you need on the SSD _**before**_ doing any other steps.  This will save you many headaches. 
[*]Have the Ubuntu Live CD or the HDD Ubuntu instance available for the first copy of partitions to the SSD with GParted 
[*]Read MovingLinuxPartition, many kudos to ** [msmalin]("https://launchpad.net/%7Emsmalin") **for that one**!  **(remember to check out --boot-directory instead of -d though)  Use it to get your SSD Ubuntu booting 
[*]Unplug the HDD and use the Windows Repair disk to get the SSD Windows instance bootable (perhaps even doing this before adding the Ubuntu partition to the SSD would have been easier) 
[*]install boot-repair and use it to get the final product all booting properly 
[/LIST]

---

### Post by grahammechanical on 2016-07-02
> I'm no expert in these areas,

You are more of an expert at this than I am. I have no experience of doing what you have done. I hope that you will use your experience to guide others who may come on this forum seeking advice.

Regards.

---

### Post by steve262 on 2016-07-03
Thanks for your kind words.  If I had known at the start what I know now then I would have saved myself more than 8 hours.  Everything I was able to do depended on the great community resources surrounding Ubuntu and a lot of hard work recovering from mistakes I made along the way.

I tried to update or comment on the MovingLinuxPartition page, but it's been marked immutable and doesn't seem to have commenting available.  That page needs another update to use current partition naming since that has changed to include the partition type in the name.  Instead of (hd0,1) you'll have a name like (hd0,msdos1) to denote that the partitions are msdos style.  If anyone knows how to get updates into that page please help.

---

### Post by oldfred on 2016-07-03
Becuase of some issues, they are limiting who can edit.
 help.ubuntu.com/community lock down
[http://ubuntuforums.org/showthread.php?t=2308813](http://ubuntuforums.org/showthread.php?t=2308813) 

But hd0,1 should still work, they now use hd0,msdos1 or hd0,gpt1 to keep it clear if MBR or gpt partitioning.

It also is more complicated now that most older systems are BIOS/MBR and newer systems UEFI/gpt. And you cannot clone MBR partitions to gpt.

With Windows you just about have to clone. But I find a full install of Ubuntu, and restore /home from backup much quicker, easier. You may want to back up /etc but may only need a few settings that you manually changed. And if you installed lots of apps, you can export list of installed apps to make it easy to reinstall. But high speed Internet makes that easier.

I install each new version, but keep LTS as main working install. I just installed 16.10 in about 10 min using grub loopmounting ISO on SSD and installing to newer/faster HDD with partition already created(overwrote a 15.04 install). Since ISO was latest daily hardly any updates. Within an hour I can have a fully reconfigured system new install that matches my old install.

---


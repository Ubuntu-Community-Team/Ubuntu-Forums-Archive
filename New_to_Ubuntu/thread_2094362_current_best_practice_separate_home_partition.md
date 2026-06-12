---
title: "current best practice: separate /home partition?"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by GordThompson on 2012-12-13
I understand why, under certain circumstances, it is necessary (or just convenient) to go to the extra effort of creating a separate partition for /home instead of just accepting the default installer behaviour of making /home a subdirectory of /. I also understand why some long-time Ubuntu users might get into the habit of creating the separate /home partition and just do it that way all the time.

However, as I posted in [another thread]("http://ubuntuforums.org/showthread.php?p=12400847#post12400847"):

> **GordThompson said:**
> Many of my friends are becoming increasingly interested in Linux for their home machines and are asking me for advice. I've been reluctant to tell them that they need to do "custom" installs, including repartitioning for a separate /home partition, because I don't want them to get frightened off ("That's too technical; I'll just stick with Windows.") and I also don't want to have to do all of their installs for them. ;)

On reading some of the comments in the Linux Mint forums I gathered that they tend to recommend a separate /home partition because the preferred way to upgrade Mint is to do a clean install of the new version. OTOH, I gather that Ubuntu supports (recommends?) in-place upgrades that preserve the existing files in /home.

So, if a user has a backup regimen that includes their entire /home hierarchy, and if they don't want to dual-boot or share their /home with multiple Linux installs, is there still a significant advantage to creating a separate /home partition?

If this has been discussed at length elsewhere in the forums I apologize, but I did search and found lots of references on *how* to do it, and *why* some power-users do so, but not too much from the perspective of a "just switch on the computer and use it" user. If there are compelling reasons why that type of user needs a separate /home partition then I'll tell my friends (and accept the additional tech support workload when they ask for help), otherwise I'll just tell them to do a default install and make sure that they set up their automated backups.

Comments, anyone?

---

### Post by COMECON on 2012-12-13
In my opinion, the extra step of creating a separated /home partition, which takes you no more than 2 minutes, will save you looooots of times. I always have 3 distributions simultaneously installed, and I like to try them all, so... Imagine having to mount the partitions, copy the files, etc. With a separated /home partition, I can create a "master" folder with the Documents, Music, etc. folders, and then symlink to them from my "temporal" user accounts.
If you plan to stick with the same distribution for all your live, you should also create it... Like the D:\ partition of Windows. If you have to reinstall the operating system and you can't save anything, all your data will be destroyed! Else, having a /home partition, will let you format only the root partition and keep your data save :)
That's just my opinion!

Catbuntu

---

### Post by DuckHook on 2012-12-13
Let me try to explain it in non-technical terms: I suppose that it's the classic case of applying forethought. A little bit more work and complexity up front translates into a lot less work and simpler upkeep for a long time afterwards.

You say:

> **GordThompson said:**
> If there are compelling reasons why that type of user needs a separate /home partition then 'll tell my friends (and accept the additional tech support workload when they ask for help)

Firstly, kudos to you for helping your friends and spreading Linux-use this way. The choice is yours, but do you continue to provide tech support in the longer term? If so, then the separate /home partition tends to lessen workload on subsequent installs, because all of their e-mail, data, personal settings etc are preserved. One of the biggest advantages for me is the way it preserves my virtual machines. When I first took up Linux, I too installed everything in one partition. But every time an upgrade broke my system (it happened quite often in the old days, esp if you customize your installation far beyond its generic initial state), I would have to reinstall each VM. If you've ever tried reinstalling a Windows VM, it takes the better part of a day. Since I keep half-a-dozen VM images at any time, this gets pretty old pretty fast.

Once I made the move to a separate /home partition, the process couldn't be easier. The new VM app gets upgraded with the system upgrade, but because my old images haven't been touched, it's a simple matter to attach them to the new VM and, presto, they're back up and running with no muss, no fuss.

With absolute beginners (what this subforum is about) I'm actually 50/50 on need for separate /home, so am not advising you preferentially either way. There *is* added complexity, and the big downside is that non-techy users sometimes bork their Windows partition due to inexperience. No point in introducing Linux if they then associate a disaster with that first experience.

You're the one providing the support, so it's your decision. Just hoping to give you more relevant info to assist in that decision.

---

### Post by Vaphell on 2012-12-13
separate partition for user data beats single partition for everything every single time. That said, there are some drawbacks with /home if you share it between different installs, as single config for different versions of the same program can lead to problems (eg if newer config is not backwards compatible with older version of the program that is lives in another system)

In case of multiple installs and distro hopping you want to have a separate data partition for all your stuff and link to it from your systems. /home would store only configs for its setup which means it could be very thin or even live inside /

If you use only 1 distro, separate /home is good, end of story. Screwup that requires reinstall, eg recursive chmod in /? fix by reinstall takes 15 minutes. Rolling back if the newest release is not to your liking? Reinstall older version - 15 minutes.

---

### Post by COMECON on 2012-12-13
> **DuckHook said:**
> Let me try to explain it in non-technical terms: I suppose that it's the classic case of applying forethought. A little bit more work and complexity up front translates into a lot less work and simpler upkeep for a long time afterwards.

You say:



Firstly, kudos to you for helping your friends and spreading Linux-use this way. The choice is yours, but do you continue to provide tech support in the longer term? If so, then the separate /home partition tends to lessen workload on subsequent installs, because all of their e-mail, data, personal settings etc are preserved. One of the biggest advantages for me is the way it preserves my virtual machines. When I first took up Linux, I too installed everything in one partition. But every time an upgrade broke my system (it happened quite often in the old days, esp if you customize your installation far beyond its generic initial state), I would have to reinstall each VM. If you've ever tried reinstalling a Windows VM, it takes the better part of a day. Since I keep half-a-dozen VM images at any time, this gets pretty old pretty fast.

Once I made the move to a separate /home partition, the process couldn't be easier. The new VM app gets upgraded with the system upgrade, but because my old images haven't been touched, it's a simple matter to attach them to the new VM and, presto, they're back up and running with no muss, no fuss.

With absolute beginners (what this subforum is about) I'm actually 50/50 on need for separate /home, so am not advising you preferentially either way. There *is* added complexity, and the big downside is that non-techy users sometimes bork their Windows partition due to inexperience. No point in introducing Linux if they then associate a disaster with that first experience.

You're the one providing the support, so it's your decision. Just hoping to give you more relevant info to assist in that decision.

I don't think it's too complex, reading a few tutorials about "advanced" partitioning before installing Ubuntu and creating the partition + automount it while installing isn't too hard. Also, IMO, doing this can avoid you lots of headaches :)

---

### Post by Vaphell on 2012-12-13
i suggest training in virtualbox to figure manual config out.
create fake hdd in virtualbox, boot linux iso in it, poke it with the stick, try partitioning.

---

### Post by COMECON on 2012-12-13
> **Vaphell said:**
> i suggest training in virtualbox to figure manual config out.
create fake hdd in virtualbox, boot linux iso in it, poke it with the stick, try partitioning.

I agree, messing around in VirtualBox is perhaps the best way to learn the most important things, because it doesn't matter how many times you break it; you always can restore a snapshot :P

---

### Post by lykwydchykyn on 2012-12-13
It all comes down to upgrades for me.  I usually use a separate home partition and leave enough empty space for another / partition -- especially on other people's systems.

The reason is simple:  say two years from now they come to you and say that their version of firefox is too old and giving them warnings.  You want to get them on the latest LTS, but you don't know how it will run on their system.

If you've done the partitioning like I described, you can install the new LTS on the empty space, mount the home directory, and know right away if it's going to work.

If not, you have to just test with the liveCD (which won't help you with proprietary driver compatibility), then either (a) backup all their data and install over the currently working installation, or (b) upgrade and hope everything works.  

This strategy has served me well on my family's systems over the years.

---

### Post by deadflowr on 2012-12-13
It is far more important to have a reliable back up system in place than to have partition dedicated directories.
While convenient, having a separate /home partition in this day and age is unnecessary as hard drive capacity is quite large.

---

### Post by DuckHook on 2012-12-13
> **Vaphell said:**
> If you use only 1 distro, separate /home is good, end of story. Screwup that requires reinstall, eg recursive chmod in /? fix by reinstall takes 15 minutes. Rolling back if the newest release is not to your liking? Reinstall older version - 15 minutes.

+1

Much more succinct than my long-winded explanation. Also speaks to OP's question about ease of support.

P.S. It is safe to assume that absolute beginners (of the sort supported by OP) will only use one distro. Multi-distro issues are way off in the distant horizon.

---

### Post by oldfred on 2012-12-13
I have to agree with deadflower that backup is probably more important.

I am a proponent of separating system from data, both Windows & Linux. That makes it bit easier to reinstall system, but does not negate importance of backups.

But for a very new user it is not critical. I used just Windows, Linux and a shared FAT32 partition for years. 

But with Windows 7 they have made it difficult to create new partitions. Almost always Windows 7 will use all 4 primary partitions under MBR and get you into the issues of partitions. 

Most Windows users do not even know what a partition is. Windows calls both physical drives and partitions as drives. So you have to get into what partitions are.

But now I have multiple installs and find separate data partitions more important and do not have separate partition for /home.

---

### Post by DuckHook on 2012-12-13
> **deadflowr said:**
> It is far more important to have a reliable back up system in place than to have partition dedicated directories.

Agreed. But OP has already looked after this:

> **GordThompson said:**
> ...make sure that they set up their automated backups.

His real question is cost/benefit to him (as a support source) and his friends (end users) of separate /home

> While convenient, having a separate /home partition in this day and age is unnecessary as hard drive capacity is quite large.

Don't entirely agree. Utility of separate /home is not to spread info over 2 drives. As noted by many posts, it is for ease of recovery, ease of upgrade, etc. It's necessity will be determined by OP's needs. Example: If he spends more time trying to recover from borked manual repartitioning attempts, then best to make use of automated install process into one partition and just live with the result. If he spends more time untangling upgrades, fighting with backups, reinstalling VMs, etc, then separate /home will save him tons of heartache.

---

### Post by tartalo on 2012-12-13
> **deadflowr said:**
> It is far more important to have a reliable back up system in place than to have partition dedicated directories.

While that is true, it's also true that *ain't nobody got time for that*, so having a partition based strategy for friends and family will save *you* time.

---

### Post by debodas on 2012-12-13
When installing my first distro, I only made a / partition. Later, I needed to reinstall it (long story why). Anyway, without a /home partition, I wiped all my docs, photos etc. I had a backup, but it was still a lesson learned. I would always recommend a separate / and /home partition, it is so much easier in the long run.

---

### Post by DuckHook on 2012-12-13
Exactly my own experience. I would guess that most long-time users would cite a similar learning-curve. But sometimes, hindsight can be distorting: would you say that you had to go through the learning-curve before being convinced that a separate /home was a good idea? In my case, I don't think any amount of warning from any guru no matter how experienced would have convinced me to do a complex partition when I was starting out. The fear of screwing up my system *today* just trumped any consideration of ease of use in the vague future.

---

### Post by lykwydchykyn on 2012-12-13
> **DuckHook said:**
> Exactly my own experience. I would guess that most long-time users would cite a similar learning-curve. But sometimes, hindsight can be distorting: would you say that you had to go through the learning-curve before being convinced that a separate /home was a good idea? In my case, I don't think any amount of warning from any guru no matter how experienced would have convinced me to do a complex partition when I was starting out. The fear of screwing up my system *today* just trumped any consideration of ease of use in the vague future.

When I was starting out, this was the default arrangment for the distro I was using.  It's a shame the installer isn't making this an option.  It's been a while since I used Ubiquity; is it really just a choice between one partition and custom partitioning now?

---

### Post by debodas on 2012-12-16
> **DuckHook said:**
> Exactly my own experience. I would guess that most long-time users would cite a similar learning-curve. But sometimes, hindsight can be distorting: would you say that you had to go through the learning-curve before being convinced that a separate /home was a good idea? In my case, I don't think any amount of warning from any guru no matter how experienced would have convinced me to do a complex partition when I was starting out. The fear of screwing up my system *today* just trumped any consideration of ease of use in the vague future.

My first linux distro, I just made a / partition, and didn't bother with a /home.

Took me all of one reinstall to realise that was a bad move. I think most people can learn how to make partitions, and it sure it better.

---


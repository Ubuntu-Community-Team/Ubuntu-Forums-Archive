---
title: "Reconfigure Partitions and 12.10 Fresh Reinstall"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by dexter.lives on 2013-03-29
I've been away from Ubuntu for a few years and have become a little rusty...not that I was ever super talented. When I got a new laptop I (think that I) made a mess of the partition.
[ATTACH=CONFIG]240683[/ATTACH]
Then I upgraded from 12.04 to 12.10; it was not a clean upgrade. Since then, I constantly get errors. To me, it seems that I should just reinstall 12.10. It makes sense to me that I should fix the partitions first so that
[LIST=1]
[*]The Win partition is only about 100 GB
[*]The Ubuntu OS is on its own, small partition
[*]The UOS reads from another partition where all my files would be stored. This should be a large partition
[/LIST]

Clearly, I am not doing something correctly. Any advice for getting this done? Am I even on the right track?

---

### Post by oldfred on 2013-03-29
It seems like a reasonable plan. I also prefer small system partitions for both Windows & Linux with separate data partitions or /home. I often suggest separate /home for newer users just to get them started on separating system from data. But I leave /home inside root and have all data in other partitions.
When dual booting with XP, I created a shared NTFS data partition. Now that I do not boot XP, I stll have old NTFS, but all new data is going into a Linux formatted data partition.

Be sure to backup all of Windows and any data you have in Ubuntu & /home. If you have installed a lot of applications in Ubuntu you can export a list to make it easy to reinstall. 

Use Windows to shrink the Windows NTFS partition, but not to create any new partitions. Reboot into Windows a couple of times for it to run chkdsk  and make other repairs due to its resize.
You then can use gparted from Ubuntu liveCD or gparted or partedmagic liveCDs to modify partitions. You will have to move extended left into unallocated.

You will have to use Something Else or manual install whether you fully create partitions in advance or partition as part of the install. Did you encrypt /home as the smaller partition is now shown in gparted. But that is how gparted shows swap when /home is encrypted as swap is also encrypted and therefore cannot be seen.

---

### Post by DuckHook on 2013-03-29
Welcome back to Ubuntu!

You are absolutely on the right track. Here are my recommendations:

1. Backup, then backup your backup. It looks like you have W7 installed, so if you have W7 install/recovery disks, have them at hand. Partition changes are the leading cause of borked HDDs, lost data and frantic pleas for help on these forums.

2. Resize the MS partitions using MS tools. W7 throws hissy-fits having its partitions resized with Linux tools.

3. Ubuntu has recently announced that future versions will only have 9 month support, so if you are intent on using 12.10, just be aware that you are committing to a journey on the unending upgrade treadmill. By contrast, 12.04 is LTS that will be supported until 2017. Choose your version wisely.

4. Your current partition architecture along with your proposed scheme is fine. Reduce Win partition, expand Linux partition, and Ubuntu goes into the extended partition as a number of separate logical partitions.

5. Is there a reason you need a NTFS partition in sda6? It's just my personal opinion, but NTFS is a horrible file structure that needs to be defragged constantly, whereas ext 3/4 is almost maintenance-free. However, if you need this to be readable from Win, then I suppose you are stuck with it.

6. It's best to create your Ubuntu partitions first using gparted, then map your various directories to these partitions during the install. Since you are planning a fresh install, you can just destroy the current Linux partitions rather than resize them (which takes forever and is fraught with risk)

7. Create one partition of 30 GB at beginning of extended space for /

8. Create one partition of whatever you want, but at end of extended space for swap.

9. Create a third partition of all remaining space for /home.

10 [Optional] Instead of giving everything to /home, you can create an additional partition for /data to be split with /home. You can decide on proportion based on your own data needs.

That's it (in a general sense). Map out your strategy properly beforehand, take it slow and steady, and you should have no problems.

Did I mention... backup?

<edit>

beaten to the punch by *oldfred*

@OP: If advice conflicts, always listen to *oldfred*

</edit>

---

### Post by oldfred on 2013-03-29
There is no one right answer to partitioning. DuckHooks suggestions are all good. Did he mention backups? :)

I find even my own optimal partition scheme a couple of years later is not very good. But I do not trust hard drives, so every few years I get a new drive usually a lot larger, so more room for data. Old drive often is also backup. Last larger drive I got, I left a lot of space unallocated. Decided to install Ubuntu next version in another new 25GB partition. Now almost all that space has different installs and now needs housecleaning.

---


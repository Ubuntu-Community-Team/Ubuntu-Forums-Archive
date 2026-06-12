---
title: "HOWTO: Install K/X/Ubuntu to ext3 partitions with dir_index enabled"
date: 2006-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by K.Mandla on 2006-07-31
**Introduction**

This is a short guide for installing K/X/Ubuntu to ext3 partitions with the dir_index option enabled. Borrowing from the [Hoary how-to]("http://www.ubuntuforums.org/showthread.php?t=37806"), dir_index is a "hashed b-tree implementation for ext3." It has been [a default option for Fedora]("http://www.google.com/search?q=fedora+dir_index") for some time, and is [suggested as a default]("https://wiki.ubuntu.com/CommunityEdgyIdeas/Performance") for ext3 in the Edgy release.

**What good is it?**

[INDENT]It's possible you might see a substantial speed increase when using the dir_index option enabled. Boot times, load times and drive access times might seem faster. That will, however, depend on your hardware; different file systems perform differently under different [CPU speeds, throughput speeds and workloads]("http://fsbench.netnation.com/"). 

As a loose rule, if you're using older hardware (i.e., Pentium III or earlier) you might notice an improvement with dir_index over ordinary ext3. There's no guarantee of course, but in most cases it's worth checking.[/INDENT]

**Before you start**

[INDENT]You might want to try converting your existing ext3 partitions to dir_index. In that case, use the commands listed in the [Hoary how-to]("http://www.ubuntuforums.org/showthread.php?t=37806"). I know for some people it's possible that you can convert without reinstalling; I had no luck with that. 

(Note that you can check if your dir_index option is enabled with the *sudo tune2fs -l /dev/hda1 | grep dir_index*; if the result is nothing, then it's not enabled. I checked a squeaky-clean default installation of Xubuntu and it was not there.)

If you're using a different file system altogether and you want to convert to dir_index but don't want to reinstall ... you'll have to look it up. It will probably require some serious acrobatics, and I leave that up to you.[/INDENT]

**What you'll need**

[LIST]
[*]An error-free K/X/Ubuntu desktop (live) CD
[*]Your computer, with important stuff backed up
[*]About an hour of your life, depending on the speed of your hardware
[*]**Optional:** A copy of [KillDisk]("http://www.killdisk.com") or something similar, if you want to blank the drive first
[/LIST]
**Getting started**

[INDENT]There are couple of points that should be mentioned, since they form the rationale for this method.

First, the alternate CD installer won't let you select file system options during installation. You can pick a different file system, but the dir_index option is selected with the mke2fs command, and you don't have access to that in the partitioner.

Expert installation doesn't offer those options, either.

Furthermore, the alternate CD installer formats each partition with or without your consent, which means even if you could preset your partitions, you would (I think) lose the option when the partitioner reformats.

For those reasons, the alternate (install) CD isn't acceptable. If you don't have the desktop CD on hand, you'll want to download it. This method should work fine with the Ubuntu DVD, but I haven't tried it.

Personally, I make a point of blanking a drive before I reinstall; that's where the [KillDisk]("http://www.killdisk.com") CD comes in. [/INDENT]

**Partitioning**

[INDENT]Make sure everything is backed up, then reboot your computer using the desktop (live) CD. When your machine is ready, open a terminal window and enter this command.

```
sudo fdisk -l
```
This is just a preliminary measure to see what partitions you have already installed. If you blanked the drive, you'll get a message about a missing partition table; if you are installing over other information you'll see it there.

I prefer cfdisk to fdisk for partitioning; I find it easier to spot my mistakes.

```
sudo cfdisk /dev/hda
```
I'm using /dev/hda as an example; if your drive is a different assignment, change those last letters to match it.

I like to partition my drives with a separate boot area, root partition and home area. For that case, I generally build this:

```
/dev/hda1 100Mb boot
/dev/hda2 2Gb root
/dev/hda3 512Mb swap
/dev/hda4 (whatever's left) home
```
One point worth noting: cfdisk asks for partition sizes in megabytes, but has a tendency to clip those amounts when it actually builds the partition. For example, I've found that entering 2048Mb for the root partition results in something slightly smaller -- 1910Mb or so. The partitioner will balk at installing Ubuntu to a partition smaller than exactly 2Gb, so I do this:

```
/dev/hda2 2.1Gb root
```
or 2252Mb to cfdisk. The resulting amount is enough to keep the installer happy.[/INDENT]

**Build the file systems**

[INDENT]Once your partitions are set and the partition table is written to disk, make the file systems. In my case I use ext2 for the boot partition (I have heard other file systems give grub some problems, and I prefer to use grub).

```
sudo mke2fs /dev/hda1
```
Next, swap.

```
sudo mkswap /dev/hda3
```
Now for the root partition.

```
sudo mke2fs -j -O dir_index /dev/hda2
```
The -j flag sets the partition to ext3, and -O enables the dir_index option. Depending on the size of the drive and the speed of your hardware, that command could take a minute or so to finish.

Last, the home partition. The command is identical to the last one.

```
sudo mke2fs -j -O dir_index /dev/hda4
```
Now the partitions are set and the file systems are built. Now we can use the desktop installer to build the system.

When you reach the part where the drive is partitioned, make sure you ...

[LIST]
[*]mount each partition to the correct location, and
[*]disable the reformat option.
[/LIST]
Mismounting would be catastrophic, of course. And if you reformat, you might lose that dir_index option ... which is why we're here in the first place. :)

Install as usual. In about 20 minutes or so, you should have a new system.[/INDENT] 

**Check your work**

[INDENT]When your new system reboots, open a terminal and make sure the option is enabled.

```
sudo tune2fs -l /dev/hda2 | grep dir_index
```
Again, if that command gives you no output, then something went wrong and dir_index isn't there. 

On the other hand, if you see a line that shows it is enabled, then you're done. Congratulations!
[/INDENT]
**Reaping the rewards**

[INDENT]Once more just to be clear, if you're using older hardware, you might notice an improvement. I use two 1Ghz machines, one with a 7200rpm drive and the other with a pair of 5400rpm drives, and in both cases the difference was noticeable. But as always, your mileage may vary.

On the other hand, I suspect newer machines are so fast as to make this technique a moot point. You never know, though. ... 
[/INDENT]
***[COLOR="Red"]Good luck![/COLOR]***

**Postscript**

It is conceivable (but I haven't tried) to use this same procedure to build other file systems (I'm thinking of reiser4 here). Just thought I'd mention it. ;)

---

### Post by Schuttwegraeumer on 2007-05-14
deleted

---


---
title: "Best way to partition drives"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by LPShred on 2008-08-22
Hello,  this is my first post so please pardon any idiocy.

So, I'm looking to install Ubuntu and dual-boot it with Vista.  Right now I have XP and Vista.  I never use XP any more, so I'd like to replace it with Ubuntu.  It would be nice to just wipeout that entire XP partition, but I have like 20 GB of music on it, and it won't all fit on my Vista partition.  I plan on putting on a friend's external HD during the install, but I'll need somewhere to put them permanently.

Also, I heard about installing your /home folder on a different partition than Ubuntu.  Is this difficult and/or advantageous.

So right now my plan is to have three partitions. One for Vista and its installed programs, one for Ubuntu and its installed programs, and one as the /home folder where I will keep all of my media files and other loose, non-installation files.

Is this a good idea?  Will both OSs be able to read all three partitions?

How much room should I leave for Ubuntu?  I want to have enough room that I won't have to go back and resize it for more, but I also want to maximize space for the /home partition.

Thanks in advance for the help.

---

### Post by tamoneya on 2008-08-22
that sounds like a good idea.  Just remember you want a swap partition as well.

Here is what I recommend:
1. vista at least 30 GB
2. ubuntu swap partition 2-4 GB
3. ubuntu / "root" partition: 10 GB
4. ubuntu home partition: whatever is left

As for reading from different OSes you will be able to read ntfs (windows) from linux by default but to read ext3 (ubuntu default) from windows you need to install fs-driver.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by LPShred on 2008-08-22
Thanks for the quick reply.

So basically I need 4 partitions.
I have 110GB or so to use.

1) Vista is 45 GB now. - NTFS
2) Ubuntu swap partition - What is the advantage of making this larger?  I'll go for 4GB now - ext3
3)Ubuntu root - This is where the OS is actually installed, correct?  And 10GB is all I should really need? - ext3
4)Ubuntu home partition - Whatever is left will be around 50 GB.  Sounds good to me. - ext3

All the ubuntu partitions will be ext3, correct?

And is there a reccomended install guide for what I want to do.  I can google one, but if you guys know of a good one, that would helps.

Thanks for everything.

---

### Post by WRDN on 2008-08-22
LPShred, the swap partition should be formatted to linux-swap, not ext3. The size really depends on your usage. Some say the swap should be 2 x RAM, though this is not needed in my opinion. You should always have more swap than RAM, so if you hibernate, the contents of the RAM can be placed in the swap. Unless you are doing multiple memory heavy tasks, you shouldn't have to worry about running out of memory.

---

### Post by Paqman on 2008-08-22
> **LPShred said:**
> 
Also, I heard about installing your /home folder on a different partition than Ubuntu.  Is this difficult and/or advantageous.


It's advantageous because it lets you do a clean install without touching any of your config files and personal data. After reinstalling your OS and apps (and in Linux you can reinstall every single one of your apps in one operation) it will be exactly as it was before. Since there's a whole new version available every 6 months people reinstall a lot, hence why it's so popular.

As for difficulty, it involves a bit of prior thought, and you have to partition the drive yourself, instead of letting the installer do it automatically. It's not at all difficult, but can be intimidating the first time you do it.

Always defrag thoroughly and back up before doing any partitioning, btw.

---

### Post by tangibleorange on 2008-08-22
There is a good guide here:

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

with screenshots. just be sure to select 'Manual' at the partitioning stage, and configure the partitions as you mentioned above.

---

### Post by LPShred on 2008-08-22
Thanks for the help.  I'm going to try to get this started this week.  I'll let you know how it goes.

Any other suggestions are welcome.

---

### Post by philinux on 2008-08-22
What paqman said is very true.

> As for difficulty, it involves a bit of prior thought, and you have to partition the drive yourself, instead of letting the installer do it automatically. It's not at all difficult, but can be intimidating the first time you do it.

Always defrag thoroughly and **back up** before doing any partitioning, btw.

And make sure the backups are good.

---

### Post by Paqman on 2008-08-22
> **LPShred said:**
> 
Any other suggestions are welcome.

One thing that won't be an issue now, but might in the future, is that you're only allowed a max of four primary partitions on any one drive. If at some later date you wanted to add a partition (to try out another distro, say) you wouldn't be able to.

The way around that is to set up an extended partition at this stage, and put some of your partitions inside it. An extended partition can contain as many partitions as you like, breaking the four partition limit. It's a doddle to do.

---

### Post by bodhi.zazen on 2008-08-22
Partitioning is an art and there is not absolute right or wrong way to do it.

Before partitioning a hard drive be sure to back up any data on it. Although rare, if you make a mistake you may have data loss.

Partitions should be managed from a live CD.

If you do not like the sizes, you can always resize them later with gparted.

Documentation: [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

Last, 4 Gb swap is almost certainly way too large. In general swap should be RAM X2, max 1 Gb (some people say max 512 Mb). The more RAM you have the less you need swap.

The exception is hibernation, in which case you need swap = RAM.

Also rather then a /home partition consider making a data partition.

In general for linux /root of 10 Gb is plenty, the rest can go into a data or home partition.

If you use a data partition you then use links ;

ln -s /media/data/music /home/user_name/music
ln -s .media/data/documents /home/user_name/doucments

and on ...

As you add or change partitions you may need to update fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by sandysandy on 2008-08-22
go thru the gparted tutorial here

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by LPShred on 2008-08-23
[IMG]http://www.personal.psu.edu/ssk5033/Pics/partitionpic.jpg[/IMG]

That was a snapshot of my HD right now.  I just want to double check that what I'm doing will work and is possible.

Pretty much, I'm going to replace the D: drive with:
1) Ubuntu installation
2) Ubuntu swap
3) /home directory

That should give me 4 primary partitions and everything I need.

Will this plan work?

Also,  What are the first and last partitions?

---

### Post by tamoneya on 2008-08-23
that looks good.  The last and first partitions are empty unformatted space.  You could use the first partition for your ubuntu install as well as expanding your vista partition into that space on the right.

---

### Post by stansult on 2008-12-16
> **tamoneya said:**
> that looks good.  The last and first partitions are empty unformatted space.  You could use the first partition for your ubuntu install as well as expanding your vista partition into that space on the right.I think that the first one on the snapshot is EISA configuration, which is not exactly "empty unformatted space". But some actually delete it - I'm not sure if it's ok...

---

### Post by stansult on 2008-12-16
> **bodhi.zazen said:**
> Last, 4 Gb swap is almost certainly way too large. In general swap should be RAM X2, max 1 Gb (some people say max 512 Mb). The more RAM you have the less you need swap.

The exception is hibernation, in which case you need swap = RAM.Could you please explain this (sorry for not getting this, but I'm new to it). My RAM is 3Gb, so RAM x 2 = 6Gb; but you wrote it's max 1 Gb. So... how much should I actually use?

---

### Post by bodhi.zazen on 2008-12-16
Think of swap as additional RAM on your hard drive. So, when you run out of physical RAM your machine will use swap (rather then lock up or crash random applications). Swap is obviously slower then physical ram.

If you had 100 Mb RAM (to use an extreem) you would need a lot of swap and your system would be slow.

If you have 3 Gb RAM, to use another extreem, you will almost never use any swap as you have an abundance of physical RAM.

Linux does not use RAM the same as windows an most desktop users will not user more then 1.2 Gb RAM

Now, if you have a laptop, and use sleep or hibernation, your RAM is written to the Swap on the HD, so you will always need swap to be a wee bit larger then yoru physical RAM.

On Desktops, however, you will not do this, so you can use swap of 0 or 512 Mb.

---

### Post by stansult on 2008-12-16
> **bodhi.zazen said:**
> ...On Desktops, however, you will not do this, so you can use swap of 0 or 512 Mb.Oh thanks a lot! So if I use desktop, I'll make it 512 Mb, just in case. Thanks!

---


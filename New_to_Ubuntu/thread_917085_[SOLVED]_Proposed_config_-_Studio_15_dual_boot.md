---
title: "[SOLVED] Proposed config - Studio 15 dual boot"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by AirWreck on 2008-09-11
I'm a totally stoked Kubuntu nooB.  Installed K'buntu Hardy for grins on Friday = haven't booted to WXP since Monday :guitar:

Unfortunately, I'm also long winded so I'll post my questions before ADD strikes ;)  See waaay below for proposed Dell Studio 15 configs and "the story".

1)  I'm down to 512mb RAM on my Inspiron with a failed DIMM = K'buntu gets kind of clunky with FF, TB and music going.  I'm assuming that the new rig proposed below will more than handle my needs?  It looks like power concerns are more orientated toward Vista than K'buntu.  I think this is a good balance but am open to any suggestions or considerations I missed :)


2a)  I'm scheming on partition options for an internal 320gb drive.  What is a reasonable assumption for the Vista Home Premium C: partition, assuming off the shelf install and no personal data bloat?  = How big is Vista and how much room does it actually need?  

2b)  It also sounds as if Vista comes off the shelf with a backup/recovery partition = reasonable assumption of partition size (no bloat)?

3)  Given that I'm a nooB looking at a dual boot Vista system and frequent Kubuntu updates, what is the current thinking on whether to pull /home out to its own partition?  I've tried to find all the related posts and it looks like it can be more about personal preference than anything.  It also looks like the answer may have evolved in the last few years.  I was all set in the dedicated /home partition camp until I saw a post that said that you might miss update features if you use old config files.  I'm a KISS guy but am also thinking of bringing in ~30gb of personal data into /home.  Maybe its best to keep my personal data separate and keep /home in the root, the same practice as I kept with My Documents and WXP?  Six o' one...?

"The story"... :popcorn: 
My trusty 5 year old Inspiron 8500 is finally talking to me about retirement options.  I've been wandering the laptop aisles for a couple of weeks but have finally come back to Dell.  I had a few issues with this machine but everything considered, its been a pretty good work horse.  With my new K'buntu affliction, its also nice to see a machine that is being offered with Ubuntu off the shelf (although I will be going with Vista option).  Hopefully this will have the added benefit of a decent sized K/Ubuntu user group for future feedback/support.

So...before pulling the trigger at the Outlet, I'm seeking a little hand hold please :)

I'm going with the below config with the thinking that I'll dual boot Vista.  Its looking like I'm a K/Ubuntu convert but I need to keep a foot in the Windows camp = my ship's network and the navigation apps are all Windows based.  We usually have an ET guy aboard and good IT support shoreside but they rotate so its good to maintain Windows skills.  Also want to get 4-5 years out of the new machine so want a system that will handle the ravages of "progress".  I usually just surf, multi-task the usual low end apps and play/manage a 500gb music collection.  I do go on the occasional AutoCAD jag, mostly for grins.  Basic photo resizing, no vid editing, no games.  Might get wild hair to learn more about code beyond the scant ip and dir DOS commands in my current quiver.  Here's where I'm at:

_Dell Refurb Studio 15_
T8100 2.1/800/3MB processor
320gb HHD
4gb RAM (more than I need...right now)
Intel x3100 card
Bluetooth (just b/c it might be cool to have a wireless mouse)
can go either way on fingerprint and backlit keyboard, more crap to break

Thanks in advance!

---

### Post by bobnutfield on 2008-09-11
I've read your entire post, and it appears to boil down to a question on whether or not to have a separate /home partition and whether or not the hardware you are suggesting is compatible.

I highly recommend a separate home partition.  While you should still do frequent backups, when reinstalling data is kept intact.  

Your new computer almost definitely will come with a small recovery partition for Vista.  Leave it alone or you could bork your Vista install.

Past reading tells me that your proposed hardware will work "out of the box" with Ubuntu/Kubuntu.

Your only concern is to be careful with your partitioning.  Use Vista's partitioning utility if possible as I have read that Vista is very fussy about messing with partitions using third party partitioners.

---

### Post by AirWreck on 2008-09-11
Bob, thanks for Vista partitioning advice and info on the separate home partition.  Thanks also for wading through the post...I should have edited that way down :shock:

Anyone with the down and dirty on these two?

2a) I'm scheming on partition options for an internal 320gb drive. What is a reasonable assumption for the Vista Home Premium C: partition, assuming off the shelf install and no personal data bloat? = How big is Vista and how much room does it actually need?

2b) It also sounds as if Vista comes off the shelf with a backup/recovery partition = reasonable assumption of partition size (no bloat)?

Thanks.

---

### Post by AirWreck on 2008-09-16
Okay, kinda solved this myself.  I ended up with this for a partition plan:

71mb for that little EISA partition
40gb C: Vista OS
10gb D: Vista recovery

15gb /root Kubuntu
10gb /Home
3.3gb Swap

220gb NTFS "data" for all personal docs, etc.

Of course its not a done deal yet because I hosed Vista last night trying to do this repartitioning;)

Trying to repartition Vista is a pain in the butt.  I had MFT files in the middle of the drive so it wouldn't let me "shrink" it anywhere near where I wanted.  I tried to get tricky and outfox it.  I cloned it using Acronis and then cloned it back, customizing the partitions as per above first three Vista specific parts.  Computer is stuck in a boot cycle.  Can get into F2 setup and F12 boot menu but no F8 recovery.  Definitely hosed.  I tried using an Acronis bootable disk and maybe trying recloning the C: without all the custom repartioning but running off the disk makes that a losing proposition = 24 hours for task.  So Dell sending Vista install disk "sir, I must inform you that Dell does not recommend repartitioning your hard drive."  Uh yeah, thanks.

So no new questions here and marking "solved."  All this info is available around the net but just following up in case any other nooB stumbles upon this thread.

Aloha,
Eric

---


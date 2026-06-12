---
title: "Gparted is sloooooooooooow"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-04-22
I instructed gparted to rezise a partion on my external hdd from 450gb to 150gb and format it as fat32 (to use on ps3 hihi).

Gparted is at it for **more than 2 hours** now. How long should this still take?

Screenshot for clarification:

[[img]http://xs126.xs.to/xs126/08172/gparted574.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs126&d=08172&f=gparted574.png)

The external harddrive isn't making any noise and my cpu and ram usage are normal. What gives?

[I][SIZE="2"](ps: I disabled compiz fusion and thus emerald, I normally never use those ulgy windows borders)
[/SIZE][/I]

---

### Post by forestpixie on 2008-04-22
I did a resize and move with about 40Gb and it took an hour or more from memory - and I had no apparent work going on from the pc either - but it finished eventually.

So I'd imagine that it's still doing something still - you obviously know not to turn it off assuming it's crashed, so the only thing you can do is wait unfortunately.

---

### Post by billgoldberg on 2008-04-22
Yeah, I'm not going to turn it off. There's about 160 gb of data on there and I didn't back it up. 

If 40gb takes around an hour than 200gb should take 5 hours :p :p

I guess I won't be playing cs source today.

I just wished it used up more resources. I have this hardware for a reason, so things would go faster.

---

### Post by Joeb454 on 2008-04-22
Gparted took a while when I used it from the Gutsy Live CD ages ago...

I prefer to partition before doing anything...perhaps you'll prefer to do the same from now on (I had a similar experience to yourself ;))

---

### Post by forestpixie on 2008-04-22
It' be quite nice if it gave some idea of the time involved though I think - as it is watching the bar get's a bit on the boring side :D - some sort of warning - THIS OPERATION IS GOING TO TAKE 2 DAYS  would spice things up a bit.

Good luck

---

### Post by billgoldberg on 2008-04-22
I guess the only thing I can do is have patience.

---

### Post by billgoldberg on 2008-04-22
> **forestpixie said:**
> It' be quite nice if it gave some idea though I think - as it is watching the bar get's a bit on the boring side :D - some sort of warning - THIS OPERATION IS GOING TO TAKE 2 DAYS  would spice things up a bit.

Good luck

haha

---

### Post by Joeb454 on 2008-04-22
Listening to music helps pass the time :) or browsing these forums

---

### Post by billgoldberg on 2008-04-22
> **Joeb454 said:**
> Listening to music helps pass the time :) or browsing these forums

I'm doing both :p

It's time to get some more beans. :p

---

### Post by Joeb454 on 2008-04-22
I'm trying to get to 1500 before the end of the day ;) It's 4.30 pm here.

I think I was on around 1,390 when I started...

---

### Post by billgoldberg on 2008-04-22
> **Joeb454 said:**
> I'm trying to get to 1500 before the end of the day ;) It's 4.30 pm here.

I think I was on around 1,390 when I started...

I'll try to hit 750 today. It's only 17:32h here.

---

### Post by lswest on 2008-04-22
yeah, my experience is that gparted is slow at resizing large amounts of data (well, because it does it **well**), so i usually run it at night, before i go to bed or so, so that it's all done in the morning :P

---

### Post by Can+~ on 2008-04-22
I have a workaround for gparted:

```
sudo gparted /dev/sda /dev/hda
```

That way, you force gparted to open on the specific hard disks (where /dev/sda and /dev/hda are MY hard disks, you set it for yours), instead of having to scan through non-existant devices, making it lag.

---

### Post by Joeb454 on 2008-04-22
> **lswest said:**
> yeah, my experience is that gparted is slow at resizing large amounts of data (well, because it does it **well**), so i usually run it at night, before i go to bed or so, so that it's all done in the morning :P

That's exactly what I do ;)

---

### Post by billgoldberg on 2008-04-22
Now an hour after I posted this (gparted has been running for 3 hours) there isn't any visible change.

...

Maybe the guys from the gparted team should consider putting in a loading bar that actually tells you how far along the process you are. Not one that goes from left to right, indicating nothing. 

It can be done in 30 seconds or in 10 hours, no way to know.

---

### Post by lespaul_rentals on 2008-04-22
The only time GParted ever takes that long for me is when my hard drive is going bad.  You may want to run a check for bad blocks if you have been noticing other suspicious activity.

---

### Post by billgoldberg on 2008-04-22
> **lespaul_rentals said:**
> The only time GParted ever takes that long for me is when my hard drive is going bad.  You may want to run a check for bad blocks if you have been noticing other suspicious activity.

No, there is nothing wrong. I know gparted is doing it's thing. I would just like to have some indication on how long it was going to be and was looking for a way to speed it up (wich isn't possible now).

---

### Post by Jammy4041 on 2008-04-22
Just remember that the pS3 has a.) a slower processor than a normal PC
                               b.) less ram than a normal PC
                               c.) you have a bigger hard drive than most people. 450GB is huge. So I would think that the problem isn't with gParted.

---

### Post by Joeb454 on 2008-04-22
> **billgoldberg said:**
> Maybe the guys from the gparted team should consider putting in a loading bar that actually tells you how far along the process you are. Not one that goes from left to right, indicating nothing. 

It can be done in 30 seconds or in 10 hours, no way to know.

:lol: Yeah it is a pain in the <insert pain location here>

Perhaps you should submit a feature request?

---

### Post by billgoldberg on 2008-04-22
> **Joeb454 said:**
> :lol: Yeah it is a pain in the <insert pain location here>

Perhaps you should submit a feature request?

Mmm, maybe in the weekend, I don't feel like it right now (lazyness shows its ugly head).

ps: still no change from gparted's side.

---

### Post by Joeb454 on 2008-04-22
I think you should let us know when it's done :) I'm quite curious how long it'd take to trim ~300Gb off a partition :p

---

### Post by Oldsoldier2003 on 2008-04-22
> **lswest said:**
> yeah, my experience is that gparted is slow at resizing large amounts of data (well, because it does it **well**), so i usually run it at night, before i go to bed or so, so that it's all done in the morning :P

Having used Gparted and the gparted live cd extensively in the past month or so I've found that growing partitions is horribly slow especially when you grow them to the left. 

Whenever its possible I'll run Gparted from a live *installation * instead of the live cd. When its not possible and the live cd is the only solution, if it is all possible back up the data and perform the shrink operations... then instead of growing a partition, nuke it and recreate it. Copying the files back is much faster than growing a filesystem (especially to the left, but growing to the right isnt that fast either)

---

### Post by billgoldberg on 2008-04-22
> **Oldsoldier2003 said:**
> Having used Gparted and the gparted live cd extensively in the past month or so I've found that growing partitions is horribly slow especially when you grow them to the left. 

Whenever its possible I'll run Gparted from a live *installation * instead of the live cd. When its not possible and the live cd is the only solution, if it is all possible back up the data and perform the shrink operations... then instead of growing a partition, nuke it and recreate it. Copying the files back is much faster than growing a filesystem (especially to the left, but growing to the right isnt that fast either)

I'm running from a real installation, not the live cd and it's stil slow.

It's yet another hour later and still no change whatsoever from gparted's side.

---

### Post by Oldsoldier2003 on 2008-04-22
> **billgoldberg said:**
> I'm running from a real installation, not the live cd and it's stil slow.

It's yet another hour later and still no change whatsoever from gparted's side.

have you expanded the dialog box? you can see the progress of the Gparted operations and it will give you a clue to where you stand in each step of the process and how long each step has taken...

---

### Post by louieb on 2008-04-22
Haven't used it for real work yet. Just to add partition labels (something that GParted can't do).  But GParted now has fork called _[COLOR=Blue][PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")[/COLOR]_. It has some features not found in GParted.

---

### Post by canthus13 on 2008-04-22
The best speed-up is to simply format the entire drive and go from there. It only took a few minutes to resize the Vista partition down to 0.:)

--Me

---

### Post by SpongeBob SquarePants on 2008-04-22
What's the software you're using to display your system processes on the desktop? I used to use SuperKaramba in KDE. Is that a GNOME equivalent?

---

### Post by Oldsoldier2003 on 2008-04-22
> **canthus13 said:**
> The best speed-up is to simply format the entire drive and go from there. It only took a few minutes to resize the Vista partition down to 0.:)

--Me

+1 Indeed! It is way faster to nuke the partitions and start over if you have proper backups. Sometimes it become necessary when poor planning has made your partitions non adjacent over the course of a few switches...

---

### Post by canthus13 on 2008-04-22
It's under System > Administration > System Monitor.  It's quite similar to Windows Task manager in style, but with more reliable functionality.

--Me

---

### Post by SpongeBob SquarePants on 2008-04-22
> **canthus13 said:**
> It's under System > Administration > System Monitor.  It's quite similar to Windows Task manager in style, but with more reliable functionality.

--Me

Hi there,

I meant how do you display the processes on the desktop, as is shown in the opening posts screenshot.

---

### Post by Joeb454 on 2008-04-22
You're looking for Conky :) Search the forums, there's many threads on Conky :)

---

### Post by SpongeBob SquarePants on 2008-04-22
> **Joeb454 said:**
> You're looking for Conky :) Search the forums, there's many threads on Conky :)

Cheers :)

---

### Post by stchman on 2008-04-22
> **billgoldberg said:**
> Yeah, I'm not going to turn it off. There's about 160 gb of data on there and I didn't back it up. 

If 40gb takes around an hour than 200gb should take 5 hours :p :p

I guess I won't be playing cs source today.

I just wished it used up more resources. I have this hardware for a reason, so things would go faster.

You did not backup data and are resizing partitions?!!!!!  That is just nuts.  You are asking for disaster.

---

### Post by Joeb454 on 2008-04-22
Actually gparted did absolutely nothing to any data I had when I partitioned (I **forgot** to back up when I did it) so I was quite relieved :)

---

### Post by billgoldberg on 2008-04-22
Just letting you know gparted apperently hasn't done anything.

It's been going at it for ages. I hope it's done in the morning.

@ Stchman, call me crazy but I don't feel like waiting a few hours to transfer 160gb before I start the work I had in mind.  :p

I don't like waiting, thats why gparted is driving me crazy.

---

### Post by billgoldberg on 2008-04-23
Just letting you guys know that 11 hours later (gparted has been at it for more than 13 hours) there is still no visable change from gparted side.

To make things worse, I couldn't help but tinker with gutsy a bit before I move to hardy and I need to restart x (broke a few things), but I can't. :p:p

I just hope it's ready by tomorrow so I can install hardy.

---

### Post by forestpixie on 2008-04-23
My word - that is a loooong time. Hope it's ok !

---

### Post by billgoldberg on 2008-04-23
> **forestpixie said:**
> My word - that is a loooong time. Hope it's ok !

Me to, or I'm out 160gb of videos.

---

### Post by Joeb454 on 2008-04-23
I hope it's ok too :) 160GB of Videos is a lot, though if they're not videos' you've made yourself it's not as bad.

At least it's not real important data etc. :p

---

### Post by billgoldberg on 2008-04-23
> **Joeb454 said:**
> I hope it's ok too :) 160GB of Videos is a lot, though if they're not videos' you've made yourself it's not as bad.

At least it's not real important data etc. :p

True, but still.

---

### Post by forestpixie on 2008-04-23
Just had a quick look in the gparted forum's found this for a ntfs resize from 450Gb to 245Gb using USB

> It finally finished after about 45 hours of non-stop running... Everything still works fine

So I guess that it's not all lost - but if it looks like there's no apparent movement maybe it'd be worth posting the question?

Edit - there is another there that took 2 days!!

---

### Post by billgoldberg on 2008-04-23
> **forestpixie said:**
> Just had a quick look in the gparted forum's found this for a ntfs resize from 450Gb to 245Gb using USB



So I guess that it's not all lost - but if it looks like there's no apparent movement maybe it'd be worth posting the question?

Edit - there is another there that took 2 days!!

My god. That's forever.

I'll miss the ubuntu launch :mad: 

And I'm moving more than those guys.

---

### Post by Joeb454 on 2008-04-23
:lolflag: Wow, means it might take nearer 3 days for this resize then! :lol:

---

### Post by billgoldberg on 2008-04-23
> **Joeb454 said:**
> :lolflag: Wow, means it might take nearer 3 days for this resize then! :lol:

Well this will be be last time I'm resizing partitions. The next time, i'll back up the media and format the whole drive, should be done in under an hour.

---

### Post by ByteJuggler on 2008-04-23
Any reduction in partition size or expansion to the left, involves potentially very expensive operations for GParted, making them potentially very slow.  Expansion to the left means GParted really must move the entire partition to the left first, then expand to the right.  Moving 160GB of data on a single disk, is going to be slow, whichever way you look at it.  Reduction of a very large partition may involve having to manipulate the filesystem a lot to ensure the files are not located in the area being lopped off, which likewise can take a loooong time for a large partition.  It is in effect having to do a kind of a defrag then.

Other than the above, most other operations (including expansion to the right) will be very quick providing your HDD is working properly.

---

### Post by forestpixie on 2008-04-23
> The next time, i'll back up the media and format the whole drive, should be done in under an hour.Oh well - as you say after the nipple everything's learnt :D

---

### Post by billgoldberg on 2008-04-23
> **forestpixie said:**
> Oh well - as you say after the nipple everything's learnt :D

:lolflag:

---

### Post by billgoldberg on 2008-04-24
Another 21 hours later and still no visable change from gparted.

Oh my god!

---

### Post by forestpixie on 2008-04-24
Just dropped by for my daily fix - I guess you're hoping that Hardy isn't released till Monday now then :D

If it's still not done by tomorrow perhaps a scream on the gparted forum might be worth a go, figuratively speaking of course.

Edit - it's nice to see that you used the tags on the thread I wonder how many actually will do so.

---

### Post by billgoldberg on 2008-04-24
> **forestpixie said:**
> Just dropped by for my daily fix - I guess you're hoping that Hardy isn't released till Monday now then :D

If it's still not done by tomorrow perhaps a scream on the gparted forum might be worth a go, figuratively speaking of course.

Edit - it's nice to see that you used the tags on the thread I wonder how many actually will do so.

I already have the hardy cd on my desk. 

I already made a post on the gparted forum, and they told me the same thing people here told me. It's going to take a long time.

---

### Post by billgoldberg on 2008-04-24
God damn, I'm missing all the hardy fun.

---

### Post by Cadmus on 2008-04-24
Arr, I know how you feel, I have the disc in my hand, sadly I'm still at work so it's another few hours until I get to play (and find out if I plugged the CD drive back in properly).

---

### Post by billgoldberg on 2008-04-25
Another 18 hours later and gparted is still going at it.

This is driving me crazy!

Gparted must have running for over 60 hours now.

---

### Post by billgoldberg on 2008-04-25
Hour 70:

I gave up.

I stopped gparted.

All data is intact !!!!!! :):):)

I'm finally able to do a clean hardy install.

[B]
Never again![/B]

---

### Post by Oldsoldier2003 on 2008-04-25
wow! well i certainly wouldn't have expected gparted to take that long... theres a lot to be said for the backup , delete partition, recreate partion method.

---

### Post by amtam on 2008-08-30
Mmm... I seem to have run into the same problem....:(
It took Gparted more than an hour to move just 900KB??????

That's just ridiculous...

Why would it take more than 9 hours just to move about 130GB?

> **Never again!**

Same here.

---

### Post by clubsoda on 2008-11-06
Bump.
I tried the Intrepid version of gparted (0.3.8) from the Xubuntu live CD.

The bad news: The title of this thread is still true.
The good news: Now at least you get an estimate of how long the current operation will take.

Strangely, gparted seems to do things twice.  I asked it to move a 45GB partition about 20GB to the right.  First it said ```
*copy 96095025 sectors using blocksize 4096*
```This took slightly longer than the estimated 50 minutes.  Next it did a couple of quick 12MiB moves which I assume were FATs.  Then I got a rude shock:- ```
*copy 96095025 sectors using blocksize 8192*
```Estimated time: 1hr 47mins.  But why?  Does gparted resize the blocks on some whim?  I didn't dare shut it down midstream although this looks reassuring:- > **billgoldberg said:**
> I gave up.

I stopped gparted.

All data is intact !!!!!! Perhaps gparted manages to maintain data integrity much of the time.  That would be impressive.

Gparted was only using about 30% CPU on my old clunker and there's no way it takes hours to move a few GB in and out of a 7200rpm drive.  I assume most of the time is spent waiting for the drive heads to seek.
Seek..Read..Seek..WriteJoural..Seek..Write..Seek..ClearJournal..Seek..UpdateFAT..
Or something like that.

Plenty of scope for speeding things up, such as removing the fsck checks before and after, not resizing blocks, disabling the journal and not updating the FAT so often.  Admittedly those last two could be a bit dangerous.

As for feature suggestions, it would be nice to know the estimated time before clicking the Jean-Luc Picard button. ["Engage!"]
Perhaps also add a "safe interrupt" button so you could reschedule these operations.

---

### Post by phidia on 2008-11-06
There is nothing wrong with the CLI cfdisk except it does the job without gui and in a fraction of the time.

---

### Post by clubsoda on 2008-11-06
Footnote: from the spec sheet of my Seagate drive```
SUSTAINED TRANSFER RATE (MB/sec)__________up to 58
```That would mean 13 minutes to read or write 45GB.  The partition was only 20% full though.

---

### Post by clubsoda on 2008-11-06
> **phidia said:**
> There is nothing wrong with the CLI cfdisk except it does the job without gui and in a fraction of the time.But does it move partitions?

Along those lines, I was wondering if **parted** is any quicker than gparted (excluding of course the time taken to read and understand the manual page :)).

*Edit: DOH! Both depend on libparted, so the answer must be "no".*

---

### Post by handydan918 on 2008-11-06
> **billgoldberg said:**
> I guess the only thing I can do is have patience.

Heh....
or learn to use fdisk....
you'd be done and back to gaming a LONG time ago!

---

### Post by kalross on 2009-04-10
Arrrrggggghhhhhhhhhh.  Moving partition 3GB to right to make space for larger swap cos I upgraded memory to 4GB.  14 hours of hell!

---

### Post by vahnx on 2009-05-02
Nooo, I hate how it like says 4 hours then after those 4 hours it begins another 4 hour process! I find partition magic much faster, but I've lost data more often in the past than GParted. About three times each by GParted and Partition Magic I lost all my data. Of course it's backed up, but both of these partitioning apps are very unstable.

---

### Post by -kg- on 2009-05-02
> **kalross said:**
> Arrrrggggghhhhhhhhhh.  Moving partition 3GB to right to make space for larger swap cos I upgraded memory to 4GB.  14 hours of hell!

Well, it's been long ago since you posted this but, depending on what you're doing with your computer (and whether or not you use hibernation) I could have told you you likely didn't need to extend your swap file.

The biggest reason you would need to do that is if you use hibernate.  During the hibernate process system RAM is copied to the swap partition and, when you take the computer out of hibernate it copies the information back to RAM.  The only other reason is if you're using a RAM intensive software that takes more than 4 GB of RAM at a time (and I surely don't know what that would be!).

I have 2 GB of RAM and approximately a 3 GB swap file.  I don't use hibernate, and I have never used the swap file.  Oh, and I have edited videos and audio clips, which take a bit of processing power.

I was wondering something which I don't believe was ever mentioned in the post; before performing these partitioning operations, did you defrag the partition (assuming that it was FAT or NTFS in the first place)?  If you are performing partitioning operations on a FAT or NTFS partition, it is highly recommended to defrag it as much as possible before performing the operation(s) (as well as back it up, obviously).

It is much less difficult for the partitioner to perform operations on a defragmented partition and therefore takes much less time.  I recently moved a (approx) 25 GB NTFS partition to the left, and since I removed unnecessary files and defragged it to death, it took me about an hour to do the whole operation.  This is with 15 GB used.

Something that will also help with speeding up the process is to eliminate as many files from the partition as possible.  If you have another hard drive to back some of it up to and then delete those files from the partition, that will speed the process up as well.  "Less data to move = less time."

Yes, a 450 GB partition is a bit large and will take some time, but with some preparation the operations can be made a lot easier and quicker.

---

### Post by vahnx on 2009-05-05
About defragging first, I never thought of that, but would it matter? I'm pretty sure GParted does it sector-by-sector whether data is there or not. If there's like 100GB of free non-contiguous space doesn't it still take the same amount of time to move that empty area as it would if data was scattered there?

---

### Post by lisati on 2009-05-05
> **kalross said:**
> Arrrrggggghhhhhhhhhh.  Moving partition 3GB to right to make space for larger swap cos I upgraded memory to 4GB.  14 hours of hell!

Ouch! I thought the 5 hours or so to resize and move a partition of about 120Gb by a few gigabytes to the left on one of my laptops was a test of the patience! Many cups of coffee and a nap later.....

---

### Post by ByteJuggler on 2009-05-05
> **vahnx said:**
> About defragging first, I never thought of that, but would it matter? I'm pretty sure GParted does it sector-by-sector whether data is there or not. If there's like 100GB of free non-contiguous space doesn't it still take the same amount of time to move that empty area as it would if data was scattered there?

No, to perform the actual resize, the filesystem itself is essentially truncated -- no free space is moved around needlessly.  This truncation can only happen if there's no data blocks towards the end of the partition.  Last time I checked GParted didn't do any logical filesystem defragging in order to empty the space at the end of the partition in preparation for the truncation -- this is left to Windows based filesystem defraggers.  

However, any other moving of the partition obviously happens sector by sector and takes no notice of the filesystem blocks in the partition, so will take the same amount of time regardless of the fragmentation state of the filesystem in the partition.

---

### Post by Ambly on 2009-05-08
Well i try to read all "conversation", but its endless.
Thank you for sharering your mistakes, cause i was about to do the same on my ps3 (320gb hd, 250gb for ubuntu and 70 for ps3 OS). I will backup everything (important stuff) to the original 40gb HD (now external), format from the beginning and reinstall ubuntu.
Hope that takes a few hours not days. LOL

---

### Post by Lockheed on 2009-11-28
What a useless piece of software Gparted is! To resize the same partition Acronis and most any other partition tool takes seconds!
Gparted developers should really have their heads checked.

---

### Post by mgol on 2009-12-15
Actually, if You look at what exactly GParted does You'll see that it does fsck after nearly each operation (sic!); it also often does read-only test before doing an actual move, it chooses optimal blocksize etc. etc. I don't see what is the reason for all that redundance. Come on, if I wanted to check my partition integrity, I would do it myself. Because of that I saw several times the following scenario on large partitions:
1) fsck - 1 hour
2) shrink/etc. - a few seconds
3) fsck - 1 hour
No wonder why it takes so much time...

Anyone knows what's the point of all those time-consuming steps?

---

### Post by tom.swartz07 on 2009-12-15
> **mgol said:**
> Actually, if You look at what exactly GParted does You'll see that it does fsck after nearly each operation (sic!); it also often does read-only test before doing an actual move, it chooses optimal blocksize etc. etc. I don't see what is the reason for all that redundance. Come on, if I wanted to check my partition integrity, I would do it myself. Because of that I saw several times the following scenario on large partitions:
1) fsck - 1 hour
2) shrink/etc. - a few seconds
3) fsck - 1 hour
No wonder why it takes so much time...

Anyone knows what's the point of all those time-consuming steps?
Stability, sir. Stability.

I understand your point- it does seem a bit redundant, but when youre moving hundreds of gigabytes of data, you need all of the safety checks possible, to make sure nothing is 'lost' along the way. 
Id rather take a 3 hour resize over losing my whole disk in 10 minutes

---

### Post by lisati on 2009-12-15
I'd rather have fsck take an hour and find nothing wrong, than have to spend several hours recovering data because of a problem that would have been fixed if fsck had been run but didn't find because it wasn't run.

---

### Post by mgol on 2009-12-15
I see Your point but I sometimes resize partitions with no unrecoverable & fragile data but with things I could recreate within a day or two. Taking that partition failures happen very seldom (from my experience) I would still win a lot of time (in average). At least an "unsafe" operation procedure should be available (of course, with all warnings etc. etc.) for such operations.

---

### Post by rkakkar on 2009-12-15
Couldn't gparted be program in such a way that if a particular sector doesn't have data on it (free space), then there is no point copying/moving it? i guess that would improve the speed drastically!

---

### Post by mikechant on 2009-12-15
I'd just add that I think there's more going on with the original problem than just 'gparted being slow'. I've used it a lot, and generally can resize/move multi-hundred Gb partitions on internal and external drives in a few hours, not days. I suspect that the orginal poster's external drive was running at USB 1.1 speeds rather than USB 2.0 (which with USB1.1 being 40x slower than USB2.0, would definitely make gparted take 'forever' on some operations!).

---


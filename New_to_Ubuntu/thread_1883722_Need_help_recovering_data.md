---
title: "Need help recovering data"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by twitch7669 on 2011-11-19
I desperately need help.. Think I just made a major mistake...

I was trying to "reclaim" part of a drive that was no longer being used - long story, but had problems updating to Ocelot and had copy of Ocelot installed on second drive and used this install to recover primary installation.  Now that primary install is OK, wanted to get this drive space back.

I was trying to use disk utility to format this portion, and looks like I reformatted the entire drive!!! 

I really thought I knew what I was doing, so I can't give the entire process that I followed (i.e. first selected format volume, etc.).  But at this point this drive shows up as unallocated space.  I had a LOT of information on this drive that I do not want to lose - pictures of kids, videos, etc.  

Is there anything I can do, or any measure I can take to recover this partition?  I'm not sure if the drive is truly formatted and wiped clean, but I didn't want to monkey with it any more until I get some expert advice.

If you haven't noticed, I am a complete novice at Linux, so any help/guidance/prayers for recovering this data would be greatly appreciated.  Thanks in advance!

---

### Post by Rex Bouwense on 2011-11-19
Try using Testdisk.  It is in the repositories.  That should solve your problem unless your data has been overwritten.

There was another program, I think it was called PhotoRec.  It may be the same program.  I know for sure that Testdisk is there.

---

### Post by rbc on 2011-11-19
First of all, if you want to do this the right way, stop using the hard drive. I think you’ve figured that out already. Secondly, you should get two more hard drives of equal or greater capacity. You want to use the dd command to clone the messed up hard drive to one of the spares. This way, you’re experimenting on a copy instead of the original. Do a lot of reading on the dd command, and ask questions before proceeding. If used incorrectly, dd can make matters worse, and irreparable. As the previous poster suggested, try using testdisk and/or photorec. Tesdisk has become a tool for repairing partition tables and deleted partitions. This may actually fix you problem. If not you’ll want to move on the photorec. Its primary use is carving files, even after they’ve been deleted, or if they were on a partition that was reformatted. If you end up using photorec, you will want to carve the files from the clone, and recover them to the third hard drive that I mentioned. Be aware that when photorec recovers files, the files will not have their original names, so you will have a lot files to wade through. Best of luck and please post back with questions.

---

### Post by rng on 2011-11-19
I have had similar problem earlier. A quick format changes only partition table etc so the data may still be there. Consider following steps: 

1. Do not use that computer/ hard disk unless you know exactly what to do.
2. Get a good linux livecd (I would use ubuntu 10.04 long term support) and boot it on another computer so that you are comfortable using it.
3. learn about 'dd' command; use it very carefully since if you write on the hard disk, the data will surely be lost. General format is ' dd if=/dev/sdx  of=/dev/sdy ' where 'if' stands for infile and 'of' stands for outfile; sdx and sdy are disk drives which should be correctly identified and entered, else you may write on wrong disk. Obviously, sdy disk drive should be same or larger in size than sdx. Many users have directly used testdisk without backing up crashed disk since backup using dd takes lot of space and time, and is not without risk.
4. Download Testdisk application from synaptic while running livecd and use it to recover the partitions. It has saved many lost partitions.

Wait for more responses to this thread; do not proceed in a hurry. Give priority to suggestions by experts/moderators. Also consider professional help for precious data.

---

### Post by twitch7669 on 2011-11-19
Thanks for the advice guys...

Found this site linked to a similar problem:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Tried testdisk first, but didn't seem to detect much.  However, running Photorec right now and seems to be doing the trick.  Still gotta a couple of hours to go, so post an update when done.

---


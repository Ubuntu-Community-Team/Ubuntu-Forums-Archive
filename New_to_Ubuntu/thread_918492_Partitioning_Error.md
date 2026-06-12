---
title: "Partitioning Error"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Steel Bovine on 2008-09-13
So I put together a new system, threw in my WD velociraptor 74GB hard drive, and started her up.  Of course, I can't boot into Windows because of some activation issue, and I can't activate because its not picking up my network connection.  So..  I reach into my binder of CDs and pull out a Feisty Fawn live CD.  Score, right?  I just want to wipe that drive clean, but I am having an issue.

I wanted to do a 15GB ext3 partition at the end of the drive (I am a Windows developer, I will need to have Windows as my primary OS) for Ubuntu.  I was fine with using the Feisty disc and updating later.  It took me through the partitioning process, I set everything up - front of the disc empty space, last 15GB ext3, fought with its insistence that I should have a dedicated swap partition (I think this is stupid) and told it to Make It So.  It starts the process, gets to about 15%, and has the following error:

> Failed to create file system: The ext3 file system creation in Partition #1 of SCSI4 (0,0,0) (sda) failed. 

Then it just goes back to "Starting up the partitioner"

Any clues?

---

### Post by Pro-reason on 2008-09-13
A Feisty CD must use quite an old version of the partitioner.  We're nearly on Intrepid.  Before that, there's Hardy and Gutsy.  Feisty is looking a little elderly.  I wouldn't be surprised if a more recent CD could do a better job.

Perhaps you could let it install to the entire drive (it might prefer that), and then once you're online you could do whatever you need to do.

---

### Post by antoz on 2008-09-13
Maybe it would work better if you also create the windows partitions in front of your ext3 and swap?

---

### Post by bumanie on 2008-09-13
Off the live cd you could try to pre-partition with ext3. > sudo apt-get install gpartedin terminal. Then System --> Administration --> Partition editor. If that fails there is always the gparted live cd. By the way, although a swap is not necessary these days with the amount of RAM most users have, it is still mandatory - I always hope that ubuntu will get of this feature or at least make it optional, as unless on an old computer, it is never used. I have installed with a swap and then removed it later with no ill-effect. Have presently got a swap as I have heaps of hard drive space.

---

### Post by Pro-reason on 2008-09-13
I believe that I was able to install without swap at one point.  Maybe I misremember it.

---

### Post by caljohnsmith on 2008-09-13
If you don't like having a swap partition, you can instead make a "swap file" in your main Ubuntu install, and make it any size you wish. If you want to go that route, let me know and I'll help you with the details of doing it.

---


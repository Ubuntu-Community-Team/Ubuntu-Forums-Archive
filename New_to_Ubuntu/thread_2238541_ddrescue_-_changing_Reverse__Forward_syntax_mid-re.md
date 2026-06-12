---
title: "ddrescue - changing Reverse / Forward syntax mid-recovery &amp; save to same image file"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by ryusoom on 2014-08-08
Hello,

I experienced a failing of a Samsung HD54UI drive and I have over the course of May/June/July tried many different attempts at recovery. Having recently stumbled across ddrescue and the associated reading, I now realize that I could have significantly benefited from having made an image of the failing drive in the first place, before doing any poking around. Anyway what's done is done and now I find myself here. Hello!

So I have two drives; the faulty 1.5TB (**sdg**) and another 1.5TB (**sdh**) for the backup. From memory **sdg **had numerous partitions and the first partition (**sdg1** I believe?) is approx 340GB. It’s a few weeks out of date but I do have an image backup of sdg1 thankfully but all the data after **sdg1 **is where all the bad sectors appear to be residing. Prior to using ddrescue I'd often run into problems when attempting to mount the faulty drive (presumably due to the bad sector count) so my logic after some ddrescue reading was to try and recover the data in reverse.

I’ve run the command: **ddrescue -R -d  /dev/sdg O_Faulty_DD.img test.logfile**

which appears to be working (slowly - 16 days) and shows the following in the terminal:

GNU ddrescue 1.14

Press Ctrl-C to interrupt

Initial status (read from logfile)
rescued:   698597 MB,  errsize:    155 GB,  errors:     240
Current status
rescued:   698617 MB,  errsize:    155 GB,  current rate:    65536 B/s
   ipos:   645924 MB,   errors:     240,    average rate:    87477 B/s
   opos:   645924 MB,    time since last successful read:       0 s
Copying non-tried blocks...

Having watched with great admiration how this wonderful utility has been chipping away at all the bad sectors at a determined yet snails pace, speed has now increased beyond B/s and I’m inclined to think that the recovery has passed all the bad blocks and is now, recovering the remaining good blocks. So my questions:

Is it possible to Ctrl+C and whilst using the same log file (**test.logfile**), instruct ddrescue to start recovering the blocks from the beginning of **sdg **until it eventually merges/joins up at the position (640GB approx) where it is now, without wiping out any of the data already rescued by the reverse operation? If it is, could somebody let me know the syntax I’d need to use in order to do this please?

The other question is one that I haven’t been able to dig into yet which is how I’d finally go about restoring the recovered image (**O_Faulty_DD.img**) on to a third hard drive (**sdi**) in order to retrieve ‘the recovered good blocks’?

Any help would be much appreciated.

---

### Post by ryusoom on 2014-08-13
bump

---


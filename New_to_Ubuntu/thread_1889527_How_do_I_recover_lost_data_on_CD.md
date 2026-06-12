---
title: "How do I recover lost data on CD?"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by bwallum on 2011-12-01
Hi

I have a 4.7GB write only cd on which 2.7GB of images has been saved. I could see them now I can't, it reports 'no files found'.

Is there any linux utility that can look at a cd and recover lost files?

---

### Post by androssofer on 2011-12-01
> **bwallum said:**
> Hi

I have a 4.7GB write only cd on which 2.7GB of images has been saved. I could see them now I can't, it reports 'no files found'.

Is there any linux utility that can look at a cd and recover lost files?

i think GNU ddrescue shud do it...

there is info on it here:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Mark Phelps on 2011-12-02
> **bwallum said:**
> I have a 4.7GB write only cd ...

If it really was "write only", once you wrote to it, you couldn't then read from it.

So, which media format is it: CD-R or CD-RW.  I'm guessing what you meant is CD-R.

If you write to a CD and then do not finalize it, sometimes it can't be read because it's not actually been "closed".

---

### Post by Garland Fox on 2011-12-02
At 4.7 gb it not a cd it a dvd

---

### Post by bwallum on 2011-12-08
Garland Fox - Indeed it is a data dvd, apologies if the generic cd confused.

androssofa - thanks for the gddrescue cue, it is currently trundling away having recovered most data, it is now 'splitting' damaged blocks and recovering more bits albeit very slowly.

Mark Phelps - its a dvd -R

gddrescue is quite intimidating at first. If you try to put a path in front of the output file it thinks you want to write the recovered data directly to the partition of the path AND completely over write the drive. You need to write the recovered data as a diskimage, then burn it onto a new cd (or dvd -R in my case)

I used this simple command:-

```
ddrescue /dev/sr0 dvdimage logfile
```/dev/sr0 is my optical drive, dvdimage, the image file that you burn to new media, is written to the Home folder. (/home/Yourusername)The logfile is written there too.

The logfile keeps track of the recovery and enables you to stop and restart the data scan without going back to the beginning each time.

It is taking days but is fully automatic. Other interesting finds on the journey include:-

[https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive](https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive)

Having made the first big bite at recovery, I risked cleaning the dvd with contact lens solution and quite firm radial wipes using a lint free cloth. This helped. From an initial 110MB in 'errsize' I am now down to 13.7MB and still running. Total run time has been around 36 hours so far.

Hope the above helps and thanks again for your assistance.

EDIT
I tried the following command and it cut the recovery time down to 15 minutes!
```
ddrescue -b 2048 /dev/sr0 dvdimage2 logfile2
```

---


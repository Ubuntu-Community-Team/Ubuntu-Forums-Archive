---
title: "New 8.10 install - two drives"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Yankee_Fan on 2008-11-04
I am installing 8.10 on a clean machine with two hard drives: drive 1 - 300GB, and drive 2 - 750 GB.  I want to use the machine for Ubuntu only, no dual boot.  What would be the best way to partition these drives?  Thanks.

---

### Post by platinumits on 2008-11-04
Basically the partitions are more useful for computers with only one small disk or using differents operating systems but in your case you have space enough to use, maybe the good practice is use one of your disks for backup

---

### Post by Yankee_Fan on 2008-11-04
Huh?  You mean dont use a drive?  I thought I could use something like LVM to make both drives look like one....How can I do that?

---

### Post by Zzl1xndd on 2008-11-04
You can use LVM although I personally wouldn't do that in your situation, I would store my OS on the smaller one and keep the larger one for all my music/moves etc, that way if my OS goes bad I can reinstall without touching my files.

---

### Post by Paqman on 2008-11-04
> **Yankee_Fan said:**
> Huh?  You mean dont use a drive?  I thought I could use something like LVM to make both drives look like one....How can I do that?

Yep, I believe you'll need to alternate CD for that. It should have an option during partitioning to set up LVM.

---

### Post by Yankee_Fan on 2008-11-04
> **tweakedenigma said:**
> You can raid the drives together although I personally wouldn't do that in your situation, I would store my OS on the smaller one and keep the larger one for all my music/moves etc, that way if my OS goes bad I can reinstall without touching my files.

hmm...using a 300gb drive just for OS...?  Seems like a waste of space...but I like the idea of having all my files on separate drive.  If I were to go this route, how would I set up the partitions on the drives...I'm a newbie at this so I'm kind of confused

---

### Post by Zzl1xndd on 2008-11-04
You could just use the guided install on the first drive and then format the second drive in the format of your choosing.

---

### Post by Yankee_Fan on 2008-11-04
Would it make sense to put /home on the second drive?

---

### Post by Zzl1xndd on 2008-11-04
That would probably be a good Idea seeing as all your setting and such are stored there.

---

### Post by Elfy on 2008-11-04
If you go that route I would set up some partitions on the smaller drive

root - 15Gb
swap - if you need to hibernate then should equal RAM, otherwise you can use less
home - (although I no longer do it - and store all data elsewhere)remainder of drive

or if you go without a seperate home

root - 20Gb
swap - as above
data - remainder

---

### Post by louieb on 2008-11-04
You only need 10-30GB for the OS. The rest of both drives can be used for data storage. I like to partition so that my data is on a different partition from the OS.   Might take a look at how I partition my Ubuntu Linux only desktop. [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") 

One drive looks like this. 
[IMG]http://louboldt.com/part_whitebox.png[/IMG]

You could do something similar. This setup is on a 40GB drive. If I were to put on a larger drive the only change I would make is increase the size of the last partition to take up whatever space is left after seting up the other partitions.

The other drive (40GB drive too) has a small swap partition. the rest of the drive is one partiton and is used for storing data.

---


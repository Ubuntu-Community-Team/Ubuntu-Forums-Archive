---
title: "I reformated my External and I don't know how to get my data back."
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Sugi on 2008-06-06
Oh kay, I know I am dumb for doing this, but let me explain the problem.  I was going to reformat and install Windows XP on my old computer.  So, I had my external hard drive in and a USB wireless adapter in.  Not knowing, I unplugged the USB adapter and left the external plugged in.  I went to reformat and made two partitions out of my external, after notices what I have done.  I freak and turned off my computer.  Now, I have two partitions both in a raw format on my external.  What should I do?

In windows, I do have a trial of Get Data Back (I heard it was pretty good.)  I am afraid though, because it's two partiton.  I will only get half of the my data back.  Should I just make another reformat for the external?  I don't know what to do and I am pretty scared.

Is there a good program for linux?  I would be willing to try anything. >.<

Thank you for your time,
Sugi

---

### Post by CameO73 on 2008-06-06
Almost any recovery program will analyze the data before trying to restore it. That means you can try a couple of programs to find out how much data you can get back.

A couple of tips:

[LIST]
[*]Don't try to restore the data on the same disk (!) Get another disk and use that as the 'recovered data'-disk. Only reformat or repartition the damaged disk when you're sure you got everything you need.
[*]Make sure no other programs will be using the disk (e.g. a defragger utility) in the mean time. Remember: the more data is shuffled or written to that disk, the less you can recover!
[*]Depending on the stuff you did you can recover a lot or (almost) nothing at all. A quick format is nothing more than a 'remove the index list of this partition'; the actual data is still available. A full format makes it a whole lot more complicated (since the actual data will be overwritten with empty blocks). Repartitioning is not as bad as a full format, but will diminish your chances of recovery.
[/LIST]
I don't want to try to discourage you, but -depending on how much you have done to the disk- getting half your data back will be a miracle. I usually have more luck getting the stuff from other locations (e.g. from previous e-mails, the original download site, a backup CD, on another PC) than from a formatted and repartitioned disk.

A (very) good tool is the [System Rescue CD](http://www.sysresccd.org/Main_Page). But using that to full effect will require some knowledge about the filesystem and Linux system tools.

My advice: try to get that data back some other way. If that's not possible, try some (non-destructive) other methods (like using another drive for the recovered data).

Good luck (you'll need it)!

---

### Post by Sugi on 2008-06-06
CameO73, thanks for the advice.  I haven't done anything else to the external then the windows reformat program (what ever they use before installing windows xp.  It's the blue screen with a list of partitions)  I think it would be define as a quick reformat?  Do you think I should just do another quick reformat to make the two partitions into one or just let it as it is?

Sugi

---

### Post by didac on 2008-06-06
Check:

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Wandering on 2008-06-06
If all you have done in Windows is to create two new raw partitions on your drive, you can salvage everything, by 

delete both new partitions
create one new partition of the whole drive make it Primary, Active
Name it as before
if it was a windows partition, assign the same drive letter to it.
Don't format it.

It should be back with all data intact.

It may work with a Linux partition as well, and is worth a try. 

In any event good luck

---

### Post by Sugi on 2008-06-06
I "Deleted" the partition and made two new partitions out of it. I did not click reformat on it or put anything new on those two partitions.  Just to clear that up, I did not push reformat.  I just deleted it's partitions (if that makes any difference).

Wandering, I think the external was named Local Disk, but I don't think it was given any letters. Because every time you pluggedthe external into windows, it would get a letter depending on how many HD and cd drives was in the windows box.

Example:  If the person had a C: drive, the external would be D: drive.
But if the person had a C: and cd drive named D: then the external would be a E: drive.

So, How should I go about fixing it?  Should I just delete the two partitions and make it a single partition and name it "Local Disk"?

Thanks,
Sugi

---

### Post by cariboo on 2008-06-06
As per your sig:): You have to install it first. Here is a link:

[http://www.linuxgenuineadvantage.org/](http://www.linuxgenuineadvantage.org/)

Have fun:)

Jim

---

### Post by Wandering on 2008-06-09
Well, based on what you say, you can

delete both new partitions

create one new partition as extended

Name the partition as close as you can get to the old name

You don't have to assign a drive letter to it.

All the above is done in XP's Disk Management.

Hopefully, when you close the DM and unplug the usb cable, you should be able to plug it back in again, shortly, and all will be well.

Hopefully!

In any event you have nothing to lose. You can always use the various recovery packages, but much will still be lost.

Good luck.

---


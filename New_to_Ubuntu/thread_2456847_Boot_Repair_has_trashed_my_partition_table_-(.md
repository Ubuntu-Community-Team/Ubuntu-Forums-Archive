---
title: "Boot Repair has trashed my partition table :-("
date: 2021-01-20
forum: New to Ubuntu
---

### Post by brian911uk on 2021-01-20
I had been executing a very large backup of video files from my home area to an external USB drive.  Part way through it hung and I rebooted.  Unfortunately the boot failed.  I think if I remember it said it couldn't access my boot disk but not 100% sure that's what it said.

I inserted my boot-repair DVD and accessed boot repair.  I remember also when it asked me did I want to update I said yes.  I have used boot repair before and remember it did everything automatically but this time it gave me instructions to execute various commands in a terminal which I did (but didn't take a note of what they were)

Completed boot-repair and pasted report [http://paste.ubuntu.com/p/Ns5DQkWnq4/](http://paste.ubuntu.com/p/Ns5DQkWnq4/)

Rebooted and it again but said couldn't boot because it couldn't find disk 2a6fbbec-b2b4-417f-aea9-c0c1244b92ee which was my sdb6.  Back into boot repair.  

This time it said it couldn't complete repair and on examining pasted report it was obvious it had lost all but one if my partitions [http://paste.ubuntu.com/p/G4ThmmPWcR/](http://paste.ubuntu.com/p/G4ThmmPWcR/)

Question is, is there any way I can recover any of the data but especially the sdb6 partition from the first report.

TIA.

---

### Post by oldfred on 2021-01-20
Boot-Repair does not modify partitions.

But now report shows no sdb drive at all.
Does BIOS still show drive? If not then no software can do anything.
If shown does testdisk see drive?
or from Disks and icon in upper right corner, does Smart Status say drive is good or bad?

Do you have good backups?

---

### Post by brian911uk on 2021-01-21
Hi Oldfred,

thanks for pointing out that sdb drive was not shown on report.  For some reason I thought that the 500GB drive shown was the partition on my sdb drive which contained Ubuntu.  When I went back to check I discovered that as you say it was not shown.  The reason was that it was not mounted due to errors on startup.

Whilst trying to recover sdb drive I discovered issues with my DVD drive which I suspect was the cause of the corruption of sdb.  I disconnected this DVD drive and used a portable drive I was able to perform an fcsk on the sdb drive and then use boot-recover to finally fix everything with no major data loss.

I have continued with my backup process which started this problem.

Thanks again.

Brian

---


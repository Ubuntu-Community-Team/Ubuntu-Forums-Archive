---
title: "Help with unuinstallation"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Beefdawg on 2008-11-29
Hi everyone..I want to uninstall ubuntu. I have a little problem, I deleted it's partition using the windows disk, but when i go to look at my harddrive through windows, its says my hard drive only has 236gigs when in fact its supposed to be around 500, I deleted ubuntu but my hardrive still only has half the the space can someone help me fix this?

---

### Post by taurus on 2008-11-29
Sounds like you only removed Ubuntu from the partition but you still need to merge that space to your windows partition.  You can do that with gparted (System -> Administration) from Ubuntu LiveCD.

---

### Post by oilchangeguy on 2008-11-29
> **Beefdawg said:**
> Hi everyone..I want to uninstall ubuntu. I have a little problem, I deleted it's partition using the windows disk, but when i go to look at my harddrive through windows, its says my hard drive only has 236gigs when in fact its supposed to be around 500, I deleted ubuntu but my hardrive still only has half the the space can someone help me fix this?

from the partition manager, on the live cd, expand your windows partition to fill the unused space.

---

### Post by Olivier2371 on 2008-11-29
Hello there,

Did you delete the files or the partition?

I you are able to run windows, look under "Computer Management", then "storage", then "Disk Management".

Hope it helpful.

---

### Post by Beefdawg on 2008-11-29
I can run windows, but how do I get to computer management?

---

### Post by oilchangeguy on 2008-11-29
> **Beefdawg said:**
> I can run windows, but how do I get to computer management?

you need to follow previous instructions. and do this from the lived cd. you can't do this from windows disk management.

---

### Post by Beefdawg on 2008-11-29
Ok so I boot from the ubuntu cd and then where do i go?

---

### Post by oilchangeguy on 2008-11-29
> **Beefdawg said:**
> Ok so I boot from the ubuntu cd and then where do i go?

system, admin, partiton manager.

---

### Post by Olivier2371 on 2008-11-29
if under windows XP/vista

Control Panel->System->Administrative tools->Computer Management->Storage->Disk Management

---

### Post by oilchangeguy on 2008-11-29
> **Olivier2371 said:**
> if under windows XP/vista

Control Panel->System->Administrative tools->Computer Management->Disk Management

you can't do this from windows (at least xp) in xp the only this the op can do is to format the former ubuntu partiton. which will appear as a second drive.

---

### Post by Beefdawg on 2008-11-29
> **oilchangeguy said:**
> you can't do this from windows (at least xp)

Yeah hes right..so what do I do from the ubuntu cd then?

---

### Post by SunnyRabbiera on 2008-11-29
well what was so bad about ubuntu you have to use doze again?
We could help you out if you asked.

---

### Post by Olivier2371 on 2008-11-29
How to use Disk Management ix XP
To start Disk Management:

   1. Log on as administrator or as a member of the Administrators group.
   2. Click Start, click Run, type compmgmt.msc, and then click OK.
   3. In the console tree, click Disk Management. The Disk Management window appears. Your disks and volumes appear in a graphical view and list view. To customize how you view your disks and volumes in the upper and lower panes of the window, point to Top or Bottom on the View menu, and then click the view that you want to use.

NOTE: Microsoft recommends that you create a full back up of your disk contents before you make any changes to your disks or volumes.

Back to the top
How to create a new partition or a new logical drive
To create a new partition or logical drive on a basic disk:

   1. In the Disk Management window, complete one of the following procedures, and then continue 

to step 2:
          * To create a new partition, right-click unallocated space on the basic disk where you want to create the partition, and then click New Partition.
          * To create a new logical drive in an extended partition, right-click free space on an extended partition where you want to create the logical drive, and then click New Logical Drive.
   2. In the New Partition Wizard, click Next.
   3. Click the type of partition that you want to create (either Primary partition, Extended partition, or Logical drive), and then click Next.
   4. Specify the size of the partition in the Partition size in MB box, and then click Next.
   5. Decide whether to manually assign a drive letter, let the system automatically enumerate the drive, or do not assign a drive letter to the new partition or logical drive, and then click Next.
   6. Specify the formatting options you want to use by using one of the following procedures:
          * If you do not want to format the partition, click Do not format this partition, and then click Next.
          * If you want to format the partition, click Format this partition with the following settings, and then complete the following procedure in the Format dialog box:
               1. Type a name for the volume in the Volume label box. This is an optional step.
               2. Click the file system that you want to use in the File system box.

                  You can change the disk allocation unit size, and then specify whether to perform a quick format, or enable file and folder compression on NTFS volumes.
            Click Next. 

   7. Confirm that the options that selected are correct, and then click Finish.

The new partition or logical drive is created and appears in the appropriate basic disk in the Disk Management window. If you chose to format the volume in step 6, the format process now starts.

---

### Post by oilchangeguy on 2008-11-29
> **SunnyRabbiera said:**
> well what was so bad about ubuntu you have to use doze again?
We could help you out if you asked.

let's face it. there are just some things easier to do with another operating system. linux is not a cure all for every problem.

---

### Post by SunnyRabbiera on 2008-11-29
> **oilchangeguy said:**
> let's face it. there are just some things easier to do with another operating system. linux is not a cure all for every problem.

Yes but the point is he just joined us and now he wants doze back?
If he had issues he should have told us about them, we are a community made for that purpose.

---

### Post by Beefdawg on 2008-11-29
Well basically I can't get sound on to work on ubuntu(Stupid xfi xtremegamer) I've tried all the instructions everywhere and nothing...so I'll wait until my drivers get some support. That's about it...plus I just really want to see how to fix this problem I have with the harddrive.

---

### Post by SunnyRabbiera on 2008-11-29
> **Beefdawg said:**
> Well basically I can't get sound on to work on ubuntu(Stupid xfi xtremegamer) I've tried all the instructions everywhere and nothing...so I'll wait until my drivers get some support. That's about it...plus I just really want to see how to fix this problem I have with the harddrive.

well all you had to do was post your information, there could be better instructions for you.
Linux development is always improving, if it doesnt work now it will work soon :D

---

### Post by Beefdawg on 2008-11-29
Theres no simple way to do this is there...

---

### Post by Olivier2371 on 2008-11-29
What is the make of your HDD.

---

### Post by Beefdawg on 2008-11-29
Uh its a 500 gig western digital

---

### Post by Olivier2371 on 2008-11-29
Could do the following.

Log in to Ubuntu.

Then go to :

Application->Accessories->Terminal

Then run the following command:

sudo fdisk -lu

Post the result.

---

### Post by Beefdawg on 2008-11-29
Ok look I don't have ubuntu, I put in the windows disk, and deleted that partition. NOW I have an allocated free space, and I don't know how to merge them, i've just tried a program called paragon but the merge button there was gray and I don't know what to do, I just want my hard drive to go back to 1 section, a full 500 gigs instead of 250 which is what I'm running windows xp on.

---

### Post by oilchangeguy on 2008-11-29
> **Beefdawg said:**
> Ok look I don't have ubuntu, I put in the windows disk, and deleted that partition. NOW I have an allocated free space, and I don't know how to merge them, i've just tried a program called paragon but the merge button there was gray and I don't know what to do, I just want my hard drive to go back to 1 section, a full 500 gigs instead of 250 which is what I'm running windows xp on.

ok, this has gone on long enough. 3 pages over 20 replies. you've already been given your answer. boot from the ubuntu live cd, when the desk top loads go to system, admin, partition manager. select your windows partition and follow the prompts to expand it. it's not that hard.

---

### Post by Olivier2371 on 2008-11-29
alternatively go to the western digital website support find your hard drive and then download the softwre for windows call "Data Lifeguard Tools 11.2 for Windows".

They also explain you what to do.

---

### Post by oilchangeguy on 2008-11-29
> **Olivier2371 said:**
> alternatively go to the western digital website support find your hard drive and then download the softwre for windows call "Data Lifeguard Tools 11.2 for Windows".

They also explain you what to do.

there's no need for this. the op has the tools they need. if they'll simply use the live cd.

---

### Post by Olivier2371 on 2008-11-29
Sorry oilchangeguy, I am just trying to help.

Beefdawg seems to be more comfortable using windows.

---

### Post by oilchangeguy on 2008-11-29
> **Olivier2371 said:**
> Sorry oilchangeguy, I am just trying to help.

Beefdawg seems to be more comfortable using windows.

sorry to say, i don't think the op get's it. maybe it's time to take the computer to a shop.

---

### Post by Beefdawg on 2008-11-29
WAIT wait no..I got it just finished....thanks a LOT everyone...It's just i've been installing and playing around with ubuntu and my system bios since like one in the morning and I'm like a zombie I need some sleep....tomorrow I'm gunna learn the basics and start ubuntu again, I just really want the sound to work somehoe.

---


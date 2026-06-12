---
title: "Errors At Boot?"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by Akacheebe on 2012-08-23
I get the following errors at boot on a clean install but 12.04 will still boot and run normally after about 30 seconds?

[I][B]error: out of partition.
error: no suitable mode found.
error: no video mode activated.[/B][/I]

I've also seen these errors too.

[I][B]error: invalid enviroment block.
error: out of partition
error: no suitable mode found.
error: no video mode activated
error: invalid enviroment block

Press any key to continue...[/B][/I]

Disk Utility says that the hard drive has a few bad sectors but I've used this drive before with Windows 8 without any of these problems showing up?  

Any help?

---

### Post by BBQdave on 2012-08-23
> **Akacheebe said:**
> Disk Utility says that the hard drive has a few bad sectors

I would not trust this hard drive. It is failing, or has failed. Either way, do not trust your data to it.

---

### Post by oldfred on 2012-08-23
In Disk Utility what does Smart Data say about drive. It can run a lot of tests, but all I really know is green is ok and anything else is new drive.

What video card? 

Out of partition may be some partition is not correct, but not your / ?

Even though this is more for boot issues it reports a lot of good info on system.
Post link to run of BootInfo:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Akacheebe on 2012-08-23
Well, I'm somewhat embarrassed about this but believe it or not, those error messages is gone now??  I'd been seeing them at boot since I did that clean install last night and again this morning before I made this post but now it's gone.   I've shut down and rebooted this thing about a dozen times and get no errors now?  

Things that make you go Hummmm......................

FYI that drive is reported as healthy with a green dot in Disk Utility and and it says that it has 14 bad sectors.  From what I understand, ALL hard disks have XX number of bad sectors, even NEW ones so I'm going to us it since it's all I've got.  I keep my data backed up anyway so that won't be a problem.

Oh, and thanks for the replies ppl.  If it shows up again I'll bring this post back up. 

Have a great day!

---

### Post by Lisiano on 2012-08-23
Not to burst your bubble but no, not all HDD's have bad sectors when bought. To be exact, most disks when bought have exactly 0 bad sectors. In Fact it's rare if there are. Most likely those bad sectors are a manufacturing defect, meaning that they probably will not increase. Either way, try to keep your eye on the count and if it ever goes up. Get a new disk ASAP.

---


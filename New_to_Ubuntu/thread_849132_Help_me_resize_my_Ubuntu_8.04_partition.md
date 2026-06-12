---
title: "Help me resize my Ubuntu 8.04 partition"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by carusoswi on 2008-07-04
So, I'm running dual boot, XP/Ubuntu.  When setting up, I must have miscalculated, because now, my Ubuntu partition (/ directory on my /dev/sda2/) runs never lower than 92% used space, and, when it gets to 99% used, Ubuntu starts acting up.  Then, I go looking for whatever new files might have taken up that last precious crumb of space and have to relocate it to some other spot on my system.

My two operating systems reside on a 150 GB physical drive that has, perhaps, 50% unused space, so that isn't a problem.

I want to resize the relative size of my partitions to give Ubuntu more room, since I spend more time there than I do in XP.

However, even though I consider myself somewhat knowledgeable as a computer "consumer", it seems every time I go to adjust partition sizes, the Ubuntu partitioner of the day appears unfamiliar to me, and I find myself guessing at just which of the choices to make.  Unfortunately, there is little forewarning IMO in the dialog as to the consequences of the choices one must make to resize partitions.

The world would not come to an end if I messed things up.  I keep my important data on other physical drives (internal and external), but I really don't feel like spending a chunk of my holiday weekend (American Independence Day this weekend) watching scroll bars crawl across my screen as I reinstall the plethora of applications that are part of my setup.

So, could someone be so kind as to list, step by step, what I would do in using the partitioner that is part of the 8.04 installation CD, to grab some of the space in my XP partition and assign it to my /dev/sda2 partition?

I would be ever so grateful.

Caruso

---

### Post by hyper_ch on 2008-07-04
well, what would you do to achieve your goal?

---

### Post by carusoswi on 2008-07-04
> **hyper_ch said:**
> well, what would you do to achieve your goal?

I would resize my Ubuntu partition to make it bigger.  I just don't want to slip up and ruin the installation, because I don't feel like wiping my disc and starting over from scratch, having to re-install XP, then Ubuntu, then all my aps on both platforms?

Thanks for responding, but was my question that unclear?

Caruso

---

### Post by qrwe on 2008-07-04
> **carusoswi said:**
> I would resize my Ubuntu partition to make it bigger.  I just don't want to slip up and ruin the installation, because I don't feel like wiping my disc and starting over from scratch, having to re-install XP, then Ubuntu, then all my aps on both platforms?

Thanks for responding, but was my question that unclear?

Caruso

Reboot with your Ubuntu LiveCD and execute 'geparted' or 'gparted' (don't know exactly right here and know, think it's available under Administration, otherwise: try it in terminal). It's an excellent GUI for handling several filesystems, just like you're trying to do right now.

---

### Post by carusoswi on 2008-07-05
> **qrwe said:**
> Reboot with your Ubuntu LiveCD and execute 'geparted' or 'gparted' (don't know exactly right here and know, think it's available under Administration, otherwise: try it in terminal). It's an excellent GUI for handling several filesystems, just like you're trying to do right now.

GRWE, thanks for the response.  I am generally familiar with the process . . . it's that "generally" part that make me hesitate.  I really don't want to mess up my setup and have to go back and find all the various pieces of software on discs around the house in order to rebuild it.

There must be some step by step description that pertains specifically to the 8.04 CD on this topic.  I just have to find it before I proceed.

Thanks again for your help.

Caruso

---

### Post by uarale on 2008-07-05
This is the partitions shown in Gparted:
[IMG]http://imageupload.in/files/mx0yogxfic7rugu6talc.png[/IMG]

I want to take 5GiB from /dev/hda5 for /dev/sda7 but i dont know how to do, because there's a weird unallocated partition between a windows partition and linux partition.

Is there something harmful happens if i take the unallocated partition for linux partition too?

Thanks for your help.

---

### Post by bumanie on 2008-07-05
If you remove the extended partition, you will also remove the partitions that are within. Therefore I think you are stuck, as there is no room to shift the extended partition into any unallocated space, as you have none. What is in sda1? Is that /? If so why is it taking up 17g, mine takes up about 4-5g. If /home is in sda1 along with / may be moving /home to another partition will help. [Here's how to do it]("http://www.psychocats.net/ubuntu/separatehome") but with so little space left, I'm not sure that will work. If for instance 10g of sda1 is /home, you do not have that much space left in any partition to move it to.

---

### Post by louieb on 2008-07-05
:(Go out and watch the fireworks. Your disk is rather full.  Don't think I would trust resize  - the chance of data corruption goes up the fuller the disk is. I try  to keep  NTFS partitions under 70% full, your is over 80% full. 

Anyway you can move some data to another drive?

---

### Post by uarale on 2008-07-05
to bumanie: sda1 and sda5 are windows vista partitions, while sda6 (swap) and sda7 (/) are for ubuntu. i've just get into ubuntu/linux, so i dont have much experience on these things. 

Thanks for responding, may be here is my solution:
I will take 5GiB from sda5, then move /home to it. What do you think?

By the way, which size is suitable for / (not include /home)? I think maybe about 5GiB is not enough if we work in ubuntu environment usually. I wonder because i think i will switch from vista to ubuntu totally in near future, and i dont want to reinstall ubuntu regularly.

Thank you again.

---

### Post by kansasnoob on 2008-07-05
You're really pinched for space. Time to add another drive IMO.

But, you do know that any resizing must be done from the Live CD rather than from Partition Editor from your mounted Ubuntu OS?

Seriously though, with so little free space the odds of data loss are astronomical!

---

### Post by uarale on 2008-07-05
Hi guys,

After backup current data to another disk, i format my disk and do these things:
First, i install Vista on /dev/sda1 (second from right), and make another partition for storing some windows data (sda5).

[IMG]http://imageupload.in/files/w1r6lq3rysfzrotwxxwv.png[/IMG]

Then, i want to make three partitions: the first from left for /, the second for swap, and the last for /home.
But in the last step, GParted had a warning: It is not possible to create more than 4 primary partitions! :(
I went back to the first step, tried to choose "Logical Partition" or "Extended Partition" but they are disabled! So i dont know how to make it possible.

Can you help me out of this situation? It would be great.

---

### Post by louieb on 2008-07-05
Lots of ways just a suggestion.
I guess sda5 doesn't  have anything on it yet. go ahead and delete sda5, sds2 (an extended partition), and the swap partition..
Create an extended partition in the unallocated space to the left - use all of it.
Create logical partitions inside the extended partition for swap and Ubuntu and /home.
Finally you can create a primary partition in the Unallocated space to the right.
This will keep you within the limits of 3 primary partitions + 1 extended  partition   

Might want to do a little reading on partitions and how they can be laid out on a drive. [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by -kg- on 2008-10-03
> **uarale said:**
> Hi guys,

After backup current data to another disk, i format my disk and do these things:
First, i install Vista on /dev/sda1 (second from right), and make another partition for storing some windows data (sda5).

[IMG]http://imageupload.in/files/w1r6lq3rysfzrotwxxwv.png[/IMG]

Then, i want to make three partitions: the first from left for /, the second for swap, and the last for /home.
But in the last step, GParted had a warning: It is not possible to create more than 4 primary partitions! :(
I went back to the first step, tried to choose "Logical Partition" or "Extended Partition" but they are disabled! So i dont know how to make it possible.

Can you help me out of this situation? It would be great.

First off, yes...the conventions are that you can only create 4 primary partitions.  One of these can be an extended partition, in which you can create many logical partitions.  Since Linux can run from the extended partition, you should have installed Vista in a primary partition (which it must be) and created your extended partition in the remaining space.  Install Linux in the extended partition, and make all your remaining logical partitions, which Vista can access (the correctly formatted ones, that is) and Linux can access and be booted from.  For sure, you don't need your swap partition as a primary partition!  That's taking up a primary partition space by itself.

Thing is, once you transfer your data back to this hard drive (if that's what you intend), you will still be faced with the same conundrum...not enough space.  If you intend to leave the second hard drive connected to your system, then no problem...you're home free.  But if you want to only use one hard drive, it is as has been suggested before...you need to upgrade to a larger hard drive, which would be my suggestion at any rate.  On my desktop I have 560 GB in two physical hard drives, plus I just added an external HD at 1TB.

One thing, though.  I assume you know that, if you add the second hard drive permanently, your drive letters under Vista will change.  You will have to point the appropriate software to your data on another drive letter.  Same with your data under Linux.  Of course, you have reinstalled Vista, so this shouldn't be a problem.

Another thing from an earlier post:

> If you remove the extended partition, you will also remove the partitions that are within. 

As far as I know, there is *no* partition editor that will delete an extended partition until the logical partitions within are deleted first.  Take it from me, I've tried, both with Partition Magic and GParted.  If there are any logical partitions contained within, when you highlight the extended partition, the delete option is grayed out.  Only once you've deleted all the logical partitions do you have the option of deleting the extended partition.

Edited P.S. - I re-read your question, and now I think I know what you wanted to do (I think!):

> I went back to the first step, tried to choose "Logical Partition" or "Extended Partition" but they are disabled!

Now I realize what you were trying to do (I think)!

If you wish to resize your extended partition, you are going to have to move dev/sda1 first.  Move it all the way over close to your swap partition (I would still delete that partition and create it in the extended partition once you expand it), then you should be able to resize your extended partition.  Is this the information you needed?

---

### Post by -kg- on 2008-12-27
I realize it's been a couple of months since the last post on this thread, but I have recently re-written the "How To Partition" section of the Community Wiki's.  You likely have already resolved this problem and moved on, but you can find a good bit of the information you were unclear on at:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

I think you might find this Wiki "Howto" quite informative.

---


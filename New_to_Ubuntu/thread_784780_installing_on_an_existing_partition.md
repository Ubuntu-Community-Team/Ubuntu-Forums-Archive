---
title: "installing on an existing partition"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by jxhndxe on 2008-05-06
Hello.  I've been running Ubuntu via Wubi, and I'm ready to take the plunge and properly install it on my laptop.  I'm currently running Windows XP, and want to make it a dual-boot by installing Ubuntu on what was my DATA partition.

I've gone through the installation steps, but I'm afraid I'm too much of an 'Absolute Beginner' to know what to do once I reach the partitioning segment.

I know that I should be able to just merge that partition in with the other with Partition Magic, but I keep getting errors about table inconsistencies.  Even so, XP runs just fine, and the second partition contains no errors.

So...the question is...how would I go about installing Ubuntu on this existing partition?  I'm sure I'm not the only one who has done this, so if there are some simple instructions on the web, please point me to them.

Thanks!

---

### Post by tjwoosta on 2008-05-06
its very easy

first you boot the ubuntu live cd

then you go to System-Administration-Partition Editor (this is gparted, its way better for this than partition magic)

when in gparted just delete the partition that you will be installing ubuntu to (leave it unallocated) then click apply

once the partition is deleted go back to your desktop and click the install icon

when it asks you how to install select
 "Guided Install: Use largest continuous free space"

this will install ubuntu to the unallocated space


Note: if you are planning to resize or make any changes to your XP partition at all make sure you defragment a few times first 
(just to get all the data to the beginning of the partition rather than all spread out)

---

### Post by thisiam on 2008-05-06
i think he will have to use manual, guided will install it over the whole drive which would include windows which he wants to keep.
in manual you will have to select from the unallocated space like 10gb for ext3 and say 1024mb for swap.

edit: i guess there are 3 options for guided. that would work aswell

---

### Post by tjwoosta on 2008-05-06
> edit: i guess there are 3 options for guided. that would work aswell

yes there are three option for guided install, just make sure you choose the one that says 
Guided Install: **use largest continuous free space**

not the one that says 

Guided Install: use entire disk

by the way i love your avatar thisiam

---

### Post by jxhndxe on 2008-05-07
Thanks, folks.

I'll give this a try.  I appreciate your responses.

---

### Post by jxhndxe on 2008-05-07
Ack.  I should I known this already...the partition I want to install it on isn't the "largest continuous free space".  I know it should be, seeing as it was my DATA partition...*shrug*

So, I don't think I can use the Guided Install, which scares me a little. :)

So, how would I go about using the manual without hurting my system?

---

### Post by bodhi.zazen on 2008-05-07
If you do not understand linux partitioning I suggest you stop and do some reading.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

Then back up your data from windows XP, defragement your disk from windows.

I prefer to set up my partitions prior to running the installer. You can do this with gparted, on the Ubuntu desktop CD.

How to gparted : [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

Then run the installer. At the partitioning section select manual partitioning.

Mount your windows partition at /media/windows DO NOT FORMAT IT.

Mount your root ubuntu partition at / and swap at swap. Optional mount home at /home (if you wish a /home partition). You may also want a /data partition to share with windows.

HTH

---

### Post by tjwoosta on 2008-05-07
largest continual **Free Space**

is it not the largest **unallocated** space?

but yes you should definatly read up on this stuff if your confused.

---

### Post by bodhi.zazen on 2008-05-07
yes and no

largest continual **Free Space **usually refers to free space within a partition (ie free space on a ntfs partition)

largest **unallocated** space usually refers to free, unpartitioned space. for example if you had a 20 Gb HD and the NTFS partition was 10 Gb, the remaining 10 Gb would then bee free, unallocated space in which you can create a 10 Gb (ext3) partition.

---

### Post by jxhndxe on 2008-05-08
> **bodhi.zazen said:**
> 
Mount your windows partition at /media/windows DO NOT FORMAT IT.

Mount your root ubuntu partition at / and swap at swap. Optional mount home at /home (if you wish a /home partition). You may also want a /data partition to share with windows.

I wasn't absolutely certain why I would have needed to mount my windows partition, so I went ahead with everything BUT that, and it seems that everything worked out great!  I appreciate everybody's input.  Thank you.

---

### Post by Sef on 2008-05-08
> that partition in with the other with Partition Magic

It is not advisable to use Partition Magic.  It and GNU/Linux tend not to get along.

---


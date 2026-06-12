---
title: "Reclaim unallocated space with GParted?"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by mlnease on 2012-06-17
Hello,

I've just deleted a partition after yet another failed attempt to make a practical desktop of 12.04 (dual boot).  So I have 230GB of unallocated space left over (please see attached).  Can I--and should I--use GParted to reclaim that space for my Lucid partition?  Is this practical or advisable?

Any advice would be much appreciated.

Thanks in Advance,

mike

---

### Post by drs305 on 2012-06-17
It's personal opinion. 

I'd keep it separate; it's in an extended partition so you can divide it up into as many logical partitions as you like. I prefer having a separate partition for my data, musice, etc rather than keeping it in the OS. It allows smaller and more targeted backups and I can still access the data should the OS fail.

One thing you might do before creating new partitions is to the shrink the extended partition just a bit and create one more primary partition to the left. It's much easier to create a primary partition now than it would be later.

---

### Post by mlnease on 2012-06-17
> **drs305 said:**
> It's personal opinion. 

I'd keep it separate; it's in an extended partition so you can divide it up into as many logical partitions as you like. I prefer having a separate partition for my data, music, etc rather than keeping it in the OS. It allows smaller and more targeted backups and I can still access the data should the OS fail.

One thing you might do before creating new partitions is to the shrink the extended partition just a bit and create one more primary partition to the left. It's much easier to create a primary partition now than it would be later.
Thanks very much for the quick response.  I have next to zero experience in partitioning (besides dual installations--I wouldn't begin to know how either to use a separate partition for data *or *create another primary partition--not to mention what for--) so, if it really doesn't matter much, I suppose I'll just leave things as they are for the time being.  Thanks again.

---

### Post by Mopar1973Man on 2012-06-17
> **drs305 said:**
> It's personal opinion. 

I'd keep it separate; it's in an extended partition so you can divide it up into as many logical partitions as you like. I prefer having a separate partition for my data, musice, etc rather than keeping it in the OS. It allows smaller and more targeted backups and I can still access the data should the OS fail.

One thing you might do before creating new partitions is to the shrink the extended partition just a bit and create one more primary partition to the left. It's much easier to create a primary partition now than it would be later.

Agreed... I'm setup that way on my Windows side...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219863&stc=1&d=1339981556[/IMG]

---

### Post by AgentZ86 on 2012-07-04
Hi people

Wondering about this topic a little

Is there any reason to try to make the unallocated space of an extended partition into a primary partition ? and can that be done ?

I have primary partition windows xp, extended partition ubuntu 11.10

I want to create 2 more partitions with windows 7 and ubuntu 12.04

Can this be done easily with the extended partition

The problem is that I shrunk the primary partition so now I have unallocated primary partition space

And shrunk the extended partition with ubuntu 11.10 to make way more room also

So now I have 2 unallocated spaces, 1 in the primary and 1 in the extended

How can I reclaim the space and make unallocated space in either partition to do whatever I want ? 

Please advise thanks

---


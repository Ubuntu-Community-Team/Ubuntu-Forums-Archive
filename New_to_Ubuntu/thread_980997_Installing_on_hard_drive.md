---
title: "Installing on hard drive"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by SectorNitad on 2008-11-13
Hi,

total newbie question:

I have two hard drives. One has Vista, which is the default boot. I need to install Ubuntu 8.10 on to the other hard drive. I started to run the install app but got cold feet half way through as it did not appear to ask me where it was going to install to. The second hard drive is not even formatted yet but does show up in the bios.

do i need any additional software? Any help much appreciated..

thanks
H

---

### Post by taurus on 2008-11-13
How far along did you get with the installer before you terminated it?  Did you get pass the partition screen?

---

### Post by Paqman on 2008-11-13
Don't worry, it _will_ check with you where it is going to install the system.

(Unless you are using Wubi, in which case it always installs into the Windows partition)

---

### Post by kansasnoob on 2008-11-13
Well, time to do some studying:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

That of course is just one example from:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

What you must first understand is how Linux recognizes drives and partitions. You can forget about Drive C etc! First hard drive is sda, second sdb, third sdc, etc. 

First partition on drive #1 is sda1, second is sda2, etc.

First partition on drive #2 is sdb1, second is sdb2, etc.

I strongly suggest doing some intense studying first.

---

### Post by mapes12 on 2008-11-13
> I strongly suggest doing some intense studying first.

.......and this is the first place I would look up: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

> Don't worry, it will check with you where it is going to install the system.
 I wouldn't bet on it. The default is "Guided - use entire disk" may zap your first HDD. A Better option is to use GParted (Off the live CD or from the GParted website) and set up your partitions properly ahead of the install. Then, when you get to the "Partitioning" stage select "Manual" and for each partition set the variables. If you read the Psychocats link above you will see what I'm talking about.

---


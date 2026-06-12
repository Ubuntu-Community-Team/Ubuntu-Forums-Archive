---
title: "I just installed ubuntu on a 1TB drive...is this good?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-06
Hi,

Should i shrink it and make 2 partitions ?

What should i do?

Thanks

---

### Post by iaculallad on 2008-06-06
Installing Ubuntu on a 1TB drive (w/o any partition) would be an overkill. I mean, try creating partitions to be in the safe side for your data backups. You wouldn't want to store all your documents, music, movies, etc.. on a single drive without thinking of consequences.

---

### Post by hopelessone on 2008-06-06
ok what to do..? a reinstall? shrink it?

---

### Post by hopelessone on 2008-06-06
Any partition help on a clean install on a 1TB drive...?

Thanks..:popcorn:

---

### Post by Technoviking on 2008-06-06
> **hopelessone said:**
> ok what to do..? a reinstall? shrink it?

Sound like you are fairly new to Linux. A re-install would probably be easier if you have your data backed up.

---

### Post by hopelessone on 2008-06-06
Ok i'll boot back into the live cd then post here...

:(

---

### Post by hopelessone on 2008-06-06
> **Mike said:**
> Sound like you are fairly new to Linux. A re-install would probably be easier if you have your data backed up.

Ok i back in the live cd...

how to i partition to say Operating System,home and the rest ext3

any suggestions on size etc...

thanks

---

### Post by Sef on 2008-06-06
You want Ubuntu as the sole OS, right?

I would make the Ubuntu partition around 10 GB.  A swap around 1 GB.  The rest could be a home partition.  

You would need to manually partition the hard drive.  It is not 
too hard to do, but it can be confusing the first time.  

A basic tutorial:

1) Delete the partitions first, then highlight the free space (Enter):

2) For partition 1, set it as a primary partition (next) > 10 GB (next) > it should come up with root (/) > set it to be bootable > Done setting up the partition (Enter).

Highlight the remaining free space (Enter):

3) For partition 2, set it as a primary partition (next) > all except 1 GB (next) > set a home partition (/home) > Done setting up the partition (Enter).

Highlight the remaining free space (Enter):

4) For partition 3, set it a primary partition (next) > 1 GB (next) > Change ext3 to swap > Done setting up the partition (Enter).

5) From the main Partition Menu > highlight  Finish partitioning and write changes to disk (Enter) > Yes

---

### Post by hopelessone on 2008-06-06
Oh hi Sef nice to see you again..

> > set it to be bootable > Done setting up the partition (Enter). in Gparted how do i achieve this?

thanks

---

### Post by hopelessone on 2008-06-06
like this?

finalize it?

thanks..

---

### Post by hopelessone on 2008-06-06
OK after I finalized it i set it to boot...

Dunno how to set the second one to home though?

Ok gonna try install...

---

### Post by hopelessone on 2008-06-06
Ok am stuck..what do i do here?

Thanks..

---

### Post by hopelessone on 2008-06-06
Ok i think i actually got it...go ahead?

---

### Post by hopelessone on 2008-06-06
Well i did the install and get ERROR 17: Cannot mount...

Arrrrrhhhggg..

What do i do to fix?

---

### Post by skybreaker on 2008-06-06
Hello, I am french, so sorry for any mistake,

your partition table is not good but and you have to define mount point for each ext3 partitions.

So first, create a 10GB partition for the system, another partition for your document on Ubuntu, and a third to store you document. Don't forget to create a 2GB swap.

I saw that you have another disk with ntfs partition so you may have windows.

If its true, set the third partition as ntfs too (ntfs3g works fine now) or fat32 to make this partition available on windows.

Else, set the three partition to ext3.

Next, when you prepare partition, select a partition and clic on the Edit button. On this new message box, define the mount point.

For the system 10 GB partition : /
For your home partition (document on system): /home
For your document : /media/document or /media/extra or /media/whatyouwant.

The swap partition dont have mount point so don't worry.

---

### Post by Sef on 2008-06-06
> Well i did the install and get ERROR 17: Cannot mount...

GRUB Error 17:

> 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Let me check and see if I can spot anything.

Also /sdd2 is only 1 GB.  If you want to use it as /home, then you need to make it bigger.

Are you using the Live CD to reformat?

---

### Post by hopelessone on 2008-06-06
i started a new thread as this was getting off topic here:

[http://ubuntuforums.org/showthread.php?t=820251](http://ubuntuforums.org/showthread.php?t=820251)

i am awaiting your commands oh mighty one...

---

### Post by hopelessone on 2008-06-06
How big should home be? Make it the rest of the drive?

Are you using the Live CD to reformat?

yes..

---

### Post by skybreaker on 2008-06-06
For me, i think 3gb mini, Home is for your document, but for your configuration of some software too, skin, icons... so it must be the size that you need. If you have place on your hardrive, 10gb or more.

[edit]Have you just rezize partition or clean all and make new ?

---

### Post by hopelessone on 2008-06-06
ok...
gonna do a new install right now..

---

### Post by hopelessone on 2008-06-06
can i make it
10Gb as "/"
1Gb as "swap"
rest as "home"

what do you think? or is it better to do home as 3Gb as suggested....

btw am eagerly awaiting to install ubuntu...glued to the keyboard you might say...

---

### Post by hopelessone on 2008-06-06
one guide says:
4.4.3. Where should I put my swap space?

The short answer is anywhere is fine. However, if you are interested in extracting as much speed as possible, 
    *      Put each swap partition on the outer tracks. 
so "swap" last?

please reply so i can start the install...

i appreciate your help..

---

### Post by _sphinx_ on 2008-06-06
Ok, I must say I may be wrong at this but I am quoting my experience. If your RAM is more than 1GB your swap doesn't really affect your speed of System. But if it is less than 512MB it does. My guess is that you have more than 1GB, so if you don't want to hibernate your System frequently you can place your swap anywhere, but if you do then I guess you should place it in outer tracks. I repeat I am not sure about my last statement but for the rest, I am pretty much sure.

---

### Post by billgoldberg on 2008-06-06
> **hopelessone said:**
> can i make it
10Gb as "/"
1Gb as "swap"
rest as "home"

what do you think? or is it better to do home as 3Gb as suggested....

btw am eagerly awaiting to install ubuntu...glued to the keyboard you might say...

This is perfect.

After you partitioned, choose a manual install, and give the 10 gb "/", the 1 gb swap (from the list) and the 990 gb -> /home.

---

### Post by hopelessone on 2008-06-06
Thanks...I got 4Gb Ram...

so last question then i can install make home the rest of the drive or make it 3gb? does it really matter?

---

### Post by hopelessone on 2008-06-06
> **billgoldberg said:**
> This is perfect.

Ok off i go...!!

---

### Post by _sphinx_ on 2008-06-06
I have 1GB RAM and 1GB swap and 99% of the time my swap usage is just 0%. Hope this make you more confident towards your 1GB swap.

---

### Post by billgoldberg on 2008-06-06
> **hopelessone said:**
> Thanks...I got 4Gb Ram...

so last question then i can install make home the rest of the drive or make it 3gb? does it really matter?

If you make home only 3 gb, you'll get in trouble

/home is where you store everything, including videos, music, ...

so 3gb is way to little

but I see you already got it.

---


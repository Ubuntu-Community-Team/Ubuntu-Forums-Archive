---
title: "Can I replace Windows Vista with Ubuntu"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by michellabruyere on 2012-09-03
Hey there,

So, I'm really new to Ubuntu and till so far I'm really enjoying this! I really support the use of open source software but unfortunately I'm not that handy  with the technical aspect, yet.

I'm using a laptop with not that a terrible big amount of diskspace (I have two disks of approx30GB) and one of those disks is already 2/3 full with Windows Vista (24GB) and the other one has Ubuntu on it. (approx 15GB) So my question is: can I replace the windows operating system with Ubuntu? 

And, does the space Windows Vista uses influence the working speed of Ubuntu?I don't think I'm using wubi (off which I have understood it is running under Windows OS)

So there it is, an absolutely beginners question! I hope someone can help me out!

---

### Post by mastablasta on 2012-09-03
> **michellabruyere said:**
>  can I replace the windows operating system with Ubuntu? !
yes, if hardware is supported all you need to do is reformat the hard disk and install ubuntu (you can format it during instalation)
>   
And, does the space Windows Vista uses influence the working speed of Ubuntu?
 
not with side by side dual boot. make sure you have enough swap space in /swap parition and also more disk space i salways good to have.
 
if it's a wubi install then NTFS fragmenation could slow it down a bit.

---

### Post by michellabruyere on 2012-09-03
Thanks! I guess an external hard disk can solve my space problem then. And how can I find out if I'm using Wubi? If not, than I have a fully independent OS with Ubuntu right?

---

### Post by coldraven on 2012-09-03
Here's another option.
Buy a new hard drive, I got a 250GB drive for £30.
Buy an USB drive enclosure, mine cost £5 from ebay
This link was the first one that my search found
[http://www.ebay.com/itm/2-5-Hard-Drive-Sata-External-Enclosure-Silver-Case-Box-USB-2-0-/150870955586?pt=US_Drive_Enclosures_Docks&hash=item23209c1642](http://www.ebay.com/itm/2-5-Hard-Drive-Sata-External-Enclosure-Silver-Case-Box-USB-2-0-/150870955586?pt=US_Drive_Enclosures_Docks&hash=item23209c1642)

Swap your existing drive for the new one and put the old one into the enclosure.
Install Ubuntu onto your new drive.
Bingo! You now have lots of space and can access your files via USB. When you are happy just format the old drive and use it for portable storage. I usually format them as NTFS so that I can transfer files between Windows, Mac or Linux machines

---

### Post by king EZi on 2012-09-03
> **michellabruyere said:**
> Thanks! I guess an external hard disk can solve my space problem then. And how can I find out if I'm using Wubi? If not, than I have a fully independent OS with Ubuntu right?

If you are using wubi you would have to log in to your Windows account to use Ubuntu, but if you install and you get an Ubuntu log in prompt after boot then you aren't. 

PS: If you plan to replace Vista with Ubuntu, don't use Wubi. 

Good luck on the move :)

---

### Post by Bartender on 2012-09-03
Laptops with two physical HDD's aren't very common, so please don't be offended if I ask this question.  Are you sure you've got two HDD's, or are you referring to separate partitions?  

It sounds like you're not using Wubi.  One rule-of-thumb I've heard more than once is that Windows likes to have at least 20% of a HDD free.  After that it begins to slow down.  I don't know if Ubuntu is similar?

Can you give us the exact model of laptop?  Two reasons: we can check to see if there are actually two HDD's, and we can see how difficult it is to get to your drive or drives.  

I mention this because +1 on coldraven's idea.  Laptop drives are pretty darned cheap anymore.  HDD's can be really easy to access, but not all of them are.

However, there are some complications.  If you actually have two physical HDD's, and Ubuntu is installed to the second drive, then I'd say that you might as well remove BOTH drives and put in one new drive.  Mostly because GRUB will be set up to boot to either drive, and GRUB (part of GRUB anyway) is on the Windows drive. Removing the existing Windows drive will make GRUB non-functional and Ubuntu non-accessible.  I'm pretty sure there are ways to fix GRUB but the technical aspects might be intimidating.  

If you have just one physical HDD, and you're willing to replace it with a bigger drive, then it's a fairly simple thing.  The existing drive is safely set aside, and you do a clean install of Ubuntu to the new drive.  Data on the old drive can be accessed via an external dock.  Ubuntu would be able to access data in either partition, while a Windows PC would only be able to read the Windows-formatted (ntfs) partition.

Before doing any of this, does the Windows side of the laptop have a utility for making recovery discs?  If so, have you made them?

---

### Post by Paqman on 2012-09-03
> **Bartender said:**
> 
One rule-of-thumb I've heard more than once is that Windows likes to have at least 20% of a HDD free.  After that it begins to slow down.  I don't know if Ubuntu is similar?


It is. Even Linux filesystems will get fragmented if they're run too full. Keeping it under 80% would be a good idea.

---

### Post by newb85 on 2012-09-03
If you're new to Linux, I wouldn't recommend removing Windows just yet, especially if you don't have a way of re-installing it later.

You may find down the road there is something you still need to occasionally boot into Windows for.  I make it a point to always have Windows installed on one of my machines, even though the only thing I boot into it for is updating the Windows virus definitions.

---

### Post by michellabruyere on 2012-09-08
Thanks for the info! First of all I have an Acer Aspire 3690 Laptop 

I think that I probably have one hard drive (80GB HDD) which has been partitioned under windows in a C and D drive. (when I opened up my computer it was physically also just one disk) . I am also able to disconnect my ACER drive (/media/acer) so this probably a result of the partitioning right?

For now I'm not going to remove Windows yet, it is probably the safest option since I really want to know what I'm doing first. (I already made a backup of the  windows settings on an external hard disk.) But I sure enjoy having a working OS and the freedom of control.

---

### Post by afulldeck on 2012-09-08
> **coldraven said:**
> Here's another option.
Buy a new hard drive, I got a 250GB drive for £30.
Buy an USB drive enclosure, mine cost £5 from ebay
This link was the first one that my search found
[http://www.ebay.com/itm/2-5-Hard-Drive-Sata-External-Enclosure-Silver-Case-Box-USB-2-0-/150870955586?pt=US_Drive_Enclosures_Docks&hash=item23209c1642](http://www.ebay.com/itm/2-5-Hard-Drive-Sata-External-Enclosure-Silver-Case-Box-USB-2-0-/150870955586?pt=US_Drive_Enclosures_Docks&hash=item23209c1642)

Swap your existing drive for the new one and put the old one into the enclosure.
Install Ubuntu onto your new drive.
Bingo! You now have lots of space and can access your files via USB. When you are happy just format the old drive and use it for portable storage. I usually format them as NTFS so that I can transfer files between Windows, Mac or Linux machines

I think some folks underestimate this solution. Swapping out the old spinning 5400 rpm hard drive with a new solid state drive does wonders for the performance of older pc at a fraction of the costs.

---

### Post by offgridguy on 2012-09-08
On the technical side you can replace any windows OS with a linux OS.
Depending on what applications you use you may find some limitations to
run your favorite programs.

---

### Post by michellabruyere on 2012-09-09
Everybody, thanks a lot for all your help. So in the end I had a bit of try and error situation. I tried to do a partition of my disk (with Gparted) to enlarge the part where I had ubuntu installed on. 

In my natural instinct for not sensing any danger and going all out for the adventure I made the disk I installed Ubuntu on my root disk. Apparently this wasn't the best idea I guess because at the next boot I was thoroughly f, well you know.

So, I got the NTLDR is missing message, tried about every button and boot order on my laptop and just couldn't get my laptop working. Offcourse I had a pre-installed windows laptop, thus not any boot cd.

After that my one solution I could think of real quick was to download Ubuntu on a disk, boot Ubuntu from the cd and install it replacing the current system. 

So in the end! Yes, I can replace Vista with Ubuntu. Actually I did found out the stupid way. But then again, how exciting would it be without a bit of risk.

Thanks again everybody for all the help anyway!

---

### Post by michellabruyere on 2012-09-09
(and luckily I did back up all my usefull files just before all of this)

---

### Post by offgridguy on 2012-09-09
I've got to admire someone as adventurous as yourself, enjoy your ubuntu.

---

### Post by jaithehulk on 2012-09-09
I have a Asus-K53SD Laptop.
I am trying to do the same - replace Win7 with Ubuntu.
but unfortunately I require Win7 occasionally for some of my softwares and GAMES :P .
For all else its Ubuntu all the way!

---

### Post by mips on 2012-09-10
> **afulldeck said:**
> I think some folks underestimate this solution. Swapping out the old spinning 5400 rpm hard drive with a new solid state drive does wonders for the performance of older pc at a fraction of the costs.

That laptop seems a bit on the oldish side so could potentially have a PATA interface/drive and PATA SSDs are as scares as hens teeth. If it has a SATA interface/drive then SSD would be the way to go unless you need lots of space & have budgetary constraints.

---


---
title: "I want to put DSL on an old PC?"
date: 2007-11-24
forum: Other OS Talk
---

### Post by derby007 on 2007-11-24
I have an old PC, 10yrs old, its a Packard Bell Executive 120MHz PC, 16MB ram, has a CD ROM, Win95 on it at the mo, I have the original disks, I dont want to get rid of Win95, sentimental reasons & also my daughter could use it, ie. games, & has alot of childrens software. Actually alot of software came with it, it advertised as : £1000 worth of software, free !!!!!! 

But I'd like to put DSL, or similar on it. Has anyone done this? could you guide me thru the process? Partitioning, swap set-up, will it see the C:\ drive partition? etc.

---

### Post by K.Mandla on 2007-11-24
I think partitioning for a hard drive installation of DSL is still handled through console programs (this might have changed; it's been over a year since I tried to install DSL to a hard drive). 

That means you'll probably want to resize the Windows partition before you set up the DSL space. I don't know if any of the more common Windows partitioning programs will run on Win95, so you might need a GPartEd live CD to get started. I don't know what the memory requirements are for that. ... :-k

After that DSL has (or had, anyway) a prompt-driven installation sequence, so it should be fairly easy to install it in the right place. Maybe someone can give you better advice on what the current DSL installation procedure is. ... 8-[

P.S.: You'd be doing yourself an enormous favor if you could bump up the RAM at all. Is that an option?

---

### Post by derby007 on 2007-11-24
It will be a slow project/process, as the PC is at my Mothers house, cause I don't have room for it at home (2 little baby girls decided to move in with me & the wife !). 
I'll investigate the RAM. I wonder if I have : 168 pin or 78pin modules. 
I'm thinking that 'fdisk' might be on one of my set-up or recovery floppy disks....mmm. I should be able to use that for partitioning, right?

  > so you might need a GPartEd live CD 
I don't think my PC will boot from CD, as it came with boot floopies to install in the 1st place.

I'll post back sometime in the future, if you're interested on my progress...thanks again.

---

### Post by tdrusk on 2007-11-24
So you can format the hard drive and reinstall windows with no problem right?

okay then.

run DSL. Open a terminal and
log in as root
```
sudo -s
```
run cfdisk for you hard drive. change hda to the name of your hard drive.
```
cfdisk /dev/hda
```

Make 3 partitions. The first linux swap (twice the size as your ram and make sure to  change the mode to 82), the second a normal partition _that is marked as bootable_, the third should be fat32. Save it and quit.

Boot into the windows cd and install to the fat32 partition.

Boot back into DSL. setup the swap.
```
 sudo -s
        mkswap /dev/hda1
        swapon /dev/hda1
```
Then install
```
dsl-hdinstall
```
and follow the instructions EXACTLY. In other words, if it tells you to type (for example) "hda1" then you type in "hda1". But if it tells you to type in "/dev/hda1" then you type in "/dev/hda1".

Use ext2 and install lilo (i had trouble with grub but there probably isnt a problem.)

When you boot up it should have window 95 and DSL as choices for boot.

---

### Post by mickey57 on 2007-11-24
[COLOR="DarkRed"][SIZE="3"].....I tried to put ATT/Bellsouth on a friends old 232mhz.The DSL Demanded 300mhz.Even tried to over-clock the damn thing.The install didn't happen:rolleyes:
..............Mickey[/SIZE][/COLOR]

---

### Post by tdrusk on 2007-11-24
> **mickey57 said:**
> [COLOR="DarkRed"][SIZE="3"].....I tried to put ATT/Bellsouth on a friends old 232mhz.The DSL Demanded 300mhz.Even tried to over-clock the damn thing.The install didn't happen:rolleyes:
..............Mickey[/SIZE][/COLOR]

You are so far off topic.

This thread is about Damn Small Linux.

---

### Post by mickey57 on 2007-11-24
> **derby007 said:**
> I have an old PC, 10yrs old, its a Packard Bell Executive 120MHz PC, 16MB ram, has a CD ROM, Win95 on it at the mo, I have the original disks, I dont want to get rid of Win95, sentimental reasons & also my daughter could use it, ie. games, & has alot of childrens software. Actually alot of software came with it, it advertised as : £1000 worth of software, free !!!!!! 

But I'd like to put DSL, or similar on it. Has anyone done this? could you guide me thru the process? Partitioning, swap set-up, will it see the C:\ drive partition? etc.
***********************************************:oops::oops::oops::oops::oops:

---

### Post by tdrusk on 2007-11-25
> **mickey57 said:**
> ***********************************************:oops::oops::oops::oops::oops:
It's cool. I didn't mean to sound harsh.

---

### Post by dptxp on 2007-11-25
Try the LIVE CD first. DSL did not run on my P100, 32 MB RAM.
I use W98 on it

---

### Post by derby007 on 2007-12-06
Update: I had an hour or two to mess around with the PC. In the BIOS it let me choose to boot from CD but my GParted Live CD would not boot. I then booted from a boot floppy & tried an old RedHat install CD. It came up with 2 options to partition, but neither was straight foreward, & I didn't have the time to go thru all options. I've only 200MB free so its going to be tight....
I'll keep trying/persisting.

---

### Post by banewman on 2007-12-06
You could run puppylinux straight from cd - if you add or want to save stuff it recommends 512mb of hard disk space.
Runs on my 266mhz pent2 64mb ram comp as quick as ubuntu on2ghz pent4 1gig ram. :)

---

### Post by derby007 on 2007-12-06
That wouldn't do me then, I have a Pent 120MHz, 16MB ram, 200MB free hard drive space.

---


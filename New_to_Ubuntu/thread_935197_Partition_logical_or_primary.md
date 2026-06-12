---
title: "Partition logical or primary"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by wenbill on 2008-10-01
Hi, I have settled on the common /,/home,swap partition scheme. But, I have seen people make all three primary, / and home primary with swap logical, and finally only / being primary with home and swap as logical. What is the best way.
   Also, for sizes is 25gig / partion reasonable for a 320g drive?

---

### Post by anotherdisciple on 2008-10-01
25 Gigs should be more than enough...


about the primary/logical thing... I can't even begin to explain what it means... I've always been advised to make them all primary.

---

### Post by anotherdisciple on 2008-10-01
After some research... the only time it matters is when you have more than (4) partitions. The boot record will only allow 4... so you can do extended partitions (logical... like a partition inside a partition I guess).

---

### Post by rolnics on 2008-10-01
> **anotherdisciple said:**
> After some research... the only time it matters is when you have more than (4) partitions. The boot record will only allow 4... so you can do extended partitions (logical... like a partition inside a partition I guess).

Yes you're correct on that. If I remember correctly it's the bios that will only see the first 4 primary partitions on a disk, so if you have or are planning to install more distros then I would put your root on a primary partition and create an extended / logical partition for your /home and swap

But I'm sure somewhere I read that linux is just as happy on a logical partition, I'll rewrite that I've got linux on logical, see my attached screenshot.

---

### Post by Kellemora on 2008-10-01
Hi WB

That 4 Primary partition limit is what has kept me from buying a 1 Terrabyte drive!

I've seen posts here of those using Ubuntu with as many as 12 Partitions, but none have ever said how they did that.

You are supposed to be able to put Logical Drives inside of an Extended Drive, but the gparted program don't seem to give me that option.

Sure would make backups a whole lot easier of you could make One partition for Data Storage.

I haven't had time to study this on my own.  Have been hoping someone would just make a post on how to create multiple partitions on these humongous drives we have these days.

All I know for SURE is that at my brothers business, ALL of the HOME directories are on their own partition, sda4/HOME/users.
And it don't matter which computer they sit down at, they draw from and save to their /home/user folder on the computer in my brothers office.  Each computer has it's own file system too!
And to the best of my knowledge, it's NOT set up as a Server, just as a workgroup computer is all.

And from what I understand, in Linux, it doesn't matter which machine something is on, each machine sees the drive and file the same as if it was on their OWN machine, even if it's not.

But I'm a Noob to and just learning about these things.

TTUL
Gary

---

### Post by estyles on 2008-10-01
It's actually very easy to make Logical Partitions in gparted.  I don't have it in front of me, so I hope this is the right terminology, but what you do is make 1 large Extended Partition (basically, if you already have 3 Primary Partitions, make the Extended Partition go from the end of the 3rd partition to the end of the drive).  If you already have 4 Primary partitions, you have to delete one of them before you can make an Extended partition.  Once the Extended Partition is made, make new Logical partitions to your heart's content.

If starting on a new machine, I would make a 20-40 GB primary partition as sda1 for Windows, then a 1-2 GB primary partition for swap.  If I was making a separate /boot or /grub partition (which I would do if I was multi-booting 2 or more linux distros), that would be the 3rd primary partition at about 256MB.  Then the rest of the drive would be an Extended Partition, with a logical partition for /, a Logical partition for Data (to be mounted in user's home directory - I personally don't like a separate /home partition, unless you're sure you'll only use one distro on this machine, or unless you for some reason want a different /home partition for each distro), and then potentially a separate Logical partition for /var using... umm... Reiser FS, I think was the file system to use.  My current setup isn't exactly like this, because I started with a drive that was already chopped up a little, and tried a number of different things by trial and error such that it's not worth it to try and get that optimal setup.

---

### Post by The Cog on 2008-10-01
Just to expand on estyles rather good answer:

An **extended** partition must be one of the 4 primary partitions, and it then acts as a container for many **logical** partitions. I think the limit is 64 logicals but I wouldn't bet on it. The extended partiton was invented when it became clear that 4 partitions weren't enough (as disks got larger) and doesn't break the basic partition table format.

I would generally put all of Linux on all logicals, but can't think of a really compelling reason why.

---

### Post by Kellemora on 2008-10-01
I think I may have gotten off on the wrong foot by trying to create more than ONE Extended partition.

My goal on a triple boot, NO DOZE system, was to have a /home directory for each Linux Distro as it's own partition for simpler backups.  NOT only ONE /home for all 3 Distro's, but three separate /home partitions, one for each Distro.

When gparted wouldn't let me create the second Extended partition, I though it also would NOT let me create a Logical partition in the first extended partition either.

My ultimate goal was to have two equally sized HD's.  One as a backup.  And be able to keep things separate, like you can do with Files on a Doze Box.

How I've done this currently is in my /home folder, I have created multiple primary folders /home/personal, /home/business/, home/images, /home/clubs, etc.

BUT, they are all in the Partition for the OS which is limited.
I was hoping to make the /home partitions in growable space.  Like the remainder of the hard drive space not assigned to the OS.

I have plenty of hard drives, so will play around with different configurations again, now that I've learned a little bit more about Linux.
I'm not doing bad though.  Only have ONE old Doze XP box left!  Everything else is all Linux now, and 2 of the machines are triple boot to CentOS (business), Debian (learning) and Ubuntu (primary personal and quickly becoming the preferred business OS now too).
Open Office is what actually made it possible for me to migrate over to Linux so easily, as most of our files were Office files.  Migration had no glitches at all which was great.
Some programs I have only run on Windows and are too expensive to replace, but their output can be piped to Linux and used with the necessary files they are used in.
I haven't tried Wine yet, but have been trying some Open Source programs that should do what my existing programs do, but not quite there yet.  Two of the programs I use require a 7 button mouse, can get by with a 5 button mouse, but so far have not found a Linux mouse driver that can handle a 3 button scroll mouse properly yet.  And yes I know the scroll is equivalent of two buttons!  You can think of these mice as CAD table mice although they serve a different purpose.

Even Red Hat can't come up with drivers for their existing client base who still use some Doze machines for some software.

TTUL
Gary

---

### Post by HousieMousie2 on 2008-10-01
For the mouse:

Try btnx to assign the buttons.

---

### Post by drs305 on 2008-10-01
I have one windows primary partition and everything else, including all my ubuntu partitions, are logical partitions within the extended partition. It works fine.

---

### Post by bodhi.zazen on 2008-10-01
> **Kellemora said:**
> Hi WB

That 4 Primary partition limit is what has kept me from buying a 1 Terrabyte drive!

I've seen posts here of those using Ubuntu with as many as 12 Partitions, but none have ever said how they did that.

You are supposed to be able to put Logical Drives inside of an Extended Drive, but the gparted program don't seem to give me that option.

Sure would make backups a whole lot easier of you could make One partition for Data Storage.

I haven't had time to study this on my own.  Have been hoping someone would just make a post on how to create multiple partitions on these humongous drives we have these days.

All I know for SURE is that at my brothers business, ALL of the HOME directories are on their own partition, sda4/HOME/users.
And it don't matter which computer they sit down at, they draw from and save to their /home/user folder on the computer in my brothers office.  Each computer has it's own file system too!
And to the best of my knowledge, it's NOT set up as a Server, just as a workgroup computer is all.

And from what I understand, in Linux, it doesn't matter which machine something is on, each machine sees the drive and file the same as if it was on their OWN machine, even if it's not.

But I'm a Noob to and just learning about these things.

TTUL
Gary

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

:lolflag:

---

### Post by Kellemora on 2008-10-01
Hi Mouse

How do I do that?

btnx - command not found

It's also not in Synaptic to install either.

TTUL
Gary

---

### Post by Kellemora on 2008-10-01
Hi bod

Thanks, I read that when I first started, then forgot about it with trying to learn so much other stuff.
NOW it's bookmarked!

TTUL
Gary

---

### Post by bodhi.zazen on 2008-10-01
> **Kellemora said:**
> Hi Mouse

How do I do that?

btnx - command not found

It's also not in Synaptic to install either.

TTUL
Gary

[http://www.linux.com/feature/126295](http://www.linux.com/feature/126295)

---

### Post by HousieMousie2 on 2008-10-02
> **bodhi.zazen said:**
> [http://www.linux.com/feature/126295](http://www.linux.com/feature/126295)

Thank you for providing the link, bodhi.zazen, I had my hands full.



You might take a look at the btnx site:

[http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)

---


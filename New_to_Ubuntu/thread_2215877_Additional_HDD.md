---
title: "Additional HDD"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-04-08
Bonjour~

This is a super noob question but I'd like to know a few things about expanding HDD space:

1) When adding a new HDD; does this put any strain on the existing motherboard, power, CPU in any noticable way?
2) When adding a new HDD; can I just plug it in? (SATA connection) and Ubuntu detects it and I can just format it to EXT4 and away I go, or is there some prep work or installation disk stuff needed?
3) Ultimately is it better to just use one huge disc rather than two separate ones? If so, how big is the difference? Is there a marginal difference or whut~

Thank you all.

---

### Post by sudodus on 2014-04-09
> **Drowz0r said:**
> Bonjour~

This is a super noob question but I'd like to know a few things about expanding HDD space:

1) When adding a new HDD; does this put any strain on the existing motherboard, power, CPU in any noticable way?

It will need power, obviously, but a standard computer's power supply unit should have a good margin for that. Otherwise, I think no significant strain.
> 
2) When adding a new HDD; can I just plug it in? (SATA connection) and Ubuntu detects it and I can just format it to EXT4 and away I go, or is there some prep work or installation disk stuff needed?
Shut down the computer and plug it in. Boot the computer, and it should be recognized and ready for making partition(s) and formatting the partition(s)> 

3) Ultimately is it better to just use one huge disc rather than two separate ones? If so, how big is the difference? Is there a marginal difference or whut~

Thank you all.

I think it is cheaper and simpler to use one huge disk rather than two separate ones. But it will probably be faster to use two smaller ones.

-o-

Finally, remember to make a plan for ***backup*** of your data (system, personal files ...)! Test that it really works and stick to that plan, or develop it, so that you need not come back here and ask for a rescue operation, when the hard disk fails ;-)

---

### Post by Double.J on 2014-04-09
Hi there!

Don't worry, there are no stupid questions before opening a computer!

2 things:
1) always make sure you are backed up.
2) practice electrical safety; make sure computer is unplugged, you are earthed and press the power button a few times after unplugging. 

Yes you can just pop a blank drive in and power on. Ubuntu's tools will format it just as you want. To get advanced, I recommend gparted.

Does another hdd use extra resources? Well yes, technically it will. It will use a bit more power, your bios (motherboard) will check it at boot, and your cpu will have two drives to access. Fortunately this is such a minute impact you will not notice it. At all. 

So is it better to have one big or two small? Well it's certainly cheaper to have one 2TB drive than two 1TB drives! However, contrary to what you may think, you may get better performance from two drives. To your cpu, a hard drive must seem like it's standing still; even with an ssd, the cpu is so fast, it's constantly waiting for the drive to do what it's asked. While it's waiting, it will do other tasks. If it has to access data or write data to two disks at once, this will be faster than if all that data was on one disk - there is a benefit to using those resources! 

Finally if you have multiple (preferably identical) drives, you can set up RAID between them. At the cost of available space (negative) you can protect yourself against hard drive failure (positive).

final thing to remember. Windows can't see ext4. There are some drivers that kind of work for ext2/3 but basically assume that windows and linux can use ntfs, only linux can use linux file systems. So if you will dual boot in the future, it is better to use ntfs than ext4. Ubuntu will prefer ext4 if its the only system. Also if you do put an ntfs partition on the drive it must be at the start for windows to see it.

happy configuring!

Jj

---

### Post by Drowz0r on 2014-04-09
Hello~

Thanks both. That answers my questions exactly. I'll be sure to back everything up first! This should be easy enough.

---

### Post by sudodus on 2014-04-09
Good luck :-)

---

### Post by Double.J on 2014-04-09
> **sudodus said:**
> Good luck :-)

+1 keep us updated!
:D

---

### Post by Drowz0r on 2014-05-14
I uh, started a new thread here because things advanced a little:

[http://ubuntuforums.org/showthread.php?t=2223461](http://ubuntuforums.org/showthread.php?t=2223461)

Struggling a touch, just as an update :o

---


---
title: "[SOLVED] What size for swap partition?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by two4two on 2008-10-20
I only have a 13G HDD for my Ubuntu (8.10).  I installed with the defaults from  the partitioner.  It only gave me 510MB for the swap  partition.  Could this affect my downloads?  Also, is there some kind of cache or temp storage where downloads are temporarily kept while the download is proceeding?  I see Firefox has some cache for the size to be specified, but I'm talking about when I do the downloads for updates for Ubuntu.  This is FTP and not involving the firefox browser.  I ask this because it seems that when I do these downloads it gets so far and then slows down to a crawl.  The downloads must have a timer because once they slow down they fail.  Also, by that time Firefox browser won't work either any more.  I use a TrendNet TEW-424UB (using the RealTek driver).  Anyone have any ideas?

---

### Post by pytheas22 on 2008-10-20
The packages that you download via Ubuntu updates ultimately get stored at /var/cache/apt.  It's possible that they're copied into memory first and stored there until all downloads complete, but I suspect that that's not the case; they're probably written directly to disk, or cached in memory to a certain point and then written to disk as needed.  In other words, they should have nothing to do with swap.  Firefox downloads I believe work the same way--they get stored directly on your desktop as the download happens, not cached temporarily anywhere else (Internet Explorer does it differently).

From the behavior you're describing, it sounds more like your network interface is just crashing.  This sometimes happen with certain devices when they're placed under heavy load, as yours would be if you're downloading a large number of updates at high speed for a sustained period of time.

The next time the crash happens, please immediately open a terminal, run the following commands (in this order) and post the output here:
```

dmesg | tail
lshw -C Network
ifconfig
ping -c 5 google.com
ping -c 5 72.14.207.99
lspci -nn
lsusb
```

That will help to figure out what's really going on when the downloads stop.

---

### Post by PointyWombat on 2008-10-20
If you suspect memory shortage problems, monitor swap behaviour to see if the swap device is actually being used. If it's not, then your problems are elsewhere. Use the free command, paying attention to the swap used metric. This value is typically zero. As you add memory load, you may start to see swap begin to be used as you run out of physical memory.

```

user@box:~$ free -s 1
             total       used       free     shared    buffers     cached
Mem:       2062192    1094792     967400          0      62236     638120
-/+ buffers/cache:     394436    1667756
Swap:      6040400          **0**    6040400

```

For your specific case though, I suspect memory shortfall is not the problem and pytheas22 is most likely on the right track.

---

### Post by kansasnoob on 2008-10-20
It would help to know your full system specs.

Processor speed:

```
 cat /proc/cpuinfo
```

Mem info:

```
 cat /proc/meminfo
```

---

### Post by sazan on 2008-10-21
swap size must be minimum of the size of ur RAM ...

---

### Post by two4two on 2008-10-22
Pointy,  I entered the command as I think you wrote it and instead of just one reort back it just kept doing it over and over again and I didn't know how to stop it except for closing the terminal window.  I see what you wrote as "free -s 1" (that's 1 as in one).  What did I do wrong?

---

### Post by ChildOfMana on 2008-10-22
[QUOTE="two4two"]I see what you wrote as "free -s 1" (that's 1 as in one). What did I do wrong?[/QUOTE]

It should be a lower case L, not a 1.

A mistake I make on a regular basis! :confused:  If in doubt; copy and paste are your friends :)

---

### Post by egalvan on 2008-10-22
> **two4two said:**
> I entered the command as I think you wrote... instead of  one reort it kept doing it over and over again and I didn't know how to stop it except for closing the terminal window. 

pressing
 <ctrl>-<alt>-c 
while the memory info is showing will stop the process.

---

### Post by egalvan on 2008-10-22
> **sazan said:**
> swap size must be minimum of the size of ur RAM ...

If you have enough physical ram, no swap is needed.

Swap comes into play when ram is lacking, or for 'sleep' or 'hibernation'.

---

### Post by Lazy-buntu on 2008-10-22
I've heard a range from the size of your RAM to two times your amount of RAM.

---

### Post by OldGrey on 2008-10-22
I have been told it's 2 x the RAM up to a max of 512MB. Certainly with my 1GB of RAM 512MB is fine.

---

### Post by pytheas22 on 2008-10-22
> Pointy, I entered the command as I think you wrote it and instead of just one reort back it just kept doing it over and over again and I didn't know how to stop it except for closing the terminal window. I see what you wrote as "free -s 1" (that's 1 as in one). What did I do wrong?

The information that everyone else is providing is good and accurate, but I don't think that it's going to get to the root of the problem.  I really strongly suspect that swap size is not the issue here.  It's much more likely a problem with the network driver.  I think this because 1) Firefox doesn't cache anything to the swap partition; and 2) you say that when the downloads stop, you're also unable to browse web pages--if it were just a case of running out of swap space, you should still be able to connect to websites.  But if the whole connection is breaking, as is known to happen in certain cases when your networking interface is under heavy load, then that would explain why viewing pages fails at the same time as downloads.

When you get a chance, please post the output of the commands that I mentioned in post #2 after your connection breaks.

---

### Post by billgoldberg on 2008-10-22
> **two4two said:**
> I only have a 13G HDD for my Ubuntu (8.10).  I installed with the defaults from  the partitioner.  It only gave me 510MB for the swap  partition.  Could this affect my downloads?  Also, is there some kind of cache or temp storage where downloads are temporarily kept while the download is proceeding?  I see Firefox has some cache for the size to be specified, but I'm talking about when I do the downloads for updates for Ubuntu.  This is FTP and not involving the firefox browser.  I ask this because it seems that when I do these downloads it gets so far and then slows down to a crawl.  The downloads must have a timer because once they slow down they fail.  Also, by that time Firefox browser won't work either any more.  I use a TrendNet TEW-424UB (using the RealTek driver).  Anyone have any ideas?

Swap is used when you are out of ram memory.

Depending on what you have 510mb could be good enough.

I think it's good to have at least 1x your ram memory as swap.

Unless you have less than 1gb, then I would double it.

I don't think the swap memory is the problem here.

---

### Post by two4two on 2008-11-12
8.10 solved my problem.

---


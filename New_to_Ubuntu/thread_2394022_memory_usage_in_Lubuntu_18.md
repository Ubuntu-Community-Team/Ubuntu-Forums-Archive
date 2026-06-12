---
title: "memory usage in Lubuntu 18"
date: 2018-06-11
forum: New to Ubuntu
---

### Post by ramanterola on 2018-06-11
Hi,

Is there a way to reduce the amount of amount of memory that Lubuntu 18 is using?   I got my hands in this cheap dell 3542 laptop with a celeron, 2gb ram & 32gb emmc.   I am basically using it for email, document editing  and browsing.   So far the processor is not having problems with the load, as it stays at about 35%, the memory however is heavily utilized.  Without any other processes running, 868 Mb of memory is used, as soon as I run Chromium 1.6 gb of a total of  1.9 gb are used.  My chromium installation is only using one extension (Tab activate).  Firefox uses a similar amount of memory.  So when I am running basic stuff: Browsing, Thunderbird & LibreOffice, the computer starts lagging, and lots of times it stops completely until the memory swapping is completed.

 Is there a way to reduce the memory used by the default system?   Htop and task manger both show 116 tasks, are there some that I can delete/shut off to free up memory?  Would I benefit if  I go to Lubuntu 16?

Your input will be greatly appreciated.

R

---

### Post by DuckHook on 2018-06-11
Memory usage is often misinterpreted. I don't know which app you are using for reporting, but system cache is usually included in mem statistics and Ubuntu tends to use as much cache memory as the system has (within limits). However, this cache is freed up when apps actually need them. To see actual memory use, do:```
free -h
```&#8230;and post results back to this thread.

Web browsers are notorious memory hogs. It is possible for either Chrome (-ium) or Firefox to eat up to 2 GB of ram. A lighter browser like Epiphany might help, but it will not have all the bells and whistles.

EDIT

Sorry, did not completely read your post. The combo of T-bird, Libreoffice and a full-fledged web browser is not chopped liver. That's serious memory usage and 2GB won't do it. There is no lighter weight distro that will work better because it's not the OS that is bottlenecking you here. Try lighter weight versions in all of those apps if you must have them up at the same time: eg. Epiphany, Sylpheed and Abiword. That was what Lubuntu used to ship with, although so many likely complained about stunted features that they gave in and shipped with resource hogs in recent builds.

Also, if your system can accept more memory, that's actually the best way to solve your issue.

---

### Post by ramanterola on 2018-06-11
Duck,

Thank you for the prompt reply.

I am going to start with the browser and work my way down

Here is a dump of the memory:

```
              total        used        free      shared  buff/cache   available
Mem:           1.9G        630M        719M         98M        554M        1.0G
Swap:          1.3G         87M        1.2G
```

Any other ideas?

Thx

R

---

### Post by DuckHook on 2018-06-11
Not sure if you read my edited version of first post. It contains further details. Your bare system looks good. You are unlikely to get much better than 630 MB on a modern distro. It is possible to squeeze that down further by starting with a bare bones CLI install (say Ubuntu Mini) then adding only the very minimum necessary GUI elements, but we are talking serious geek fu to achieve that. Some people here believe in doing that.

Try the replacement apps. They may do the trick for you.

I'm stepping out of the house for the rest of the day, so won't get back to you for a few hours. Hopefully, other forum members will have things to add.

---

### Post by ramanterola on 2018-06-11
Duck,

I did read the entire/edited post.    I guess that it surprised me that 3 applications would consume so much memory, after all  I have run servers with a less memory.   I will take this toy apart later and see if I can upgrade the memory.

Thx again

R

---

### Post by Autodave on 2018-06-11
According to what I found online, that machine has one slot only. It will take a 2 gig, 4, or 8 gig chip.  Further looking shows that you van get a 8 gig stick for about $60..00.

---

### Post by ramanterola on 2018-06-11
I have to open the hood and check it.  It is after all a toy computer.    I know it has 2gb, I might spring for the 4gb,  I cant see myself putting 8gb in this machine.

---

### Post by cruzer001 on 2018-06-11
I have a similar laptop, single core/2G ram and running lubuntu.  Can't open too many tabs in firefox, movies cannot run in full screen, just not enough ram or cpu for todays browser.  But I still keep it by my bed and use it as is :)

---

### Post by DuckHook on 2018-06-11
> **ramanterola said:**
> …after all  I have run servers with a less memory…It's a common assumption that servers take up lots of RAM. But this depends on the server function: things like file, print and DHCP servers in a SOHO environment use very little RAM. And if the server is running on a CLI interface, the RAM footprint is not only small but very efficient. It's the GUI elements that create all the bloat. Of course, cloud, web, mail and VPN servers in enterprise level environments need all the RAM they can get, but that doesn't usually fall within the comparison sphere of what most people do with their private servers.

I'm not sure it makes sense to beef your RAM up any further than 4GB. That should allow you to concurrently run the three apps that you want. Any more, and you will get diminishing returns and poor value for money on your machine.

---

### Post by ramanterola on 2018-06-12
Duck,

Thank you for the input.   I am looking at the memory sticks.   I can see your point on the graphic needs and lowering the ROI once I go past 4gb.    I wasnt making assumptions on the server configuration, it was actually a db server (MS-SQL server) with large data sets, servicing a large number of concurrent requests.  We will leave the server conversation for another day.

Thank you again for the input guys.

R

---

### Post by VMC on 2018-06-12
> **ramanterola said:**
> 
I am going to start with the browser and work my way down

Here is a dump of the memory:

```
              total        used        free      shared  buff/cache   available
Mem:           1.9G        630M        719M         98M        554M        1.0G
Swap:          1.3G         87M        1.2G
```
Your using 630M with the browser running? If not, what is running?
Without browser running:```
              total        used        free      shared  buff/cache   available
Mem:           3693         261        2866           7         564        3210
Swap:          1999           0        1999
```
with chrome running:
```
              total        used        free      shared  buff/cache   available
Mem:           3693         483        2566          30         642        2965
Swap:          1999           0        1999
```
This is on my Xubuntu Bionic. I would think Lubuntu would be less.
What services are active?

edit: With chrome , Libre calc running:
```
$ free -m              total        used        free      shared  buff/cache   available
Mem:           3693         567        2336          31         789        2880
Swap:          1999           0        1999



```

---

### Post by geofftf on 2018-08-14
I have loaded Lubunti 18.04 on an old machine that I have upgraded from 1 GB of RAM to 2 GB.
 
 
 With nothing running:
 
 
               total        used        free      shared  buff/cache   available
 Mem:           1983         251         928          26         802        1544
 Swap:          2047           0        2047
 
 
 After starting LibreOffice Writer:
 
 
               total        used        free      shared  buff/cache   available
 Mem:           1983         301         742          40         939        1480
 Swap:          2047           0        2047
 
 
 After starting Firefox too:
 
 
               total        used        free      shared  buff/cache   available
 Mem:           1983         620         385          55         976        1199
 Swap:          2047           0        2047
 
 
 Firefox with six tabs loaded with different sites:
 
 
               total        used        free      shared  buff/cache   available
 Mem:           1983        1125         132          76         724         963
 Swap:          2047           0        2047
 
 
 The usage actually went down a little when I added Sylpheed:
 
 
               total        used        free      shared  buff/cache   available
 Mem:           1983        1092         147          82         743        1022
 Swap:          2047           0        2047
 
 
 Even with all this stuff running, I have barely over-run 1 GB, and still have over 1 GB available, with no swap.
 
 
 It is important to understand the difference between available and free memory:
 
 
 [https://www.linuxatemyram.com/](https://www.linuxatemyram.com/)
 
 
 This guy recommends reducing swappiness from 60 to 10 to reduce the tendency to swap:
 
 
 [https://sites.google.com/site/easylinuxtipsproject/first-lubuntu](https://sites.google.com/site/easylinuxtipsproject/first-lubuntu)

Upgrading to 2 GB doubled the number of active memory channels, but it did not greatly increase the performance. Upgrading the processor from a 

Pentium E2140 (with a Passmark score of 871) to a Core 2 Duo E6700 with a Passmark score of 1694) gave me a big improvement in performance.

---


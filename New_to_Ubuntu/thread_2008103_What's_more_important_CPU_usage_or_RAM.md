---
title: "What's more important: CPU usage or RAM?"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by vasa1 on 2012-06-22
We often come across references to RAM "usage" or "consumption". Here are two instances:
[http://blog.bodhizazen.net/linux/desktop-environments-ram-use/](http://blog.bodhizazen.net/linux/desktop-environments-ram-use/)
and
[http://www.ghacks.net/2012/06/21/chrome-uses-way-more-memory-than-firefox-opera-or-internet-explorer/](http://www.ghacks.net/2012/06/21/chrome-uses-way-more-memory-than-firefox-opera-or-internet-explorer/)

I'm just wondering why people don't look at CPU usage. Any thoughts?

---

### Post by Grenage on 2012-06-22
It's far more common for an OS and its default applications to use a lot of memory, than it is for applications to just sit there and max out the CPU.  In fact, if it does just sit there and burn, a program is probably broken - or being run on a machine that is simply ancient.

While RAM for many is no loner an issue (8GB+ is common for home builds), it does give reasonable indications.

---

### Post by zombifier25 on 2012-06-22
When CPU is maxed out, things are still normal; when RAM is maxed out, it will lag like heck.

Probably evidenced by the Folding@home software, which uses spare CPU cycles, therefore maxing the CPU all the time (which renders the CPU monitor useless :P ), but my computer is still running fine.

---

### Post by MadmanRB on 2012-06-22
It can vary per setup though as some CPU's can take load pretty well

---

### Post by *^kyfds( on 2012-06-22
RAM all the way.

---

### Post by vasa1 on 2012-06-22
Well, one of the reasons I asked was this: when people compare the "efficiencies" of two "equivalent" programs, say two browsers, they often refer to RAM. Now, if RAM is **not** a limiting factor, then does it really matter? But, other things being equal, let's hypothetically say that browser A "uses" more RAM than browser B but shows a lower CPU usage than browser B, which browser would you prefer.

Sometime ago, I had viewed the same HTML5 video in Chrome and Firefox and eyeballed the CPU usage. It appeared to me that Chrome's CPU usage was noticeably lower.

(I'm going to try again, this time comparing Chrome, Firefox, Opera, and Seamonkey.) ;)

---

### Post by redmk2 on 2012-06-22
> **vasa1 said:**
> Well, one of the reasons I asked was this: when people compare the "efficiencies" of two "equivalent" programs, say two browsers, they often refer to RAM. Now, if RAM is **not** a limiting factor, then does it really matter? But, other things being equal, let's hypothetically say that browser A "uses" more RAM than browser B but shows a lower CPU usage than browser B, which browser would you prefer.

Sometime ago, I had viewed the same HTML5 video in Chrome and Firefox and eyeballed the CPU usage. It appeared to me that Chrome's CPU usage was noticeably lower.

(I'm going to try again, this time comparing Chrome, Firefox, Opera, and Seamonkey.) ;)

RAM holds the data that the CPU may (or may not) process.  If you have a fire to put out which is more important to you, the water (data) or the pump (the cpu).  I'd say; both of them, but for different reasons.

Some situations require large amounts of RAM (such as databases) while others require a large amount of CPU cycles (mathematical computation).  There is one other item that should be brought into the equation; that is disk I/O.  A slow hard drive is very noticeable in file intensive work (i.e backups)  

My desktop has a fast Core 2 3 GHz CPU with 8GB of RAM, but my storage server is a P3 with only 256MB of RAM.  The storage server does have fast SATA II drives for quick disk I/O.

---

### Post by HiImTye on 2012-06-22
to put it in layman's terms, the more memory a program is using, the more demanding it is on the CPU (or GPU, or both). the CPU (or GPU) is just processing that information that is in the memory and the more information it has to process, the more demanding it is on the CPU.

that and a process using 100% of the CPU isn't indicative of poor programming, it is indicative of the process adequately using the processor. a better indicator is CPU *time*, that is, how much time the process has been using the CPU. a process can periodically use 100% of the CPU (and a lot of processes do, to save power), to get all of its work done in as few cycles as possible

---

### Post by Peripheral Visionary on 2012-06-22
This web page has a few enlighteing bits of useful info for Linux newbies: [Help! Linux ate my RAM]("http://www.linuxatemyram.com/")!

---


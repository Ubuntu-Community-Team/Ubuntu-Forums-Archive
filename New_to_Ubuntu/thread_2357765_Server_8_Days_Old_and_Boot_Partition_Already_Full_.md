---
title: "Server 8 Days Old and Boot Partition Already Full -- What should I do?"
date: 2017-04-05
forum: New to Ubuntu
---

### Post by jmartino on 2017-04-05
Dumb Newbie Question Ahead...

I ordered this server only 8 days ago.  Set it up with Serverpilot.io, but otherwise have done very little with it -- moved a few very small websites over to it, and that's all.  

Today I noticed that ServerPilot is reporting that my fullest disk (/boot) is already 79% full *(.18GB of .22GB)*.

Have been researching the issue (since I know nearly nothing about Ubuntu).  And have managed to install ncdu.  This is what it looks like:

[IMG]http://i.imgur.com/ELsJZUb.png[/IMG]

So my question is... what should I do?
 
Make the /boot partition bigger?  *edit: (Can it be made bigger without screwing up my live websites?)*

Delete some files?   [I]edit: (Is it even safe to delete files from /boot?)

[/I]Thanks for any insights you can share.

---

### Post by SeijiSensei on 2017-04-05
First, try opening a Terminal and entering the command
```
sudo apt-get autoremove
```
This will often clean out old operating system "kernels" in /boot that you no longer need.  The default is to have the current kernel and its immediate predecessor.

---

### Post by jmartino on 2017-04-05
**Quick update:**  I just ran a Benchmark test on this server via ServerScope.io.  To my eye, the results are kinda scary.

```
Test results for Dedicated Server (2x L5520 + 16GB RAM + 4x 1TB SATA + RAID 10) at dacentec
Server specs: 16 × Intel(R) Xeon(R) CPU           L5520  @ 2.27GHz
16 GB  RAM / 2 TB disk space
Ubuntu 16.04 Xenial
Rochester, United States
Benchmark summary:UnixBench - 5583.9
Disk Read - 3 MB/s
Disk Write - 1266 MB/s
Bandwidth - 679.00 MB/s
```
Full Report: [https://serverscope.io/trials/Lj2Y](https://serverscope.io/trials/Lj2Y)

It says the Disk Read speed is only 3 MB/s !?!  Whuuuuu?

I'm thinking I should have ordered a better server.

---

### Post by jmartino on 2017-04-05
Thank you for that tip, SeijiSensei.  Really appreciate it.

I researched that command and it seems to be compatible with ServerPilot, so I took a deep breath and ran it.  Now I'm down from 79% full to 61% full.  Awesome.

So I guess I need to run that every week or so?  I'm kinda not liking the way they set up this server.  :-?

---

### Post by mastablasta on 2017-04-06
if 197 MB means that 79% of boot is full then the server setup has rating garbage. if they do use a separate /boot they should give it at least 1 GB and not 250 MB which appears is what they actually did.

is the whole server yours or do you host only on part of it? if you have only part assigned then this Will likley be some sort of virtual server. in which case i am not sure that the read/write speeds would be accurate.

how are the websites setup? is it is your server then it might be easy to move them.

as for the apt-get autoremove, it really does appear oyu woul dneed to run it connstantly in this setup. you could write a script and add it to cron Jobs. however i think the host should provide assistance with the issue sinc ethey are the ones that did the server setup.

---

### Post by sp40140 on 2017-04-06
The command from Sensei largely helped you with removing the older kernels (and any other obsolete packages). You don't need to run it weekly. However, as you are running linux server, you should read up on server maintenance best practices. 
The real surprise is that you have 4 X 1TB drives. That's 4 TB! You should keep the sites on those drives. Not on boot drive, which is bit too small for my liking as it is @22GB.

---

### Post by jmartino on 2017-04-06
> [COLOR=#000000]if they do use a separate /boot they should give it at least 1 GB and not 250 MB which appears is what they actually did.[/COLOR]
I contacted support and yes, indeed, 250MB is the preconfigured profile they use for new servers (unless specifically told otherwise).

> [COLOR=#000000]is the whole server yours or do you host only on part of it? [/COLOR]
Yes.  All mine.  For better or worse.  So I'm wondering if the HW RAID is why the Read/Write speeds look so wonky.  But a big reason I opted for a 4x1TB HW RAID-10 was to have blazing fast disk speed (which is supposed to be the case).  So let's just say I'm quite disappointed, unless I can find a reason for those benchmarks to be wrong.

> [COLOR=#000000]as for the apt-get autoremove, it really does appear oyu woul dneed to run it connstantly in this setup. you could write a script and add it to cron Jobs.[/COLOR]
Yep.  If I stay with this provider, that's exactly what I'm going to do.

> [COLOR=#000000]however i think the host should provide assistance with the issue sinc ethey are the ones that did the server setup.[/COLOR]
That is my thought exactly.  But they said they can't do anything about it other than rebuild the entire OS.  Which would mean undoing (and then redoing) all the website migration work I've been doing over the last several days.

Let's just say I'm less than pleased with this provider so far.  The best thing I can say about them is that they setup my server very quickly, and have answered my support tickets very fast -- even at 3 am -- if only to say, *"good luck."*

---

### Post by jmartino on 2017-04-06
> [COLOR=#000000]The command from Sensei largely helped you with removing the older kernels (and any other obsolete packages). You don't need to run it weekly. However, as you are running linux server, you should read up on server maintenance best practices. [/COLOR]Thankfully, ServerPilot helps me keep up-to-the-minute on my drive state.  So if it gets full, I'll know right away.  I'm planning to setup autoremove on a cron job anyway.  As for server maintenance... yes.  That's on my shortlist.

> [COLOR=#000000]The real surprise is that you have 4 X 1TB drives. That's 4 TB! [/COLOR]
No surprise really.  All my sites are image-heavy, and I need the room.  Also, since it's a mirrored+stripped RAID, it's actually only 2TB -- which is actually only 1.8TB.

---

### Post by SeijiSensei on 2017-04-06
I have no idea what serverpilot.io is, but I would suggest you simply start from scratch with the [Ubuntu Server 16.04 disk image]("http://cdimage.ubuntu.com/ubuntu-server/xenial/daily/current/") and install it yourself.

Figure out first how you want your drives organized.  Do you want/need RAID 10?  You might be better off with one independent drive ("/dev/sda"), and the other three in a RAID 5 arrangement.  I'd start with installing Ubuntu to /dev/sda and leaving the other three disks alone at the outset.  Partition the drive to have about 1-2 GB for /boot, 8-16 GB for swap space, and make the rest into an "extended" partition with a logical drive mounted as /, the root of the filesystem.  With 16 GB of memory, you're unlikely to use much swap, but you have disk storage to spare on this machine.

Once things are running well, you can use the mdadm utility to create a RAID 5 with the other three disks.  You might consider creating two partitions on each drive and building two RAID 5 arrays.  I'd split them about 80/20 and mount the larger array as /home and the smaller one as /var.

Will this be more work than letting someone (something?) else install your system?  Yes, of course.  But you will learn a lot about Linux and storage management as a result.

---

### Post by jmartino on 2017-04-06
> [COLOR=#000000]I have no idea what serverpilot.io is, but I would suggest you simply start from scratch with the [/COLOR][Ubuntu Server 16.04 disk image]("http://cdimage.ubuntu.com/ubuntu-server/xenial/daily/current/")[COLOR=#000000] and install it yourself.[/COLOR]
ServerPilot is the coolest thing ever (for a webmaster).  It is a super-lightweight, web-based replacement for cPanel / Plesk / DirectAdmin, etc.

Starting from scratch is a total non-starter for me.  I don't know any of this stuff, and to be honest, I really don't want to.  I am a webmaster.  NOT a server tech.  I put up with all this server crap because I have to, not because I like it.

> [COLOR=#000000]Figure out first how you want your drives organized.[/COLOR]
I chose RAID 10 (mirrored+striped) because I'm under the impression that it's the fastest and most secure way to have lots of storage at a relatively low price.  I need space.  So SSDs aren't really an option for me at this point.

> [COLOR=#000000]You might be better off with one independent drive ("/dev/sda"), and the other three in a RAID 5 arrangement. I'd start with installing Ubuntu to /dev/sda and leaving the other three disks alone at the outset. Partition the drive to have about 1-2 GB for /boot, 8-16 GB for swap space, and make the rest into an "extended" partition with a logical drive mounted as /, the root of the filesystem. With 16 GB of memory, you're unlikely to use much swap, but you have disk storage to spare on this machine.[/COLOR]

[COLOR=#000000]Once things are running well, you can use the mdadm utility to create a RAID 5 with the other three disks. You might consider creating two partitions on each drive and building two RAID 5 arrays. I'd split them about 80/20 and mount the larger array as /home and the smaller one as /var.[/COLOR]

[COLOR=#000000]Will this be more work than letting someone (something?) else install your system? Yes, of course. But you will learn a lot about Linux and storage management as a result.[/COLOR]
I sincerely appreciate your thoughts.  Really.  I do!

But all of that stuff makes my head spin.

We're coming at this from two completely different directions.  I don't have time (or desire) to be a server tech.  I have enough (endlesssss) work to do just to keep my websites/communities running.  For me, all this command line server stuff is a means to an end.  Nothing more.  I dread opening up Putty, because I always feel like I'm a keystroke away from catastrophe.

I simply want my sites to run fast and to be secure.  That's all.

---

### Post by sp40140 on 2017-04-06
I feel for you. Getting pushed into Sys Admin work is not fun. (I was pushed into DBA duties! so I know.) However, you do want to set-up the machine properly, or you will keep running into issues and that will directly impact your site uptime and performance. So, I think it would be better to sort this space thing upfront and not wait until it becomes real threat.
Good luck.

---

### Post by mastablasta on 2017-04-07
> **jmartino said:**
> 
That is my thought exactly.  But they said they can't do anything about it other than rebuild the entire OS.  Which would mean undoing (and then redoing) all the website migration work I've been doing over the last several days.


it really all depends on your configuration of the server.

if OS is kept separatelly (as ti should be) or at least on separate partition then it might be possible to correct it all relatively fast.

database backup
media backup (jus in case)
website backup (copy)
config files backup

redo the OS.

restore backup.

i had to do it once when i got hacked. took me about 2 or 3 hours before i was back online. but most time i spent looking for backups (the host had bad and infected backups only) rather than with the page itself. site was on wordpress, so i then added plenty of extra security layers and a better backup system.

if it is your server it might be good to really put it separatelly and then have it backed up regulary and versioned. 

what kind of platforms are you using?

---


---
title: "dual-boot with vista"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by eragon100 on 2008-09-01
Yesterday I installed vista ultimate after 11 months of exclusively running ubuntu. It's running circles around ubuntu on my machine, large circles. Everything on the desktop literally works 4 times faster, and all games have a 20 % higher frame rate.
All the applications I and games I used / played in linux run on windows, as well, and I have absolutely no other reason to even consider a dual-boot. However I still want to have one, because I am computer nerd after all, and computer nerds like to do that kind of thing. It will also serve as a backup os, an os to experiment with so I can help people on the forums better, it will make it easier to apply as an ubuntu brainstorm moderator, and finally, it just feels like "home" even tough it performs 5 times slower and looks uglier than vista. Am I right when I say that it is very easy to install a dual-boot, and this comes at no risk for the vista installation:

1. Defragment windows partition with windows system tools. (defragmentation currently underway...)

2. Shrinken windows partition by, say, 80 GB (it's a 320 GB harddisk)

3. Use alternate cd and at the partition options select "use largest free space" ?

I have done this once to dual-boot two linux distributions and this was the procedure back then, it worked perfectly. Does the GParted livecd also work with shrinking vista partitions and is this procedure absolutely 200 % safe with vista? I can't reinstall it because I have already used the license key and activated windows, and I don't want to ruin my vista installation for a million gold pieces. So, what do you think, safe enough to take the risk even if it isn't really necessary for anything?

---

### Post by Bodsda on 2008-09-01
Rezising a partition with data on it is not 100% safe, but it cant possibly bork vista anymore then microsoft have.

If your a computer nerd, why not find out why your ubuntu is so slow?

and it doesnt matter if youve registered the key on windows, ive reinstalled my xp with the same key ove 20 times, neve had any hassle with it

---

### Post by eragon100 on 2008-09-01
> **Bodsda said:**
> Rezising a partition with data on it is not 100% safe, but it cant possibly bork vista anymore then microsoft have.

If your a computer nerd, why not find out why your ubuntu is so slow?

and it doesnt matter if youve registered the key on windows, ive reinstalled my xp with the same key ove 20 times, neve had any hassle with it

My ubuntu isn't slow, it performs great. Vista is just 5 times faster, and I know why. The same reason it uses so much ram: prefetch. Idling, it doesn't **use** 800 - 900 mb at all. About 500 mb of that amount is reserved to start programs faster. Which is why firefox usually takes 2 or 3 seconds to start in ubuntu, and is started in vista before I can move the cursor of the shortcut. Literally. Vista doesn't waste your ram, it **uses** it (for prefetch). That's what I buy it for. I haven't bought 2 GB additional ram not to have it used. Ubuntu didn't get any faster at all with the upgrade, which I think is a bit ridiculous. Games did, but nexuiz, etqw and sauerbraten still have 26 more fps average on vista than on ubuntu (with a nvidia card, a geforce 8 8600 GT 512 mb to be precise).

Anyway, I want a dual-boot, how big is the chance my vista installation is ruined by gparted if I defrag it first?

---

### Post by falcon61102 on 2008-09-01
As far as your Vista worries go, you want to defrag at least once before using gparted but that really depends on how full your HD is prior to all this.  Also, if I could recommend a program, google Ultra Defrag and use that instead of Vista's.  For one, Vista's sucks and two, Ultra Defrag is more powerful and gives you a visual so you can see where your data is on the drive.

Once you have defragged and gotten everything consolidated, you run a very low risk of losing any data.  Do expect Vista to run a chkdsk when you first reboot Vista but that's normal.

---

### Post by arubislander on 2008-09-01
Don't know what your chances are, but I've done it on two machines, and it all went flawless...

---

### Post by bumanie on 2008-09-01
Defrag and then use the vista partitioner, it is the best for resizing vista partitions. Not sure if this is still the case, but, early on in vista's life there were dome bad experiences with people resizing vista partitions with gparted. I know some have done it without issue, whilst others have had problems. Microsft programs usually work well on microsoft products so use the vista partitioning tool, but remember resizing partitions is never 100% safe, although usually works O.K - if there is an unusual occurrence such as a power outage part-way through the partitioning, good-bye OS.

---

### Post by eragon100 on 2008-09-01
> **bumanie said:**
> Defrag and then use the vista partitioner, it is the best for resizing vista partitions. Not sure if this is still the case, but, early on in vista's life there were dome bad experiences with people resizing vista partitions with gparted. I know some have done it without issue, whilst others have had problems. Microsft programs usually work well on microsoft products so use the vista partitioning tool, but remember resizing partitions is never 100% safe, although usually works O.K - if there is an unusual occurrence such as a power outage part-way through the partitioning, good-bye OS.

Goodbye OS, excuse me? if it's only resizing the partition by removing a part of it which doesn't contain any files, how could a power outage mean that the partition is destroyed. I figure it would only mean you'd have some free space on your hard drive which wouldn't do anything, right=


Okay, I have run vista´s defragger and it says my filesystem is not fragmented. This is confirmed by ultra defrag, see the attached screenshot. Just one question tough: the white blocks are probably free space, right? I wonder if having free space in between the files on your hard drive can cause problems with Gparted resizing the partition, even if the files themselves are not fragmented?

---

### Post by SuperSonic4 on 2008-09-01
> **eragon100 said:**
> Goodbye OS, excuse me? if it's only resizing the partition by removing a part of it which doesn't contain any files, how could a power outage mean that the partition is destroyed. I figure it would only mean you'd have some free space on your hard drive which wouldn't do anything, right=


Okay, I have run vista´s defragger and it says my filesystem is not fragmented. This is confirmed by ultra defrag, see the attached screenshot. Just one question tough: the white blocks are probably free space, right? I wonder if having free space in between the files on your hard drive can cause problems with Gparted resizing the partition, even if the files themselves are not fragmented?

I'd just use vista's partition and shrink it according to the size of the ubuntu partition you'd like (and swap).

---

### Post by eragon100 on 2008-09-01
I forgot to upload the screenshot, so look in my post above to find it (attachment). Is the white space a problem when resizing?

---

### Post by eragon100 on 2008-09-01
bump

---

### Post by sea_monkey987 on 2008-09-01
No white space shouldn't be a problem.  But use vista's built-in repartitioner to repartition as other people have pointed out.

Problems using gparted to resize vista's partition:
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by eragon100 on 2008-09-01
Succes! Both are working fine now, vista has 250 gb (176 GB free, lots of programs installed), ubuntu has a little under 50 (50000 mb), 40 GB free.

Thanx for the help people! :guitar:

---


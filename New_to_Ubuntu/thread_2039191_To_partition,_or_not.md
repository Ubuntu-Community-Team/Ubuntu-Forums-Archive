---
title: "To partition, or not?"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Rabark on 2012-08-08
Hello everyone,

I've recently decided to take the plunge and install Ubuntu.  However, I'm a gamer.  So I need to keep Windows around for running games that don't like Linux (EA, I'm looking at you). 

Which means I need to install Ubuntu alongside Windows.  That leaves me with two options: either create a partition on my hard drive for Ubuntu, or buy a second hard drive and install Ubuntu on it.  I'm having trouble deciding which path would be best.

Part of me wants to get a second hard drive.  After all, what's the point of having 4 hard drive bays if you don't use them, right?  Right?

On the other hand, if there's no real advantage to setting up a second hard drive, then why bother?  Just create a partition.

So with all of that out of the way, could you please provide a basic rundown of the pros and cons of partitioning vs. a second drive?  Or just flat out make a recommendation.  That's cool too.

-Bob

---

### Post by albandy on 2012-08-08
Better 2 harddrives. At least if one fail, you can work with Linux or Windows.

---

### Post by LiamOS on 2012-08-08
> **Rabark said:**
> Hello everyone,

I've recently decided to take the plunge and install Ubuntu.  However, I'm a gamer.  So I need to keep Windows around for running games that don't like Linux (EA, I'm looking at you). 

Which means I need to install Ubuntu alongside Windows.  That leaves me with two options: either create a partition on my hard drive for Ubuntu, or buy a second hard drive and install Ubuntu on it.  I'm having trouble deciding which path would be best.

Part of me wants to get a second hard drive.  After all, what's the point of having 4 hard drive bays if you don't use them, right?  Right?

On the other hand, if there's no real advantage to setting up a second hard drive, then why bother?  Just create a partition.

So with all of that out of the way, could you please provide a basic rundown of the pros and cons of partitioning vs. a second drive?  Or just flat out make a recommendation.  That's cool too.

-Bob
I also have to keep Windows around(Battlefield 2, yeah!), but I keep it on a 5G partition, since I use it for absolutely nothing else.

As far as I can reason, the only reason you'd have to get another drive is if you want another drive. It's unnecessary unless you have a good reason for it(Truism...).

If your current drive is big enough, you should be okay. Back up everything you have on Windows, download a gparted live CD, and use it to shrink your windows partition down to whatever size. With the spare space, you can make your own partitions when you install Ubuntu.

---

### Post by cortman on 2012-08-08
I agree with LiamOS; no real need for another HDD if your current one is large enough. But first, before you even think about putting the installation CD in the drive:

[SIZE="4"]Backup your data.[/SIZE]

Also, DON'T resize the Windows partition with Ubuntu- use Windows for that, as it tends to be a bit finicky with who's resizing its partitions. You can find info on that all over the web; I believe it's in Control Panel> Administrator> Computer Management or something to that effect.

---

### Post by audiomick on 2012-08-08
I guess I am just agreeing with Cortman. Backup your data before you do anything. And use the Windows tool if you want to re-size a windows partition, and boot into that install a couple of times when you have done that. Let it do any check disk stuff it wants to before you do anything else.

If your drive is really big enough, there is no need to be spending money on new drives. Having said that, I have a 2 TB drive on here as well as the original 500GB, 80GB and a newer 60GB drive. I think I have about 150GB full... I'll get back to the reasons why in a minute.

Don't forget to back up your data before you do anything.

I originally had this machine, which is Linux only but has 2 installs of Ubuntu on it currently, with an 80GB (the smallest drive I could buy) for the OS and a 500 GB drive for the /home partition. I was quite happy with this solution.

Backing up your data before you start really is important.

This put me in a situation similar to the advantage the albany mentioned that if the system drive should mess up completely, the drive with all my data may still be completely ok. It also means that if I start messing around with second or third installs, I can do them to the smaller drive with much less risk of accidentally messing up something on the drive with my data on it.

I'm not kidding. Do a backup before you start.

At some point I got the fixed notion to get an SSD drive for my System partition. That is where the aforementioned 60GB drive comes into the picture. The 2TB one is there because I was in the shop, and whats the point of having 4 bays for drives if they're not all full? Right?

Did I mention you should backup your data?

So, given all that, I would personally probably go out and get a small SSD for the Linux system and a larger conventional HDD for the Linux /home and possibly one or more data partitions.

This would save you the trouble of having to re-size your windows partion, and minimise the danger that you may accidently over-write anything you want to keep. I also means that, as mentioned, if either of the OSs develops a problem, you have another one on another drive that will almost certainly still work. Having another large drive in there will give you somewhere to back up stuff out of the windows install to. I have my 2TB divided up into 4 500 GB partitions. I am only actually using one of them right now, but at least one of them is destined to become an archive partition.

So, to sum up: The system will run when just fine whether you have two or more drives in there, or just one. There is no really strong reason for getting a new drive.

Having said that, my experience is that the Ubuntu install on my SSD drive is noticeably snappier in the way it runs than the one on the conventional drive, and it boots quicker. You may make the installation process more fool proof and easier to plan if you add a drive or two. You gain an amount of safety if your stuff is spread around on several drives. You are more likely to always have a system that will boot if there are installs on different drives (although the boot loader is always only on one drive, and you can also always boot from a live CD/ USB in an emergency). 

So the question is, how much money do you have? Oh, and have you done your backups yet? ;)

---

### Post by oldfred on 2012-08-08
+1 on audiomick comments.

If you have good backup procedures then the drive question is not as important,  if you have space. But I find I do not backup to externals as often as I should and regardless of warranty, I do not trust hard drives to last, so I do like having separate systems and being able to copy data to another drive on a more regular basis.

My configuration is like audiomick's in that I have my two original 160GB drives that were XP (now not used) and some backups on one & Ubuntu on the other, a couple year old larger 640GB with several Ubuntu installs and new 60GB SSD to boot current & next Ubuntu.

---

### Post by d4m1r on 2012-08-08
+1 for a 2nd HDD. Too much trouble to repartition a windows partition (if its currently using the full disk) and you put data at risk by doing so...

A 2nd physical HDD also guarantees you should always have at least 1 functioning OS. If they both on the same one, and it crashes...Your PC is not unusable.

---

### Post by Paqman on 2012-08-08
If you've got space on your single drive there's no point wasting money on a second one. Using it as an excuse for an upgrade and sticking Linux onto a little SSD isn't a bad idea though. You can get Intel ones down to about 30GB or so, which would be more than enough for the root partition of a Linux distro.

---

### Post by vexorian on 2012-08-08
Never had much issue with partitions and at least in the most recent releases it is much easier than before. As long as you have enough space in your windows partition, the ubuntu installer will do it for you.

A second hard drive will consume more energy. Only reasons to do it are if you don't have space in your windows or if you really appreciate the ability to keep on working on your computer in the rare case your hard drive fails (The live CD used to install ubuntu can do it too, though).

---

### Post by Bashing-om on 2012-08-08
+3 on separate Hard drives; for all the reasons listed above. Now-a-days drives are not sooooo pricey. I do not know about a lot but I get curious and whoops! what did I do to crash my system ???? sure is nice to have another ready to boot! (not to mention my data is backed up on another drive nice/safe/secure) know how long it took me to learn this ? 
  That is my 2 dollars worth.
                                    carry on=>          BDQ

---

### Post by Rabark on 2012-08-08
Thanks for the replies,

Making a backup is a good idea; I honestly hadn't thought about it since the live CD ran so effortlessly.

Only problem is I don't have an external drive or anything else to put the backup on.  I'm also using more than 50% of the hard drive, so I can't even do a backup partition for lack of space. :(

Seeing as how I'd have to purchase a backup drive anyway, I figure I might as well go ahead and just get a second hard drive.

Any suggestions on what kind of hard drive to get?  Does Ubuntu have any known issues with specific type(s) of drives?

-Bob

---

### Post by megamister on 2012-08-09
Yep my vote is a 2nd drive too. Make an image of your Windows drive and keep it stored on a Ntfs partition on the new drive. In case you need to use it.  You can also use luckybackup or another backup type pkg for Ubuntu or Windows to keep an updated backup of your gaming data etc. The nice thing with luckybackup is the chrontab ability to set it to backup say every night so you have a constant backup of your gaming achievements. Nothing worse than reaching prestige levels and mapping keys, just to lose it and start back at level 1.

I'm partial to Samsung products, but Seagates are doing pretty good from what I can remember.

---

### Post by audiomick on 2012-08-09
> **megamister said:**
> Yep my vote is a 2nd drive too. Make an image of your Windows drive and keep it stored on a Ntfs partition on the new drive.

This is a good idea. Another variation on that theme would be to create a partition on your new drive and simply copy important data across to there using the Live CD / USB environment. That's probably what I would do, simply because I know how to do that and it is really easy. ;)

> 
I'm partial to Samsung products, but Seagates are doing pretty good from what I can remember.

:lolflag: I dislike Samsung intensely. ;)

I'm not aware of any issues with hard drives with any particular brand. I think that hard drives are such a mature technology that they all pretty much just work. I personally would not buy the absolutely cheapest ones available, but also not that most expensive ones. I believe Seagate is good. Western Digital was really good a while back. Don't know how they are now.

---

### Post by d4m1r on 2012-08-09
No, Ubuntu supports all kind of drives. My advice (self proclaimed hardware guru :)) is for either a 1TB Samsung Spinpoint F3 (7200rpm, 32mb cache or 64mb, Sata II) or a Western Digital Black of the same specs.

---

### Post by baconmaker on 2012-08-26
What I did and really like, is put Ubuntu on one hard drive and Windows on another.  The unique twist is that I bought a T-7 Storm Series hard drive removable rack.  Now I have in my Ubuntu drive most of the time. On the rare occasion I need to use Windows, I power down and exchange hard drives and I am back up and running.

---

### Post by BDNiner on 2012-08-26
> **baconmaker said:**
> What I did and really like, is put Ubuntu on one hard drive and Windows on another.  The unique twist is that I bought a T-7 Storm Series hard drive removable rack.  Now I have in my Ubuntu drive most of the time. On the rare occasion I need to use Windows, I power down and exchange hard drives and I am back up and running.

This is a really great idea. I keep Ubuntu and Windows on separate drives and just have to remember to change the boot order when starting the computer. I used to have a partitioned drive, but I broke my ubuntu install and ended up deleting the wrong partition trying to fix it.

For my peace of mind I would go with 2 drives.

---


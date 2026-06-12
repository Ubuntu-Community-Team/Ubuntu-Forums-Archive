---
title: "Beggining in ubuntu"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by maxmow on 2008-11-04
Hi! I'm beginning to use Ubuntu, I am pretty much new in this area, I played a bit with live cd and i'm now running a wubi installation to see if I can really use it.
Now, the only problem I have is that my webcam doesn't work, and I searched around but I can't fix it (tried Easycam 2 but it didn't work also, the web cam is Microsoft Lifecam vx-1000 if anyone has experience with that or can help mw with it, I would appreciate it a lot!).
I have a 230 GB HD, currently with two partitions, A 54.9 GB for C:/ drive in windows and the rest for a F drive, where I install software and games and store my big files.
Now, I heard that you need to partition your hard drive to four: one for "/" , one for "/home"(I know it optionally, but I think I want it) and one for swap and the other for windows if I want to.

So, Would I have to reformat and repartition my disk? 
I would also like to get advices on how to partition the disk, I heard that the root partition needs to be 10-15 GB, but it's where I install my programs right? so don't I need a bigger partition for that?

Thanks in advance!

---

### Post by Peter09 on 2008-11-04
If you are thinking of dual booting then the Ubuntu Installer will do most of the partitioning for you. You just need to tell it how much of the disk to use.

---

### Post by phidia on 2008-11-04
There are guides on partitioning. I'll include links to those. Partitioning is important so it's not a part of using linux that you want to short change.

Most people probably use gparted because that's the partitioner by default from the Ubuntu installer. Partitioning [guide]("http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning") another [guide]("http://www.psychocats.net/ubuntu/partitioning").

There's also a guide [here]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") with screen shots for shrinking an existing windows install to make room for linux.

---

### Post by dorkdork777 on 2008-11-04
To install Ubuntu, you will need to repartition, yes. I would suggest about 10-15 GB for "/" (you're right, that is where your programs go, but I can't imagine a program that would take up more than 500 MB - most are less than 10), and about the same for /home.

Why about the same? If you've already got all your files organised neatly in another partition, you might as well just ignore /home for storing your files, and put them on that partition. The same way you've always been doing.

As well as this, you'll need a swap partition: the best size for this depends on how much RAM you have, and how much you need. I would suggest a swap equal to the amount of RAM in your system.

So there's three new partition's I'd advise you create - "/home" (10-15 GB), "/" (10-15 GB) and a swap partition (about the same as how much RAM you have). To make room on your hard disk, simply shrink down the other two you have, to make some free space. To do this, GParted is a very reliable tool that's always worked for me. It's included on the Ubuntu LiveCD under "System - Partition Editor", or you can do it while installing, which makes a little more sense, as all the tools you need are built into the installer. :)

That's coming from somebody with about 18 months moderate Linux experience - anybody with more experience will probably give you better advice than me, though. :P

---

### Post by maxmow on 2008-11-04
Ok thanks for the replys!
So if I have to reformat I guess I would have to wait until hanukkah because I have a lot of exams that I need to worry about other than back-up the windows files and defragment and all. but it's okay I guess.It's still wierd that the root partition is 10-15 GB, because I plan to install games (I heard Spore works fine with Wine, needs to verify that though.) so I still want more details on the size. And I have 1 GB ram but I plam on extending (I got a 100 on my math exam, so I deserve it lol).

Thanks  a lot.

Edit: Oh, I already read those links, and I know how to use GParted, I used the live cd version on it to partition my disk the first time.

---

### Post by phidia on 2008-11-04
You don't need to reformat your entire drive. Gparted will shrink the window's partition so that you can install linux. You do need to see how much free space you have available but the partitioner will tell you that.

---

### Post by dorkdork777 on 2008-11-04
You can make the / partition as large as you see fit - if you plan to install a lot of games, then it's probably a good idea to make it larger. **But remember - all your Windows apps and games will be saved to your home partition - not /!** They're by default saved to ~/.wine/drive_c, so they're not on your / partition at all. There may be a way to change this, but I've not encountered it.

With this in mind, maybe it's a better idea to not have a seperate /home?

---

### Post by maxmow on 2008-11-04
> **dorkdork777 said:**
> **But remember - all your Windows apps and games will be saved to your home partition - not /!** They're by default saved to ~/.wine/drive_c, so they're not on your / partition at all.

With this in mind, maybe it's a better idea to not have a seperate /home?

What do you mean?
The wine application I install are installed to the /home folder?
If so - then what should I do?
Make a 20 GB /home partition? make a 50 GB root partition without a /home one?

---

### Post by o.besner on 2008-11-04
[http://appdb.winehq.org/](http://appdb.winehq.org/)

This is the website that you can check to know if a particular program is working with Wine. From my personnal experience I can tell you that all Steam games (Half-life 2 and it's mods) I've tried worked very well.

Spore is currently rated silver (1.00) - gold (1.01), which means that you could probably run it with a few tweaks.

All your wine games will be installed in your /home folder. /home on a linux system represents you : your configurations, your preferences, your music, your movies, your pictures. I suggest you make it a separate partition from /. This is why : If Ubuntu ever fails you, or you do something regrettable and your mess up your installation, all you have to do is format / _but leave your /home intact._This way, you won't lose your personnal files. Just make your /home partition jumbo, and give +- 10 GB to /. I currently use 3.2 Gb on my / , and all the programs I use are installed.

swap is optionnal, but useful. You should have some. Everybody will give you a different size though, since no one agrees. I guess if I didn't know what it was I would make it the same size as my Windows pagefiles.

---


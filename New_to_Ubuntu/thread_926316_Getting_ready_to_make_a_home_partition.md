---
title: "Getting ready to make a /home partition"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by thunderdan on 2008-09-21
I'm getting ready to make a /home partition, using this tutorial:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

But I just want to ask a couple of questions first.

1. Is everything in this tutorial still relevant and functional with 8.04?

2. How big should I make the partition for the OS? I want it to be big enough to handle future installations of Intrepid, etc. How much space does a standard Ubuntu installation take up? 5 GB? 10?

I'm getting really excited about using Ubuntu. I've been forced to learn more than I ever thought my Microsoft-numbed mind could handle. Thanks for taking the time to read this, and extra thanks if you can answer those questions for me!

---

### Post by MegaJim on 2008-09-21
Psychocats is a very well maintained and accurate source of information so following it is a good idea.

As regards the size of your / (root) partition, there are a couple of things to consider... creating DVD images may use up a lot of space in the root partition unless you mount /tmp to a different, larger partition, so if you want to do any kind of dvd authoring try to have at least 4gb free on it.  You don't have to take into account a page file like in windows as the swap partition is set up in a different place.  In my experience (dependent on how much software you want to install) 15gb is the maximum I've ever allotted to root and it has never got below 9gb free; 10gb would be fine in 90% of cases.

---

### Post by kjohansen on 2008-09-21
1)
i recently set up a home partition and this seems right.

The only note I would make is when you are adding this line to fstab
```

/dev/hda7 /home ext3 nodev,nosuid 0 2

```

The "dev/hda7" will most likely be different for you, so make sure you replace that with the actual name of the partition you make.

2)My main OS partition is currently at 4.6 GB of 15GB.  10 GB should be fine, most everything is going to go on your /home partition

---

### Post by linux5uper on 2008-09-21
I looked at it and it seems to me that there's absolutely no reason for this not to work with Hardy. I did my partitioning before install though, so maybe someone else can confirm this.

My / partition where the OS files and programs are, is 12 GB. I think the standard installation is about 2GB, but with all the apps I need I tend to get up to 7-8 GB. 

Why do you ask about the root partition though? Are you planning on reinstalling the whole system? In that case you should probably follow the other tutorial (linked in the one you posted).

---

### Post by solitaire on 2008-09-21
I've put aside 10Gb for "/" and the rest for "/Home" (60Gb)
I've used only 51% of my "/" drive so far (But will clean it out when 8:10 is relesed in a few weeks) :D.

10Gb should be more than enough. I think the standard install takes about 4Gb of space.

---

### Post by C.S.Cameron on 2008-09-21
I followed the instructions at:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Just a week or so ago.
Seemed to work just fine with my Ubuntu install.
Until, I tried to interpolate them to try to share the home folder with a Xubuntu install, my fault.
Better next time to use manual formatting at install.

---

### Post by thunderdan on 2008-09-21
> **linux5uper said:**
> Why do you ask about the root partition though? Are you planning on reinstalling the whole system? In that case you should probably follow the other tutorial (linked in the one you posted).

When Intrepid comes out, I plan on just using the update manager. But I also want to have the option of making a clean installation from CD and leaving my documents and whatnot intact.

> **linux5uper said:**
> My / partition where the OS files and programs are, is 12 GB. I think the standard installation is about 2GB, but with all the apps I need I tend to get up to 7-8 GB.

So if I follow this guide, will all my applications still be on the same partition with the OS? And furthermore, will those applications be erased should I do a clean installation on that partition when Intrepid comes out?

---

### Post by thunderdan on 2008-09-21
> **kjohansen said:**
> 1)
i recently set up a home partition and this seems right.

The only note I would make is when you are adding this line to fstab
```

/dev/hda7 /home ext3 nodev,nosuid 0 2

```

The "dev/hda7" will most likely be different for you, so make sure you replace that with the actual name of the partition you make.

2)My main OS partition is currently at 4.6 GB of 15GB.  10 GB should be fine, most everything is going to go on your /home partition

What does this line of code do? When you say most everyting will go on my /home partition, does that mean I will be able to install programs on that partition, or will they go on the partition with the OS?

---

### Post by linux5uper on 2008-09-21
> **thunderdan said:**
> When Intrepid comes out, I plan on just using the update manager. But I also want to have the option of making a clean installation from CD and leaving my documents and whatnot intact.



So if I follow this guide, will all my applications still be on the same partition with the OS? And furthermore, will those applications be erased should I do a clean installation on that partition when Intrepid comes out?

What you do with the procedure described in the linked tutorial, is take your /home folder to a partition of its own (where it's safe from reinstalls). So usually this means you will move your personal files and the programs' settings, but not the programs themselves. Your current programs will be erased when you do a clean install, but the new versions should optimally start up with your old settings, so Firefox will have your bookmarks, Gnome will have preserved settings, etc.

---

### Post by steveneddy on 2008-09-21
> **thunderdan said:**
> I'm getting ready to make a /home partition, using this tutorial:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

But I just want to ask a couple of questions first.

1. Is everything in this tutorial still relevant and functional with 8.04?

2. How big should I make the partition for the OS? I want it to be big enough to handle future installations of Intrepid, etc. How much space does a standard Ubuntu installation take up? 5 GB? 10?

I'm getting really excited about using Ubuntu. I've been forced to learn more than I ever thought my Microsoft-numbed mind could handle. Thanks for taking the time to read this, and extra thanks if you can answer those questions for me!

You could always ask the author of that tuturial - aysiu

---

### Post by thunderdan on 2008-09-22
Cool cool. Thanks :)

---

### Post by Settler on 2008-09-22
hi,

I would like to ask if i should care about root partition or home. Meaning I want to switch to ubuntu on a 640GB drive. I have a lot of data, media which as far as I have read should go to the data folder. 

1.so 15-20GB for root is ok for later distros?.

2.Will data be safe in /data folder or I should partition the disk in another way?

---

### Post by linux5uper on 2008-09-23
> **Settler said:**
> hi,

I would like to ask if i should care about root partition or home. Meaning I want to switch to ubuntu on a 640GB drive. I have a lot of data, media which as far as I have read should go to the data folder. 

1.so 15-20GB for root is ok for later distros?.

2.Will data be safe in /data folder or I should partition the disk in another way?

1. Yes, that's even slightly more than enough.

2. Put the folder /data on its own partition, or at least on one that is separate from the root partition. That way it will last through all reinstallations without the need to transfer it to another medium. (I have /home on its own partition, and i keep /data inside /home for example)

---

### Post by Prometheas on 2008-09-23
please ignore, just testing if I can post :)

---

### Post by Settler on 2008-09-23
How do I "order" linux to make a separate partition for /home and put /data folder in it?

Thanks but all tutorial are a bit unclear on the howto in this part of install.

Thanks again

---

### Post by linux5uper on 2008-09-23
I assume you want to do a clean install (i.e., you haven't installed ubuntu yet).

During the install, you will come across a section called "Partitioning". It gives you some automatic options by default, but you will want to choose "Manual".

Here you will normally have to create an ext2 or ext3 partition that is about 2 times your RAM memory in size, and tell it to be used as 'swap' (there is a drop menu for this purpose, it should be obvious). 

Second, you have to create a partition for your OS and programs (root partition). Mine is 12 GB in size. Set it to be used as /root

Third, make a partition for your home directory and all data (you set the size - either all remaining space or as much as you want). Set it to be mounted as /home from the drop menu. This is the way I did it. After install you can create your /data directory within /home and transfer your stuff in it.

If you're not sure about a step, the safest thing to do is pause or cancel the installation, and ask questions here before proceeding.

---

### Post by Settler on 2008-09-23
Thanks a lot linux5super. Your answer is clear as crystal water. I'll have another pc by when installing to cerf the forums so I think it won't be any of a problem.

Thanks again!

---

### Post by solitaire on 2008-09-23
To the OP:
I'm not sure if anyone has suggested this but..
Download the latest *.ISO Distro
Install one of the 'Virtual Machines' into your current install,
Mount the ISO as a CD drive then run the install in the virtual Machine, 
You can then play about with the install options including partitioning the drives for Root & Home once you are comfortable you can take it to your full system... 

Virtual Environments are good for practice! :D:D

---

### Post by timjohn7 on 2008-10-02
I have what must be a fairly common scenario...
I have just taken the leap from dual boot (WinXP & Hardy) and gparted my 40Gb HDD (OK.. it's an old laptop), formatting the 15 Gb XP partition as ext3.  I then grew my Ubuntu partition to maximium.
What I'd now like to do is the reverse of the psychocats seperate home tutorial ie move my \ directory to the smaller 15Gb partition while leaving my current 25Gb Ubuntu partition as \home.
I haven't been able to find any advice on this situation.
I also plan on installing Intrepid this week, so please take that into account if you are going to help!
I assume that if I install Intrepid to the smaller partition I would be part way there, but how could I then get rid of the Hardy installation on the larger partition to leave it just as \home?

---

### Post by Settler on 2008-10-03
And another thing. If I install Linux in an empty HDD,

1. Will I be able ton install newer versions of Linux without touching /home folder and 
2.Will I be able to install windows somewhere in there?


Thanks

---


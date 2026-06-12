---
title: "Multi Booting XP and Ubuntu and partitions"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Billsputters on 2008-08-20
I've finally taken the plunge and decided to switchover totally to Ubuntu, and to this end have gone out and bought a larger disc for my laptop.

Having read as much as I can find (that I understand!) about multi booting systems, it seems to be recommended that XP is installed first. No problem - 10Gb partition, plenty of room and I can run RiscPC emulator as well. I tried to get XP to run under OSE Virtual Box but get a virtual box kernel errors asking to install them again. Tried but failed, and time for the switchover is moving on.

OK.So my main working OS will be Ubuntu, and I'd like to have Ubuntu Studio installed as a separate entity as well. And a couple of other partitions on the disc to try other Linux flavours. I'd like to keep UStudio separate, just so the two don't interact, and I don't want to burden UStudio with email and Office and all the other bits and bobs for everyday use. I want to keep UStudio clean, as it is out of the box.

I want to be able to share data between all OS's. There will be little traffic between XP and anything else so I can just use the XP partition for this as required. I would like Ubuntu, Ubuntu Studio to have access to the same data, which will mainly be multimedia files, and also share with any other flavours of Linux I install. 

Now this is where I start to get confused. I have a /home partition with richard as the (only) user. I then want every other intall to use /home/richard as the home directory. Not problems there I think, shouldn't be any interactions.

Am I correct that any other applications that I add for a particular distro effectively go in the /of that distro? 

If so, does this partition table look viable, or is there a better solution

HDA 200GB

HDA1 Windows XP     10GB
HDA2 Ubuntu          6GB
HDA3 Ubuntu Studio   6GB
HDA4 Extended Partition
HDA5 Swap            2GB
HDA6 /Home          150GB
HDA7 Another distro   6GB
HDA8 Ditto            6GB

Alright the numbers don't add up to 200, but you get the idea. I take it that sharing the swap is not a problem.

Many thanks for reading this rather long post, and I look forward to any feedback.

---

### Post by Elfy on 2008-08-20
It seems that it is best that different distros don't share /home - it could cause problems - although that is just what I've read. It would be better to have a large data partition that all can access and let eachg distro have it's own /home within / and correspondingly smaller.

The thinking being that if different distros have the same application accessing the configs in the same home then conflicts could occur.

So if you were to give each distro 10Gb then that would be 50Gb total and 150Gb left for data and a swap.

---

### Post by tarps87 on 2008-08-20
As far as I'm aware it should be fine, if you want to access the Ubuntu partition (ext3 format) from windows there are drivers available but I have never used them, if not you can access the windows data from Ubuntu as long as the ntfs support is activated. There's a gui installable from synaptic.

> **Billsputters said:**
> I can run RiscPC emulator as well.
Another one :), out of interest what do you use the RiscPC for?

---

### Post by Too Late on 2008-08-20
One tip when having multiple distros is to have the same UID in each one. That will ensure that you have same permissions everywhere. Many distros (if not all) allow you to choose your UID number somewhere during install. Ubuntu defaults to 1000 (you can see it by typing "id" in terminal), while some others use eg. 500 by default.

---

### Post by Billsputters on 2008-08-20
> **tarps87 said:**
> As far as I'm aware it should be fine, if you want to access the Ubuntu partition (ext3 format) from windows there are drivers available but I have never used them, if not you can access the windows data from Ubuntu as long as the ntfs support is activated. There's a gui installable from synaptic.


Another one :), out of interest what do you use the RiscPC for?

Used to use one a while ago, but it's slow and out of date now, but still like some of the programs, and also it cures themisty eyes!:)

---

### Post by Paqman on 2008-08-20
> **forestpixie said:**
> It seems that it is best that different distros don't share /home - it could cause problems - although that is just what I've read.

Nope, sharing a single /home between several distros is no problem. You do however have to set up different users. Since each user is a completely separate folder within /home, there's no way they can mess with each other.

If you really wanted to have a single username across multiple distros, you would have to set up multiple /home directories. That could get pretty gnarly partition-wise.

I really wouldn't advise having a single user on a single /home across multiple distros. It's unlikely to cause any real damage, but your session would be a mess.

---

### Post by tarps87 on 2008-08-20
I still play elite some times, I've go an acorn a3010 (either 512KB or 1MB of RAM). They maybe old but there still about and working ;)

---

### Post by Elfy on 2008-08-20
> Nope, sharing a single /home between several distros is no problem. You do however have to set up different users. Since each user is a completely separate folder within /home, there's no way they can mess with each other.That I can understand - but I was responding to this from the OP, perhaps I should have worded it differently - I tend to think of /home as /home/user :)

>  I have a /home partition with richard as the (only) user. I then want every other intall to use /home/richard as the home directory. Not problems there I think, shouldn't be any interactions.

Personally I think it's best to use /home for configs and not data, then they won't get too big - and have completely seperate data partitions that all can share

---

### Post by Paqman on 2008-08-20
> **forestpixie said:**
> That I can understand - but I was responding to this from the OP, perhaps I should have worded it differently - I tend to think of /home as /home/user :)

Ah, then you're absolutely right :)

> 
Personally I think it's best to use /home for configs and not data, then they won't get too big - and have completely seperate data partitions that all can share

Good idea, but it all goes out the window if you start using Wine. It installs it's fake Windows hierarchy into /home, so you end up with not only data, but apps as well. It can get pretty fat.

---

### Post by Elfy on 2008-08-20
Didn't know about wine's behaviour as I don't use it - good to know that :)

---

### Post by tarps87 on 2008-08-20
> **Paqman said:**
> Good idea, but it all goes out the window if you start using Wine. It installs it's fake Windows hierarchy into /home, so you end up with not only data, but apps as well. It can get pretty fat.

You can add drives (well really there just folders) to wine in the wine config menu, as long as when you install a program you send it to that drive letter it will put it in the folder linked to it.
I believe you can move the c: drive as well but it will have to test that to confirm it.

---

### Post by Billsputters on 2008-08-20
The problem highlighted with sharing /home is something I've read about and some seem to discard it. But the obvious problems of apps screwing up common configs does seem to put that idea out of the window.

So either have a different login name for each user, let the apps sort themselves out in their own space and have a common data directory within home where all the real meaty data is stored. But I think there might be permissions to correct across all the users.

or

Have a separate /Data partition and all users access that for program data and files. /home partitions for each distro can then be small as no real heavy big files stored there.

I think I'd prefer the first option, as /home can be large and accommodate everything.

---

### Post by Elfy on 2008-08-20
Go for it then - it's all about choice in the end :)

Good luck with it.

---

### Post by Billsputters on 2008-08-26
Ok. I've partitioned the disk, and added three OS's (XP, Ubuntu and Ubuntu Studio). So now I want to set up a new directory in the /home partition that all users can access to save data and share between them.

I can't do this as a normal user as I need root privilages to add to the /home directory. So I have to *sudo* and add my password. But a simple test (I am treading carefully) of *sudo cd ~* which I expected to take me to the /home directory somes up with *cd: command not found*.

Now I am doing something wrong, or making the wrong assumption somewhere.

What I was thinking of doing was creating a directory in /home, making a new group in each distro with permissions to only that folder and adding the user to that group. Is that the long winded way around oris there a simpler way, as I am sure there is.

---

### Post by Elfy on 2008-08-26
It would be best to my mind to have a seperate partition that all can access.

You shouldn't need root rights to access your /home. 

You can't sudo cd afaik

If you want/need to use sudo to make a dir then

sudo mkdir /path/to/the/new/folder/evn/if/it's/home

eg sudo mkdir ~/name

would create a folder /name in /home, but the permissions would probably need to changed as using sudo would create a folder with root rights.

---

### Post by Billsputters on 2008-08-26
> **forestpixie said:**
> It would be best to my mind to have a seperate partition that all can access.

See my post above for the reasons. It's a choice between a separate partition, or all users from whatever installation usung /home for their data. That way, /home and data can be large, with lots of room to grow as required, rather than trying to guessitmate a good size for the /home partition to hold emails and wine apps. It's just a case of how to make a data directory in /home available to all.   

> You shouldn't need root rights to access your /home. 

Agreed.

> You can't sudo cd afaik

Ah! Now, now that I didn't know. Why not?

> If you want/need to use sudo to make a dir then

sudo mkdir /path/to/the/new/folder/evn/if/it's/home

eg sudo mkdir ~/name

would create a folder /name in /home, but the permissions would probably need to changed as using sudo would create a folder with root rights.

That seemed to create a folder in /home/richard (richard being the user).
I used * sudo mkdir /home/data* which did the trick. This creates a folder owned by root, below all the users and should therefore be accessable to the users.

I just have to change ownership. I tried sudo chmod -R :datausers /home/data, but I can't save files there. Any ideas?

---

### Post by Elfy on 2008-08-26
> Why not?No idea :D but then you don't need to do it, you can just make the folder as I showed you, if you wanted to make the folder inside its parent then cd there first, but it's easier to just make the folder as you want. 

>  Any ideas?You are getting chmod and chown a bit confused, have a look at this thread it should help you, it's certainly where I saw the light...

There is a community page here [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Billsputters on 2008-08-26
I think I've sorted it. Even though I set the folder owner to a group, being a member of that group didn't give you rights. Changing the user owner of the older from root to a 'normal' user allowed any user to access that folder, as long as they are members of the group.

I then made a symbolic link of the folder and placed that in the users home folder and bingo. Just what I wanted.

I was getting confused myself by /home and what Ubuntu calls home which is /home/user, as mentioned earlier in this thread.

Many thanks to all that helped.

---


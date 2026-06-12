---
title: "[SOLVED] Home Partition...Is it necessary to have one?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by flamingswrd on 2008-09-05
I am currently installing Ubuntu and am playing with dividing up 44 gb of free space. How much space should I give to a Home partition, and is it even necessary to have? When making the root partition, all applications, documents and other regular system processes go on it, correct? Would 10gb be good for everyday use? 

*Notes: I know I can save elsewhere on the drive, mainly the windows portion (yes, I am dual-booting) and I have an external drive for larger files.

Assistance is appreciated! :)

---

### Post by Zack McCool on 2008-09-05
You do not NEED a /home partition.  If you do not define one, it will use space from /.  The default installation is to just have a / and swap.

If you decide to use a /home, the size is up to you.  The important part is making sure you have enough space for everything else.  / should be 8GB minimum, 12 GB should be comfy, then a swap and whatever is left for /home.

---

### Post by iaculallad on 2008-09-05
> **flamingswrd said:**
> I am currently installing Ubuntu and am playing with dividing up 44 gb of free space. How much space should I give to a Home partition, and is it even necessary to have? When making the root partition, all applications, documents and other regular system processes go on it, correct? Would 10gb be good for everyday use? 

*Notes: I know I can save elsewhere on the drive, mainly the windows portion (yes, I am dual-booting) and I have an external drive for larger files.

Assistance is appreciated! :)

How much space will you give to your Home partition? Well, that depends on what type of user you are. If you're mostly inclined on having mp3's, movies, ebooks, pictures being saved on your Home directory, then, you have to allocate a bigger space for your home directory (That's just an option since you can save those types of files on [separate]("http://www.psychocats.net/ubuntu/separatehome") partitions though). Home partition is necessary in Ubuntu as it's a way of ID'ing the user's own folder.
The root partition (/=Filesystem) is automatically created when you install your Ubuntu OS.
10GB? That depends on you.

---

### Post by knix on 2008-09-05
basically lets you keep your files/setting after a fresh install, or share a home folder between distros. but its not necessary.
If you use one, I would put in an extended partition.

---

### Post by alienexplorers on 2008-09-05
I always use a /home page, because if you ever and that time will come to reinstall you can have all your configurations and files saved as long as you do not format /home.

---

### Post by flamingswrd on 2008-09-05
The guide I am following suggests 4+ gb for the root partition, but since I may only install about 6 things (VLC, Gimpshop, WINE, a few games) I guessed at 10gb. What would you suggest?

---

### Post by kjohansen on 2008-09-05
i just setup a separate home partition after the fact.  there were some scary moments when I thought I had ruined everything.  but here is a link to the tut I followed.

[http://www.linuxquestions.org/questions/linux-newbie-8/home-directory-on-separate-partition-627445/](http://www.linuxquestions.org/questions/linux-newbie-8/home-directory-on-separate-partition-627445/)

---

### Post by iaculallad on 2008-09-05
> **flamingswrd said:**
> The guide I am following suggests 4+ gb for the root partition, but since I may only install about 6 things (VLC, Gimpshop, WINE, a few games) I guessed at 10gb. What would you suggest?

If you have a large capacity drive then you can give it >=15GB. It won't go to waste since you can try installing other applications if you like.

---

### Post by Shazaam on 2008-09-05
Some users swear by a separate home partition. I have 6 distros scattered over 3 drives with no separate home partition(s). My tweaking/updating/trashing them has not posed a problem for me. IMHO about the only time it "might" come in handy is if you want to dist-upgrade/reinstall Ubuntu.

---

### Post by Slug71 on 2008-09-05
Id just do 20gb for / and 20gb for /home and 4gb for swap.

---

### Post by iaculallad on 2008-09-05
> **Slug71 said:**
> Id just do 20gb for / and 20gb for /home and 4gb for swap.

4GB of swap? How much physical RAM do you have?

---

### Post by flamingswrd on 2008-09-05
Therein lies my problem...I can't devote all the space to Ubuntu...yet. I want to leave some with my existing XP and give Ubuntu some room to grow and grow on me. 

So here lies my data situation...120GB hard drive originally - 111.79 after Windows takes its space

Hard drive space remaining after two years...~44gb. Some of it (1/4 at least) I would like to remain with XP. Now comes the good news: 500GB external, with over 350GB left (it holds all my backed up files).

Now I ask for recommendations...and if a home partition would be a smart idea.

---

### Post by flamingswrd on 2008-09-05
> **iaculallad said:**
> 4GB of swap? How much physical RAM do you have?

I have 2GB of RAM currently installed in my laptop...I should really get around to putting sys specs in my signiture.

---

### Post by Oldsoldier2003 on 2008-09-05
> **Shazaam said:**
> Some users swear by a separate home partition. I have 6 distros scattered over 3 drives with no separate home partition(s). My tweaking/updating/trashing them has not posed a problem for me. IMHO about the only time it "might" come in handy is if you want to dist-upgrade/reinstall Ubuntu.
After playing with the separate home partitons I have found that I prefer NOT using them and just keeping my data on separate data partitions. I link them into my home directory for easy accessibility.

---

### Post by Vivaldi Gloria on 2008-09-06
> **Oldsoldier2003 said:**
> After playing with the separate home partitons I have found that I prefer NOT using them and just keeping my data on separate data partitions. I link them into my home directory for easy accessibility.

+1

This is also what I do. I like having fresh /home and config files when I reinstall/upgrade ubuntu.

---

### Post by Slug71 on 2008-09-06
> **flamingswrd said:**
> I have 2GB of RAM currently installed in my laptop...I should really get around to putting sys specs in my signiture.

I too have 2gb of ram. 

In which case 4gb is good for a swap. Go 15gb / and 10gb /home and the rest of the 15gb make FAT32 which would be a shared partition for Ubuntu and Windows. I have my Pictures and music on my shared so i can access them in Vista or Ubuntu.

Thats actually axactly like mine is setup. 15gb /, 10gb /home, 4.096gb swap but i have a 50gb shared.

Actually i think mine is 10gb / and 15gb /home.

---

### Post by Slug71 on 2008-09-06
Or like Soldier an Vivaldi said, just have a / with 20/30gb and a shared.

---

### Post by knix on 2008-09-06
> **Oldsoldier2003 said:**
> After playing with the separate home partitons I have found that I prefer NOT using them and just keeping my data on separate data partitions. I link them into my home directory for easy accessibility.

honestly, same here. It keeps me from accumulating too much junk because i have to evaluate what to back up.

---

### Post by flamingswrd on 2008-09-06
A home partition only stores data files, such as docs, pictures, etc.? I had the impression that it stored configurations (themes, backgrounds, mouse, other preference settings) as well. Is that true or not?

---

### Post by Vivaldi Gloria on 2008-09-06
> **flamingswrd said:**
> A home partition only stores data files, such as docs, pictures, etc.? I had the impression that it stored configurations (themes, backgrounds, mouse, other preference settings) as well. Is that true or not?

If you do not setup a seperate storage partition then all your personal files are kept on your home folder.

---

### Post by flamingswrd on 2008-09-06
Does the shared partition have a unique name like root or home? I'm new at the whole dividing up my hard drive thing. I know how to get around WinXP and keep "most" malicious stuff away, but thats about it.

---

### Post by Shazaam on 2008-09-06
4gig swap with 2gigs installed ram is overkill unless your pc is setup to sleep/hibernate or is a pc that shares memory with video.

---

### Post by Vivaldi Gloria on 2008-09-06
> **flamingswrd said:**
> Does the shared partition have a unique name like root or home? I'm new at the whole dividing up my hard drive thing. I know how to get around WinXP and keep "most" malicious stuff away, but thats about it.

Generally you mount storage partitions in /mnt, say /mnt/mydisk. Then you can put a symlink of it in your home folder.

I suggest you give 12GB to root, 2GB for swap, rest for storage partition.

---

### Post by iaculallad on 2008-09-06
> **flamingswrd said:**
> I have 2GB of RAM currently installed in my laptop...I should really get around to putting sys specs in my signiture.

Whoaaahhh.. 2Gig of Physical RAM and you had configured your system to have a 4Gig of SWAP? Huh, I think you played it by the book when you did this (# of RAM * 2). No offense but this is an overkill as you could try executing the **free** command on your terminal, what should display is that your SWAP partition will never be used (Unless you're doing some video editing or other applications requiring extensive usage of RAM).

---

### Post by Slug71 on 2008-09-06
> **flamingswrd said:**
> Does the shared partition have a unique name like root or home? I'm new at the whole dividing up my hard drive thing. I know how to get around WinXP and keep "most" malicious stuff away, but thats about it.

No its just called that because you can use it between OS's. Its a partition. Linux and Windows can see and work with FAT32. Whatever size you decide to use for shared just choose FAT32 filesystem and mount as windows. That will be your shared. 

Then once you log into Ubuntu go Places(top left next to applications)-Computer-File System and in there will be a folder called windows.
That will be your FAT32 partition.

---

### Post by flamingswrd on 2008-09-06
I have a meter showing my RAM consumption/usage and it rarely gets over 50%, so a small swap partition is in my future...root I am considering devoting 15GB.

A few of you have mention a storage partition...excuse my lack of competence with this issue, but is that a completely separate partition, the home partition or what?

Edit: So instead of a home partition I would make one just for storage? I've at least done my research on file systems so what type it should be isnt an issue.

---

### Post by Slug71 on 2008-09-06
> **iaculallad said:**
> Whoaaahhh.. 2Gig of Physical RAM and you had configured your system to have a 4Gig of SWAP? Huh, I think you played it by the book when you did this (# of RAM * 2). No offense but this is an overkill as you could try executing the **free** command on your terminal, what should display is that your SWAP partition will never be used (Unless you're doing some video editing or other applications requiring extensive usage of RAM).

:lolflag:
Not doing any of that. Yeh i did that by the book, swap = RAM x2.

Oh well its only 4gb.
:lolflag:

---

### Post by flamingswrd on 2008-09-06
> **Slug71 said:**
> :lolflag:
Not doing any of that. Yeh i did that by the book, swap = RAM x2.

Oh well its only 4gb.
:lolflag:

In all honesty if I had a "blank slate" for a computer I would probably do the same...Now if I just had a job I could really have some fun. Gotta work with what you got though. :)

---

### Post by Slug71 on 2008-09-06
flamingswrd, my hdd looks something like this

40GB NTFS Vista                 Primary
50GB FAT32 (shared)             Extended
10GB EXT3 /                     Extended
4.096 swap (i know, i know)     Extended
15GB EXT3 /home                 Extended

---

### Post by Shazaam on 2008-09-06
> **flamingswrd said:**
> I have a meter showing my RAM consumption/usage and it rarely gets over 50%, so a small swap partition is in my future...root I am considering devoting 15GB.

A few of you have mention a storage partition...excuse my lack of competence with this issue, but is that a completely separate partition, the home partition or what?

Edit: So instead of a home partition I would make one just for storage? I've at least done my research on file systems so what type it should be isnt an issue.

Yes it would be a separate partition. I haven't tried it that way yet but you would have something like this...
1. Windows
2. /swap
3. Ubuntu
4. Fat32 shared DATA/STORAGE for Windows/Ubuntu

---

### Post by flamingswrd on 2008-09-06
The last two replies help a whole lot. :) I think I have enough information to continue the install process confidently. When I was doing my research I slightly questioned the helpfulness of the linux community...no more questions! Finally a support group that answers questions and doesn't do an "excellent job of answering without answering." I'm sure you've dealt with that...

Thanks.

---

### Post by flamingswrd on 2008-09-06
One last minor thing. Root has a mount point of /
What would I set the storage mount to or does it matter?

---

### Post by Vivaldi Gloria on 2008-09-06
> **flamingswrd said:**
> A few of you have mention a storage partition...excuse my lack of competence with this issue, but is that a completely separate partition, the home partition or what?

completely separate partition

> Edit: So instead of a home partition I would make one just for storage? 

Yes.

> I've at least done my research on file systems so what type it should be isnt an issue.

Go with ext3. Stable.

-------------------------

Some people like a /home partition so that they can keep their config files from one install to another. Some people like me don't like it because we actually like fresh installs. Here are your options. 

**Partitioning A - 3 total partitions.**
root partition (doesn't include /home) - 15GB
swap - 2GB
/home - rest

**Partitioning B - 3 total partitions.**
root partiton (includes /home, no separate partition for it) - 15GB
swap - 2GB
a storage partition (say /mnt/disk) - rest

EDIT: I forgot that there's also windows partition.

---

### Post by iaculallad on 2008-09-06
> **flamingswrd said:**
> One last minor thing. Root has a mount point of /
What would I set the storage mount to or does it matter?

You just give it the slash (/) and that's it (EXT3).

---

### Post by flamingswrd on 2008-09-06
Thanks. I'll let you know how things go and then when all is well and good I can close this topic. :)

---

### Post by Slug71 on 2008-09-06
Yeh let us know how you installed.

---

### Post by flamingswrd on 2008-09-07
I got past the basic regional things, but now I am a bit nervous on the partitioning portion. When I go to resize my windows partition it says I can't undo the changes and the number representing used space does not add up with others I am given in Windows or the Ubuntu live CD. 
Should I trust the numbers given or check it with another program or something? I have never really installed an operating system and would probably have trouble reinstalling windows if I screw something up. 

Long story short:
1) Trust the numbers given by the Ubuntu partitioner and resize my drive?
2) Check it with a program to view partitions?

---

### Post by Slug71 on 2008-09-07
Id resize with PartionMagic or a program similiar to that with Windows. That way you can create a retore point first and then resize your partition and then do a restart and make sure windows still works correctly. Then go ahead and create the rest of the partitions you need using Ubuntu partitioner. 
Thats just what i would do to play it safe.

---

### Post by flamingswrd on 2008-09-07
something like gparted? I found it through some google and wikipedia research? Anyone have experience with it?

[gparted site]("http://gparted.sourceforge.net/")

---

### Post by Shazaam on 2008-09-07
Yes that is a very good tool (gparted livecd) to have. But as stated before, backup your critical Windows files and defragment Windows before you resize partitions. Read up as much as you can about dual-booting and partitioning. Once you have a working knowledge go ahead and take the plunge.
Two very good links that you can check out....
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Oh, and remember, Ubuntu Intrepid Ibex 8.10 is just around the corner (October release).

---

### Post by flamingswrd on 2008-09-07
I may skip formatting my laptops drive in dual boot until then. I think I have an old box to play with so I will try Ubuntu on that. Hopefully it still works! :-?

---

### Post by Slug71 on 2008-09-08
Sounds like a safer idea. GParted is good though and like previously said, just back up and defragment and you should be good. 
But always better to play it safe.
If you could i would write all my stuff to CD from Windows then just do a fresh install and do all your partitioning then. Just make sure Windows is your first Partition.

---

### Post by flamingswrd on 2008-09-08
Well instead of taking the chance of screwing up my fully capable computer (if MS can be capable...) I found an old box to play with Ubuntu on. I have no idea what hardware it's got, so it should be fun. I'll let you know how things go on this one. Then maybe I'll be willing to mess with my laptop.

---

### Post by flamingswrd on 2008-09-08
Success on this box anyway. :) Ubuntu installed nicely and all of it's little updates worked well. This box had two drives. One 10gb and one 60gb. I made the root partition on the 10gb and the home and swap partitions on the 60 gb. I like it so far...everything is in much easier reach than Windows...if only I could get my screen resolution to get bigger (stuck at 800x600 for some reason). 

I this works out well I might just consider reformatting my laptop with Ubuntu...either Hardy or the new one coming out in October. 

Thanks for everyone's help and support! It is a nice breath of fresh air considering other "tastes" of support I have had before.

---

### Post by Slug71 on 2008-09-10
Glad it worked out for you! I really dig Ubuntu. Im gonna build up a new desktop next year and very much doubt it will see Windows. Up until i installed Ubuntu a couple months ago i hadnt used Linux since 05 and i tell you its come a long way since then!! And it can only get better. I see lots of improvement from Hardy to Intrepid already too and i only used Hardy for about 3 weeks. And im using 64 bit. This Laptop is probably only about 4 months old, has built in webcam and mic and everything works perfect. Have Skype and Adobe Reader running fine too.

---


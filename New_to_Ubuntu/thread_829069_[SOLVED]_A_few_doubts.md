---
title: "[SOLVED] A few doubts"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by pablote on 2008-06-14
Hello! I'm *really* an absolute beginner so i was wondering if some of you out there could help me with i few doubts i have regarding Ubuntu 8.04 instalation. Here we go:

1) First of all, a tremendously naif question: Is it normal if Ubuntu booted from the Live CD runs kinda slow? I have a Pentium 4 3 GHz and 500 MB of RAM. Is it enough to install and run Ubuntu?

2) My plan is to install Ubuntu keeping Windows (al least for a while). My disc (80 gb) is already partitioned. In C: i have my documents and Windows, and I keep D: (40 gb) for backuping, which is very useful everytime I have to REinstall windows because IT SUCKS, ejem. Now, what I wanted to do is to format D: to install Ubuntu in it, but, i also wanted to keep a little partition (around 10 gb) for backuping. So, that would leave me with a 30 gb partition for Linux (is that enough?). And, if i'm not mistaken, Ubuntu instalation creates 3 partitions in the unit in which you install it, right?? So, i think that leaves me with to many partitions: 5 =S . As far as i know, only four partitions can me created in a single HD, right?.

3) In case I *can* create the partitions, these can be done directly from ubuntu installation? or do you recommend to download Partition Magic o something like that?

Well, I hope someone can help me ! i'm lookinf forward to install ubuntu and get it running !

Thanks in advance (and forgive my english, i'm from argentina jej)

Pablo

---

### Post by the_doc on 2008-06-14
Welcome.

1.  Yes it will run slowly, as it is obviously relatively slow to access the CD/DVD drive.  Your system specs seem ok, I'm not too sure on that amount of RAM, but you should be fine.

2. Not to sure here but I think the limit is 4 primary partitions, you can have three primary and one extended, which in turn can contain multiple logical drives.

3.  I think it can be done directly from the Ubuntu install.

---

### Post by rraj.be on 2008-06-14
> **pablote said:**
> Hello! I'm *really* an absolute beginner so i was wondering if some of you out there could help me with i few doubts i have regarding Ubuntu 8.04 instalation. Here we go:

Just get here.

```
[[COLOR="Blue"]http://ubuntuguide.org/wiki/Ubuntu:Hardy[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")
```


> 
1) First of all, a tremendously naif question: Is it normal if Ubuntu booted from the Live CD runs kinda slow? I have a Pentium 4 3 GHz and 500 MB of RAM. Is it enough to install and run Ubuntu?

Its normal to be somewhat slow in live cd.

i use pentium dual core 3.2GHz 512MiB ram and i am much satisfied.

> 
2) My plan is to install Ubuntu keeping Windows (al least for a while). My disc (80 gb) is already partitioned. In C: i have my documents and Windows, and I keep D: (40 gb) for backuping, which is very useful everytime I have to REinstall windows because IT SUCKS, ejem. Now, what I wanted to do is to format D: to install Ubuntu in it, but, i also wanted to keep a little partition (around 10 gb) for backuping. So, that would leave me with a 30 gb partition for Linux (is that enough?). And, if i'm not mistaken, Ubuntu instalation creates 3 partitions in the unit in which you install it, right?? So, i think that leaves me with to many partitions: 5 =S . As far as i know, only four partitions can me created in a single HD, right?.


1--> first reinstall your windows  [IF YOU WANT TO}

2--> 7 to 10 Gib is more than enough for your Ubuntu installation.

you will need only 5 GiB at the most .

Aditionally a 1 GiB swap.

> 
3) In case I *can* create the partitions, these can be done directly from ubuntu installation? or do you recommend to download Partition Magic o something like that?

You have gparted in live cd itself.

just open

applications-->acessories-->terminal

and type 

```
sudo gparted
```
> 

Well, I hope someone can help me ! i'm lookinf forward to install ubuntu and get it running !

Thanks in advance (and forgive my english, i'm from argentina jej)

Pablo



May i know if you need further help.

---

### Post by rogier.de.groot on 2008-06-14
1) Yes your machine is good enough. Ubuntu runs slow from LiveCD because it contains a compressed (like a ZIP file) file system so they can put more stuff on one CD. This makes reading files slower because uncompression needs to be done. Besides, reading from CD is slower then reading from HDD anyway.
2) I alway do my partitioning manually (in the installer you can pick several option for partitioning) and only make root and swap partitions. But you can have up to 8 partitions per drive. BTW, why do you think Windows sucks? I never have any problems (with XP anyway).
3) The installer (the "Install" icon on the livecd desktop) has built-in partitioning support, AFAIK it can even resize windows partitions.

Good luck!

---

### Post by nothingspecial on 2008-06-14
Yes it is normal for Ubuntu to run slow from the live cd.

Yes your pc will run it no problem.

As for your 3rd question, all I have ever done during a Ubuntu install is completely nuke windows. All my files are on external drives and I like the tweaking part of a clean install. Someone else will have to help you with partitioning.

Carlos Tevez`s my favourite player btw.

---

### Post by SunnyRabbiera on 2008-06-14
Well you really dont need Ubuntu to split into two or three separate partitions.
Actually Ubuntu only needs two partitions, a main partition and a swap partition though most recommend three as it helps with updating.

---

### Post by Happy_Man on 2008-06-14
1) Yes, it's normal for the live session to run slow, and yes, that is plenty for Ubuntu. 

2) All right, here's what you're gonna do. First, back up your D: drive, just to be safe. Then, go ahead and boot up the Live cd and go to System --> Administration --> GNOME Partition Editor. Delete your D: drive (see? that's why we backed up) and create a new "extended" partition in the empty space. Then, create a 10 GB "logical" partition formatted as ext3, a 1 GB "logical" partition formatted as "swap", and another "logical" partition with the rest of the space formatted as either ext3 or NTFS (your choice). 

Once you're done that (don't worry, it's less complicated than it looks), go through the installer. When it comes time to do the partitioning, select "manual". From that screen, right-click your 10 GB partition and go to "edit partition". Select "/" from the dropdown, and click Ok. Click the "format" box next to the 10 GB partition. BE VERY CAREFUL, IF YOU ACCIDENTALLY TELL IT TO FORMAT THE WINXP PARTITION IT WILL. No need to format anything else other than that. Then, let it install. You should be all set!

Some other notes: 10 GB is more than enough to run a very expansive Linux install, because Linux doesn't bloat up like Windows. And extended partitions are the answer to the 4 partition rule. Hope this helps!

---

### Post by pablote on 2008-06-14
Thank you VERYYYYY much!!!
I'll get going with the installation as soon as i Backup all my files

Tevez Rules! ja!

---


---
title: "Help Please!!!"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by KillBoss92 on 2008-11-07
Hello everybody. As you can see I'm new to Ubuntu. I believe I have a quite valid question seeing as how the person that got me to convert to Ubuntu can't even answer this question. Alright so when I switched my Windows XP to Ubuntu I wasn't so sure how much I should convert to Ubuntu and how much to leave as Windows and such. So I went for the safe route and chose to keep 15% Windows and converted 85% to Ubuntu. Now that I realize that Ubuntu is the way I want to go, how can I convert the 15% of windows I kept over to Ubuntu? Thanks in advance for any help or advice I may receive.

---

### Post by tvtech on 2008-11-07
simple install the front end for gparted ```
sudo apt-get install gparted
``` if that doesn't remove check install apps.  remove your windows partition stretch your ubuntu partition or just leave it as a separate partition to store files on and reinstall grub. double check on how to reinstall grub  I've broken ubuntu a few times doing this.  and breaking it is a pain in the butt.  Otherwise... back up your files and do a fresh install.

---

### Post by KillBoss92 on 2008-11-07
I'm guessing that was in Terminal.
The command worked and gave me this...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
Suggested packages:
  jfsutils ntfsprogs reiser4progs xfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 348kB of archives.
After this operation, 2150kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main gparted 0.3.5-1ubuntu3 [348kB]
Fetched 348kB in 2s (146kB/s)   
Selecting previously deselected package gparted.
(Reading database ... 116838 files and directories currently installed.)
Unpacking gparted (from .../gparted_0.3.5-1ubuntu3_i386.deb) ...
Setting up gparted (0.3.5-1ubuntu3) ...


I read through this and I'm not entirely sure whether or not that changed it. guess the only way to check is to restart my computer. Well wish me luck.

---

### Post by bscbrit on 2008-11-07
The actions that you took simply installed the packaged 'gparted', which is  a program that allows you to modify the partitions on a hard drive.  It has not 'automatically' removed the Windows partition.  You will have to run the program (System->Administration->Partition Editor) to carry out the necessary changes.  Be careful, if you make a mistake using this program you could render the system unbootable and you might need to re-install Ubuntu again.

Whenever you run apt (or aptitude etc) it will check for old packages that are installed but no longer required.  While installing gparted it discovered that you have old linux-headers packages installed.  You can remove them by running the following command in a terminal:

sudo apt-get autoremove

However, you might find it easier to use Synaptic (System->Adminstration->Synaptic Package Manager) to manage all of your packages as it uses a GUI to make life a little more pleasant.

Finally, I hope that you enjoy Ubuntu as much as many millions of others have.

---

### Post by B34ST1Y on 2008-11-07
> **KillBoss92 said:**
> I'm guessing that was in Terminal.
The command worked and gave me this...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
Suggested packages:
  jfsutils ntfsprogs reiser4progs xfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 348kB of archives.
After this operation, 2150kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main gparted 0.3.5-1ubuntu3 [348kB]
Fetched 348kB in 2s (146kB/s)   
Selecting previously deselected package gparted.
(Reading database ... 116838 files and directories currently installed.)
Unpacking gparted (from .../gparted_0.3.5-1ubuntu3_i386.deb) ...
Setting up gparted (0.3.5-1ubuntu3) ...


I read through this and I'm not entirely sure whether or not that changed it. guess the only way to check is to restart my computer. Well wish me luck.

what you've just done, is use the package manager "apt-get" to "install" the program "gparted". 

"gparted" is a partition manager, and can be used to resize and manipulate your partitions on your disks. You should easily be able to open up a terminal, and type ```
sudo gparted
``` then enter in your password as prompted...it will open up "gparted" with administrative priviledges. If you've never used a basic partition manager before, you may want to check a wikipedia article about it. :)

---

### Post by KillBoss92 on 2008-11-07
Ahhh I see that it was just an install now...
Okay so should I just go and delete the part that I know is Windows? Or should I format it to /dev/sda3 which is as I know it the Ubuntu portion of my computer. Because as it stands the Windows portion is known as /dev/sda2 . Or is there another way I should go about it?

---

### Post by B34ST1Y on 2008-11-07
simply delete the windows partition, and if you so desire...extend the partition of your main ubuntu mounted drive.

---

### Post by bscbrit on 2008-11-07
Do not format it to the same as your existing Ubuntu partition!  That will destroy all of your Ubuntu OS.

Take things slowly. Unless you URGENTLY need the space being taken up by Windows, you needn't rush these steps.  An error could stop your system from booting.  Come back to discuss the task in more detail before you make any sudden actions so that you know exactly what each selection you make will do to your hard drive.

---

### Post by hyper_ch on 2008-11-07
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---


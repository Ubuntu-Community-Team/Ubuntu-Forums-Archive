---
title: "[SOLVED] How to install newer Ubuntu in existing partition?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by paker on 2008-10-02
When I installed 8.04, I did as recommended here, home directory in a separate partition. This would allow installing 8.10 over 8.04 without touching the home directory. Now 8.10 is about to come out and I still don't understand how to. When I install 8.10, it will have its own home directory. Will I not have 2 home directories?

Thanks.

---

### Post by markjensen on 2008-10-02
Well, one of the things that can be done is an in-place upgrade.   You don't need to download an 8.10 CD, burn it and boot from it to install.

The intention of a separate home allows you to install Fedora or such along side and share some of the same user "home" files (like photos or music you have saved there, or documents you have typed up for work or school).

---

### Post by Paqman on 2008-10-02
If you want to do a full reinstall, just run the LiveCD installer and choose "manual partitioning". Select your current root partition to be 8.10's root (and tell it to format), pick your current /home to be 8.10's /home but DO NOT format it. The installer should spot all your existing user accounts in your /home and import them into the new version. Simple as that!

---

### Post by bobnutfield on 2008-10-02
Intrepid's installer and partitioner is more intuitive than Hardy's.  As Paqman has indicated above, the partitioner will recognize your already existing /home partition.  Just basically leave it alone, and only format the / partition.  You can also leave your existing swap partition alone as well, as Intreid will recognize that too.

---

### Post by Georgia boy on 2008-10-02
Hi. Now you have got me to wondering also. When I installed the Hardy I had let the system install itself, was told that it was the easier thing to do. All I did was to measure between the Windows partition and the Ubuntu partition with the divider to make sure that each had plenty of room to play with. I didn't do a manual install. So, should it have installed a home by itself? 

Will I be able to do an upgrade without doing another Live CD again? 

Will the new 8.10 have more things in the reposotiers to look at and install than what we have here with Hardy? There are plenty of things that I haven't installed yet in Hardy due to not needing yet. 

Will the applications such as OpenOffice.org etc be updataed in the 8.10 or will that come in later as an automatic update?

Thanks 
Tom

---

### Post by bobnutfield on 2008-10-02
> Will I be able to do an upgrade without doing another Live CD again?

Yes, you will be offered the opportunity to upgrade when the stable release comes out.  Though, upgrading versus a fresh install is a subject for debate.  I have done both, and I prefer a fresh install.  The guided partitioner does not automatically create a separate /home partition.  That has to be created during the install, or beforehand with a partitioning program like Gparted.  If you decide to do a fresh install after backing up all of your files, you can add a separate /home parttion if you want to, making future fresh installs a little easier.

---

### Post by paker on 2008-10-02
> **Paqman said:**
> ........ Select your current root partition to be 8.10's root (and tell it to format), pick your current /home to be 8.10's /home but DO NOT format it. ..........Thanks. I forgot I had formatting option when I installed 8.04. 

As far as I am concerned, my question is answered and I will mark the thread [solved] later.  Hopefully, the other poster's question will get answered shortly.

---

### Post by Georgia boy on 2008-10-02
So, I will be able to do either an upgrade or a fresh install. How hard will it be to do a fresh install. I have a dual boot set up with Windows XP and 8.04 Hardy. As I said I had let it do the set up automatically and just did the slider bar for the space allowed for the two. 

Will it be hard to set up the /home  partition? The reason I went with the automatic installation was for the ease it provided. What's the difference from doing the fresh and the upgrade?

Thanks 
Tom

---

### Post by bobnutfield on 2008-10-02
You will find the partitioning tool while installing Intrepid pretty easy to follow.  Better than what Hardy had.  There are visual graphs of what your partitions look like the whole way.  When you do a fresh install, it is importand to know exactly where your Windows partition is so that you do not interfere with it.  It is always a good idea to load the Gparted Live cd to examine your partitions, or to prepare for a new installation.  An example is this:

sda1    Windows
sda2    Linux /   (where the operating system itself is installed, 10GB is enough)
sda3    /home     (your home partition where all of your files will live, I use 50GB)
sda4    swap      (usally about double your ram)

This is how I usually partition my disks and it allows me to reinstall the operating sytem and leave my /home partition intact with profiles and bookmarks stored.  Though it is always critical to do a backup of your important files before doing any reinstalling or partitioning.  Things can always go wrong.  Grub will also be reinstalled in a new installation.

---

### Post by Paqman on 2008-10-02
Two of your best friends for doing a reinstall:

[list]
[*] A separate /home partition. If you didn't create one last time you installed, have a read of Psychocats good article about [creating a separate home](http://www.psychocats.net/ubuntu/separatehome) on an existing system.
[*] The trick to [automatically reinstall all your packages](http://ubuntuforums.org/showthread.php?t=261366).
[/list]

If you decide to go for an upgrade instead of a reinstall, then disable any oddball repos before starting. Also, the more strange/self-compiled apps and tweaks on your system the less likely it is to upgrade smoothly. On a default system there's no reason why anything should break.

---

### Post by Georgia boy on 2008-10-03
Thanks guys! I've bookmarked this thread so that I can refer back to the information here. Thanks for letting me tag on to this thread. The original poster can go ahead and mark as solved. If I need any more information I'll look and post a new thread if I can't find what I'm looking for. Have a great day everyone!!!

Tom

---


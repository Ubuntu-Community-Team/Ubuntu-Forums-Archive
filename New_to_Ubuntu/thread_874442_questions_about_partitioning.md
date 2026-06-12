---
title: "questions about partitioning"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by johnlvs2run on 2008-07-29
I'm partitioning to run several distributions, for example ubuntu, mint, arch, and something else.

1)  Can all of these access the same thunderbird email and same chat programs, located in /home;

2)  Is it better to use one /home partition, or a /home partition for each distribution;

3)  How do you go from one distribution to another"

4)  What 4th distribution would you recommend, to help me learn more about the command line and Linux?

Thanks

---

### Post by gmoney on 2008-07-30
I can't answer all of your questions, but I'd like to help as much as I can, so here's my thoughts:

If you partition your drive, I recommend using gParted.  Sure, you can partition a drive while you're installing Linux, but gParted has a nice GUI that makes it easy to see what you're doing, and you can resize partitions easily.  I've used it a lot, and it's always done well for me.  You can either download gParted as an iso and run it as a live cd (which is what I do), or I believe you can just download it via apt-get or synaptic.  Honestly, it kind of makes me nervous to partition my drive while my primary OS is running, so that's why I use the live cd version of gParted.  

As far as question #3 goes:  If you have multiple operating systems on a partitioned drive, you select which OS you want at boot time with a tool called a boot loader.  Grub is the boot loader that is most commonly used these days.  For example, lets say you are installing Ubuntu on a system that already has XP, and you want to have both installed.  During the installation process, the Ubuntu installer will set up Grub.  Grub will then allow you to select which OS you want to load every time that you boot the PC.

Have you considered installing the additional distros as virtual machines?  If you use virtual machine software like VMWare or Virtual Box, you can run multiple distros at one time.  It's a great way to try out a new distribution...you don't have to reboot in order to switch up distributions.  This is what I would recommend, rather than partitioning the drive a bunch of times.  If you go this route, it's not necessary to re-partition your drive at all, which is always a plus.  

In regards to question #4, I've always heard of slackware as being the best distro to teach you how to really master the command line.  Of course, any disribution can teach you a lot about the command line.  Just hit CTRL+ALT+F1, and you're at a bash prompt (hit CTRL+ALT+F7 to get back to the gui).  Speaking of the command line, here's my personal favorite web site when it comes to learning about the Linux command line:  [http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)
Also, [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

I'm not sure the answers to question #1 or #2.  I'm sure it's possible to do what you're talking about in #1, but I don't know how one would go about doing that.  

I hope you find some of the above information helpful. Let me know if you have any questions about the stuff I was talking about.

Peace.

---

### Post by johnlvs2run on 2008-07-30
Hi gmoney,

Yes, I am using a gparted livecd for partitioning.

I am using only Linux distributions, not XP or any other MS.

I used to dual boot with XP, and was wondering if each Linux distribution requires the same type of a separate boot.

Thanks for your help.

---

### Post by hopelessone on 2008-07-30
well..

you can't use the same /home for other distro's...unless you want a few loopy things...

go with VirtualBox or your favorite VirtualOS and install them through there...clean, fast and easier than what you are doing...

i test out lots of other distros...and still have windows there...sniff...sniff..

hope that helps..

---

### Post by roquefilipe on 2008-07-30
In the past I had use the same firefox and thunderbird profiles in ubuntu and windows. Sure it gave me some problems because I was using it on FAT32 partition which doesn't deal with permissions, but I call the experience a sucess. So I believe that 1) will work.

I am a big fan of a separate parition for /home. But I don't use as many distros as you are going to. A friend said that this may backfire due to permissions. Example: different users in the different distros. Also if some of the distros use Gnome and others Kde, you should expect lots of hidden files. 

But I suggest virtualization as gmoney said.

---

### Post by johnlvs2run on 2008-07-30
What is a virtualos and what does that do?

Currently I'm using Ubuntu, but Mint seems to run a lot smoother.

My end objective is to use one distribution and run it from command line.

I don't mind dual booting, unless there's a more straightforward way.

---

### Post by roquefilipe on 2008-07-30
Virtualbox is a emulator to run other Operating systems. 

Is quite easy to use. Give it a try: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by Dr Small on 2008-07-30
Yes. Please go with VirtualBox and save yourself alot of partitioning headaches.

---

### Post by bodhi.zazen on 2008-07-30
IMO it is best to give each distro it's own /home and use a shared data partition.

You can usually share a /home partition, but there can be permission problems or conflicts with config ( . ) files in /home. If you share /home use a separate user name for each distro.

If you use a data partition, use links:

ln -s /mnt/data/music ~/music

and on.

---

### Post by vanadium on 2008-07-30
+1

---

### Post by johnlvs2run on 2008-07-30
> **bodhi.zazen said:**
> IMO it is best to give each distro it's own /home and use a shared data partition.

Thanks.  Mostly my concern is with email.  

I'm sticking with partitioning, not going the virtual route.

---

### Post by johnlvs2run on 2008-08-03
Here is the redone partitioning with gparted.  How does this look?

1- boot partition with ubuntu and files - 40gb
2- 1gb swap
3- extended
. 5 / distro 1 - 17gb
. 6 /home - 20gb
. 7 / distro 2
. 8 /home
. 9 / distro 3
. 10 /home
. 11 / distro 4
. 12 /home
4- /shared - 43gb

Can I move ubuntu and files to #5 and #6?
When I put mint in #7, will it know it's files are to go in #8?

---

### Post by louieb on 2008-08-03
> **johnlvs2run said:**
> 

Also, when I put mint in #7, will it know it's files are to go in #8?

No.  Unless you use the manual partitioning option during the install and tell it to mount #8 as home.

Good dual boot stuff here [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")  
Your going to want to go through the GRUB page. In particular do a find on **configfile** and look at the configfile and chainload options of GRUB. 

With that many distros installed on 1 PC it would be a good idea to use a deicated GRUB partition too. There information on that site about doing that.
Have fun, Good Luck.

---

### Post by Paqman on 2008-08-03
There's absolutely no problem with having one /home partition for several distros. As long as you set up separate users for each distro you'll be fine. I have my machine set up that way myself.

---

### Post by johnlvs2run on 2008-08-04
.

---

### Post by johnlvs2run on 2008-08-05
.

---


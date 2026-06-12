---
title: "I'm installing a new hard drive in my laptop."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Czarman on 2008-09-11
I'm installing a new hard drive in my laptop.  I want to reinstall XP Pro and add Ubuntu and SuSE Linux.  In which order should I install the programs?  Other people have suggested using Wubi or  [Gag]("http://gag.sourceforge.net/index.html")(The Graphical Boot Manager).  I'm new to Linux and need help in the best way to proceed.  

Thanks,
Czarman

---

### Post by ronnielsen1 on 2008-09-11
I can't tell you how to do the partition setup because you don't say how big the hard drive is. I would load the windows first (well personally I would give the windows about 5 megs space but that's just me) as windows doesn't like not to be first (1st partition on the hard drive, then load Suse on the 2nd partition system and finally ubuntu since it's the best at picking up other OS's and will setup grub

---

### Post by Czarman on 2008-09-12
Sorry!!  The new hard drive is a WD Scorpio EIDE 250 gb.

---

### Post by SunnyRabbiera on 2008-09-12
I would suggest installing XP first, then your other systems.

---

### Post by Bucky Ball on 2008-09-12
> **SunnyRabbiera said:**
> I would suggest installing XP first, then your other systems.

Totally agree with SunnyR. Any other way is doable but more trouble than it's worth and problematic.

---

### Post by Czarman on 2008-09-12
Thanks everyone for the help.  What software should I use to make the partitions?  Is there any advantage using a boot manager?  

Thanks Again,
Czarman

---

### Post by acidsolution on 2008-09-12
Well Czarman 
First of all install winxp and and use the first partition to do so. other wise if u install linux in first partition than winxp denies to install if it found unknown partition in first sector.
Winxp doesnot recognise the linux installation so it will replace the mbr entry of linux. 
So order of installation shuld be 
WINXP
LINUX ( any distros ) in any order :)



Ps- This is mine 100th Posts..

---

### Post by SunnyRabbiera on 2008-09-12
> **Czarman said:**
> Thanks everyone for the help.  What software should I use to make the partitions?  Is there any advantage using a boot manager?  

Thanks Again,
Czarman

well let XP handle the initial paritioning, and then use the live CD of ubuntu or suse to do the rest.

Both have partitioning tools, you may want to do initial partitioning with suse as its partitioning tool might be a little easier for a windows user but the ubuntu partition tool is just as easy in the long run.

---

### Post by tarps87 on 2008-09-12
As it is a "fresh" drive and there's no data to lose I would partition it with each OS as you install them.
1. In XP I think you press c at the partition screen (it will tell you at the bottom of the screen) to create a partion you can then enter the size you want it to be in MB's then follow the install through.
2. SuSE will need a / (root) partition, a swap partition is optional but I would recommended having one, when you ram is full this will be used to store data not being used at the time (paging), also if you want to hibernate you will need one that is at least 1 1/2 times the size of your ram.(2GB of ram 3GB swap)
3. For Ubuntu you will need a separate / partition but you can use the same swap partition as SuSE.

As for a boot manager its up to you, I am using the normal bootloader which is relatively easy to edit and easy to use. If you need help editing or just understanding the bootloader there will be plenty of people here willing to help.

---

### Post by Kinetic_lord on 2008-09-12
enfortunately i did something really wrong, i wanted to install windows XP on my flash. after copying the setup files, a blue screen appeard (yeah... of course... Xp right?) and i couldn't boot into linux again, at booting:"Windows cannot find the os files or something like that... anyway i had to install ubuntu, but at the boot loader i must choose between 3 versions of ubuntu and windows XP... even if i unpluged the flash. stupid Xp has let some traces on my second 160Gb drive. what can i do to get it out of the boot manager?

---

### Post by Bucky Ball on 2008-09-12
All sounds awful complicated.

What I normally do is ...
1/ In the Windoze installer, wipe the drive so no partitions, then make one for Windoze the size I want. Install Windoze.
2/ Run the Ubuntu installer and use 'Manual Partitioning' which you will get to as you go through the install. In there, partition for Ubuntu, Swap twice the size of the RAM and whatever other partitions are required. I usually plop on a FAT32 partition for sharing files between OSs (there are tweaks and software for other file formats but this is my preference).

Before any of this, I get a cup of tea, a piece of paper and a pen, and work out the partitions I am going to need and where they are going to live.

'Bout as simple as that, but everyone has their preferences and I am by no means saying any of the instructions in other posts on this page are in any way inferior, so right here, please don't any of you good people get me wrong. This just suits me and as always, willing to be educated if anyone has suggestions.  :)

Main thing is, unless you want to do some tweaking and screwing around, get Windoze on that first  partition and create the other partitions during the Ubuntu install. You have a little more control that way as the Windoze installer sometimes can appear to have a mind of its own (one which I could no longer be bothered psychoanalyzing unless vital). 

If I have both OSs installed and want to delete or create partitions, I use the partition editor Gparted which you can install by through Synaptics or open a terminal and type:

**sudo apt-get install gparted**

Then:

**sudo gparted**

... to run it. Should then be listed under System->Administration-> as Partition Editor.

Good luck however you choose to go and don't hesitate to post in case of ... ](*,)

---

### Post by tarps87 on 2008-09-12
> **Bucky Ball said:**
> Before any of this, I get a cup of tea, a piece of paper and a pen, and work out the partitions I am going to need and where they are going to live.


What it they don't like tea :)

As long as windows is the first on really you can do what you want with the rest, but if you do need to reinstall windows at any time your other partitions will be safe (unless you tell it to format them) but you will need a boot fix cd to repair the MBR (boot bit of the hard drive). Hopefully someone can suggest an easy to use one, as I have windows on a slave drive and reinstall by a bit of swapping, so have not used them

---

### Post by Bucky Ball on 2008-09-12
[quote=tarps87]What it they don't like tea :smile:[/quote]

Haha. Green tea, at that! Scotch, coffee, beer ... your preference. Cheers! :)

---


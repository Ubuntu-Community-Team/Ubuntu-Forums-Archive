---
title: "how to setup dual boot in ubuntu 8.04?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by jrecortel on 2008-10-06
hello. i have a compaq presario v3901tu.it comes with windows vista.i want to dual boot it with ubuntu 8.04.1.the problem is the laptop just comes with a emergency repair disk and i cant edit the partions on the hard drive using the disk.my question is how can i make a new partition in the hard disk so that i will have separate file system for window and ubuntu without destroying the windows partition and retain the windows os.any help is greatly appreciated.thanks in advance.

---

### Post by Zzl1xndd on 2008-10-06
The Ubuntu installer has a program called Gparted that is able to do this. When you install it will give you an option to resize your partitions.

---

### Post by jrecortel on 2008-10-06
thank you tweakedenigma for the immediated reply.:)
will resizing using gparted won't destroy the windows os?

---

### Post by Zzl1xndd on 2008-10-06
It will not destroy your Windows partition. Gparted is much like Norton Partition Magic. Although I still suggest backing up anything important as you are messing with your hard drive.

---

### Post by jrecortel on 2008-10-06
thanks a lot.:)

---

### Post by jerome1232 on 2008-10-06
If your really worried about screwing the partitions I would recommend wubi, You install Ubuntu from within windows and it creates a virtual drive, basically a file on you existing windows that ubuntu treats as a real disk. No partition, no boot loaders get install (It does modify the windows boot loader to add itself) and you can uinstall it just like any windows program.

The only draw backs are you will get reduce performance with disk access while in Ubuntu, and you won't be able to hibernate from within Ubuntu.

---

### Post by jrecortel on 2008-10-08
sorry for not replying sooner since i have a problem wiht my inet connection.
using wubi, can i have the benefit of linux filesystem ext3?what i want to do is to have a separate filesystem for each os.since my computer comes with vista,it uses all the hard disk for its filesystem.as tweakedenigma said about how gparted wont destroy my windows partition, will i still able to boot to windows after adjusting the partition with gparted?
thanks to tweakedenigma and jerome1232 for their informative reply.

---

### Post by pi.boy.travis on 2008-10-08
I would recommend against Wubi, unless you are just "trying out" Ubuntu, and want something more usable than the live CD.  I have never been able to get it to work on any of my machines.

You are better off in the long run installing Ubuntu on a dedicated partition.

---

### Post by jerome1232 on 2008-10-08
> **pi.boy.travis said:**
> I would recommend against Wubi, unless you are just "trying out" Ubuntu, and want something more usable than the live CD.  I have never been able to get it to work on any of my machines.

You are better off in the long run installing Ubuntu on a dedicated partition.
It's never given me problems, as always ymmv, I think it's nice for those afraid of partitioning though.

> **jrecortel said:**
> sorry for not replying sooner since i have a problem wiht my inet connection.
using wubi, can i have the benefit of linux filesystem ext3?what i want to do is to have a separate filesystem for each os.since my computer comes with vista,it uses all the hard disk for its filesystem.as tweakedenigma said about how gparted wont destroy my windows partition, will i still able to boot to windows after adjusting the partition with gparted?
thanks to tweakedenigma and jerome1232 for their informative reply.

In that case then I would recomend doing a normal install as well, it was just a suggestion if you don't feel up to partitioning.

Yes after shrinking the vista partition you can still boot into windows. It might decide to run chkdsk on itself after you resize.

During the install of Ubuntu it actually has an option that will shrink vista for you, install Ubuntu to the freed up space, and configure your machine to give you the option on start-up of which os you would like to boot to.

---

### Post by Zimmer on 2008-10-08
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

I think this is the tutorial I used as a basis for dual booting.
I certainly recommend EasyBCD.

I did plenty of other reading before setting out to do it.

But Vista was still reluctant to give up drive space. Despite all the tips about turning off page files and recovery it still kept 70 gig of the 160 gig HDD to itself . I used Vista's own partitioning software BTW to shrink the Vista partition, seemed the safest thing to do to preserve the installation.
I did manual partitioning when installing Ubuntu to preserve the extra Vista recovery partition. 
I may remove that sometime in the future, but this is a brand new laptop.... (and I keep hearing the words 'just in case..' in my head...).
EDIT!
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
will help too

---

### Post by jrecortel on 2008-10-08
thanks again to the great people who responded to my questions:)
in ubuntu install, it gave me an option to shrink my vista partition.but i would like to give more space for my vista partition,something like 50% of hard drive for vista and the other 50% for ubuntu.the other options are to use the entire disk which obviously will delete my vista os and the other is the manual adjustment.how can i make the 50-50 partition?

---

### Post by jrecortel on 2008-10-08
btw, when i boot my laptop, my c: partition uses about 150 gb and d: partion uses about 10 gb.what will happen with my d: partition after using gparted?

---

### Post by jerome1232 on 2008-10-08
> **jrecortel said:**
> btw, when i boot my laptop, my c: partition uses about 150 gb and d: partion uses about 10 gb.what will happen with my d: partition after using gparted?

nothing as long as you don't format it. Just resize the bigger partition (under linux it will be /dev/sda1).The other partition is probably the 'recovery partition' that is so popular with pc manufacturers today.

---

### Post by Sef on 2008-10-08
1) Shrink the Vista partition with its own partitioner, not GParted.

2) Read [Psychocats Ubuntu]("http://psychocats.net/ubuntu") for how to install a dual boot.

---

### Post by jrecortel on 2008-10-08
thank you jerome1232.:)
how can i partition my hard drive to use 50% of it capacity for vista and the other 50% for ubuntu?

---

### Post by Papa-san on 2008-10-08
The best way to do what you want is to go into Vista and use it's utility to 'shrink' the hd space it allocates for itself... The gparted method (and the others suggested) worked well with winxp, but Vista is quite different. I have heard of many people who have experienced nightmares because they didn't do this... If you use a *nix application to do it, windows Vista is going to be expecting to find 150 gb of space to use, and won't know how to handle finding only 75 gb... 

Trust me... you want to do the windoze re-size first!!!

EDIT:

I would also strongly suggest that when you set up the Ubuntu partitions, that you set up a separate /home partition. You should be able to find step by step instructions, but when you do this, all of your personal data doesn't get wiped out when the inevitable Ubuntu re-install has to happen... It will only affect your 'root' (/)partition... I learned this the hard way!

(Sef... Can I be a Skinny Soy Caramel Haunter?!? Pleeze lol )

---

### Post by jrecortel on 2008-10-08
thank to Sef and Papa-san.:)
but when i tried to shrink the vista partition, i can only recover about 50gb of space. what i want is to have about 80gb for vista and 80gb for ubuntu.gparted looks easy to use but cant be used for vista without running into problems as you said.any help how can i have the desired space allocation for each os?thank in advance.

---

### Post by Papa-san on 2008-10-08
you need to 'clean up' your current Vista partition to make more space available. That's what is stopping it from moving as far as you want it to. Also, it would be a good idea to see what is on that 10 gb partition and see if it can be reformatted...

---

### Post by jrecortel on 2008-10-08
the D: drive contains the recovery partion which i dont like to delete.my C: drive uses only about 40gb out of 140gb.but using the disk management in vista, it informs me that after shrinking, i will only recover some 40+gb.what is the easiest way so that i can have an equal amount of available hard disk space for each filesystem?

---

### Post by Papa-san on 2008-10-08
Vista will only allow you to make empty space available for re-partitioning... I'm not sure how it was configured, but Vista seems to think you only have 40 gb of space available... It has something on the rest... (See why gparted would have been a problem?) :-)

Look at the links Sef gave you. the psychocats site will have most of the information you need for this. Also, see if you can determine what Vista thinks it has all over your hard drive and see if you can move it...

---

### Post by jrecortel on 2008-10-08
yes, i look at the links.but it only show the partitioning tool of ubuntu during install.also it uses xp instead of vista.so am i stuck to using only 40gb of hard disk space for ubuntu?

---

### Post by drowner on 2008-10-08
I've not used Vista, but do you need to defragment it? Try that, if it exists.

---

### Post by Papa-san on 2008-10-09
Sorry... gotta sleep sometime...

Look through the programs you have, and see if there are any you can get rid of. If you have a spyware scanner, use it. (I'd suggest using adaware AND spybot search and destroy.) Then do a clean-up. Get rid of EVERYTHING you don't need. Games and video files are HUGE. Then do a defrag. It will help greatly. (Ubuntu doesn't need to do this because of the architecture of the nautilus filesystem it uses... Very space efficient.)

Do a search on shrinking a vista partition and find out what you can do to optimize it.  Get all the space you can, and then use that for Ubuntu. (In actuality, 40gigs is really pretty sufficient for an Ubuntu install, so don't let that stop you. I ran XP and Ubuntu side by side on a 20 gig HD for a couple of years...

Then, during your install set up 3 partitions: one for / (root), one for swap (Which, I've heard, needs to be of a size twice the size of however much memory you have.), and one for /home (This is where your personal stuff gets stored.)

---

### Post by pi.boy.travis on 2008-10-09
> **jrecortel said:**
> yes, i look at the links.but it only show the partitioning tool of ubuntu during install.also it uses xp instead of vista.so am i stuck to using only 40gb of hard disk space for ubuntu?

40GB is plenty for Ubuntu.  Remember that you can mount your Vista partitions form within Ubuntu.

---

### Post by Papa-san on 2008-10-11
And keep us posted!
:-)

---


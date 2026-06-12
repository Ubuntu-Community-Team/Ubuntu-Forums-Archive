---
title: "installing ubuntu 8.10 - guided partitioning"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by hanmul on 2008-10-30
Hello?

I'm new to ubuntu. Well, I used it for a month now, and trying to use the newly released one(8.10).

-What's on my system-
I'm using Windows Vista and XP in same hard drive with seperate partition. (c: and D: )

-What I know-
When I installed ubuntu 8.04, it allowed me to install it where I left free space for it. (20 GB of unpartitioned space)

-What I'm trying to do-
I have 29.99GB unpartitioned space left in my hard drive where I want ubuntu to fit in. However, during installation of Ubuntu 8.10, when I choose the option #3, 'Guide - Let ubuntu use largest free space available'(I can't remember the exact name), the graph on the top shows that ubuntu is going to take over my whole hard drive.
(it shows 100% ubuntu with all blue color block just like the 2nd option)

-My 1st question-
Is there an error with the graph or is it really going to take all my hard drive just for ubuntu 8.10 which 8.04 didn't act in the same way?

-What I found-
I ignored the blue bar and continued to step 7.
Interestingly, when I read the listing of what will happen, it shows that partition #6 and #7 will be created in sda(0,0,0).

-My 2nd question-
Is that mean ubuntu 8.10 is not going to wipe out my Windows Vista & XP and just install in the left over space?



-My mistake-
I shoud've post this under 'Installation & Upgrades' forum.
Sorry about that, but I don't want to cross post it again.

---

### Post by cariboo on 2008-10-30
Are trying to do a quadurple boot, or do you just want to install Intrepid over Hardy? If you want to install over Hardy, use the manual partitioning optipn and select the partitions that hardy is aready installed on. You will manually have to set / by right clicking on the partition and selecting edit. This will allow you to set file system type as well as telling the program to format the partition. Make sure everything is coorect before clicking the apply button.

Jim

---

### Post by hanmul on 2008-10-30
I removed ubuntu 8.04 to do fresh installation for ubuntu 8.10.


I got around with this problem with merging unpartitioned space to my D: drive and let ubuntu 8.10 take it (30 GB) from there.

However, I would still like to know the answer for my 1st question.

---

### Post by cgunther on 2008-10-31
I would like to know the answer to your first question as well.  I have a 500G drive with 400G for XP, I left 100G for Ubuntu.  Now I'm ready to install Ubuntu and the first partitioning option (Guided-resize) wants to resize my DOS partion - no thanks, I already planned ahead.  The second option (Guided-use entire disk) is not an option for me.  The third option (Guided-use largest continuous free space) sounds correct, but as stated earlier, the "After" graphic shows Ubuntu taking 100% of the disk, which is the same as the second option.

I'm hoping this is just a mistake in the graphical representation, but I don't dare go forward...

---

### Post by jasper28 on 2008-11-01
The same thing happened to me as well.  Ubuntu shows 100% in the graph when I select largest continuous free space.  This has obviously kept me from installing it on my computer.  I think this is just a graphical error in 8.10 but I'm not sure.  It's very likely since I think this is the first release with a graph.  Please, someone who knows more about this than I do reply!  Perhaps try installing a previous version and upgrading until someone can get this fixed (or give assurance that it will not wipe anyone's hard drive).

---

### Post by redbob on 2008-11-01
Miles ahead the best option to partition Ubuntu is Manual partition:
20gb for /root
20gb for /home
 1gb for swap
the rest for /opt

So you will not disturb up your Windows Partition. Go ahead!!!

---

### Post by Jake210 on 2008-11-09
> **jasper28 said:**
> The same thing happened to me as well.  Ubuntu shows 100% in the graph when I select largest continuous free space.  This has obviously kept me from installing it on my computer.  I think this is just a graphical error in 8.10 but I'm not sure.  It's very likely since I think this is the first release with a graph.

Same here -- I encountered the same situation. I was installing Ubuntu 8.10 on a second partition and was reluctant to select the "largest continuous free space" option because the graph showed Ubuntu using 100% of the hard drive, but I went ahead and selected that option hoping the blue graph was in error.

Luckily, it turns out the blue graph depicting Ubuntu using the whole hard drive under the continuous free space option *was* wrong.

The first partition was kept intact, and Ubuntu installed on the second partition without a problem. I checked the partitions with Gparted Live and everything was fine; all the partitions were setup the way I wanted them to be. 

An extended partition was created on the HDD's free space with a swap partition the size of the installed RAM inside that extended partition.

This is my first post. I was searching for the same info others on this thread were searching for as well, so I decided to post what I found out in case anyone else had reservations about choosing that option.

I've learned a lot from lurking on these boards and felt I should reciprocate somehow.

---

### Post by domu on 2008-11-10
Thanks Jake210, I too just encountered this install bug using ubuntu-8.10-desktop-i386, and found your advice very helpful. I was not brave enough to go ahead with "largest continuous free space" option because my existing partition was irreplaceable and as you rightly say, the installer shows that it is going to wipe it.

However I followed your suggestions for manual partitioning, first creating a logical swap partition equal to ram size (768M in my case) at the end of the free space and then creating an EXT3 filesystem, mounted at /, for the rest of the free space. It worked!

---

### Post by Jake210 on 2008-11-10
Awesome, glad to hear domu.

It actually took me twice to adjust the partitions correctly. The first time around I manually created the partitions for Ubuntu using Gparted Live, but after logging on after resetting, the screen froze up. (It turned out to be my old chipset wasn't compatible with Compiz, so I had to unistall compiz through the command line interface). 

But before I unistalled Compiz I had booted up with Gparted and wiped out the Ubuntu partitions. So the free space wasn't formated for ext3 or swap; the unallocated HDD space was just unused at that point -- unformatted.

Then when I installed Ubuntu again, I used the continuous free space option and Ubuntu automatically created the partitions -- the main Ubuntu partition with the swap partition/space, both inside the extended.

That's cool you were able to use the manual option to get it done though. Later on I plan on experimenting with different partitioning schemes with some of the ideas the previous posters on this thread had. 

:)

---

### Post by harry01 on 2008-11-10
Hey Everybody,  I had the same basic problem as all above. Ubuntu 8.10 was screwy with the partitioning, just wouldn't work. I switched to Xubuntu and the partitioning worked great, a piece of cake. I found out Xubuntu was the one for me, it supported all my hardware and I love it. All my printers work and the gamma works on my ATI radeon 9250 card which did not work with Ubuntu. Try all versions of Ubuntu and maybe you will hit the jackpot like i did with the Xfce version.

---

### Post by bumanie on 2008-11-10
To avoid anything going wrong at the partitioning stage, it is always best to choose to manual at the partitioning stage. You have complete control over the partitioner that way. It's also handy if want to setup a separate /home.

---

### Post by Jake210 on 2008-11-11
Xubuntu looks pretty good -- light on resources -- especially good for older systems. I might install it on an old PC I'm working on for someone else. 

Just to clarify -- if you select the continuous free space option, you don't have to worry about it overwriting your entire hard drive with Ubuntu; and you don't have to manually configure a swap and ext3 partition.

If you manually create a swap partition (using Gparted or other 3rd party partition editor) and then select the continuous free space option, then you'll have two swap spaces instead of just one. That's what I found out.

If you want a simple partition scheme (just an ext3 and swap) then just defragment your first OS (Windows) then use GParted or PartedMagic or whatever partition editor that works for you, and allocate enough space for a second partition -- don't worry about formatting the partitions to ext3 or swap.

Then install Ubuntu and select the continuous free space option. Ubuntu will not touch your first partition and will automatically create an ext3 and a swap partition for you.

That's what I learned atleast, after installing Ubuntu on an old Dell OptiPlex GX100. But of course if you want a more sophisticated partitioning scheme with  /home, /var, etc partitions then you'll have to manually create those partitions -- as opposed to using the continuous free space option in the Ubuntu installer.

---

### Post by codewrighter on 2009-01-05
FYI - Careful with the manual option - Using the manual partioning option, alloting 4gb for swap, 100gb for / (ext3), etc, created the partitions, but still installed ubuntu over my vista install (luckily it was a new install too...no data loss...would have backed up prior if it had data anyway). This is the first release to suffer this issue. Unfortunately, when manually partitioning, you cannot specify to which partition(s) to install (at least with the config I went into it with...a single hd and vista in the primary). So for those of you who do not want to wipe anything, option 3 is the way to go (it will use the free space).

---


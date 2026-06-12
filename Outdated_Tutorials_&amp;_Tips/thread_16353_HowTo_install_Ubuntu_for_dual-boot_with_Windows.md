---
title: "HowTo: install Ubuntu for dual-boot with Windows"
date: 2005-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Ozitraveller on 2005-02-20
Installation Help

How do you easily install Ubuntu for dual-boot with Windows? 
[http://www.ubuntuforums.org/showthread.php?t=16287&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=16287&page=1&pp=10)

Some usefull stuff here, worth adding to the Start Guide?

---

### Post by machiner on 2005-02-21
I tried to neaten-it-up:
----------------------------------------------------------------------
Please read through once before attempting. Print if necessary.

If you're like most people, you probably purchased your computer from a large retailler. This has pro's and con's but for the purposes of this tutorial we will be concerned with the modifying your current setup.

Firstly, you might want to be a little familiar with the hardware comprising your computer. We will be discussing Hard Drives (hdd, HDD, harddrive).

Your hdd is the device that stores your software - your Operating System and everything associated. Please see the following page for images:
[http://images.google.com/images?q=hard%20drive%20pictures&hl=en&lr=&client=firefox&rls=org.mozilla:en-US:unofficial&sa=N&tab=wi](http://images.google.com/images?q=hard%20drive%20pictures&hl=en&lr=&client=firefox&rls=org.mozilla:en-US:unofficial&sa=N&tab=wi)

For the purposes of installing anything on your harddrive, file systems and partitions need to be created. As well, for the purposes of this tutorial only basic information necessary to complete the task is provided.

A partition is simply an organizational structure. Picture your home - the hdd. Now, in your home there are rooms, your partitions. It's that easy.

On your existing hdd is one large partition ( get into it: [http://www.google.com/search?hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=what+are+hard+drive+partitions&btnG=Search](http://www.google.com/search?hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=what+are+hard+drive+partitions&btnG=Search) )that the manufacturer of your computer has created to install the operating system and ancillary programs.

Your computer can be better utilized by re-partitioning your (no doubt giant - 60-200 GB) hdd. This can be accomplished in such a way that you keep your current installation of Windows intact and useable following this tutorial.

For the purposes of this tutorial it is necessary for you to goto: [http://www.sysresccd.org/download.en.php](http://www.sysresccd.org/download.en.php)  and download, then burn, this disc. You will be booting to this disc to accomplish this task.

----------

If necessary - back up whatever it is that you would NOT LIKE TO LOSE. YMMV, I have never lost data this way but a prudent person has a backup. As well, I have used and recommend the program: NTFSResizer. It is a small program you put on a floppy and boot to in order to resize your NTFS partition(s). You might consider using this method to resize your current Windows XP (NTFS) partition instead of booting to the systemrescue disc. I like the systemrescue disc because there are other very useful utilities on it. Either way you're good.

This tutorial assumes you have a comfort level running programs. I assume you will be able to navigate graphical programs to complete this task.

----------------end long-winded intro--------------


Insert the SystemRescue Disc into your cd-rom (your master, if applicable). Reboot your machine to the cd-rom drive (if necessary you will need to change a BIOS setting to allow this. Google it.)

You will be greeted with a prompt shortly, at this point type:  menu,  hit enter. 
At the next prompt:  arrow right, then down to select Rescue.  Hit enter.

Let it boot. 

At the next prompt, when it's finished booting, type: run_qtparted,   hit enter.
At the next prompt, choose your mouse. For a ps/2, just type: 3, hit enter.

When QTParted opens you will see that it's a familiar looking application. It's sectioned. On the left, in the column at the top you will see your hdd's. It probably reads: hda.

If you would please, click on that hda. Now, to your right in the other column you will see your partitions. You probably see only 1, and it occupies all of the space on your hdd. We can resize, or delete this partition. NOTE: this partition has your Windows installation on it, so if you are keeping that, we are RESIZING now.

If you would, please click on your partition; either the large "bar" image over the right column, or your partition in the right column. I think you can right click and choose "resize". If no, then click the partition and look up in the menu for the option to resize. Choose resize.

You will be greeted with a window with another "bar" image representing your large partition. You will see that it has "handlers" on either end. Grab the right-side one with your mouse and drag it left. Keep it to 2GB**. You just resized it. Hit OK or whatever it says (I am writing this from memory).

Now, in your menu - find the option to "commit" and choose it. Don't let the warning messages scare you - it's your hdd and you're in charge.

Now, you will see that the rectangle image representing your hdd has changed. You will see inside the rectangle now a small partition on the left side. Now you may click on the whole rectangle and right-click and choose "create". In this way you may create more partitions. Keep this in mind:  You may only have 4 "Primary" partitions on your hdd. However, you may make many "Logical" partitions. In this tutorial we make 3 other partitions. They are all Primary.

To keep things simple we'll use the following architecture (40GB hdd): 

hda1: winXP, C:\, NTFS, 2GB** (set ACTIVE, if not already)
hda2: linux, /, ext3, 10GB
hda3: linux, /home, ext3, 27.75GB
hda4: linux, swap, 250mb

Arbitrary partition sizes. For swap (if even necessary. Have 1GB RAM? Then no swap - you'll never need/use it.) I usually create a partition equaling about 1/2 my RAM. 

** Sizing up your partitions is really subjective. I have no idea how many programs you have installed or the real size of your current partition use. You may need 5 or even 10GB for your current windows installation. I don't know, you do. Change sizes to reflect your needs.

-------------
This tutorial does NOT address backing up your newly resized, existing windows partition. I will write another one for that purpose. Prudent folk have backups.
-------------

Close the QTParted program. You are now back at that prompt. You may now type: reboot, hit enter.  You will reboot, during reboot - quickly, replace the SystemRescue Disc with your Ubuntu Installation Disc.

You will be greeted with An Ubuntu Logo install routine, just hit enter to begin the installation. Soon enough into the installation a Partition Manager will open in order to tell the installation routine where to install Ubuntu and your other directories (/Home, et al.)

You just made your new partitions so during this phase of the install, you wouldn't want to allow the installer to wipe your drive. You'll want to be in command of your partitions, so pay attention to the prompts during install. At the Partition Manager you want to manually effect your drive.

"Manually partition your hdd" (it reads something to that effect) is one of the choices you will be prompted with in the Partition Manager.  Choose it.  Be careful you don't select to format entire drive, or similar - You will see what I mean, use your arrow keys to select to Manually edit your harddrive.

Next screen appears with your hdd partitions; use your arrow keys and enter to select and modify:  

****  You have an opportunity here to resize your partitions; by deleting and re-creating.  Some people like to manage their partitions with the install routine of a linux distro. More power to 'em. I like to use other options. So at this point you might decide to change your partition scheme, or resize, or whatever.  I'm not saying do it, I'm just letting you know that you could. ****

On your first partition, ( hda1), the Windows one we just saved, choose to not use it,  (you may mount it later if you like).  Arrow right down to hda2. Choose to use this - you will see, use your enter key to make selections here.

hda2 will be your "/" directory . You should let the install routine reformat your partitions...it only takes a second. Choose to use this partition, choose ext-3 file system, / mount point, and then arrow down to Done. 

hda3 is your /home directory. Repeat steps for hda2, labeling it /home.

we made hda4 swap. It's ok to ignore this, it's found already. When you have finished, arrow down to the bottom of the page and choose Done - or the like.

Next screen, Yes to allow the changes -  then continue with your install.

Finally, you will be prompted to allow Grub to be installed. Grub has seen your Windows partition/installation already - it is safe. Allow Grub to be installed, where it wants, and you will be good-to-go.

Your machine will reboot shortly. At this reboot it is necessary to go into your bios and choose to Boot to HDD-0. Please see another tutorial for this purpose. It's easy, don't fear this.

Leaving your BIOS, your machine will reboot and in about 2 screens you will see GRUB at the bottom of your screen - hit the ESC key. Do you see that? It is listing your new Ubuntu installation as a choice to boot to, and it is also listing - at the bottom - your Windows installation as a choice as well.

Choose Ubuntu. You did it. 
---------------------------
I need a mighty DISCLAIMER right about now. I'm not at all experienced writing tutorials. My writing style, and the horrible edits,  will probably leave folks confused, sorry. I hope this helps some folks that would normally be scared to attempt this. Sure, it's an intermediate (?) level task, I suppose, and things CAN and just MIGHT go wrong. Sure, there are any number of ways to accomplish this, as well. The one I mention I employ frequently and with good results, as I said, I have never lost data - but I have had to perform rescues of a more advanced sort. I don't know the condition of your hdd or your panic level. 

It's just a hdd, and it's a routine task to partition it. Even resizing is common - and hey, give NTFSResizer a go. It really is good (and free - or was a few years ago when I found it), and you can still make new partitions when you are installing Ubuntu, with the Ubuntu installer's Partition Manager.
--------------------------
Happy Computing

Any mod might think this or the other thread to be redundant now.  Feel free to delete at will.  As well - this tutorial (Oop, Ack!) screams for an editor!

---

### Post by Ozitraveller on 2005-02-21
[QUOTE=machiner]I tried to neaten-it-up:
----------------------------------------------------------------------
Please read through once before attempting. Print if necessary.

If you're like most people, you probably purchased your computer from a large retailler. This has pro's and con's but for the purposes of this tutorial we will be concerned with the modifying your current setup.

Firstly, you might want to be a little familiar with the hardware comprising your computer. We will be discussing Hard Drives (hdd, HDD, harddrive).

Your hdd is the device that stores your software - your Operating System and everything associated. Please see the following page for images:
[http://images.google.com/images?q=hard%20drive%20pictures&hl=en&lr=&client=firefox&rls=org.mozilla:en-US:unofficial&sa=N&tab=wi](http://images.google.com/images?q=hard%20drive%20pictures&hl=en&lr=&client=firefox&rls=org.mozilla:en-US:unofficial&sa=N&tab=wi)

For the purposes of installing anything on your harddrive, file systems and partitions need to be created. As well, for the purposes of this tutorial only basic information necessary to complete the task is provided.

A partition is simply an organizational structure. Picture your home - the hdd. Now, in your home there are rooms, your partitions. It's that easy.

On your existing hdd is one large partition ( get into it: [http://www.google.com/search?hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=what+are+hard+drive+partitions&btnG=Search](http://www.google.com/search?hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=what+are+hard+drive+partitions&btnG=Search) )that the manufacturer of your computer has created to install the operating system and ancillary programs.

Your computer can be better utilized by re-partitioning your (no doubt giant - 60-200 GB) hdd. This can be accomplished in such a way that you keep your current installation of Windows intact and useable following this tutorial.

For the purposes of this tutorial it is necessary for you to goto: [http://www.sysresccd.org/download.en.php](http://www.sysresccd.org/download.en.php)  and download, then burn, this disc. You will be booting to this disc to accomplish this task.

----------

If necessary - back up whatever it is that you would NOT LIKE TO LOSE. YMMV, I have never lost data this way but a prudent person has a backup. As well, I have used and recommend the program: NTFSResizer. It is a small program you put on a floppy and boot to in order to resize your NTFS partition(s). You might consider using this method to resize your current Windows XP (NTFS) partition instead of booting to our systemrescue disc. I like the systemrescue disc because there are other very useful utilities on it. Either way you're good.

This tutorial assumes you have a comfort level running programs. I assume you will be able to navigate graphical programs to complete this task.

----------------end long-winded intro--------------


Insert the SystemRescue Disc into your cd-rom (your master, if applicable). Reboot your machine to the cd-rom drive (if necessary you will need to change a BIOS setting to allow this. Google it.)

You will be greeted with a prompt shortly, at this point type:  menu,  hit enter. 
At the next prompt:  arrow right, then down to select Rescue.  Hit enter.

Let it boot. 

At the next prompt, when it's finished booting, type: run_qtparted,   hit enter.
At the next prompt, choose your mouse. For a ps/2, just type: 3, hit enter.

When QTParted opens you will see that it's a familiar looking application. It's sectioned. On the left, in the column at the top you will see your hdd's. It probably reads: hda.

If you would please, click on that hda. Now, to your right in the other column you will see your partitions. You probably see only 1, and it occupies all of the space on your hdd. We can resize, or delete this partition. NOTE: this partition has your Windows installation on it, so if you are keeping that, we are RESIZING now.

If you would, please click on your partition; either the large "bar" image over the right column, or your partition in the right column. I think you can right click and choose "resize". If no, then click the partition and look up in the menu for the option to resize. Choose resize.

You will be greeted with a window with another "bar" image representing your large partition. You will see that it has "handlers" on either end. Grab the right-side one with your mouse and drag it left. Keep it to 2GB**. You just resized it. Hit OK or whatever it says (I am writing this from memory).

Now, in your menu - find the option to "commit" and choose it. Don't let the warning messages scare you - it's your hdd and you're in charge.

Now, you will see that the rectangle image representing your hdd has changed. You will see inside the rectangle now a small partition on the left side. Now you may click on the whole rectangle and right-click and choose "create". In this way you may create more partitions. Keep this in mind:  You may only have 4 "Primary" partitions on your hdd. However, you may make many "Logical" partitions. In this tutorial we make 3 other partitions. They are all Primary.

To keep things simple we'll use the following architecture (40GB hdd): 

hda1: winXP, C:\, NTFS, 2GB** (set ACTIVE, if not already)
hda2: linux, /, ext3, 10GB
hda3: linux, /home, ext3, 27.5GB
hda4: linux, swap, 500mb

Arbitrary partition sizes. For swap (if even necessary. Have 1GB RAM? Then no swap - you'll never need/use it.) ** Sizing up your partitions is really subjective. I have no idea how many programs you have installed or the real size of your current partition use. You may need 5 or even 10GB for your current windows installation. I don't know, you do. Change sizes to reflect your needs.

-------------
This tutorial does NOT address backing up your newly resized, existing windows partition. I will write another one for that purpose. Prudent folk have backups.
-------------

Close the QTParted program. You are now back at that prompt. You may now type: reboot, hit enter.  You will reboot, during reboot - quickly, replace the SystemRescue Disc with your Ubuntu Installation Disc.

You will be greeted with An Ubuntu Logo install routine, just hit enter to begin the installation. Soon enough into the installation a Partition Manager will open in order to tell the installation routine where to install Ubuntu and your other directories (/Home, et al.)

You just made your new partitions so during this phase of the install, you will choose to:

"Manually partition your hdd" (it reads something to that effect.) Be careful you don't select to Format entire drive, or similar - You will see what I mean, use your arrow keys to select to Manually edit your harddrive.

A screen will appear with your hdd partitions, using your arrow keys to select and modify:

On your first partition, the Windows one we just saved, choose to use it, Keep existing files (NO FORMAT) , etc, etc.
Next, going through your partitions, choose hda2 and choose to use it, format it, ext3, label it "/", etc, etc, etc. Next is /home, then swap.

Go through your partitions to tell the installer routine how to use them, then arrow down to the bottom of the screen, choose Finished, on the next screen choose YES to commit the changes, then continue with your install.

Finally, you will be prompted to allow Grub to be installed. Grub has seen your Windows partition/installation already - it is safe. Allow Grub to be installed, where it wants, and you will be good-to-go.

Your machine will reboot shortly. At this reboot it is necessary to go into your bios and choose to Boot to HDD-0. Please see another tutorial for this purpose. It's easy, don't fear this.

Leaving your BIOS, your machine will reboot and in about 2 screens you will see GRUB at the bottom of your screen - hit the ESC key. Do you see that? It is listing your new Ubuntu installation as a choice to boot to, and it is also listing - at the bottom - your Windows installation as a choice as well.

Choose Ubuntu. You did it. 
---------------------------
I need a mighty DISCLAIMER right about now. I'm not at all experienced writing tutorials. My writing style will probably leave folks confused, sorry. I hope this helps some folks that would normally be scared to attempt this. Sure, it's an intermediate (?) level task, I suppose, and things CAN and just MIGHT go wrong. Sure, there are any number of ways to accomplish this, as well. The one I mention I employ frequently and with good results, as I said, I have never lost data - but I have had to perform rescues of a more advanced sort. I don't know the condition of your hdd or your panic level. 

It's just a hdd, and it's a routine task to partition it. Even resizing is common - and hey, give NTFSResizer a go. It really is good (and free - or was a few years ago when I found it), and you can still make new partitions when you are installing Ubuntu, with Ubuntu Installers Partition Manager.
--------------------------
Happy Computing

Any mod might think this or the other thread to be redundant now.  Feel free to delete at will.  As well - this tutorial screams for an editor![/QUOTE]

Nice job Machiner!

Thanks for your effort.

---

### Post by DerekL on 2005-05-29
Hey Machiner, good walkthrough for installing Ubuntu for dual-boot with Windows.  I was reading through the walkthrough and came to a road block on the part that mentions it is necessary to change my BIOS to boot to HDD-0.  I have an HP Pavillion zd5000 notebook running PhoenixBIOS version F.12.  Unfortunately, after searching through my rather limited BIOS, I was unable to find where to change to boot to HDD-0.  I've searched online for some other threads which might aid me but of course with minimal success.  I was hoping you can help me out??

---

### Post by jsuen on 2005-06-12
booting to hdd0 should just mean that you boot from the primary (master) hdd that you've installed (possibly both) ubuntu and XP on - in short, altering the boot sequence from your BIOS menu to start with the hdd (or just skip the cd/dvd drive, my laptop boots in floppy-hdd-cd drive mode but floppy doesn't exist.)

hth,

jon

---

### Post by yesplease on 2005-08-26
I would use at the very least 10 GB for windws on a 40 GB disk, because windows needs lots of space if you actually want to do something with it. A game for instance can use 4 GB, swap is 1 GB, etc. 

On a 200 GB disk I use 50 GB for windows XP, excluding the space for data, movies, backup, etc. because they get their own 100 GB partition. This would leave 50 GB for Ubuntu and 50 GB for a FAT32 partition, because  both XP and Ubuntu can write on FAT32.

---

### Post by netneo on 2005-09-16
Hey guys

Total Newbie out here

I have been reading a few threads and decided to give it a try

Downloaded the System Rescue CD and ran QtParted

One problem though..

In each tutorial..it is mentioned that u will see your hard disk on the left column of the qtparted GUI..

/hda1 for example,right?

But i never see anything..instead...i got a message "No disks found","Not logged in as root" or something like that!

Therefore i cant proceed with my resizing of NTFS and installation of Ubuntu

What do i do?

Another lil question:
I have an 80 gb hdd with 3 existing NTFS partitions C,D and E

Now Xp obviously is in the C drive and i emptied my E drive and was planning to install Ubuntu over there in around 10 gb...out of the total 15 in E drive...with 5 for Xp

However...will i get these three drives as /hda1,/hda2/hda3 in the qtparted left column?

Or are they logical partitions and i will have to resize something else?

Also,although i have emptied E drive there is still around 800 mb occupied due to the swap file of Windows i guess.
Will that be adjusted when i resize my Hdd?

Please help me since i dont want to mess up my D drive coz there is a lot of data out there which is too big to backup.

---

### Post by baskak on 2005-10-03
Hi, it's a Linux newbie, too, and it seems I have quite a problem with the partitioning now. I hadn't read the tutorial, unfortunately, and tried to "save up" space for Ubuntu using built-in partitioning utility. (I have a laptop with 40GB hdd, a ca. 6 GB WinXP partition and 33GB "everything else" partition, all self installed.) I have resized the second partition (labelled as "d:") and put, using automation, two Linux partitions. The Ubuntu utility reported that it cannot properly set up the Linux partitions, though (I didn't write down the announcement). So I undid the change, and Ubuntu partitioning tool reported my original NTFS 33GB partition again.
However, Windows doesn't see it as "d:" anymore (only under Disk Management, as "unknown"), and Partition Magic describes the whole of it as "Linux swap", but at same time colour-codes it as "other", and doesn't allow any changes.
Needless to say, I'd like to recover my "d:" disk and have access to my files again. There were not many important ones, but at least some. 
Is there any chance you can help? Sorry for troubling and stupidity, but I feel I put too much trust into the Ubuntu tool and its intuitivity.

---

### Post by knottyboy on 2006-08-27
First time in here guys, please be gentle...

Have new Dell laptop with partitions as follows trying to install Ubuntu
dev/sda1 - fat 16 - 47.08mb
dev/sda2 - ntfs - 66.68 GB boot
unallocated - 7.84
dev/sda3 - ntfs - 19.66 GB [empty place for linux]
unallocated - 7.84
dev/sda4 - fat 32 - 3.16 GB
unallocated - 2.19 GB

Now I get that the fat 16 & the first large 67 gig partitions are the windows XP install that I want to keep. The second was an empty spot to use as backup and is empty and a likely home for Ubuntu. But what the hell is the little fat 32 at the end of the drive? Seems like its with the empty partition for backup. 

The reason I'm asking is that I can't complete my install of Ubuntu untill I have a place for swap. And I'm not sure if I can delete and create a new place for swap without screwing up my xp installation. Any ideas? I tried to creat another partion, but only 4 are allowed as primary. 

Thanks for your help in advance.
knottyboy

---

### Post by tilmaniac on 2006-10-30
Its worth noting that the default Ubuntu install CD has the ability to install itself next to an existing windows partition.  No rescue CD needed.

Its not totally intuitive but it certainly works.

---

### Post by greensmoke on 2006-11-13
Yes that is true.  People, it is not even half as complicated as the how to looks.  I did it without a walkthrough, I just followed directions on the installers and a bit of common sense.  

Unfortunately, my windows installer cd would not let me choose size for partitions, so I had to reboot with the Ubuntu installer cd, partition my hard drive, wait for the partitioning to finish, pop out the Ubuntu cd, pop in the windows cd, reboot, and then repartition with the existing Ubuntu (unknown) partitions.

I wouldn't even bother with dual boot if it weren't for the fact that certain developers will not allow their software to run on other operating systems other than MS Windows, and actually go to the point of making it impossible for people to even use them running Wine...

---

### Post by aysiu on 2006-11-13
greensmoke, this thread was started in February 2005, almost two years ago.

Since then, a lot of progress has been made.

Check out these two dual-boot guides:

**Desktop CD**
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

**Alternate CD**
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by lindseyE on 2009-11-11
Okay, I'm a newbie to Ubuntu... I've been trying to install it along side Windows 7, and I keep getting these messeges:
[IMG]http://farm3.static.flickr.com/2590/4096605144_d5a94e60d1_o.jpg[/IMG]

[IMG]http://farm3.static.flickr.com/2605/4096605108_40defcd26b_b.jpg[/IMG]

I need help!!!

---


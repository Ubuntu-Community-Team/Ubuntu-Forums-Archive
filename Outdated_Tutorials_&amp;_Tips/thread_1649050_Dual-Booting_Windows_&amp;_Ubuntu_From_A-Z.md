---
title: "Dual-Booting Windows &amp; Ubuntu From A-Z"
date: 2010-12-19
forum: Outdated Tutorials &amp; Tips
---

### Post by amjjawad on 2010-12-19
[CENTER][CENTER][LEFT]***Last Update: 6-Jan-2011***
[/LEFT]
[FONT=Verdana][SIZE=5][COLOR=Navy][U][B]
[SIZE=5][COLOR=Red]Dual Booting Guide – Windows XP & Ubuntu 10.04 From A -Z[/COLOR][/SIZE]


[/B][/U][/COLOR][/SIZE][/FONT][LEFT]

[SIZE=4][COLOR=Blue]_**[FONT=Verdana]Special Thank[/FONT]**_[/COLOR][/SIZE]
[FONT=Verdana][COLOR=Black]I'd like to show my appreciation to this great  community. I'm so thankful for all kind of help and support. Special  thank also goes to this forum and everyone who works hard to keep it  active and alive. Without this forum, I wouldn't be here and without  seeing the light after +10 years of darkness, I wouldn't use Ubuntu  specifically and Linux generally.[/COLOR][/FONT][COLOR=Black]
[/COLOR][COLOR=Black]
[/COLOR][FONT=Verdana][COLOR=Black] Thank you for everything :)[/COLOR][/FONT][COLOR=Black]
[/COLOR]




[SIZE=4][SIZE=5]_**[FONT=Verdana][COLOR=Navy]Contents[/COLOR][/FONT]**_
[/SIZE][FONT=Verdana][COLOR=Navy]**[SIZE=4]Part 1 - Installation[/SIZE]**
[/COLOR][/FONT][/SIZE][FONT=Verdana][SIZE=1]
           [SIZE=1]**[1-1]** Scenario 1: Dual Booting System from Scratch on The Same HDD.

**[1-2]** [Scenario 2: Dual Booting System from Scratch, Each OS on its own HDD.          ]("http://ubuntuforums.org/showpost.php?p=10259596&postcount=8")

**[1-3]** [Scenario 3: Dual Booting System - Windows XP is already installed and uses the entire HDD.]("http://ubuntuforums.org/showpost.php?p=10265009&postcount=9")

**[1-4]** [Scenario 4: Dual Booting System - Ubuntu 10.04 is already installed, uses the entire disk and there is only ONE HDD.]("http://ubuntuforums.org/showpost.php?p=10278677&postcount=10")

**[1-5]** [Scenario 5: Dual Booting System - Ubuntu 10.04 is already installed, uses the entire disk and there is TWO HDD.]("http://ubuntuforums.org/showpost.php?p=10287294&postcount=11")

**[1-6]** [Scenario 6: Dual Booting System - Windows XP is already installed and Install Ubuntu 10.04 on USB Drive.]("http://ubuntuforums.org/showpost.php?p=10322872&postcount=12")
[/SIZE]                                                                [/SIZE][/FONT]                              


_[**[SIZE=4][COLOR=Navy][FONT=Verdana]Part 2 - [/FONT][FONT=Verdana]Installation Problems & Troubleshooting[/FONT][/COLOR][/SIZE]**]("http://ubuntuforums.org/showpost.php?p=10324725&postcount=13")_

[FONT=Verdana][SIZE=1]**[2-1]** Installation Problems/Problems During Installation

**[2-2]** Problems After Installation



[/SIZE][/FONT][B][SIZE=4][COLOR=Navy][FONT=Verdana]Part 3 - Un-installation/Removing Ubuntu/Windows

[/FONT][/COLOR][/SIZE][/B][FONT=Verdana][SIZE=1]**[3-1] **Un-installation/Removing of Ubuntu and keeping Windows.
**[3-2]** [/SIZE][/FONT][FONT=Verdana][SIZE=1]Un-installation/Removing of Windows and keeping Ubuntu.[/SIZE][/FONT]


[/LEFT]
[/CENTER]
[/CENTER]
  [FONT=Verdana][SIZE=3]=================================================================[/SIZE][/FONT]
[CENTER][SIZE=5][FONT=Verdana][COLOR=Navy][B]

Part 1 - Installation[/B][/COLOR][/FONT]
[/SIZE][/CENTER]
[FONT=Verdana][SIZE=3]
[/SIZE][/FONT][FONT=Verdana][SIZE=3]**_Preface_**[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Definitely, this is  one of the most important topics on daily basis. Who doesn’t Dual-Boot  Ubuntu with Windows? Most of the users including me are still  Dual-Booting (Ubuntu & Windows) – if not Multi-Booting – regardless  what’s the reason behind that.[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]I see daily perhaps  10 threads or more with the same title. All posters are having  Dual-Booting Problems because in most cases they did not follow the  right procedure and they end up with problems.[/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3][COLOR=Red]**_Note that:_  **[/COLOR][COLOR=black]
A- This guide should also work with Windows Vista and Windows 7 with some differences especially the screenshots (images). The main concept should be the same. In case of major differences, I'll make sure to highlight that.

B- You need to refer to your Motherboard's Manual. My BIOS Settings could be different from your BIOS Settings. The concept is the same but there might be some minor changes.

C- I  tried to include all the images I have but I'm ONLY allowed to post 8  images. That's why you'll find links to these images. Had to update the  guide after I wrote it.[/COLOR][B][COLOR=Blue]
[/COLOR]

_ Aim of this Guide_[/B][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]To save everyone’s  time and to make it easier for Windows Users who are willing to try/use  Ubuntu or those new Ubuntu’s users who just installed Ubuntu, this  thread has been created.[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]I’ll do my best to make it as simple as possible so everyone could understand it.[/SIZE][/FONT][FONT=Verdana][SIZE=3] Even if you know nothing about computers, you should be fine with this guide. **However, I assume you have basic understanding about computers.**

[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]I believe this  thread will clear any confusion especially if users will follow each  step as it’s and read this guide very carefully.[/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]**_About this Guide_**[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]This guide has been  written by myself and I’ve never taken any single word from any other  website, guide, post or whatever source you could think about. This  guide has been written based on a real experience and the most recent  experiment of installing Windows and Ubuntu on a PC. However, I thought I  could write this guide without including any website’s link but I’d  like to give the reader more than one choice. After all, this guide will  be used by others and they have to find all or most of what they’re  looking for.[/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]My plan is to  discuss all the possible scenarios and cover everything about  Dual-Booting. Please note that this is not a thread to list some common  problems and offer some solutions. This thread is a very simple guide  that I believe if you’ll follow, you’ll not have any issue. Of course  nothing is prefect and I may forget something here or there but that  shouldn’t be a problem because I can update the thread on daily basis  and my friends here will inform me if I need to add/remove something.  After all, I’m not alone and I’m just like you, a user who Dual-Boot.[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]I believe that an  image could worth 1000 words if not more. Thus, I’ll do this my way  which I believe it’s very informative and include an image with each  step. That image will help you a lot to understand what’s going on and  what I’m talking about.[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]A Guide for Dual-Booting Windows and Ubuntu could found be here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]
However, as I mentioned, I’m trying to create a very simple guide.  [/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3][B][U]
[Hardware Used (click):]("http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7125")[/U][/B][/SIZE][/FONT][URL="http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7125"][FONT=Verdana][SIZE=3]
[/SIZE][/FONT][/URL]   [FONT=Verdana][SIZE=3]Motherboard: Intel [/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]CPU: Pentium 4 @3.00GHz[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]*RAM: 448MB DDR PC400[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]*HDD: Samsung 20GB[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Graphics Card: ATI (Built-in)[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3][B][U]

Requirements:[/U][/B][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Windows XP Disk (CD)[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Ubuntu LiveCD or LiveUSB[/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]*I decided to use the minimal hardware requirements. I’m using my Test-PC.[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Please check these links for more information about the minimum system requirements to run Ubuntu.[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]
[/SIZE][/FONT][FONT=Verdana][http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements)

[/FONT]      [FONT=Verdana][https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)


[/FONT]      [CENTER][FONT=Verdana][SIZE=4][B]_[COLOR=Red]Scenario 1[/COLOR]_: [U]Dual Booting System from Scratch on The Same HDD
[/U][/B][/SIZE][/FONT][/CENTER]
  [FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3]**_Introduction_****:** 
Installation of Windows XP and Ubuntu 10.04 on a brand new HDD or a  wiped HDD. This section will explain in details all the steps needed to  prepare the HDD, Install XP, make sure the machine is up and running  with Windows XP and then install Ubuntu 10.04 on the same HDD and while  Windows XP is already installed. This section should cover everything  needed to create a Dual Booting System with both XP and Ubuntu installed  on **[COLOR=Red]the same HDD.[/COLOR]**
[/SIZE][/FONT] [FONT=Verdana][SIZE=3]
[U][B]Plan
[/B][/U]First of all, you need a plan. In a better word, you should know what you want and how to achieve that.
Our plan here is simple: 
a) Install Windows XP on a Brand New HDD or Wiped HDD.
b) Make sure XP is up and running
c) Install Ubuntu 10.04.

IMHO, the most important step is preparing the HDD. Yes, partitioning  the HDD is very important. It's much better to start partitioning your  HDD, then, start installing.

[U][B]Part I: Installing Windows XP
[/B][/U]
[/SIZE][/FONT][FONT=Verdana][SIZE=3]1) **If your HDD is already installed**, then please go to step 3.

[/SIZE][/FONT][FONT=Verdana][SIZE=3]2) **If your HDD is new** and you have no idea how to install it in your machine, then [google ]("http://www.google.com/")is your friend. However, Please check _[this guide]("http://computershopper.com/hard-drives-burners/howto/install-a-new-hard-drive-in-five-easy-steps")_. Make sure that your BIOS is able to recognize the new HDD.

3) Make sure to check your BIOS Settings.

>> _[image]("http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7126")_ 

The image above explains itself.
Please, make sure that **your CD-Drive is your first Device to boot from all the way**.  That should be your default settings. If not, set it this way. Whether  you're installing new OS or not, it's recommended to set the CD-Drive as  the first device to boot from.

4) There are two options that you should be aware of. There is ***Boot Priority Device*** and there is ***Hard Disk Boot Priority***.

**Boot Priority Device** > List all the Drivers you have (HDD, CD-Drive, etc).

**Hard Disk Boot Priority** > If you have more than one HDD or if  you're booting from HDD and/or USB, then you need to check this option  and change the priorities according to your needs.

This image will help you to understand:

>> [image]("http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7127")

In this case, there's only one HDD drive installed. In case there is  more than one HDD or there's a USB Drive, you'll see more entries.
In this part and as long as we do have only one HDD, then you should see  something like the above image. Unless you have an USB Drive, you'll  see two entries.

[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]5) As per Step 3,  your CD-Drive should be the first device to boot from. Insert your  Windows XP Disc and start Windows Installation.

6) The HDD I have used in this guide is not new, it's a wiped HDD. You should see something like this:

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7128")_

Now, before we carry on to the next step, please remember that we're  planning to create a Dual-Boot System so there's another OS to be  installed. Make sure NOT to allocate the whole space of your HDD to  Windows.

7) This guide assumes that you'll use 10GB of the HDD (which is 20GB) and allocate it to Windows.

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7129")_

[B]Again, don't allocate the whole space to Windows.
[/B]

8 ) After that, you should see something like this:

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7130")_ 

If that's what you see, then you're good to go.


9) Whether it's new or wiped HDD, use the third option:

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7131")_

10) The rest of steps are the regular steps you need to follow to  install XP. Nothing special at all. If you don't know how to install  Windows XP, please use google.

Once XP is up and running, then it's a sign that you finished Part I. Congratulation.



[/SIZE][/FONT][FONT=Verdana][SIZE=3]_**Part II: Preparations to Install Ubuntu 10.04 **_[/SIZE][/FONT]
[FONT=Verdana][SIZE=3]
1) Please click _[here]("http://www.ubuntu.com/desktop/get-ubuntu/download")_.

2) Do not proceed unless you check the integrity of your downloaded iso for Ubuntu. _[This is how]("https://help.ubuntu.com/community/HowToMD5SUM")_.
You also need _[this]("https://help.ubuntu.com/community/UbuntuHashes")_.

3) As discussed previously, your CD-Drive must be the first device to boot from. This is just a reminder :smile:
[/SIZE][/FONT][FONT=Verdana][SIZE=3][COLOR=Red]****In  case you  are planning to use LiveUSB to install Ubuntu, then please  make sure  your USB Device should be the "first" device to boot from  then your HDD  should comes as the second one.***[/COLOR][/SIZE][/FONT] **Refer to Step 3 and Step 4 in Part I. Same screenshot but with another entry for your USB Device.**


[B][COLOR=Sienna][SIZE=4][COLOR=Navy]_Note that:_ some motherboards do not support that option to boot from USB Devices. Then you have to options:
a) Use LiveCD
b) [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)
    [/COLOR][/SIZE][/COLOR][/B]
[FONT=Verdana][SIZE=3]
4) Insert Ubuntu's LiveCD or USB and press any key. You should get this screen:

>> _[image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7132")_

Choose: Try Ubuntu without Installation.


5) Now, sometimes, you may face some problems with the LiveCD and you  may not reach the point when you can see the GUI Desktop. There are many  reasons for that. Either it's your Graphics Card, CD is corrupted, you  have low hardware specifications or it could be something else.
That's another story I might be able to discuss later on.

6) Once you see the Desktop, please run _[GParted]("https://help.ubuntu.com/community/GParted")_.

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7133")_

**_Note that:_** Starting from Ubuntu 10.04, after installation, GParted will **not** be installed **by default** with Ubuntu, you may want to install it manually later on.


7) Once you start GParted, it should look like this:

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7134")_

Before we carry on, please make sure to read _[[SIZE=4]**this**[/SIZE]]("https://help.ubuntu.com/community/HowtoPartition")_ **[COLOR=Red]carefully.[/COLOR]**


8 ) Please, refer back to the previous step. Step 7 :wink:
Yes, do yourself a favor and read it all. Trust me, you'll thank me for this :smile:


9) I'm going to list all the steps you need to do as images. These images worth more than 1,000,000 words :grin:

*Please "click" on each step so that you can access the image.

[B]_[Step (a)]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7135")_
[/B]Select the "unallocated space" - *Right Click* - and choose "New".
Please, make sure not to do anything to the first partition which is "**/dev/sda1**" as this is the Windows Partition.

[B]_[Step (b)]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7136")_
[/B]The whole remaining space will be allocated to the Extended  Partition. If you still don't know what does "Extended Partition mean,  please refer back to step 7.

_[**Step (c)**]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7137")_

_[**Step (d)**]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7138")_

[B]_[Step (e)]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7139")_
[/B]
[B]_[Step (f)]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7140")_
[/B]Please make sure to double check what you've done before clicking on "Apply".

_[**Step (g)**]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7141")_
GParted should look like that after you're done.



[/SIZE][/FONT][FONT=Verdana][SIZE=3]_**Part III: Installing Ubuntu 10.04 **_[/SIZE][/FONT]
[FONT=Verdana][SIZE=3]
1) Please click _[here]("https://help.ubuntu.com/community/Installation")_ and have a look at the official installation guide. No need to say it's a must read as well.

What I'm trying to highlight in this guide, could save your time and  everyone's else time. Everyone can install Ubuntu but not anyone could  do that without mistakes. This guide, will make sure you'll do it  without any mistake if you follow the steps correctly.

2) Unfortunately, the _[Graphical Installation Guide]("https://help.ubuntu.com/community/GraphicalInstall")_  does not show/mention the Manual/Advanced Option which is (IMHO) is the  most important part of the installation process. Thus, you need to  choose this option as per the below image:

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7142")_


3) As you may know so far, Linux uses different naming-scheme than Windows. There's no C drive and stuff like that.
Having the said, in this guide, I'm trying to install Ubuntu in  partition sda5 and use sda6 (home) and sda7 (swap) as well. Yes, the  best partitioning scheme is to have 3 partitions: root, home and swap.
Root and swap are must. Home partition is not but recommended.


4) You need to click on each partition to set the _[mounting]("https://help.ubuntu.com/community/Mount")_ point.

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7143")_


>** Creating the first mounting point which is** "[COLOR=Red]**/**[/COLOR]".

>> _[Image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7144")_


> **Creating the second mounting point which is** "**[COLOR=Red]/home[/COLOR]**".

>> _[Image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7145")_


> [B]And this is the final step. Click "Forward" but as usual, make sure everything is correct.

>> [/B]_[Image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7146")_
5) As long as you have installed Windows XP first, you'll see something like this:

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7147")_

Since you just installed XP and there's no documents to import, then just click "Forward" and that's all.


6) Now, here comes the most important part of any Ubuntu Installation, period.
You need to pay so much attention to this step. However, at this point,  if you will proceed with the default option, you're still safe but it's  much better to check it. Why? you need to be familiar with that option. 

>>> _[IMAGE]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7148")_

Step 8 as per the image above is the last step of the installation process.
Once you reach here, click "Advanced".
You'll see another window "Advanced Options".
As you can see above, these are the advanced options you got.
This step should determine which Boot Loader will take the control to boot your machine.
Long story short, the best option is to use _[[SIZE=4][COLOR=Red]**GRUB2**[/COLOR][/SIZE]]("https://help.ubuntu.com/community/Grub2") _as your main boot loader.
GRUB2 is the best boot loader I've ever seen. In order to give GRUB2  (Ubuntu's boot loader) the full control over the booting process, you  need to choose to install it on the [_MBR_ ]("http://en.wikipedia.org/wiki/Master_boot_record")of your HDD as per the image above.

**sda > means GRUB2 will be installed in the MBR.**

sda1> means GRUB2 will be installed in Windows Partition. The same  partition (C in Windows) that you used to install Windows on.

sda5 > means you'll install GRUB2 in Ubuntu's root partition.
sda6 > means you'll install GRUB2 in Ubuntu's home partition.

The only option you "have" to take is to install the boot loader (GRUB2) in the MBR which is **sda**.
Unless you have another reason that could prevent you from doing so. Yes, there are another _[boot loaders]("http://en.wikipedia.org/wiki/Booting")_ but this guide will not discuss that.

Click "Install" once you're done.

*Later on once we go further with this guide, we'll need this step a lot. **Please, make sure to understand it**.


7) Make a cup of tea or perhaps a cup of coffee and wait until the installation is done. It will take forever :grin: I'm kidding, you'll be amazed how fast the installation is.
However, if you're connecting to the internet, the installation process  will take more time. During the installation, some files/packages will  be downloaded from the internet, thus it might take a bit longer.

8 ) Once the installation is done, a restart is required but hey, don't  worry, Ubuntu (Linux) is not like Windows, "Restart" process is not a  common task that you need to do every 5 mins :razz:
Before the machine will reboot, you need to take out the installation media whether it's LiveCD or LiveUSB.
Press Enter and wait ...

9) After restarting, you should get something like this:

> _[Image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7149")_


10) You are DONE.

Congratulation, you have installed your first Dual-Booting System "successfully" :wink:

[/SIZE][/FONT]

---

### Post by Sef on 2010-12-19
Moved to Tips and Tutorials.

---

### Post by wilee-nilee on 2010-12-19
Without clicking on every link I see no mention of the bootscript. Really if a person needs this much of a tutorial they should be asking for help with this script posted.

XP wont install to a sata drive without drives as well. The bios can be set to read the ide type and installs go okay generally, when the bios allows this change.

---

### Post by amjjawad on 2010-12-19
> **wilee-nilee said:**
> Without clicking on every link I see no mention of the bootscript. Really if a person needs this much of a tutorial they should be asking for help with this script posted.


From About this guide:
> [FONT=Verdana][SIZE=3]Please note that this is not a  thread to list some common  problems and offer some solutions. This  thread is a very simple guide  that I believe if you’ll follow, you’ll  not have any issue.[/SIZE][/FONT]


However, if you read carefully, you'll understand that this guide is not finished yet. I'm planning to include more stuff.
This guide for installation not troubleshooting. Read the first part of this guide.

> XP wont install to a sata drive without **drives** as well. 
Could you explain that?

---

### Post by wilee-nilee on 2010-12-19
> **amjjawad said:**
> From About this guide:


However, if you read carefully, you'll understand that this guide is not finished yet. I'm planning to include more stuff.
This guide for installation not troubleshooting. Read the first part of this guide.


Could you explain that?

XP needs sata divers to be put on a sata drive.

I can appreciate your want to write a tutorial, but there are a bunch already and web links. A tutorial can make it seem somebody understands but can also get them into deep dodo if not followed correctly.

---

### Post by amjjawad on 2010-12-20
> **wilee-nilee said:**
> XP needs sata divers to be put on a sata drive.

My copy of XP already has that. 

> 
I can appreciate your want to write a tutorial, but there are a bunch already and web links. A tutorial can make it seem somebody understands but can also get them into deep dodo if not followed correctly.

I'm aware of that. Again, if you read the guide, you'll find it's full of websites, etc etc. On the beginning, I already included the official installation guide.
This guide is just the beginning for me. I had one before but that needs so much modifications which I'm working on. I'm still new here. I'm trying to help the beginners and new comers.
This is NOT for proficient Linux/Windows Users at all :)
I'm going to use this guide later on as I'm working on something a bit bigger.

Thank you ;)

---

### Post by wilee-nilee on 2010-12-20
> **amjjawad said:**
> My copy of XP already has that. 



I'm aware of that. Again, if you read the guide, you'll find it's full of websites, etc etc. On the beginning, I already included the official installation guide.
This guide is just the beginning for me. I had one before but that needs so much modifications which I'm working on. I'm still new here. I'm trying to help the beginners and new comers.
This is NOT for proficient Linux/Windows Users at all :)
I'm going to use this guide later on as I'm working on something a bit bigger.

Thank you ;)

Is your copy of XP a OEM?

---

### Post by amjjawad on 2010-12-20
[CENTER][CENTER][FONT=Verdana][SIZE=3]**_[COLOR=red]Scenario 2[/COLOR]_****: _Dual Booting System from Scratch, Each OS on its own HDD_**[/SIZE][/FONT][FONT=Verdana][SIZE=3]
 
 [/SIZE][/FONT][/CENTER]
[/CENTER]
  [FONT=Verdana][SIZE=3]**_Introduction_****:**[/SIZE][/FONT][FONT=Verdana][SIZE=3] 
Before reading further, I assume you already read Scenario 1 in this guide. If you haven&#8217;t done that yet, please try to at least skim it.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]This scenario should cover the installation of XP and Ubuntu each [COLOR=red]on its own HDD[/COLOR]. This is one of my favorite methods of installation, whether I&#8217;m Dual-Booting or Multi-Booting.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Windows XP will be installed on *[COLOR=red]HDD1[/COLOR]*.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Ubuntu will be installed on *[COLOR=red]HDD2[/COLOR]*.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]*I&#8217;m going to use &#8220;[COLOR=red]HDD1/HDD2[/COLOR]&#8221; in general and &#8220;[COLOR=#17365d]sda/sdb/sdb1[/COLOR]&#8221; when talking about Ubuntu.

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]If you have an old HDD that you&#8217;re not using, especially if it&#8217;s small in size (say 20/40GB) then this method is really helpful. 

[B][U]Plan
[/U][/B][/SIZE][/FONT]      [FONT=Verdana][SIZE=3]a) Install Windows XP on [COLOR=red]HDD1[/COLOR] (Brand New or Wiped HDD).
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]b) Make sure XP is up and running.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]c) Install Ubuntu 10.04 on [COLOR=red]HDD2[/COLOR] (Brand New or Wiped HDD)
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]d) Make sure Ubuntu is up and running.

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]As I mentioned before, prepare the HDD is very important step that you need to be aware of. In this scenario, there&#8217;s another important step you need to do. You need to make sure the BIOS is set to boot the right/correct HDD. Note that you have now two HDDs so it&#8217;s a bit different here.

**_Part I: Installing Windows XP_**[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]1)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Make sure your BIOS settings are correct. [COLOR=red]HDD1[/COLOR] must be the first Hard Disk to boot from. 
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]See this > _[image]("http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7174")_.

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]Remember, your CD-Drive must be the first &#8220;***device***&#8221; to boot from NOT the first HDD to boot from. I already explained that previously. Please, don&#8217;t be confused.

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]2)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Now, you&#8217;ll follow almost the same steps as before with few changes:
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]a)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Make sure to choose the correct [COLOR=red]HDD [/COLOR]to install XP on. In this guide, we&#8217;re installing Windows XP on [COLOR=red]HDD1[/COLOR].

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]b)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]You don&#8217;t need to worry about partitioning [COLOR=red]HDD1[/COLOR] (where are you going to install XP on) because the whole Hard Disk will be used by XP *unless* you want to create more than one partition for Windows XP. For me, I allocate the whole HDD for XP. As I mentioned before, most likely you&#8217;re using a small size old HDD. *[COLOR=red]If your HDD is large and you want to share it with Ubuntu then please refer back to [Scenario 1]("http://ubuntuforums.org/showpost.php?p=10257675&postcount=1")[/COLOR]*.

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]3)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Done.

**_Part II: Preparations to Install Ubuntu 10.04_**[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]It&#8217;s true that Ubuntu will be installed on [COLOR=red]HDD2[/COLOR] and it seems there is no need to prepare the HDD since Ubuntu supposed to use the whole space.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Wrong answer. Even though Ubuntu will use the whole space in [COLOR=red]HDD2[/COLOR], IMHO, it&#8217;s recommended to prepare the HDD **_before_** installing Ubuntu. Why? Because I suppose you&#8217;re going to &#8220;TRY&#8221; Ubuntu before installing it. It&#8217;s always better to make sure your machine is capable of running Ubuntu without any kind of problems and somehow the Live Session (TRYING Ubuntu without Installation &#8211;NO changes will be made to your HDDs) is a good idea and the first step that one should do.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]1)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Please refer back to _**[*[COLOR=red]Scenario1-PartII- step1 step2[/COLOR]*]("http://ubuntuforums.org/showpost.php?p=10257675&postcount=1")**_
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]2)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Now, reboot/restart your machine and change your BIOS settings so that [COLOR=red]HDD2[/COLOR] (where Ubuntu is going to be installed) will be the first HDD to boot from. 
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]See >_[image]("http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7175")_.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]I think by now, you understand what does that mean and you&#8217;re able to do it ;)

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]3)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]You&#8217;ll follow the same steps in _**[[COLOR=red]Scenario1-PartII[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10257675&postcount=1")**_ but remember, Ubuntu will use the whole space in [COLOR=red]HDD2 [/COLOR]**[COLOR=#17365d](sda).[/COLOR]** 
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Make sure you select the correct HDD (_[see this image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7176")_)

**[COLOR=#17365d]sda[/COLOR]**[/SIZE][/FONT][FONT=Verdana][SIZE=3]** is [COLOR=red]HDD2[/COLOR]**
**[COLOR=#17365d]sdb [/COLOR]**[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]**is [COLOR=red]HDD1[/COLOR]**

**[COLOR=red]>>[/COLOR]**[/SIZE][/FONT][FONT=Verdana][SIZE=3]**[COLOR=#17365d]sdb[/COLOR]****[COLOR=#17365d] ([/COLOR]****[COLOR=red]HDD1[/COLOR]****)[COLOR=red] has Windows XP so make sure NOT to select that HDD.[/COLOR]**

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]The difference in this case will be very minor:
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3][COLOR=#17365d]sda1 [/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=3][(_in this image_)]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7141")will not be used by Windows and will not be NTFS. 
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3][COLOR=#17365d]sda1[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=3] partition will be used by Ubuntu, will be ext4 and it will be the root partition.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Yes, it will remain &#8220;Primary Partition&#8221;.

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]So, you&#8217;ll have:
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3][COLOR=#17365d]sda1[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=3]: root partition (ext4) &#8211; Primary Partition
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3][COLOR=#17365d]sda2[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=3]: Extended Partition
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3][COLOR=#17365d]sda5[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=3]: home partition (ext4) &#8211; Logical Partition
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3][COLOR=#17365d]sda6[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=3]: swap partition (linux-swap) &#8211; Logical Partition

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]However, you may want to create a Data or a shared partition between Windows and Ubuntu. Remember I mentioned that this scenario might be used when you have an old IDE/SATA HDD that you are going to use it for Windows and most likely it&#8217;s small in size. Having that said, a data partition which can be used by both Operating Systems is good idea. All what you need to do is to create another partition (after you already created root, home and swap for Ubuntu) and format it as NTFS. That&#8217;s all.

**[COLOR=red]*Ubuntu _&#8220;by default&#8221;_ can access NTFS (read/write) Partitions while Windows _&#8220;by default&#8221;_ cannot access ext4 Partitions.[/COLOR]**[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]If you&#8217;ll create a data partition (NTFS) then: 
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3][COLOR=#17365d]sda7[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=3]: data partition (NTFS) &#8211; Logical Partition


[/SIZE][/FONT]         [FONT=Verdana][SIZE=3]4)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Done.


**_Part III: Installing Ubuntu 10.04_**[/SIZE][/FONT]        [FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Same procedure you followed in [COLOR=Red]**_[scenario1]("http://ubuntuforums.org/showpost.php?p=10257675&postcount=1")_**[/COLOR] except few change:

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]1)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]As we did before, you need to select the advanced option for installation (specify partitions manually &#8211; advanced)

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]2)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Please, make sure to select the correct HDD from the list. Please see this:
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]>_[image]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7177")_

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]You need to select **[COLOR=#17365d]sda[/COLOR] ([COLOR=red]HDD2[/COLOR]) **from that list. Forget the partitions which are already exist in that screenshot. The point is to show you which Hard Disk (**[COLOR=#17365d]sda[/COLOR]**) you need to select in this case.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Then, follow the same steps as discussed and explained in [[COLOR=Red]_Scenario1-PartIII_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10257675&postcount=1").

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]3)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Again, the most important part is &#8220;Installing the Boot Loader&#8221;. 
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]The only difference in this scenario is you&#8217;ll see more entries in the list.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]>> _[IMAGE]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7178")_

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]In the above image, you may see lots of entries. It&#8217;s because I couldn&#8217;t wipe my [COLOR=red]HDD2[/COLOR] which already has Ubuntu (and another OS). The point is:
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]You need to install the Boot Loader of Ubuntu (GRUB2) in the **MBR** of [COLOR=#17365d]sda[/COLOR] ([COLOR=red]HDD2[/COLOR]).

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]The reason why you need to install the Boot Loader in the MBR of [COLOR=#17365d]sda[/COLOR] ([COLOR=red]HDD2[/COLOR]) is because you want GRUB2 (Ubuntu&#8217;s Boot Loader) to take the full control over the booting process.
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]I&#8217;m planning to write more guides for troubleshooting. Sooner or later, you&#8217;ll understand why it&#8217;s important to install GRUB2 in the MBR.

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]4)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]Click &#8220;Install&#8221; and once the installation is done, you should see the _[same screen]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7149")_.

[/SIZE][/FONT]      [FONT=Verdana][SIZE=3]5)   [/SIZE][/FONT][FONT=Verdana][SIZE=3]You are DONE :)[/SIZE][/FONT]

---

### Post by amjjawad on 2010-12-21
[CENTER][FONT=Verdana][SIZE=4][B][SIZE=4]_[COLOR=Red]Scenario 3[/COLOR]_: [/SIZE][U][SIZE=4]Dual Booting System - Windows XP is already installed and uses the entire HDD
[/SIZE]
[/U][/B][/SIZE][/FONT][LEFT][B][COLOR=Red]_[SIZE=3]Please note:[/SIZE]_
[/COLOR][SIZE=3]As of now, I'm going to write a very short steps regarding this scenario. If you already read the other scenarios (1 and 2) then you should understand what I'm talking about. If not, I'll update this guide later one with more details.[/SIZE][/B]


If you have only one HDD and you decided to install Ubuntu and Dual-Boot it with Windows XP which is already installed, up and running then this is the right place to start from.

1) BACKUP All your important data. Use External HDD if possible.

2) Please, refer back to step #1.

3) There are some programs that could backup the OS itself as an image which can be restored later on. Check your HDD-manufacture's website for more details or use some common programs such us Norton Ghost. I prefer this way but if you don't mind to spend the whole day installing all your favorite applications then ignore this. Definitely, this is an extra step to be in the safe side + if you need Windows and you don't want to lose it in the process.

*4) Use [CCleaner]("http://www.piriform.com/") to get rid of all the temp files, cookies, etc.

*5) Disk Defragment.

6) Boot your machine from Ubuntu LiveCD/USB. Choose try Ubuntu and then start GParted (System > Administration > GParted).
Note that, you can use other programs but as long as you already have the LiveCD/USB, you don't need to worry about that.

7) There's one HDD. Most likely, there's one partition for Windows (this is the default case). When it comes to Linux/Ubuntu, the HDDs and Partitions names will be different. If you don't know that already, you really need to read more about the basics of Linux.
In this case, you got **[COLOR=Navy]sda[/COLOR]** (**[COLOR=Red]HDD1[/COLOR]**) and **[COLOR=Navy]sda1 Partition[/COLOR] **(***[COLOR=Red]Drive C in Windows[/COLOR]***) by default.
You need to re-size [B][COLOR=Navy]sda1.
[COLOR=Black]Make sure NOT to shrink too much. Just take what you really need or what Ubuntu needs. Nothing specific, it's totally up to you and your daily usage.

8 ) [COLOR=Red]Please, once you re-size [/COLOR][COLOR=Red]sda1, [SIZE=4]_DO NOT_[/SIZE] do any other operation. Just click "Apply" to apply the change (re-sizing sda1).[/COLOR]


[/COLOR][/COLOR][/B][COLOR=Navy][COLOR=Black]9 ) Re-boot/Restart your machine to make sure Windows is still up and running.

[/COLOR][/COLOR][COLOR=Navy][COLOR=Black]10) [/COLOR][/COLOR][COLOR=Navy][COLOR=Black]If everything is okay, insert your LiveCD/USB and restart your machine. Choose "try Ubuntu", start GParted, create Ubuntu's Partitions (root and swap if you don't want separate home partition or go for the recommended scheme and create root, home and swap) and then Install Ununtu the same way I already explained previously.

11) When it comes to the Boot Loader (GRUB2), as usual, make sure to install it in the **MBR **of **[COLOR=Navy]sda[/COLOR]**.

12) Restart/Re-boot your machine (don't forget to take out the LiveCD/USB) and you're done.


The more you install, the more you read, the better. Above all, if you don't break something, you will not learn to fix it. However, I'm doing my best to prevent that moment. Hopefully you won't face any problems.

Good luck ;)

**Note:**
* *You can do step4 and step5 before step1. I started from Step1 because it's very important step. Backing up is much more important than anything else, especially if you have important data.*

[/COLOR][/COLOR][COLOR=Navy][COLOR=Black]/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/[/COLOR][/COLOR][COLOR=Navy][COLOR=Black]/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/[/COLOR][/COLOR][COLOR=Navy][COLOR=Black]/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/
  
[/COLOR][/COLOR][CENTER]_[SIZE=3]**[COLOR=Navy][COLOR=Black] HOW TO Shrink A Partition Using GParted - Images[/COLOR][/COLOR]**[/SIZE]_
[/CENTER]

[COLOR=Red][B]
Step1[/B][/COLOR]

[LEFT][IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7208[/IMG]
[/LEFT]
 



[B][COLOR=Red]Step 2
[/COLOR][/B]
[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7209[/IMG]




[COLOR=Red][B]
Step 3

[/B][/COLOR][IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7210[/IMG]
[/LEFT]
[/CENTER]

---

### Post by amjjawad on 2010-12-25
[CENTER][FONT=Verdana][SIZE=4]**_[COLOR=Red]Scenario 4[/COLOR]_: _Dual Booting System - Ubuntu 10.04 is already installed_**[/SIZE][/FONT][FONT=Verdana][SIZE=4][B][U], uses the entire disk and there is only ONE HDD

[/U][/B][/SIZE][/FONT][LEFT][FONT=Verdana][SIZE=3][B][U]

Introduction[/U][/B]**:**[/SIZE][/FONT][FONT=Verdana]
[SIZE=3]The title of this scenario said it all. Please note that this is a bit **advanced** approach. It's **not hard** if you know what you want and what are you doing.
In general, it's recommended to install Windows "first" then Ubuntu. However, in some situations, Ubuntu is already installed and you don't want to remove it and that's why you're reading this guide. As usual, I'll do my best to keep it as simple as possible.
Also, please note that I'll skip some basic explanations. For example, I'm not going to write about howto create a LiveCD or check MD5SUM, etc. You should know all these by now ;)  


[U][B]
Plan:
[/B][/U]a) Prepare the HDD and allocate some space for Windows.
b) Install Windows while Ubuntu is already installed.
c) Make sure both Systems are up and running.
[/SIZE]
[/FONT][FONT=Verdana][SIZE=3][U][B]

Requirements:
[/B][/U]a) Ubuntu LiveCD/USB
b) Windows XP Disk
[/SIZE][/FONT][FONT=Verdana]

[B][U][SIZE=3]
Steps
[/SIZE][/U][/B][SIZE=3]1- Backup all your important data/files. Use External HDD if possible.

2- Please, refer back to step #1.

3- Insert the LiveCD/USB for Ubuntu and reboot.

4- Enter BIOS and make sure your machine will boot first from CD/USB.

5-After you'll boot from the LiveCD/USB, please run GParted (System > Administration > GParted).
You need to do the following steps:

a- Select /dev/sda1, Right-Click and select "Resize/Move".

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7248[/IMG] 
[/SIZE]

[SIZE=3]
b- Resize the partition either by your mouse (move the bar to the left) or enter the new size manually. Please make sure you take what you need. DO NOT take more. In this example, I'm working on 20GB HDD. In your case, I assume that would be at least 160GB or maybe more. Make sure both Ubuntu and Windows will have enough space for both of them.
Also note that I didn't create /home partition for this example. It's not a must but recommend. 

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7249[/IMG]




c- Once done, **[_click "Apply"_]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7250")** which is the green icon. The / (root) partition for Ubuntu will be resized.

d- Now, you have unallocated space. You need to prepare this space for Windows Installation. Select the unallocated space, Right-Click and select "New".

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7251[/IMG]




e- Because you're going to install Windows later so you need to format that new partition as "NTFS". Please, make sure it's Primary Partition. Don't worry, if you have root, home and swap partition and all of them are Primary Partitions, you still have one more left. You're allowed to have 4 Primary Partitions MAX.

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7252[/IMG]





f- After that, [**_click "Apply"_**]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7253") and you are done.


6- Reboot your machine and make sure you're able to login to Ubuntu. Remember what I wrote about NOT taking space more than your need.

7- If you managed to login to Ubuntu successfully, then it's time for the next move.

8- Insert your Windows CD and restart/reboot. Remember your BIOS settings must remain the same (boot from CD first).

9- Start the installation process of Windows XP. Choose the NTFS partition that you created using GParted earlier.

Note that, the installer will detect another "active partition" which is sda1 which is the root partition of Ubuntu. Once you choose to install Windows on Partition C (NTFS), it will ask you to make it the "active partition". Just press Enter and carry on. Don't worry about that at all. It's Windows thing. I'm telling you now so you know how to deal with it.

10- Format the partition (quick format) and go on.

11- Once Windows Installation is done, make sure you can login to Windows successfully. I suggest to restart your machine after installation, just to make sure everything is perfectly fine.

12- If Windows is working perfectly then insert your LiveCD/USB of Ubuntu and reboot your machine.

13- Now, we need to re-install GRUB2 to the MBR of sda which is the only HDD you have. On that HDD, there's Windows and Ubuntu installed before Windows.
When you install Windows, the Boot Loader of Windows will overwrite the MBR so GRUB2 is no longer taking the control and you can't boot into Ubuntu.
You need to re-install GRUB2 to the MBR of sda so that you can boot both Windows and Ubuntu using GRUB2.

[COLOR=Red]*If you have another Boot Loader, skip this and install your own. Unfortunately, this guide covers only the installation of GRUB2 as it's so much powerful already.*[/COLOR]

This is the [[COLOR=Red]**_official guide of howto Re-Install GRUB2_**[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202").


14- Applications > Accessories > Terminal
Run this command (copy and paste it to your terminal):
[/SIZE][/FONT]
[FONT=Verdana][SIZE=3]```
sudo fdisk -l
```The output of this command will tell you which partition you used to install Ubuntu on. In this example, the partition we used to install Ubuntu on is sda1.

15- Run these commands in Terminal:

[/SIZE][/FONT]```
[FONT=Verdana] sudo mount /dev/sda1 /mnt[/FONT]
```[FONT=Verdana][SIZE=3] 
[/SIZE][/FONT]```
[FONT=Verdana] sudo grub-install --root-directory=/mnt/ /dev/sda[/FONT]
```[FONT=Verdana][SIZE=3]
[/SIZE][/FONT]

[FONT=Verdana][SIZE=3][I][COLOR=Red]Please Note that in your case, most likely you'll have the same letters.
However, please double check. The output of **[COLOR=Black]"fdisk -l"[/COLOR]** should tell you everything you need.
If still in doubt, read the official guide.[/COLOR][/I]

[/SIZE][/FONT][FONT=Verdana][SIZE=3]16- Reboot your machine

17- You should be able to login to Ubuntu but you will not see anything about Windows.
DO NOT panic :)

18- From Ubuntu, run this command from Terminal:

[/SIZE][/FONT]```
sudo update-grub

```[FONT=Verdana][SIZE=3]

You should see something like this:
[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7254[/IMG]




19- Reboot your machine and your GRUB Menu should have both entires for Ubuntu and Windows XP.
Please, make sure to login to both Windows and Ubuntu.

20- If you managed to login to both Ubuntu and Windows then ... YOU ARE DONE :)
[/SIZE][/FONT][/LEFT]
[/CENTER]

---

### Post by amjjawad on 2010-12-28
[CENTER][FONT=Verdana][SIZE=4]**_[COLOR=Red]Scenario 5[/COLOR]_: **[/SIZE][/FONT][FONT=Verdana][SIZE=4]**_Dual Booting System - Ubuntu 10.04 is already installed_**[/SIZE][/FONT][FONT=Verdana][SIZE=4][B][U], uses the entire disk and there are TWO HDDs

[/U][/B][/SIZE][/FONT][LEFT][FONT=Verdana][SIZE=3]As explained in _**[[COLOR=Red]Scenario 4[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10278677&postcount=10")**_, it's recommended to install Windows first but if you had to install Ubuntu then you decided later on to install Windows, it's possible. This guide will walk you through the steps.

[B][I]It's recommended to read [_[COLOR=Red]Scenario 4[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=10278677&postcount=10") before reading this.
[/I][/B]
This scenario could be easier than [/SIZE][/FONT][FONT=Verdana][SIZE=3]**_[[COLOR=Red]Scenario 4[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10278677&postcount=10")_ **at some point.

[B][SIZE=4]
[/SIZE][/B][SIZE=4][SIZE=3][COLOR=Sienna]**HDD1**[/COLOR] = The Hard Disk Drive where **[COLOR=Sienna]Ubuntu[/COLOR]** is installed
[COLOR=Blue]**HDD2**[/COLOR] = The Hard Disk Drive where **[COLOR=Blue]Windows[/COLOR]** will be installed.[/SIZE][/SIZE][B][SIZE=4] 


There are two methods to do this:[/SIZE][/B]

[/SIZE][/FONT][U][FONT=Verdana][SIZE=5][COLOR=Navy][B]
Method (A)[/B][/COLOR][/SIZE][/FONT]
[/U][FONT=Verdana][SIZE=3]
[COLOR=Red]**Note:**[/COLOR] You need to have basic Computer and Hardware knowledge. If you have never looked inside your Computer Box/Case/Tower then perhaps it's time to do that. If you think you can not do it, then skip to **[COLOR=Navy]Method B[/COLOR]**. 

This is the easiest way ever.

[/SIZE][/FONT][FONT=Verdana][B][U][SIZE=3] Steps
[/SIZE][/U][/B][SIZE=3]1) As always, it's recommended to backup your important data/files. Use External HDD if possible.

2) Turn your machine OFF.

3) Open your Computer Case/Tower and your machine from inside should look similarly like this:

[IMG]http://ubuntuforums.org/picture.php?albumid=2139&pictureid=7271[/IMG]

[/SIZE][/FONT][FONT=Verdana][SIZE=3]
I hope the image is clear enough.
ALL what you have to do is:
**Disconnect** the _Power Cable_ and _The Data Cable_ from [/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Sienna]**HDD1**[/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3].

Even if you have never done this before in your life, it's so much easy. Just make sure to unplug it nicely. Don't use force.

4) Turn you machine ON.

5) Enter BIOS **JUST** to make sure your other HDD ([/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue]**HDD2**[/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3]) has been recognized by BIOS. If it's recognized and BIOS can read [/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue]**HDD2 **[COLOR=Black]information (size, etc) then you're fine.

Before you Save and Exit from BIOS, make sure your machine set to boot first from CD-ROM then HDD (which is [/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue]**HDD2**[/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=Black] in this case).

Save and Exit now.

6) Insert your Windows Disk and start Windows Installation.
Remember, Windows will use the Entire Disk now so no need to worry about partitions, etc. [/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue]**HDD2 **[COLOR=Black]will be used by Windows ONLY.

7) Once you finish installing Windows, make sure you can login to it and everything is fine. Try to shutdown your machine or restart it to make sure everything is ok and Windows is bootable with no issues.

8 ) Turn your machine OFF.

9) Reconnect the Power Cable and the Data Cable to [/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Sienna]**HDD1**[/COLOR][/SIZE][/SIZE][/SIZE][/FONT].

[FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=Black]10) Turn your machine ON.

11) Enter BIOS and make sure your BIOS can detect both HDDs (**[COLOR=Sienna]HDD1[/COLOR]** and **[COLOR=Blue]HDD2[/COLOR]**).

**12)** **Make sure your machine will boot first from **[/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=Black]**[COLOR=Sienna]HDD1[/COLOR]**[/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=Black]** NOT from **[/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=Black]**[COLOR=Blue]HDD2[/COLOR]**[/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=Black]**.[COLOR=Red] This is very important step[/COLOR].**

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7174[/IMG]

As always, if your BIOS does not look like the above image then you need to refer back to your Motherboard Manual.

13) Save and Exit

14) You should be able to login to Ubuntu but you will see nothing about Windows. Don't panic, take it easy :)

15) Once you login to Ubuntu, go to

Applications > Accessories > Terminal 

Run this command:

[/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT]```
sudo update-grub

```[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7254[/IMG]
***IN YOUR CASE, WINDOWS SHOULD BE FOUND ON: /dev/sdb1***


[FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=Black]16) Restart/Reboot your machine and make sure you're able to login to both Windows and Ubuntu.

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7149[/IMG]
[/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT]***IN YOUR CASE, WINDOWS SHOULD BE FOUND ON: /dev/sdb1***
[FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=Black]


17) You are DONE :)





[/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT]_[FONT=Verdana][SIZE=5][COLOR=Navy]**Method (B)**[/COLOR][/SIZE][/FONT]_
[FONT=Verdana][SIZE=3]
This is an alternative method if you feel you can't go for Method (A). However, the chance of errors in this method is higher.

[/SIZE][/FONT][FONT=Verdana][B][U][SIZE=3] Steps
[/SIZE][/U][/B][/FONT][FONT=Verdana][SIZE=3]
1) As always, it's recommended to backup your important data/files. Use External HDD if possible.

2) Insert your Windows Disc and Restart/Reboot your machine

3) Enter BIOS

4) As a reminder:

[/SIZE][/FONT]> [FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Sienna]**HDD1**[/COLOR] = The Hard Disk Drive where **[COLOR=Sienna]Ubuntu[/COLOR]** is installed
[COLOR=Blue]**HDD2**[/COLOR] = The Hard Disk Drive where **[COLOR=Blue]Windows[/COLOR]** will be installed.[/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana]Make sure [/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue]**HDD2 **[/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3]is the "first" HDD to boot from. [/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Sienna]**HDD1**[/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3] has Ubuntu already and you don't need to use that HDD as of now. You need to install Windows on the 2nd HDD which is in this case [/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue]**HDD2**[COLOR=Black].[/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT]

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7175[/IMG]

[FONT=Verdana][B]
Before you exit, make sure your machine will boot "first" from your CD-Drive. 

Save and Exit after that.

[/B][/FONT][FONT=Verdana][SIZE=3]5) Start **[COLOR=Blue]Windows[/COLOR]** Installation on [/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue]**HDD2. **[COLOR=Red]During Installation, make sure you'll install Windows on **[COLOR=Blue]HDD2[/COLOR]** not **[COLOR=Sienna]HDD1[/COLOR]**.[/COLOR]
[B]
[U][COLOR=Purple][COLOR=DarkOrchid][COLOR=DarkGreen]Tip:
[/COLOR][/COLOR][/COLOR][/U][/B][COLOR=DarkGreen]It's good idea to use "GParted" to format HDD2 before installing Windows specially if HDD2 had been used before by any Linux System.
[I]
- Note that GParted needs to be installed because starting from Ubuntu 10.04, GParted is not installed by default with Ubuntu.

- To install GParted:

Applications > Accessories > Terminal

[/I][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT]```
*sudo apt-get update*
``````
*sudo apt-get install gparted*
```[FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=DarkGreen][I]

You'll find it under:
System > Administration

OR

You could use the LiveCD for Ubutnu.


[/I][COLOR=Black]6) Make sure you're able to login to Windows.

7) Reboot/Restart your machine and Enter BIOS

8 ) Now, make sure **[COLOR=Sienna]HDD1[/COLOR]** is set to be the first HDD to boot form while **[COLOR=Blue]HDD2[/COLOR]** is the second. THIS IS A MUST.

>> **Same as Step 12 in **[/COLOR][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][B][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=DarkGreen][COLOR=Black][COLOR=Navy]Method (A).[/COLOR][/COLOR][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT]
[/B][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=DarkGreen][COLOR=Black] 
then Save and Exit.


9) You should be able to login to Ubuntu. If not, it means something is wrong:

a) Reboot your machine and double check your BIOS Settings.

[B]if not
[/B] 
b) Try to reverse the priorities (check step4 in this method). Make sure you're able to boot and login to Windows

[B]if not
[/B] 
c) Refer back to the ***Troubleshooting Guide*** in this thread - [COLOR=Red]**Coming Soon**[/COLOR].


10) From Terminal *( Applications > Accessories > Terminal), *run this command:

[/COLOR][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT]```
[FONT=Verdana]sudo update-grub[/FONT]
```[FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=DarkGreen][COLOR=Black]

This is exactly the same as step 15 in **[COLOR=Navy]Method (A)[/COLOR]**.


11) Restart/Reboot your machine and you should see the same image as shown in Step 16 - [/COLOR][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=3][SIZE=4][SIZE=3][COLOR=Blue][COLOR=DarkGreen][COLOR=Black]**[COLOR=Navy]Method (A)[/COLOR]**[COLOR=Navy][COLOR=Black].


12) And you're DONE :)


I know it seems easier but as I mentioned before, something might go wrong if you don't pay much attention to each step.


[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/FONT][/LEFT]
[/CENTER]

---

### Post by amjjawad on 2011-01-06
[CENTER][FONT=Verdana][SIZE=4][B]_[COLOR=Red]Scenario 6[/COLOR]_: [U]Dual Booting System - Windows XP is already installed and Install Ubuntu 10.04 on USB Drive

[/U][/B][/SIZE][/FONT][LEFT][FONT=Verdana]
[U][B][SIZE=3]Introduction[/SIZE]
[/B][/U]Most of Linux Distributions can be installed on an [_USB-Drive_]("http://en.wikipedia.org/wiki/USB_flash_drive") and run from there. 
Nowadays, USB Flash Drives became cheaper and with larger size than before. Imagine how easy and nice to have your OS every where you go inside your pocket? isn't that lovely?

To be specific, Ubuntu 10.04 (and 10.10) can be installed on USB Flash Drives and/or [_External HDDs_]("http://en.wikipedia.org/wiki/USB_flash_drive#External_hard_disk") with USB Connection.

You may wonder **why do I have to do that while I can use my i[SIZE=3]nternal HDD?[/SIZE]**[SIZE=3]
The answe[/SIZE]r is very easy. Ubuntu (*[SIZE=2]and other Linux Distributions[/SIZE]*[/FONT][FONT=Verdana]) is giving you more options to install it ***not*** only on your ***internal HDD*** that you perhaps never seen before but also give you more choices/options to install it on ***External HDD or USB Flash Drive.***


[COLOR=Red][U][B]Advantages of Using This Kind of Installation
[/B][/U][/COLOR]
1) Trying Ubuntu for the first time. It's true that you could do that by using the [LiveUSB]("https://help.ubuntu.com/community/Installation/FromUSBStick") but it's also good to learn how to install Ubuntu on an USB Flash Drive.

2) If you are not willing to do any major changes to your system, you could just install Ubuntu on an External HDD or an USB Drive.

3) If you don't want to change your HDD partitions or you don't have much space on your HDD and don't have an External HDD. Probably this is a rare case.

4) Take your OS (Ubuntu) with you wherever you go.

And there might be some other advantages.




[/FONT][FONT=Verdana][SIZE=3]**_Requirements:_**[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=3]Ubuntu 10.04 LiveCD
USB Flash Drive - *[COLOR=Red]*Minimum 4GB[/COLOR]*.
or
External HDD.

**[COLOR=Red]* [/COLOR]**[COLOR=Red]4GB is the minimum space you need to install Ubuntu 10.04 but that won't be flexible for daily use.



[COLOR=Black][U][B]Steps
[/B][/U]
1) I know I'm very cautious but _**better safe than sorry**_. I guess you know what I mean. Backup always comes first :)

2) Insert your LiveCD in your CD-Drive and Plug your USB Drive (or your External HDD) to your machine then Restart/Reboot.

3) Enter BIOS.

4) Make sure your BIOS is set as follows:


a) Your CD-Drive must be the first "device" to boot from.

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]



b) Your USB Drive must be the first HDD to boot from. Most of BIOS detect any USB Drive as HDD and refer to it by: **USB-HDD**.

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]


C) Save and Exit.[/COLOR][/COLOR][/SIZE][/FONT][SIZE=3]


[FONT=Verdana]5)[/FONT] [/SIZE][FONT=Verdana][SIZE=3]Your Machine will start booting from the LiveCD. Press any key, select your language from the list and choose "**_[Try Ubuntu without installation]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7132")_**".


6) Once you get the Live Desktop, start **_[GParted]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7133")_**. 

It's always **"better"** to start partitioning **"before"** installation.


7) [/SIZE][/FONT][FONT=Verdana][SIZE=3]Make sure to _[select your USB-Drive from GParted List]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7192")_. In this guide, it's **[COLOR=Navy]sdb[/COLOR]**. [B][COLOR=Red]
sda is your Windows HDD. Please, Don't touch that.[/COLOR][/B]


8 ) [/SIZE][/FONT][FONT=Verdana][SIZE=3]Now, just follow these steps as per the images:

a) [_Right Click on sdb1 and choose "Delete"_]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7193")
Then, click on the **[COLOR=Green]GREEN TICK[/COLOR]** icon to apply the change.

b) You'll see unallocated space. _[Right click on that unallocated space and choose "New".]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7194")_

c) You'll see a new window. Choose "Primary Partition" and "ext4" as a file system and then decide the size of your partition. [_That's will be your root partition_]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7195"). Then Click "Add".

>> You need to read [[COLOR=Red]_**this guide**_[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition") to understand what I'm talking about, especially if you're new to Ubuntu.

d) A new partition will be created after that. Whatever left as  unallocated space, please right click on that gray space and yet again _[choose "New"]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7196")_. 

e) Create your swap partition as per [_this image_]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7197"). Then Click "Add".

f) After that, all what you need to do is click "Apply", the green tick icon. You'll have then two partitions: **[COLOR=Navy]sdb1[/COLOR]** and [COLOR=Navy]**sdb2**[/COLOR].

[SIZE=5][COLOR=Red][B]_Please Note:_
[/B][/COLOR][/SIZE]
[COLOR=Red]**Note 1:**[/COLOR] You're trying to install Ubuntu on 4GB USB Dirve. /home partition is not required here. After all, /home is not a must but it's recommended. 

If you're using (for example) an External HDD which is ... say 20GB, */home* partition can be included. However, just keep in mind that (IMHO) **installing Ubuntu on an _External HDD or USB Drive_ is [COLOR=Red]temporary[/COLOR] and [COLOR=Red]not permanent. [/COLOR]**[COLOR=Red][COLOR=Black]Having that said, /home partition is not required.[/COLOR][/COLOR]

[COLOR=Red]**Note 2: **[COLOR=Black]If you're using 4GB USB Drive, don't create more than 512MB as a SWAP Partition. If you're using 8GB USB Drive, then create larger SWAP Partition if required.
After you finish from installation, you'll have 1GB of free space. Creating larger SWAP Partition means less free space.

[I]I don't want to go deeper in this. There are some points I'm avoiding to explain here. After all, this guide must be plain and simple not complicated.
[/I]

[/COLOR][/COLOR]
9) Once done from partitioning, close GParted and click on "Install Ubuntu" icon on your Live Desktop.


10) [/SIZE][/FONT][FONT=Verdana][SIZE=3]When you reach "_**[Step 4]("https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step4b.png")**_ in the [_**Graphical Guide**"_]("https://help.ubuntu.com/community/GraphicalInstall"), you need to select the last options which is:
[B]Specify Partitions Manually (Advanced)

[/B][I]The [_Graphical Guide_]("https://help.ubuntu.com/community/GraphicalInstall") will help you if you're new to Ubuntu.
[/I]

11) [/SIZE][/FONT][FONT=Verdana][SIZE=3]As per [**_this image_**]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7198"), you need to select **[COLOR=Navy]/dev/sdb1[/COLOR]** which is the first partition in **[COLOR=Navy]sdb[/COLOR]** [/SIZE][/FONT][COLOR=Red]***[FONT=Verdana][SIZE=1](your USB Drive OR External HDD)[/SIZE][/FONT]***[/COLOR][FONT=Verdana][SIZE=3] and that was the partition [/SIZE][/FONT][FONT=Verdana][SIZE=3]**[COLOR=Navy](sdb1)[/COLOR]**[/SIZE][/FONT][FONT=Verdana][SIZE=3] you created using GParted ***before*** you start the installation process.


12) [/SIZE][/FONT][SIZE=3][FONT=Verdana][SIZE=3]Right click/Double Click/Click **Change** on **[COLOR=Navy]/dev/sdb1[/COLOR]**.

13)  [/SIZE][/FONT][/SIZE][FONT=Verdana][SIZE=3]A new [**_window will pop up_**]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7199"). Please, set the following:

a) Use as > >  [COLOR=Red]**ext4**[/COLOR]
b) Format the partition >>  [COLOR=Red]**tick**[/COLOR] - means yes.
c) Mount Point >>   [COLOR=Red]**/** [COLOR=Black]-[/COLOR][/COLOR] means this is the root partition.

Select OK in this window. 

Note that you don't have to change anything in [/SIZE][/FONT][FONT=Verdana][SIZE=3]**[COLOR=Navy]/dev/sdb2[/COLOR]**  because this is the swap partition which you already created before  using GParted. The installer will detect that partition so you don't  need to do anything here.

**Forward** to move to the next step.


14) [/SIZE][/FONT][FONT=Verdana][SIZE=3]When you reach step 8 (***Ready to install***) which is the  final step, you'll see a list of all the changes you've made since the  beginning of the installation process. 
In the bottom, you see "**Advanced** ...". Click on that one.



[SIZE=5]15)[/SIZE] **[SIZE=5]The Boot Loader Step[/SIZE]**

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7200[/IMG]

[B][COLOR=Red]Make sure to install the _[Boot Loader]("http://en.wikipedia.org/wiki/Booting")_ ([_GRUB2_]("https://help.ubuntu.com/community/Grub2")) in the MBR of _[COLOR=Navy]sdb[/COLOR]_ which is your *[COLOR=Black]USB Drive[/COLOR]* or your[COLOR=Black]* External HDD*[/COLOR].
[/COLOR][/B]
Failure to install the Boot Loader in the MBR of sdb will cause some problems later on which perhaps you won't even notice when you finish the installation.

[B][U][SIZE=5]Further Explanation:

[/SIZE][/U][/B][/SIZE][/FONT][FONT=Verdana][SIZE=3]a) You already have Windows Installed on your Internal HDD (**[COLOR=Navy]sda[/COLOR]**) and Windows Boot Loader is installed in the **MBR** of **[COLOR=Navy]sda[/COLOR]**.
Installing GRUB2 (Ubuntu's Boot Loader) in the **MBR** of **[COLOR=Navy]sda[/COLOR]** with this kind of setup is A BAD IDEA. Your Machine will NOT boot anymore UNLESS the USB Drive or the External HDD is plugged in.

b) Installing Ubuntu Boot Loader in the **MBR **of  the USB-Drive or the External HDD (**[COLOR=Navy]sdb[/COLOR]**) means your machine will be bootable and you can login to Windows without the need of plugging your USB Drive or External HDD in your machine.

c) Also, by installing Ubuntu Boot Loader in the **MBR** of the USB-Drive or the External HDD, you created a bootable USB-Drive. Whenever you plug it to your machine,  turn it on and set the BIOS settings to boot from that USB-Drive, you'll  be able to boot up your machine and GRUB2 menu will show up. Then you  can select whether to start Ubuntu or Windows (or any other OS you have  installed already on your internal HDD).


16) Now, just click Install and that's all.

17) As always, you should see something like **_[this]("http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7149")_** after your machine will be rebooted.

18 ) You're DONE :)



[U][SIZE=5][COLOR=Red][B]IMPORTANT NOTE:
[/B][/COLOR][/SIZE][/U]
One disadvantage could be a bit annoying in this kind of setup is: Everytime you want to boot from your USB-Drive or External HDD, it must be plugged in, enter BIOS and make sure your system will boot first from that USB or External HDD.
You may want to keep it plugged in to avoid that step.

However, if your USB-Drive or External HDD is NOT plugged in, you do NOT need to enter BIOS and set your internal HDD to be the first HDD to boot from. That will be done automatically by your BIOS. There is no external device plugged in so BIOS will not detect that and your internal HDD is back to be the first HDD to boot from.
Of course, in this case, GRUB2 will not show up. Your machine will boot from Windows normally like nothing happened.


[/SIZE][/FONT][/LEFT]
[/CENTER]

---

### Post by amjjawad on 2011-01-06
[CENTER] [SIZE=5][B][COLOR=Navy][FONT=Verdana]
Part 2 - [/FONT][FONT=Verdana]Installation Problems 
& 
Troubleshooting

[/FONT][/COLOR][/B][/SIZE][LEFT][FONT=Verdana][SIZE=3][B][U]Preface

[/U][/B][/SIZE][/FONT][FONT=Verdana]When I first started this guide (Part 1), it was not in my intention to write more than just an installation guide to cover everything about Dual Booting Installation from A-Z. That was my initial plan.
Day after day, I realized it's also important to finish what I've started. The necessity of covering everything indeed from A-Z means everything should be discussed and explained whether it's "Installation" - ***Part 1*** or "Installation Problems & Troubleshooting". Thus, ***Part 2*** was born.



[/FONT][FONT=Verdana][SIZE=3][B][U]Aim of this Part
[/U][/B]
There are three (3) main aims/goals for this Part:

1- This is Part 2 of the Dual-Boot Installation Guide. In case something will go wrong, here's the place to start reading from. Although I made sure to explain everything in details (Part 1) and by following each step in Part 1 should not lead to any problem but errors, mistakes and/or problems might happen. We're controlled by the hardware and the software. If one thing goes wrong, the whole process will stop.

2- Whether you're a New User to Ubuntu, a Beginner User or even Intermediate User, this guide should help you. It's not necessary to read Part 1 before reading this part. You can skip to this part (Part 2) and you should find what you're looking for. However, there's no harm to check Part 1 as this will add more useful information to your experience with Ubuntu and Dual-Booting.

3- I believe if one follows the correct steps, he/she should not face any more problems or at least he/she will be able to fix/solve the same problem in case it occurs once more.
Nothing better than Fixing and Troubleshooting your system by yourself.

Above are my main aims/goals to write this part (Part 2).



[/SIZE][/FONT]      [FONT=Verdana][SIZE=3][B][U]About this Part
[/U][/B]
As always, t[/SIZE][/FONT][FONT=Verdana][SIZE=3]his part has been  written by  myself. I’ve never taken any single word from any other  website,  guide, post or whatever source you could think about. This  guide has  been written based on a real experience and the most recent  experiment  of installing Windows and Ubuntu on a PC.
However, I'm going to include external links when it's necessary. 

This Part should cover most (I'm not going to say ALL) of the problems that might occur "during installation" or "after installation". Note that, this is a Dual-Boot Guide and so this Part will continue to discuss the problems which might occur when Dual-Booting System is being installed.

[SIZE=5][U][B][SIZE=4][COLOR=Red]Also note that:[/COLOR][/SIZE]
[/B][/U][/SIZE]a) This part will be updated on daily basis/regular basis so more problems with solutions might be added later on.

b) No matter how many problems (and the solutions) will be discussed here, there will be "still" other problems out there. I'll make sure to cover the most common and general problems. 

c) [COLOR=Red]If you have faced a problem when Dual-Booting and you know how to fix it and that problem _**IS NOT**_ listed here, [B]please feel free to share it with us. 
[/B][/COLOR] 


There will be two main sections so far:
[/SIZE][/FONT][B]
[/B][FONT=Verdana]**[SIZE=3][COLOR=Navy][2-1] Installation Problems/Problems During Installation:[/COLOR][/SIZE]**[/FONT][FONT=Verdana][COLOR=Navy][SIZE=3][/SIZE][/COLOR][/FONT][FONT=Verdana]In this section, I'll discuss the [/FONT][FONT=Verdana][COLOR=Red]**"General Problems"**[/COLOR][/FONT][FONT=Verdana] that you might face ***before*** you start your Installation Process and/or ***during*** the Installation Process.[/FONT][CENTER][LEFT][FONT=Verdana][SIZE=3]         
[/SIZE][/FONT][FONT=Verdana]**[SIZE=3][COLOR=Navy] [2-2] Problems After Installation: [/COLOR][/SIZE]**[/FONT][FONT=Verdana][SIZE=3][COLOR=Navy][COLOR=Black]In this section, I'll discuss the [COLOR=Red]**"General Problems"**[/COLOR] that you might face ***after*** the Installation Process.

[/COLOR][/COLOR][/SIZE][/FONT] [/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---


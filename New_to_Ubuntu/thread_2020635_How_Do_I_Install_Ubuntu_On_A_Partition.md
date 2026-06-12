---
title: "How Do I Install Ubuntu On A Partition?"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by DoctorVarney on 2012-07-08
I created a fresh instalation of Windows XP so I could partition my hard drive to allow one side for Windows and the other for Ubuntu.

Now when I come to install Ubuntu from my Ubuntu boot CD, I am faced with a dialogue I struggle to comprehend, during the installation process.

My goal is to install Ubuntu on another partition, separate from where I installed Windows.  I can't work out if this installation process means it's going to install Ubuntu on the same partition as Windows or onto another one that Ubuntu will create.  When I try to install to  the partition I left free for Ubuntu, I get an error message, saying "no root directory" or something like that.

I'm not confident of this step because I don't think I fully understand the process of HD partitioning to begin with, so I need some guidance.  Please can you explain to me what I should do?

---

### Post by Shadius on 2012-07-08
"No root directory" means that you haven't created a "root" for Ubuntu. Ubuntu uses "/" to symbolize the "root". Before I begin to advise you, I'd need some information about your setup just so I give you the correct information. We can start by you providing a screenshot from GParted, that way I can see what your partitions look like. To do this, boot from your Ubuntu LiveCD, select "Try Ubuntu", go to Dash (Ubuntu Logo top-left), and type in GParted, then select it. It will open up with your device information, take a screenshot of that with the *PrintScreen* button and post back here.

---

### Post by kansasnoob on 2012-07-08
Please begin by posting the output of this command from a live session:

```
sudo parted -l
```

---

### Post by DoctorVarney on 2012-07-09
Thank for you for your time, Shadius.  I couldn't figure out how to save the image from the screenshot but I've been able to note it accurately.

Information from Gparted is as follows:[INDENT][COLOR=DarkOliveGreen]_Partition:_[/COLOR] /dev/sda 1 [COLOR=DarkOliveGreen] _File system:_[/COLOR] fat32  [COLOR=DarkOliveGreen]_Size:_ [/COLOR]19.53 GiB [COLOR=DarkOliveGreen]  _Used:_[/COLOR] 5.60 GiB  [COLOR=DarkOliveGreen]_Unused:_[/COLOR] 19.93 GiB   [COLOR=DarkOliveGreen]_Flags:_[/COLOR] boot, lba

[COLOR=DarkOliveGreen]_Partition:_ [/COLOR]/dev/sda 2  [COLOR=DarkOliveGreen]_File system:_[/COLOR] extended  [COLOR=DarkOliveGreen]_Size:_[/COLOR] 17.71 GiB [COLOR=DarkOliveGreen] _Used:_[/COLOR] _  [COLOR=DarkOliveGreen]_Unused:_ [/COLOR]_ [COLOR=DarkOliveGreen]Flags:[/COLOR] lba[INDENT][COLOR=DarkOliveGreen]_Partition:_[/COLOR] /dev/sda 5 [COLOR=Red](!)[/COLOR] [COLOR=DarkOliveGreen] _File system:_[/COLOR] unknown  [COLOR=DarkOliveGreen]_Size:_[/COLOR] 17.71 GiB  [COLOR=DarkOliveGreen]_Used:_[/COLOR]  _  [COLOR=DarkOliveGreen]_Unused:_  [/COLOR]_   [COLOR=DarkOliveGreen]_Flags:_ [/COLOR]lba
[/INDENT][/INDENT][INDENT][COLOR=Blue]_Information from:[COLOR=Blue] /dev/sda 5[/COLOR]_[/COLOR][INDENT][COLOR=Blue]_Status:_ [COLOR=Black]Not mounted[/COLOR][/COLOR]
[/INDENT][INDENT][COLOR=Red]_Warning:_[/COLOR]
[COLOR=Red]Unable to detect file system!  Possible reasons are:[/COLOR]
[/INDENT][INDENT][INDENT][COLOR=Red]_ The file system is damaged.[/COLOR]
[COLOR=Red]_ The file system is unknown to Gparted.[/COLOR]
[COLOR=Red]_  There is no file entry system available (unformatted)[/COLOR]
[COLOR=Red]_The device entry /dev/sda 5 is missing.[/COLOR]
[/INDENT][/INDENT][/INDENT]

---

### Post by DoctorVarney on 2012-07-09
> **kansasnoob said:**
> Please begin by posting the output of this command from a live session:

```
sudo parted -l
```

Thanks, though I think you assume prior understanding on my part.  Assuming 'terminal' was the place to enter this command, the command appeared not to be recognised.  By trying a few variants of the command, the volume did not appear to be recognised, but, as I say, my interpretation isn't to be fully trusted in these matters at present.

---

### Post by nothingspecial on 2012-07-09
During the installation process you will be asked "How do you want to install Ubuntu?"

Choose "Something Else"

Select the partition you would like to install Ubuntu on and click change.

Choose to use it as an ext4 journaling file system

Give a mountpoint of / from the drop down choices.

Tick/check the format box.

[COLOR="Red"][SIZE="2"]Do not do anything to the partition that contains windows.[/SIZE][/COLOR]

That's it.

---

### Post by mastablasta on 2012-07-09
it's a small letter L on the end of that copmmand. hint: you can copy and paste commands into terminal (no need to type them ;-) ).
 
install to this partition: _[COLOR=#556b2f]Partition:[/COLOR]_ /dev/sda 5 
 
you left it as empty disk space right? install will format it and repartition it. you can also do this using gparted.
[COLOR=#ff0000][/COLOR]

---

### Post by DoctorVarney on 2012-07-09
> **nothingspecial said:**
> During the installation process you will be asked "How do you want to install Ubuntu?"

Choose "Something Else"

Select the partition you would like to install Ubuntu on and click change.

Choose to use it as an ext4 journaling file system

Give a mountpoint of / from the drop down choices.

Tick/check the format box.

[COLOR=Red][SIZE=2]Do not do anything to the partition that contains windows.[/SIZE][/COLOR]

That's it.

But I get messages such as "If you create a partition here it will delete all other partitions..." etc.

When I select that unallocated space (where I want to install Ubuntu) the option to "Choose" is greyed and I can't seem to do anything with it.

Evidently, Ubuntu isn't going to install on unallocated areas of the hard disk.  Somehow, I need to format a partition in order to install it and I don't know how to do that.

The only thing it does seem to want to do is "Do *things* to the partition that contains Windows".

---

### Post by wilee-nilee on 2012-07-09
> **DoctorVarney said:**
> But I get messages such as "If you create a partition here it will delete all other partitions..." etc.

When I select that unallocated space (where I want to install Ubuntu) the option to "Choose" is greyed and I can't seem to do anything with it.

Evidently, Ubuntu isn't going to install on unallocated areas of the hard disk.  Somehow, I need to format a partition in order to install it and I don't know how to do that.

The only thing it does seem to want to do is "Do *things* to the partition that contains Windows".

Take a screenshot of gparted using the screenshot app from the live cd, open a reply click the paperclip in the reply panel and load the screenshot to the reply.

---

### Post by DoctorVarney on 2012-07-09
> **mastablasta said:**
> it's a small letter L on the end of that copmmand. hint: you can copy and paste commands into terminal (no need to type them ;-) ).

I'd love to but, I'm not sure how this would work when I turn the machine off to boot from my CD drive. :confused:
 
> install to this partition: _[COLOR=#556b2f]Partition:[/COLOR]_ /dev/sda 5 
 
> **mastablasta said:**
> you left it as empty disk space right? install will format it and repartition it. you can also do this using gparted.


Yes, I did.  But it doesn't seem as though I'm being given the option to do so by the installer.

Oh, I can use Gparted to format that partition ([COLOR=SeaGreen]dev/sda 5[COLOR=Black])[/COLOR][/COLOR][COLOR=Black] [/COLOR]?
That sounds more like it.  I'll give it a go.  I take it this works on the Live Version?

---

### Post by DoctorVarney on 2012-07-09
Okay, guys - I'm using Firefox in Ubuntu from the live CD.  This more like it.  I didn't realise at first that I could actually *use* Ubuntu in live mode. :D

Okay, how do I post the screenshot?

The problem I have now is that when I go:  - [COLOR=SeaGreen]Device > Partition Table[/COLOR] -
I get a message saying: [COLOR=Red]Warning!  This will erase ALL data on the ENTIRE disk.[/COLOR]
Obviously, I'm fearful of doing that.  I'm not sure if it means it will delete all data (obviously none present) on the partition or wipe my entire hard disk, taking Windows and everything else with it.

Please note, you really need to treat me as a foreigner who does not know the alphabet.  I pick things up fast but this is completely new to me and half the things that are being said involve commands and  processes I'm not familiar with yet.  Sorry about that.

[QUOTE=Mastablasta]you can also do this using gparted.[/QUOTE]

I'd love to.  Please can you explain how?

---

### Post by Shadius on 2012-07-09
> **DoctorVarney said:**
> Okay, guys - I'm using Firefox in Ubuntu from the live CD.  This more like it.  I didn't realise at first that I could actually *use* Ubuntu in live mode. :D

Okay, how do I post the screenshot?

The problem I have now is that when I go:  - [COLOR=SeaGreen]Device > Partition Table[/COLOR] -
I get a message saying: [COLOR=Red]Warning!  This will erase ALL data on the ENTIRE disk.[/COLOR]
Obviously, I'm fearful of doing that.  I'm not sure if it means it will delete all data (obviously none present) on the partition or wipe my entire hard disk, taking Windows and everything else with it.

Please note, you really need to treat me as a foreigner who does not know the alphabet.  I pick things up fast but this is completely new to me and half the things that are being said involve commands and  processes I'm not familiar with yet.  Sorry about that.



I'd love to.  Please can you explain how?

Yes, you can use Ubuntu from the LiveCD without actually doing an install. The LiveCD serves as various tools, whether getting a taste of the Ubuntu operating system or using it to repair things. The screenshot should be located either in your Home folder or your Pictures folder. I'm assuming you're using Ubuntu 12.04? If so, on the left side of the desktop is the Launcher, there's a folder icon there (hovering over it will display "Home Folder" caption), click it and locate your screenshot. Now to post it, come back to here, reply and attach the screenshot using the paperclip icon in the message toolbar. It will open up a window for you to browse for your screenshot. Again, find your screenshot and upload it and submit your reply. 

I hope my instructions were clear enough. :) If you don't understand something, just ask. I will try my best to help you with any issue you come across. I can understand feeling lost when you're new to something as I was an absolute beginner myself (still kind of am). :)

---

### Post by DoctorVarney on 2012-07-09
> **nothingspecial said:**
> During the installation process you will be asked "How do you want to install Ubuntu?"

Choose "Something Else"

Select the partition you would like to install Ubuntu on and click change.

Choose to use it as an ext4 journaling file system

Give a mountpoint of / from the drop down choices.

Tick/check the format box.

[COLOR=Red][SIZE=2]Do not do anything to the partition that contains windows.[/SIZE][/COLOR]

That's it.

Okay, I got as far as being able to do the above.  Now I get a message about swap space.  It says that I have not allocated any swap space and that I need to.  I know what this means, but what do I have to do next to resolve this?

---

### Post by Shadius on 2012-07-09
> **DoctorVarney said:**
> Okay, I got as far as being able to do the above.  Now I get a message about swap space.  It says that I have not allocated any swap space and that I need to.  I know what this means, but what do I have to do next to resolve this?

Just as how you selected the filesystem for Ubuntu as EXT4, designate an amount of space for Ubuntu to use as swap space. Generally, I think the recommened amount of swap space is supposed to be twice the amount of RAM you have.

---

### Post by DoctorVarney on 2012-07-09
> **Shadius said:**
> I'm assuming you're using Ubuntu 12.04?

Yes, I am using Ubuntu 12.04.

 > **Shadius said:**
> Now to post it, come back to here, reply and attach the screenshot using the paperclip icon in the message toolbar. It will open up a window for you to browse for your screenshot. Again, find your screenshot and upload it and submit your reply. 

Okay, I've attached it.  Not sure how to make it appear in my message though.

> **Shadius said:**
> I hope my instructions were clear enough. :) If you don't understand something, just ask. I will try my best to help you with any issue you come across. I can understand feeling lost when you're new to something as I was an absolute beginner myself (still kind of am). :)

Yes, really good for me.  Thank you! ):P

---

### Post by Shadius on 2012-07-09
Also, as one user suggested, running the following command from the Terminal will help:

```
sudo parted -l
```

The Terminal is located on the Launcher as well. Once you click on the Terminal, it will open for you to type in the command. Type in the command and press *Enter*. You will be prompted for your password, type it in and press *Enter* again. Then post back the results here by highlighted the results, right-click, select **Copy** then paste it between code tags in a reply here by pressing the "#" symbol. It will give you tags that looks like this: [CODE][CODE]

---

### Post by DoctorVarney on 2012-07-09
> **Shadius said:**
> Also, as one user suggested, running the following command from the Terminal will help:



Okay, thank you for the explanation.

The output from that command is as follows:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD400BD-75MR (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  21.0GB  21.0GB  primary   fat32        boot, lba
 2      21.0GB  40.0GB  19.0GB  extended               lba
 5      21.0GB  40.0GB  19.0GB  logical                lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$
```

The reason I was unable to copy & paste before, was that I was rebooting to switch from Linux to Windows.  I don't need to do that now.

---

### Post by mastablasta on 2012-07-09
it does seem a bit strange. if that partition 2 is empty (i.e. no filesystem on it) is should be unalocated disk space (like the 8GB on the end of the disk). it's like you cretaed a partition inside partition.
 
anyway this is how install goes: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
if the partition is empty you should be able to install there.
 
otherwise it will want to format it.
 
if oyu manage to get the option "install to largest free disk space" all partition will be done automaticly.
 
oh in linux / (root) is similar to what windows calls C:\
/home - (can be separate partition) is sort fo what My Documents are in Windows
/swap is sort of what page file is in windows (if you have lower than 4 Gb ram i think you need it 2x the size of RAM). e.g. you have 512MB ram you need 1GB swap. but it would be good to have at least 512MB. i tis actually not needed but it is best to have it. in case you run out of ram while working with PC the disk is then used.
 
here is a nice guide (though /home is not necessary to be on separate partition - i don't have it): [http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/](http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/)
 
Here is a nice picture explanaiton of file scheme in Linux : [http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)
 
not that to change any files outside of home (such as new programme install, changing configuration files, changing partitions...) admin user password is required and in ubuntu it usually involves command *sudo* or *gksu* (for graphical interfaces). that way viruses can't inffect the system without you permission (a clever and one of many security layers).

---

### Post by Shadius on 2012-07-09
Okay, so from your screenshot of GParted, you have a hard disk drive of 37.25 GiB and your Windows installation is on a FAT32 filesystem and has 19.53 GiB. Your Windows partition is called */dev/sda1*. [COLOR="Red"]We will not need to touch this![/COLOR] Your second partition, which is called */dev/sda2* is an extended partition, which has another partition called */dev/sda5*. This is what we'll be touching! So when you chose **Something Else** you would have selected */dev/sda5* and made the mount point of /, which is called root by following the instructions as you did earlier. However, something is puzzling me from your screenshot. I don't know why it says "unknown" instead of unallocated space as it shows for the other one. Did you try anything with the */dev/sda5* partition previously?

---

### Post by Shadius on 2012-07-09
Choosing the **Install Ubuntu Alongside Windows**... would be the easier way to do the install. Choosing the **Something Else** option lets you have more control of the partitions, if you know how to set up the partitions. In this case, I think you should choose the option to install Ubuntu alongside Windows, but if you want to have control of your partitions, we can do that method too. I'll be happy to provide some information to get you up to speed about understanding partitioning. :)

---

### Post by DoctorVarney on 2012-07-09
> **mastablasta said:**
> i
anyway this is how install goes: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 

Great!  On the subject of installation options:[INDENT][FONT=Times New Roman]"Select the third option if you know a lot about partitions and want to  manually configure stuff yourself. If you know enough to select the  third option, you don't need a tutorial telling you what to do."[/FONT]

[/INDENT]Except, I DO, because I knew just enough to make the partitions while formatting from my Windows CD...   Just not enough to freestyle it in Linux!  (There's a law which states that there is always someone who knows just enough to m*ss things up. Presently, that '*someone*' unfortunately is me). 

Next option:[INDENT][FONT=Times New Roman]"If you want to install Ubuntu next to Windows so you can choose which  operating system you want at boot-up, select the first option. As  mentioned before, do this only if you don't anticipate even a small  possiblity of returning exclusively to Windows. A traditional dual-boot  can be undone but it's not easy."[/FONT]

[/INDENT]I hope not to want want to return exclusively to Windows - but so far I haven't had the chance to ascertain the dependability of WINE.   The hope is that I won't need to worry about that.  If I could be sure I could do without it, I'd ditch Windows in the blink of an eye.

My big query with this one is that I went to the trouble of installing Windows on a partition so that I could use the other partition for Linux-Ubuntu.   If it goes and installs right next to Windows, on the _*same partition*_, then I feel I will have wasted one half of my available disk space.  If this option installs it to the free partition, then it's the one for me.

Otherwise, I'll need to learn how to make swap space.  That's the part that eludes me the most at present.

---

### Post by mastablasta on 2012-07-09
if oyu install with reformat the swap partition will be created automaticly by installer. if you create swap by yourself then you create a partition in gparted and name it /swap.
 
the easiest way to isntall next to windows XP is to go to windows disk manager and create empty disk space next to it (unformatted) then choose to install to this unformated disk space. it will be formated during install (probably to deafult option ext4) and /swap will be created automaticly. the instalation preety much involves clicking next button and typing in the user name and password.

---

### Post by Shadius on 2012-07-09
> **mastablasta said:**
> if oyu install with reformat the swap partition will be created automaticly by installer. if you create swap by yourself then you create a partition in gparted and name it /swap.
 
the easiest way to isntall next to windows XP is to go to windows disk manager and create empty disk space next to it (unformatted) then choose to install to this unformated disk space. it will be formated during install (probably to deafult option ext4) and /swap will be created automaticly. the instalation preety much involves clicking next button and typing in the user name and password.

Pretty much sums it up.

---

### Post by DoctorVarney on 2012-07-09
Thank you, everyone... a BIG hearty THANK YOU for your efforts!

I now have Ubuntu up and running.  

With a combination of advice in this thread, I've managed to get up and running.  Shadius, Mastablasta and others.

What I did was went back into Windows XP and deleted the partition I'd intended to run Ubuntu on.  Then I went back into Ubuntu (Live CD Version) and installed on what the installer instantly recognised as 'free space'.  Set 4GB of swap (twice my RAM) and hoped for the best.

It worked!  You guys are great!!!

There are some small issues, like trying to work out GNOME desktop but it's early days and I'll post some more questions soon.

---

### Post by Shadius on 2012-07-09
> **DoctorVarney said:**
> Thank you, everyone... a BIG hearty THANK YOU for your efforts!

I now have Ubuntu up and running.  

With a combination of advice in this thread, I've managed to get up and running.  Shadius, Mastablasta and others.

What I did was went back into Windows XP and deleted the partition I'd intended to run Ubuntu on.  Then I went back into Ubuntu (Live CD Version) and installed on what the installer instantly recognised as 'free space'.  Set 4GB of swap (twice my RAM) and hoped for the best.

It worked!  You guys are great!!!

There are some small issues, like trying to work out GNOME desktop but it's early days and I'll post some more questions soon.

Congratulations!

---

### Post by DoctorVarney on 2012-07-09
> **Shadius said:**
> Congratulations!

No.  Congratulations to you, Sir! :)

---

### Post by Shadius on 2012-07-09
> **DoctorVarney said:**
> No.  Congratulations to you, Sir! :)

You said you were experiencing some issues after installation, what were they? Maybe we can help you resolve those too!

---


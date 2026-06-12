---
title: "Total noob installing 12.04 LTS"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by stoneworrior on 2013-07-07
So I have Googled the Sh^%t out of this and I have searched this forum so if this answered here I am sorry I have searched and searched and I GOT NOTHIN. What is frustrating is most people who are familiar with this (Linux) operating system fail to understand the level of ignorance us "newbies" have. Its like you say just run "sudo apt-get (Whatever) then run sudo apt-install (Whatever) and you're good. I'm like Sue who??? and aptitude what??? SO now that I have shown just how stupid I am (I am trying to learn) I have installed Ubuntu 12.04 LTS on a Dell inspiron 14" Ultabook. I could NOT handle windows 8 any longer and the stupid UEI system was not playing well with a dual boot system. My solution was to backup the Windows OS (When I sell the laptop in the future) and wipe it clean and start with a fresh install of Ubuntu stand alone. Well I installed and all has gone well and I have been reading a whole bunch and playing around with learning how to compile code and install programs from the command line and I even got the Android SDK set up and it is working well with my Nexus 4 and Transformer Prime, pushing and pulling files in adb wiping the systems and starting over from scratch by installing factory images then unlocking the bootloaders and rooting again, you know all that stuff us noobs need to do over and over again until it starts to sink in. Anyway I had an error so I sent a bug report and decided to reboot the system. That is when I realized I've been allowing my system to boot on its own and there is actually a menu selection at boot that I have not been paying attention to. This menu is...
 
Ubuntu, with Linux 3.5.0-36-generic
Ubuntu, with Linux 3.5.0-36-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Ubuntu 12.04.2 LTS (12.04) (on /dev/sdb2)
Ubuntu 12.04.2 LTS (12.04) (on /dev/sdb2)

So I rebooted and actually selected the first Ubuntu 12.04.2 LTS (12.04) (on /dev/sdb2) and found that Everything that I have done up to this point is not there. So my question at this point that I am sure will sound stupid to most of you is...
#1 Why do I have all of these options? Memtest is self explanatory but not the rest
#2 What option should I be choosing
#3 If I should be choosing the Ubuntu 12.04.2 LTS option do I need to go through and install all of my apps again and re do all of my tweaks? 

Thank you in advance from a total noob.

---

### Post by tgalati4 on 2013-07-08
It takes 10 years to fully appreciate linux.  So don't be so hard on yourself.  After a year of using it it will be easier.

Each installation of Ubuntu or any Debian-based linux distribution will have at least two menu boot options:  1.  The normal boot up.  2.  A recovery mode which is a command-line, text terminal with root/admin privileges.  This is used to repair your operating system if something goes seriously wrong.

Memtest gives 2 options, one with a video card, and one with a serial port.  The second one probably got installed when you installed the Android SDK.

The first 2 options with the 3.5 kernel were probably installed with the Android SDK, because Ubuntu 12.04 uses the 3.2 version of the kernel.  Ubuntu 12.10 (and Linux Mint 14) uses kernel 3.5.

tgalati4@Mint14-Extensa ~ $ uname -a
Linux Mint14-Extensa 3.5.0-27-generic #46-Ubuntu SMP Mon Mar 25 19:58:17 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Open a terminal:

```
uname -a
```

Will tell you what kernel you are running.  The default boot is normally the top one.  So you have been running 12.10 not 12.04.

The answer to question #3 is yes, any customizations that you performed under 12.10 will need to be redone on 12.04.    You can continue to use 12.10 and just keep 12.04 as a backup or delete it completely and save it for a future update.

---

### Post by KARNVORbeefRAGE on 2013-07-08
[deleted]

---

### Post by stoneworrior on 2013-07-08
I ran the command and what I got makes no sense to me, this was the result...

Linux william-Inspiron-5423 3.5.0-36-generic #57~precise1-Ubuntu SMP Thu Jun 20 18:21:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linuxbut
 
 so I googled it and what I am getting is this is a work in progress that has passed very well 

([http://reports.qa.ubuntu.com/sru/quantal_lts_hwe/version/3.5.0-36.57~precise1-generic/](http://reports.qa.ubuntu.com/sru/quantal_lts_hwe/version/3.5.0-36.57~precise1-generic/) )

 So the way I am understanding this is just like a CM10 nightly, it may work well but I may or may not run into the occasional issue from time to time. That would explain why I had the bug error pop up asking me to report it. So basically by letting my laptop boot up on its own I have essentially been running a "release candidate" when I should have been selecting the 12.04.2 option (Stable Release) that was installed when I installed another application. So basically at this point I am learning that I should read and re-read any and all apps I may install because they may need a different kernel that 12.04 has and I will be installing that kernel to allow an app to work/run? 

So that answers my question on installing all of my applications and tweaks...I need to run 12.04.2 at boot and I need to re do EVERYTHING I just did in the last two days ARG!!!!!!!!!!!! Last question, how do I change the default at boot so I do not have to select it manually, or is that even an option?


Oh and I love ludicrous speed ;-)


[URL="http://reports.qa.ubuntu.com/sru/quantal_lts_hwe/version/3.5.0-36.57~precise1-generic/"]
[/URL]

[IMG]http://www.airport-data.com/forums/files/ludicrous_speed_662.gif[/IMG]

---

### Post by 3rdalbum on 2013-07-08
Ubuntu 12.10 is not a release candidate or a beta or anything like that. It is a 'final' release version like 12.04 and 13.04. It is supported for slightly less than a year as of today, but that's normal.

You can just keep using 12.10 and then upgrade to a later version down the track. 12.04 (and the forthcoming 14.04) is supported for five years, although most people use these long-term support releases for two years or less.

---

### Post by craig10x on 2013-07-08
If you were to re-install ubuntu 12.04 and select the option to have it wipe everything off and just install it alone (i believe you mentioned that is what you were trying to do and not dual booting with windows or another linux install) then what will happen is when you boot up you will just get the splash screen (ubuntu) and then the log in screen to go into the system...none of that page with the various selections...
That's how i have mine set up...i am running 13.04 and when i installed i just had it automatically wipe out what i was running before that (ubuntu 12.10)...

Now if i was dual booting 13.04 with 12.10...then i'd be getting the selection page first...By the way, like you, when i got my new laptop i made restore discs for windows (Just in case needed in the future) and then proceeded to have the installer wipe it out and replace with ubuntu...

---

### Post by leosubhadeep on 2013-07-08
Check your installation media for the right version of Ubuntu. And as [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar241895_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=241895") 				 				 					 						 	[**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895") said already, the first one is your default and most current installation. The "Recovery mode" contains several options too, you might want to check that.

---

### Post by stoneworrior on 2013-07-08
First of all to everyone who has responded I TRULY thank you for your time. You could have read this post and moved on so regardless of the results anyone who takes the time to respond you have my greatest respect. The way I understand it now is someplace down the line after my fresh install of 12.04 I installed something that required the use of 12.10 or greater but since I was using copy and paste in terminal and trusted my sources I didn't realized I was installing 12.10 to get either the app or the tweaks I was looking for. So basically by allowing my computer to boot on its own I was installing everything on my newest install and as it stands I am all good by just leaving well enough alone and understand from this point out I am running 12.10. So going forward with Ubuntu/Linux I need to pay attention to any future installs so I will understand that by installing a certain app or tweak I may be installing a new kernel and in effect upgrading to a new OS. I got so used to using rooted Android and using only trusted sources I just assumed doing the same with Ubuntu was the same basic OP. No where in Android can you install an app or tweak that will change/upgrade your OS version but I do understand running in terminal I did agree to this and if I would have spent a little more time reading on one of my installs I would have known this was happening. At this point my computer is running so much better than it did with windows 8 and EVERYTHING works really well so I am a new Ubuntu convert and will be sticking to it long term and will continue to learn. Thank you everyone for your help!!!!! :-D

---

### Post by farrinux on 2013-07-08
> **stoneworrior said:**
> First of all to everyone who has responded I TRULY thank you for your time. You could have read this post and moved on so regardless of the results anyone who takes the time to respond you have my greatest respect. The way I understand it now is someplace down the line after my fresh install of 12.04 I installed something that required the use of 12.10 or greater but since I was using copy and paste in terminal and trusted my sources I didn't realized I was installing 12.10 to get either the app or the tweaks I was looking for. So basically by allowing my computer to boot on its own I was installing everything on my newest install and as it stands I am all good by just leaving well enough alone and understand from this point out I am running 12.10. So going forward with Ubuntu/Linux I need to pay attention to any future installs so I will understand that by installing a certain app or tweak I may be installing a new kernel and in effect upgrading to a new OS. I got so used to using rooted Android and using only trusted sources I just assumed doing the same with Ubuntu was the same basic OP. No where in Android can you install an app or tweak that will change/upgrade your OS version but I do understand running in terminal I did agree to this and if I would have spent a little more time reading on one of my installs I would have known this was happening. At this point my computer is running so much better than it did with windows 8 and EVERYTHING works really well so I am a new Ubuntu convert and will be sticking to it long term and will continue to learn. Thank you everyone for your help!!!!! :-D

Stone your above assumptions are correct except for a few things.  The first being the two different Ubuntus being installed.  My thinking is this. You said you were dual booting Win 8 and Ubuntu 12.04.  Then you said that you backed up the Win 8 install and did a fresh install of what you thought was Ubuntu 12.04.  First question did you use the exact same installation media that you used when you installed the dual boot?  Heres why I ask.  When dual booting Ubuntu creates it's own partition on the hard drive and installs itself and then adds grub the bootloader where ever you tell it.  When booting a dual boot you would get a similar screen as the one you describe in your original post but it would look something like this

Ubuntu 12.04.2 LTS (12.04) 
Ubuntu 12.04.2 LTS (12.04) (recovery)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 8 

Now if you did not use the exact same Ubuntu install media. Which from the look of it you actually got a hold of Ubuntu 12.10. Then at installation told it to install over windows then you would have what you have. Two different Ubuntu installs. Ubuntu gives you several options at install read it carefully.  The menu you see at boot is called grub2.  There is a software package you can download called Grub Customizer that will let you change a great deal of that menu.  I believe you can even remove the 12.04 entries from the menu.  Keep in mind that it will still be installed, you just won't have the option of selecting it at boot.  As has been said that the top listing is the default usually.  But when dual booting you can change that with grub customizer.  I have been using Ubuntu since 8.10 and dual booting win with it.  I am buy no means as informed as some are here.  But I would like to point out one last thing.  I have never had a package ( software , app etc.) install a knew version of ubuntu on my computer.  It usually works the other way around.  In order to use some of the new software you must upgrade to a newer Ubuntu.  So long as you use software center or APT in terminal I do not think this could happen.  I hope you enjoy using Ubuntu.

---

### Post by stoneworrior on 2013-07-08
> **farrinux said:**
> Stone your above assumptions are correct except for a few things.  The first being the two different Ubuntus being installed.  My thinking is this. You said you were dual booting Win 8 and Ubuntu 12.04.  Then you said that you backed up the Win 8 install and did a fresh install of what you thought was Ubuntu 12.04.  First question did you use the exact same installation media that you used when you installed the dual boot?  Heres why I ask.  When dual booting Ubuntu creates it's own partition on the hard drive and installs itself and then adds grub the bootloader where ever you tell it.  When booting a dual boot you would get a similar screen as the one you describe in your original post but it would look something like this

Ubuntu 12.04.2 LTS (12.04) 
Ubuntu 12.04.2 LTS (12.04) (recovery)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 8 

Now if you did not use the exact same Ubuntu install media. Which from the look of it you actually got a hold of Ubuntu 12.10. Then at installation told it to install over windows then you would have what you have. Two different Ubuntu installs. Ubuntu gives you several options at install read it carefully.  The menu you see at boot is called grub2.  There is a software package you can download called Grub Customizer that will let you change a great deal of that menu.  I believe you can even remove the 12.04 entries from the menu.  Keep in mind that it will still be installed, you just won't have the option of selecting it at boot.  As has been said that the top listing is the default usually.  But when dual booting you can change that with grub customizer.  I have been using Ubuntu since 8.10 and dual booting win with it.  I am buy no means as informed as some are here.  But I would like to point out one last thing.  I have never had a package ( software , app etc.) install a knew version of ubuntu on my computer.  It usually works the other way around.  In order to use some of the new software you must upgrade to a newer Ubuntu.  So long as you use software center or APT in terminal I do not think this could happen.  I hope you enjoy using Ubuntu.


Now that makes more sense! I installed 12.10 during my dual boot attempt. I had it installed and even had it as an option at boot with windows 8 I just could never get it to load.  I tried everything in the forums, turning on off all of the security features in UEFI in BIOS, changing to Legacy ETC it just would not let me boot into Ubuntu. So when I decided to wipe completely I chose 12.04LTS to have the support thus the LTS :-) Now I understand what is going on, I am now FINALLY using my original install that I could never get to boot. I chose to wipe ALL at the 12.04 install so when it said it would wipe everything I guess the original Ubuntu didn't count. 
So I guess now I need to decide if I want to keep 12.04 and if not use GPARTED and incorporate that portion into my 12.10 partition.

---

### Post by fantab on 2013-07-08
You have done a good job so far 'stonewarrior'. Better than most newcommers.
When I was new to Linux, I installed and re-installed Ubuntu until I was comfortable with my set up. Don't be afraid to re-install if need be. If we had a perfect set up the first time then we won't learn, do we? 

About UEFI: This is the future. BIOS is 30 years old and is being gradually phased out. So its better if we come to terms with UEFI. It is quite easy to install Ubuntu in UEFI. So next time you install Ubuntu do consider installing it in UEFI.

12.04 is a Long Term Support [LTS] version. Its supported till 2017, that is five years since 2012. 12.10 and 13.04 are supported for NINE months only, I think 12.10 is supported a bit longer. LTS versions are generally more stable than non-LTS versions.
So as a beginner you will be better off using 12.04.

My two cents...

---

### Post by mastablasta on 2013-07-08
UEFI is not the same as secure boot. UEFI is sort of advanced BIOS while "*secure*" boot is something MS came up with and needs UEFI.

---

### Post by craig10x on 2013-07-08
I am curious....but didn't the ubuntu installer give you the option of wiping the disc and just installing your new ubuntu by itself...as far as i can recall, that automatic option appears even if you have multiple installations (say a different version of ubuntu and windows)....when wiped clean...a new grub is installed and since there is no other partitioned distros or windows, then you would not get any selection screen when you boot up...

I believe that option is always there because there was a time when i was dual booting 12.10 with 13.04 and decided i wanted to have only 13.04 so i did a clean install and had the installer just wipe everything out and install a fresh 13.04 by itself...Of course, if you use the manual partitioner, things get more complicated...i always like to go the simple way myself :)

---

### Post by farrinux on 2013-07-09
Stone

I would be careful about gparted and changing your partitions.  From what I know from some reading it really depends on where the partitions lay on the disc, their order and if any empty space is between them. If trying to add that partition to another could wind up with data corruption.  I would do some research on that.  I think it would be better just to wipe that partition and format it to an EXT 4 file system and use it for general file storage. Until such time as you feel comfortable and feel like redoing your system.

---

### Post by stoneworrior on 2013-07-09
Well I decided to re install and had the same situation with e new 12.04 in the menu list.  I have been selecting to wipe the entire HDD but what I didnt realize is the MBR is held on my 32GB SSD. By looking at the file system It looks to me as if Ive been installing my Ubuntu versions on the SSD so what I think is happening by default is the OS installs on the SSD and all of my apps and such gets stored on my 500GB HDD. Now I need to go through and clean everything up. 
EDIT: Upon further inspection when opening the file system I don't see my 500 GB HDD only my 32 GB SSD so this is going to take some fiddling around to figure out. I think I have been running strictly on my SSD and never touching the HDD even though that's what I select upon install. 
GRRRRR

---

### Post by farrinux on 2013-07-09
[QUOTE=stoneworrior;12723950]Well I decided to re install and had the same situation with e new 12.04 in the menu list.  I have been selecting to wipe the entire HDD but what I didnt realize is the MBR is held on my 32GB SSD. By looking at the file system It looks to me as if Ive been installing my Ubuntu versions on the SSD so what I think is happening by default is the OS installs on the SSD and all of my apps and such gets stored on my 500GB HDD. Now I need to go through and clean everything up. 
EDIT: Upon further inspection when opening the file system I don't see my 500 GB HDD only my 32 GB SSD so this is going to take some fiddling around to figure out. I think I have been running strictly on my SSD and never touching the HDD even though that's what I select upon install. 
GRRRRR[/QUOT

You need to change your install method since it sounds as if you want some of the install on the SSD and some on the HDD.  When the installation program starts you will want to choose the "Something Else" menu option. What you have been doing is using a "canned" install routine to one storage media.  Ubuntu by default on the install only picks one media location. Regardless of how many drives you have it will not format them at installation for Ubuntu and will not show up until you do it through a disc tool in Ubuntu.  That being said you can do it manually at installation by choosing the above mentioned menu choice.  I would do some research on which partitions you want, how big you want and where.  By default Ubuntu creates two partitions at install.  The partition "/" which is root and the "swap area".  It will work for most.  Here is what I did after some research on all 5 of my Ubuntu machines. Remember do this under the "Something Else" menu at install.

/dev/sdh1  ext4  /boot   300MiB ( this is on my 4th hdd. It is a primary extension.  It is set for boot, 300 mb in size. it is not needed however unless you run raid or other special things.)
/dev/sdh2  Extended Partition
/dev/sdh5  Swap (After research it is usually 2x to 3x your installed memory)
/dev/sdh6  ext4  /   25 GiB  (This is where Ubuntu installs everything except my home directory.)
/dev/sdh7  ext4  /home  size, the rest of the disk. (This is similar to the Windows Documents folder.)

Actually there is unallocated space on this disk to allow for either enlarging partitions or creating others.  The reason I keep my /home directory out of the / (root) folder is to keep my documents safe when I upgrade or reinstall ubuntu.  However I still back it up. An hdd failure, malware or other unforseen problem could kill it.  I would also recommend that when you start Ubuntu from the Live Image or CD which ever you are using. That you go into try Ubuntu and start gparted and look at your drives.  Both the ssd and hdd should be there.  This will also tell you any partitions on them and how they are formatted.  Hope this helps.

---


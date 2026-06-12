---
title: "I am ready to make a serious attempt at using Ubuntu! But where do I start?"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by J Tinsby on 2014-04-25
Hello,

With the demise of XP I am ready to give Ubuntu a try on one or both of my machines. Previously I have run Ubuntu from a CD but of course couldn't install any upgrades or additions to it.

I don't know what you would like or need to know about either machine so here goes.

Machine One is a dual boot machine with XP Pro SP3 and Win 7 64 bit on it & a conventional BIOS. I am using EasyBCD in XP to allow me to choose between the 2 OS's. The MB is an Asus Rampage Extreme with 6 GB of RAM and a 640 GB HD with 3 partitions, one for each OS and one for storage. The graphics card is GeForce 8800GTS and the sound card is an X-Fi that plugs into the MB in it's own PCIe x-1 slot. The mouse is a USB PS-2.There are dual DVD optical drives but no BluRay.I'd like to make an image of XP and install Ubuntu in it's place but am not sure if I need to add the EasyBCD to Win 7 to allow the system to 'see' Ubuntu or not?

Machine Two is an old Dell that runs XP Pro SP3 32 bit, but no other OS.BIOS is a standard one needless to say the mouse is USB and there is only one CD drive no DVD. The HD has 3 partitions one for the OS,  the other two I made for Ubuntu and for storage. The connection to the host machine one is wireless via D-Link with the current drivers for XP SP3, DD_CC_WDM Radeon ENU 29602. I don't know if all Ubuntu versions will find the wireless connection or not. The Dell has only 2GB RAM and a 80GB HD, sound card is on the MB as far as I know. As in the first instance must I use Easy BCD installed on XP to allow it to recognize Ubuntu?

As you can tell, I have no idea where to start, but am willing to try and learn the Linux/Ubuntu commands etc. but I don't even know what version to install on either machine and even if it will boot up when done! I know there are always new version of Ubuntu, but some seem to not be updated as often, so what to choose for the long haul and the best chance of working?

I'd appreciate hearing from anyone who can offer some guidance to a really newbie to Ubuntu. I do a lot of music editing and photo editing as a hobby so both of those are important, if not only on Win 7 but Ubuntu too if possible :D

Thanks to all in advance, I have ton's more to ask but this is quite enough for now I think!

Regards,

J T

---

### Post by suprleg on 2014-04-25
As far as dual or triple booting and setting up the bootloader/manager, I'll let someone else address that because without doing a bunch of research, I don't know as my ubuntu 14.04 LTS install is standalone.
I do know however, if you install from a live DVD the install is painless and it just, "works", after that you can add/remove/ play around very much like windows. As for needing a unix background to use ubuntu I would say no.

---

### Post by PapaNerd on 2014-04-25
For absolute starters, I'd suggest downloading and test driving several of the ubuntu variants to see which user interface is the easiest for you to use.  Then, machine #2 sounds like to obvious candidate for your initial transition.  Not having a DVD on it might make it hard to load some of the versions, but an external DVD RW (at around $35) would overcome that.

---

### Post by oldfred on 2014-04-25
Your XP & Windows 7 install may have all its boot files in the XP partition. Windows boots from the drive set in BIOS as boot and then the partition with the boot flag or active partition. No matter how many installs of Windows you have all boot files will be in that one partition. You can change drive or boot flag to force boot files to be in another partition, but have to do that when installing. May be possible to repair install to add boot files, but only if second install is also on a primary partition.

I run the 64 bit version on both my machines. My desktop is a CoreDuo with 4GB of RAM and laptop is also a older CoreDuo with only 1.5GB of RAM. Most say you need 2GB of RAM to use 64 bit, but as long as I do not load too many apps at once it works. But if I load too much then it starts using swap and is real slow.

Good back ups are vital, especially for a new user who may accidentally make mistakes.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Download Ubuntu and see how it runs from a flash drive. Not as fast as hard drive but gives an idea how it works.

      
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by 3rdalbum on 2014-04-26
> **J Tinsby said:**
> Hello,

With the demise of XP I am ready to give Ubuntu a try on one or both of my machines. Previously I have run Ubuntu from a CD but of course couldn't install any upgrades or additions to it.

I don't know what you would like or need to know about either machine so here goes.

Machine One is a dual boot machine with XP Pro SP3 and Win 7 64 bit on it & a conventional BIOS. I am using EasyBCD in XP to allow me to choose between the 2 OS's. The MB is an Asus Rampage Extreme with 6 GB of RAM and a 640 GB HD with 3 partitions, one for each OS and one for storage. The graphics card is GeForce 8800GTS and the sound card is an X-Fi that plugs into the MB in it's own PCIe x-1 slot. The mouse is a USB PS-2.There are dual DVD optical drives but no BluRay.I'd like to make an image of XP and install Ubuntu in it's place but am not sure if I need to add the EasyBCD to Win 7 to allow the system to 'see' Ubuntu or not?

Ubuntu 14.04 (64-bit) will be fine. The 64-bit edition of Ubuntu is labelled "AMD64" but it works just fine on 64-bit Intel CPUs. Ubuntu installs its own bootloader, GRUB, that can boot into all three operating systems so you don't need to worry about EasyBCD.

Back up all your data before proceeding with an install. Or make an image of XP. I can't recommend a program to image XP because I don't have enough Microsoft experience. Then boot up your computer from the Ubuntu DVD, the installer will ask you where you want to install Ubuntu, and you just select the "Erase Windows XP and install Ubuntu" option. Easy!

> Machine Two is an old Dell that runs XP Pro SP3 32 bit, but no other OS.BIOS is a standard one needless to say the mouse is USB and there is only one CD drive no DVD. The HD has 3 partitions one for the OS,  the other two I made for Ubuntu and for storage. The connection to the host machine one is wireless via D-Link with the current drivers for XP SP3, DD_CC_WDM Radeon ENU 29602. I don't know if all Ubuntu versions will find the wireless connection or not. The Dell has only 2GB RAM and a 80GB HD, sound card is on the MB as far as I know. As in the first instance must I use Easy BCD installed on XP to allow it to recognize Ubuntu?

My main concern with this one is that the CPU of this computer might not support PAE (Physical Address Extension) that Ubuntu/Xubuntu/Lubuntu etc require. My other decent concern is that you have AMD Radeon graphics in it; the older cards that are no longer supported by AMD do not have good performance on Ubuntu. It will probably be good enough to run Ubuntu, but not to run quickly, because Ubuntu requires decent 3D graphics support. And of course, Ubuntu does not fit on a CD anymore; there are ways around it (the Mini ISO, which downloads everything from the internet) but on the whole you might be best not using Ubuntu.

You could try Lubuntu 14.04, 32-bit. Before proceeding, make a backup of Windows XP, and run the Windows XP defragmenter utility.

Try booting the Lubuntu disc from a USB or from CD, I'm not sure if Lubuntu fits on a CD? If Ubuntu can work with your wifi, then all other derivatives like Kubuntu, Xubuntu and Lubuntu will be able to as well. The only difference between the derivatives is that they have different programs preloaded, and different GUIs. Underneath they are the same. The Lubuntu installer will also give you the option of "Install Lubuntu side-by-side with Windows XP" which will do all the partitioning for you, you just have to select how much space to allocate to each operating system. I'd recommend at least 10 gigabytes for Ubuntu, plus whatever you will want for your personal files.

> so what to choose for the long haul and the best chance of working?

You've come in at the right time. Generally, the newest version of Ubuntu is the best place to start. However, as you've noticed, some versions are only supported for 9 months. The current version, 14.04, is one of the two-yearly releases that is supported for five years. It's both the best chance of working (as it's the newest) and the best for the long haul. Of course, it is easily upgraded to the next version of Ubuntu which will come out in October and be supported for nine months. It will also be able to be upgraded to the next long-term support version, 16.04, which will come out in April 2016.

> I do a lot of music editing and photo editing as a hobby so both of those are important, if not only on Win 7 but Ubuntu too if possible :D

Image editing on Linux is most commonly done in a program called The Gimp, which you may be familiar with already. It's not as powerful as Adobe Photoshop, but it's still pretty good and it's a lot cheaper. It does not come preinstalled on Ubuntu but it is available in Ubuntu Software Center for easy installation.

Music editing is also a possibility on Ubuntu, but it doesn't seem as polished as on other platforms. There are people who use Linux professionally for music composition, production, recording and editing. I gave it up before I ever encountered Linux so my opinion of Linux's capabilities in this regard would be rather worthless.

Good luck, if there's anything else you need to know or need to ask we're happy to help.

---

### Post by trag on 2014-04-26
ZorinOS offers new users coming over from XP/Win7  familiar desktop layout's to ease the transition, with an XP , Win 7,or Mac OS on offer. [http://zorin-os.com/](http://zorin-os.com/)
good luck
trag

---

### Post by mastablasta on 2014-04-26
> **J Tinsby said:**
> I'd like to make an image of XP and install Ubuntu in it's place but am not sure if I need to add the EasyBCD to Win 7 to allow the system to 'see' Ubuntu or not?
Ubuntu uses it's own boot loader GRUB that can handle multiboots including windows systems and BSD systems.


> Machine Two is an old Dell - what old Dell?
> current drivers for XP SP3, DD_CC_WDM Radeon ENU 29602.  - what would that be?
use this program to give you specs. [http://www.piriform.com/speccy](http://www.piriform.com/speccy)
or even better boot into live CD open terminal and type in lshw

copy the output and post it here in code tags (the # icon)

> The Dell has only 2GB RAM and a 80GB HD, sound card is on the MB as far as I know. As in the first instance must I use Easy BCD installed on XP to allow it to recognize Ubuntu?

again grub will handle it all. f you only install ubuntu it is easy to do so. everything is done for you in about 20 minutes. you can try it in live session form USB stick where you can also install it from. computer has more than enough ram but what GPU does it have?

to create disk image (backup to external disk) i suggest ubuntu based Redobackup - it is very easy to use.
another option is Clonezilla - it is for more advanced but does image the drive well and probabyl has more options than redo.

---

### Post by LastDino on 2014-04-26
I would suggest first looking at Xubuntu, Ubuntu Unity tends to be too overwhelming sometimes and there is usually higher chance of you doing something with all the eye candy tweaks that might make your system little unstable and all of sudden its not a pretty sight where you get errors you've never heard of or worst: total crash. Xubuntu is like using XP with just better of everything and no Amezon adds like Unity.

I also shifted only recently, and I agree, its a great time to do so, but don't install same OS on both machines before you've good taste of it on one. Don't get me wrong, Unity is not half bad but it can be hit or miss depending on user.

---

### Post by Jordan_Cameron on 2014-04-26
GRUB is an amazing bootloader, so you won't need the Easy BCD.

Clonezilla is definitely worth learning.  I used to use it to make backups of my Arch Linux installs.  It basically clones parts of your hard drive that are used, allowing you to easily wipe your harddrive and restore it to the way it was during the clone.  Can have a bit of a learning curve but definitely worth using.

Xubuntu would definitely be a good starting point into Ubuntu.  It's less resource hungry than Unity Ubuntu (generic ubuntu).  However, another option would be Lubuntu, which uses the super-lightweight LXDE desktop environment.  Before installing, i would recommend making a USB image of each and trying them in live mode first.

---

### Post by oldfred on 2014-04-26
I install Ubuntu but do not use Unity, but change to fallback/flashback which is similar to what Ubuntu was with gnome2 and menus.
       [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)

---

### Post by J Tinsby on 2014-04-26
> **mastablasta said:**
> Ubuntu uses it's own boot loader GRUB that can handle multiboots including windows systems and BSD systems.


- what old Dell? >>>>>>>>>>>>. My wife's "old" machine she doesn't use,,circa 2004 with a Pentium 4  2.80Ghz processor.
 - what would that be? >>>>>>>>>>>That is the name of the D-Link program that I have to use for the wireless network to function. I included it because I don't know how Ubuntu handles Wi-Fi, I'm sure it does but the router may be too old to be recognized.
use this program to give you specs. [http://www.piriform.com/speccy](http://www.piriform.com/speccy)
or even better boot into live CD open terminal and type in lshw

copy the output and post it here in code tags (the # icon)



again grub will handle it all. f you only install ubuntu it is easy to do so. everything is done for you in about 20 minutes. you can try it in live session form USB stick where you can also install it from. computer has more than enough ram but what GPU does it have? >>>>>>>>>> The GPU is integral with the MoBo an Intel 86865G is all I can find. Nothing remarkable that's for sure.

to create disk image (backup to external disk) i suggest ubuntu based Redobackup - it is very easy to use.
another option is Clonezilla - it is for more advanced but does image the drive well and probabyl has more options than redo.

Right now I don't have the time to get the Piriform program but will do later on today.

Thank you for all the information.

J T

---

### Post by J Tinsby on 2014-04-26
Thank you ALL for the information it's a lot take in all at once. 

I did run 14.04 from a DVD on my main machine and it seemed to be fine, in that I had an internet connection with no fussing, the mouse worked, and it even located my old HP Desk jet 970Cxi printer. Oh yes the audio even worked albeit at a very low level. I am inclined to try 14.04 on the machine since it seemed relatively easy to navigate. I use Acronis TIH to make images of the HD weekly. So I don't think I can do too much damage installing Ubuntu.....famous last words!! I sure hope not. Here's hoping Grub works as it's supposed to :D

[B]I will be reading all the information again many times over, but you have all given me a lot of great stuff to get me started, it's most appreciated.
[/B]
Cheers,

J T

---

### Post by J Tinsby on 2014-04-27
Hello 3rdalbum,

I am stuck here's where I am:

I took your advice and got LUBUNTU and it fit on a CD so I thought I'd try in my second machine (Dell). It seemed to be OK running from the CD so I thought "why not go for it and try an install?" Early on it asked my for the P/W for my wireless network and I entered that, then continuing on I got to where it wanted me to install the OS. I was presented with screen that showed all my partitions (3) the first of which has XP Pro on it, the other two are formatted for NTFS and are empty. I wanted to put LUBUNTU on the second partition, I believe it was labeled /SDA5 or maybe /DEV/SDA5 (shut the machine off and am working from poorly written notes, sorry!) 

Anyway it wouldn't let me install it there saying " No Root files system defined" "Correct it from the partition editor." I got a window that said EDIT and then a whole load of files systems in the list, then a box marked FORMAT and /DOS or /WINDOWS were the choices. I tried both to no avail. It wouldn't let me go any further.

I understand that Windows XP works from a boot.ini file unlike  Vista or 7. So I didn't want to replace XP, on the Dell, I wanted to add LUBUNTU  on a second already created partition. Am I making the mistake in that LUBUNTU wants to be the first one on the HD and not on a secondary partition? 

Sorry to bother you but I don't know where to go from here. 

I was going to ask about doing a similar thing on my main machine, IE: Make it a triple boot, with XP, 7, and Ubuntu on a 3rd partition. Maybe that idea won't work without a lot of hassle?

I must say I was pleased that it wanted to connect to my WiFi network, I was worried it wouldn't, I chose to allow it to add updates on install, is that a mistake in that you can update later.

Regards and thank you!

J T

---

### Post by oldfred on 2014-04-27
It often installs better with hard wired Ethernet. 

You cannot install to a NTFS formatted partition, but only to Linux formatted partitions. And you cannot create Linux formats in Windows. 

If using Something else to choose a partition you can use + to add partitions or change to reformat a partition.  You need at the minimum / (root), usually formatted to ext4 and swap which is not formatted.

       [URL="https://help.ubuntu.com/community/WindowsDualBoot"]https://help.ubuntu.com/community/WindowsDualBoot
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29)
[/URL]
 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Attached are some screen shots of my installs of 14.04. I use gpt partitioning on one of them.





[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
[/URL]

---

### Post by LastDino on 2014-04-28
Make one more small partition of equal size of your RAM and Label it SWAP and then make your remaining area of original partition where you wanted to install Linux into ''/'' and format it to ''ext4''. If the original partition is big enough, make one more partition from it and make it ''/home'' and format it to ''ext4'' as well.   It should look like something like this size wise. SWAP  = Equal to RAM,  /            = 15-24 GB,   /Home = More than what you've for ''/'' preferably since this is where all your movies/songs etc are going to be stored.   However, you can avoid making home partition too if you choose to, but if you do so then HOME directory will be in ''/'' itself. This is not really advised but you can do it if your original partition is smaller than 40GB.

---

### Post by 3rdalbum on 2014-04-28
Root File System Undefined means that you haven't actually selected where you want to put Ubuntu. In the installer, click on the partition you want to use and click on the Edit button (it's not actually called Edit, but I can't remember the actual word on the button).

Change the filesystem to Ext4 and set the mount point to /

You can then continue the installation.

Installing updates can be done during the install or any time after installation. It is totally up to you.

---

### Post by J Tinsby on 2014-04-29
> **oldfred said:**
> It often installs better with hard wired Ethernet. 

You cannot install to a NTFS formatted partition, but only to Linux formatted partitions. And you cannot create Linux formats in Windows. 

If using Something else to choose a partition you can use + to add partitions or change to reformat a partition.  You need at the minimum / (root), usually formatted to ext4 and swap which is not formatted.

       [URL="https://help.ubuntu.com/community/WindowsDualBoot"]https://help.ubuntu.com/community/WindowsDualBoot
[/URL][https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29)

 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Attached are some screen shots of my installs of 14.04. I use gpt partitioning on one of them.
[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
[/URL]

Hello oldfred,

Thanks for the nice screenshots they will be very helpful. Yesterday I made a bootable USB thumb drive and put 14.04 LTS on it, and tried to run it on my wife's old Dell machine. As was suggested in a previous posting it ran very slowly, probably not enough CPU or GPU power to run it effectively. So on that machine I guess I am stuck with LUBUNTU.

 Today I may attempt making the partitions as you and the others have suggested. I am hoping that I can still keep the first OS , XP, on the first partition and reformat the remaining 2 for use with Linux. In a worst case I do have an image of the XP partition so no harm done if I mess it up somehow along the way. Seems that using the 14.04 LTS I encountered,Gparted along the way, I am assuming that I could have used that to reformat the partitions I need, but I chose not to. I also have Easeus Partition Manager but it only formats to EXT3 not 4 so I can't use that :/ I'll use whatever comes with LUBUNTU to make the necessary changes to the HD hoping that maybe I can retain XP. The trouble is that its my wife's machine, and the minute I change anything she'll be more lost than she is now!! :(

Thanks!

J T

---

### Post by J Tinsby on 2014-04-29
Success!

Not a big deal to you guys but to me it is!

I got LUBUNTU installed as per your directions and I STILL have good old out of date dangerous XP for the wife to use!

Where do I look to enter my passkey for the Wi-Fi network? I didn't see it come up as a choice during the install as it did on the first install attempt. It obviously located my wireless card and wanted the passkey to be entered during the first install attempt. it found my router and all the other networks in the area too, so the card is. or at least. was being recognized. Now that LUBUNTU is in place I don't know where to click to enter the passkey.

Can someone direct me to where it is so I can input my password string and get on the web?

I think I've tried all the boxes but obviously not!

Thanks,

J T

---

### Post by oldfred on 2014-04-29
I have Ubuntu and use Network connection. 
Not sure what Lubuntu uses.
If you cannot immediately find it, or search does not help post another thread with that issue in title.

---

### Post by J Tinsby on 2014-04-30
> **oldfred said:**
> I have Ubuntu and use Network connection. 
Not sure what Lubuntu uses.
If you cannot immediately find it, or search does not help post another thread with that issue in title.

Hi oldfred,

I got it to work, I simply had to go into the network area and create a new WiFi connection. Once I did that the card was recognized and I have a connection each time I boot up!

In desperation  I did do a second install to get the prompt to enter the pass-code, that seemed to work but didn't "stick" so I did it manually. I am sure I am doing the same thing that you did to make the connection. I don't know why it would ask me for my passkey and then have me enter 64+ characters only to not save them. Made no sense to me. But the system is working fine, although I did make a mistake in that I didn't make a / home partition I just have / and swap. I understand that's not thee approved way and I wonder if now that it's all in place can I go back and ADD a /home partition? There is plenty of room to do it. Certainly as a proof of concept I am very impressed with LUBUNTU!!

 **Couldn't have done it without all the help and attention from the forum, you all have been very helpful and I really appreciate it!! Volunteering can be a thankless endeavor, but I am here to say THANK YOU TO ALL:D**

Now if I may ask one other question, since LUBUNTU is working so well on my wife's machine I'd like to have UBUNTU on my main machine that is already dual boot XP & 7 . Can I use the same method of installing and formatting the 3rd partition of that drive and NOT lose XP and 7 ? I have plenty of room on that 3rd partition and it would be nice to have UBUNTU 14.04 on there but I don't want to lose the other 2 OS's. Can I do this without a lot of hassle or is it a nightmare to accomplish? If I format a portion of that drive that is already NTFS, must I do the entire partition as EXT4 or can I keep what I have already as NTFS and make the rest EXT4? I guess I'd just be making more partitions on that existing one...?

thank you! :D


J T

---

### Post by LastDino on 2014-04-30
Not having home is not going to be killer factor if you got into habit of taking backups. Although, I strongly advise to make one when and if you do full linux install. 

And yes, you can install it on it on the other PC with same method.

---

### Post by oldfred on 2014-04-30
I normally suggest 20 to 25GB for /. If your install is not much larger than that then there is not much advantage to a separate /home. But if over say 50GB then separate /home or data partition(s) may make more sense.

I used Ubuntu for about 3 years with just / & swap. But since dual booting with Windows quickly added another NTFS partition for shared data where I put Firefox & Thunderbird profiles & all photos (for Picasa). Then I could share data in both systems. Only when I got a new larger hard drive and planned to shutdown Windows did I add a Linux data partition. Since I have data partitions, I do not have a separate /home.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you have multiple Windows installs what is your current partitions? Windows is best in primary partitions and a second install of Windows only boots from first install or one with boot flag. 
You need an available primary partition to be the extended partition. All Linux partitions can be logical. Even a second install of Windows can be in a logical partition but it can be more difficult to repair and only boots from another primary partition.
Grub will only show one Windows boot option as all boot files both all Windows installs are in that one partition. If second install is primary it may be repaired to add boot files and then you can directly boot both installs from grub. 

      
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by J Tinsby on 2014-04-30
> **oldfred said:**
> 
If you have multiple Windows installs what is your current partitions? [l]("http://www.multibooters.co.uk/multiboot.html")

From Event Viewer in Win 7:

[ATTACH=CONFIG]252684[/ATTACH]

Since I am in 7 now it shows as the C:\ but really Windows XP is the first one in the boot order since it was the first to be installed on the HD. Then came Win 7 and the other partition is for storage. I realize that Win 7 has written it's boot info into the XP file and if I take XP off the drive then 7 won't boot. I am keen to try and preserve XP, not to necessarily use it online but for the many editing programs that run under a 32 bit environment. It's much easier to simply shut off my access to the 'net when doing any music editing or photography work, than to find programs to replace all of them!

I will be studying your link to the"Multibooters" page, thanks for that.

Regards,

J T

---

### Post by oldfred on 2014-04-30
You may just be able to copy bootmgr & BCD folder to Windows 7 and have it boot if boot flag is on Windows 7 partition. Then grub would find both. Or BCD may need repair or you may need chkdsk on Windows 7 just to update partition boot sector.

---

### Post by J Tinsby on 2014-04-30
> **Goten0007 said:**
> Not having home is not going to be killer factor if you got into habit of taking backups. Although, I strongly advise to make one when and if you do full linux install. 

And yes, you can install it on it on the other PC with same method.

Hello Goten0007,

I am surprised to hear that I can install Linux on my primary machine partitoned for XP, 7, "storage". I read the url at:[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) and it appears that I need a standalone bootmanager like "GAG" to handle booting of the MS OS's plus Linux. Maybe I am completely misunderstanding the very lengthy article but t goes into great detail about the various tiny programs that all line up to make an OS boot up. Fascinating stuff that but a long read. The author seems to think that allowing Grub to stay on the Linux partition is the simplest way to go and allows removal of Linux with no effect on the other MS OS's. 

Again, you are all more advance than I am in this particular area, so don't misunderstand my dubious attitude! :D

I am in no position to argue with you about this topic, I am asking all these questions so I get it right the first time to avoid a hassle I don't want or need. I was hoping to hear it ***CAN*** be done as I did on the Dell machine running XP. But right now I am a bit sketchy about trying it. Have you actually done it? I guess that's the question

Yes I have images of all my partitions on my main computer.

Thank you very much,

J Tinsby

---

### Post by pfeiffep on 2014-04-30
> **J Tinsby said:**
> Hello Goten0007,

I am surprised to hear that I can install Linux on my primary machine partitoned for XP, 7, "storage". I read the url at:[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) and it appears that I need a standalone bootmanager like "GAG" to handle booting of the MS OS's plus Linux. Maybe I am completely misunderstanding the very lengthy article but t goes into great detail about the various tiny programs that all line up to make an OS boot up. Fascinating stuff that but a long read. The author seems to think that allowing Grub to stay on the Linux partition is the simplest way to go and allows removal of Linux with no effect on the other MS OS's. 

Again, you are all more advance than I am in this particular area, so don't misunderstand my dubious attitude! :D

I am in no position to argue with you about this topic, I am asking all these questions so I get it right the first time to avoid a hassle I don't want or need. I was hoping to hear it ***CAN*** be done as I did on the Dell machine running XP. But right now I am a bit sketchy about trying it. Have you actually done it? I guess that's the question

Yes I have images of all my partitions on my main computer.

Thank you very much,

J Tinsby

If you have an external usb hard drive and the Dell in question will boot to a USB device you can install that way to preserve XP. An aside I run Ubuntu on an old Dell laptop (specs in sig) and installed [gnome flashback]("https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback") desktop environment choosing Metacity - this takes quite a bit LESS horsepower than Unity.

---

### Post by LastDino on 2014-04-30
> **J Tinsby said:**
> Hello Goten0007,

I am surprised to hear that I can install Linux on my primary machine partitoned for XP, 7, "storage". I read the url at:[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) and it appears that I need a standalone bootmanager like "GAG" to handle booting of the MS OS's plus Linux. Maybe I am completely misunderstanding the very lengthy article but t goes into great detail about the various tiny programs that all line up to make an OS boot up. Fascinating stuff that but a long read. The author seems to think that allowing Grub to stay on the Linux partition is the simplest way to go and allows removal of Linux with no effect on the other MS OS's. 

Again, you are all more advance than I am in this particular area, so don't misunderstand my dubious attitude! :D

I am in no position to argue with you about this topic, I am asking all these questions so I get it right the first time to avoid a hassle I don't want or need. I was hoping to hear it ***CAN*** be done as I did on the Dell machine running XP. But right now I am a bit sketchy about trying it. Have you actually done it? I guess that's the question

Yes I have images of all my partitions on my main computer.

Thank you very much,

J Tinsby

Before coming to Linux completely I did triple boot on machine which already had my old WinXP (5+Years) and new Win7 (1 Year). All it took me was to make a bootable USB and install Ubuntu on separate partition with right partition table, ubuntu already comes with Grub which is boot manager and it detected all 3 (Well, technically speaking it detected 2 but when selected other option I was offered good old windows booting option to boot from earlier version or win7). I've also done it with 2 windows and 2 Linux (Ubuntu and Fedora). That guide you linked is from 2007, Linux has come way too far (especially Ubuntu) from there.
Fyi, you can also boot ISO from Grub if you need to, amazing isn't it? :P

Ah, btw, you can copy ''/boot/grub/boot.img (or something like that)" to your win7 and let it do the business. (I forgot where exactly I copied it to but it should be somewhere in windows boot area). Google might help you there.

---

### Post by J Tinsby on 2014-05-01
> **Goten0007 said:**
> Before coming to Linux completely I did triple boot on machine which already had my old WinXP (5+Years) and new Win7 (1 Year). All it took me was to make a bootable USB and install Ubuntu on separate partition with right partition table, ubuntu already comes with Grub which is boot manager and it detected all 3 (Well, technically speaking it detected 2 but when selected other option I was offered good old windows booting option to boot from earlier version or win7). I've also done it with 2 windows and 2 Linux (Ubuntu and Fedora). That guide you linked is from 2007, Linux has come way too far (especially Ubuntu) from there.
Fyi, you can also boot ISO from Grub if you need to, amazing isn't it? :P

Ah, btw, you can copy ''/boot/grub/boot.img (or something like that)" to your win7 and let it do the business. (I forgot where exactly I copied it to but it should be somewhere in windows boot area). Google might help you there.

Hi Goten0007,


Thanks for all the information, sounds like what I'd like to try will work after all.
You are correct that the url is and old one, I was concerned about that when I was reading it. :/ 

 Assuming others are reading this thrread, no one has tried to steer me away from trying/dloing it. When you say that "install Ubuntu on separate partition with right partition table" are you referring to the way the partition is formatted. like EXT4 or something else? Oddly enough I had just made a bootable USB to try UBUNTU 14.04 on my wife's Dell machine, it ran slowly so I just reformatted the USB thumb drive last night lol. So I chose to install LUBUNTU there and it's working fine. A great way for the wife to have internet access and not be using XP!


Since I use Acronis to make my backup images, I can use a feature called "Try & Decide" it lets you run programs you want to try before permanently installing them w/o effecting the OS. I have used it prior to this with good success, I'm wondering if the test of the triple boot would be a great way to try it and see how it plays? The "Try & Decide" will survive multiple reboots so that wouldn't be a problem.

 I am anxious to try it and see what happens but I surely don't want to hose my machine that's running so well!

Do you have any experience using Wine to run Windows programs on Linux? There are a ton of them I use on XP that won't run on Win 7 64 and I'd love to be able to use them if I found UBUNTU was acceptable.

Thanks again for your interest and support!

J T

---

### Post by LastDino on 2014-05-01
Word of caution though: In my case XP was first, win7 was 2nd and Ubuntu was 3rd in that order of installations (It wasn't planned but that was how it was and is  suppose to be). I've some people try it and ending up breaking their MBR, if that happens you will end up going through lot of loops. I suggest you ''carefully'' looking at some tut's or Youtube vids for this. You're not the first to try that and believe me you wont be last. If you're going to experiment, at least try to learn as much as possible from it. Then even if it is failure, you probably wont regret it. 

I used wine to run few of my favourites, but I eventually let go of it completely. It was not worth the effort.

---

### Post by oldfred on 2014-05-01
I use wine for Picasa and use the Windows version or 3.9. Some have issues with connections to google +, but we do not use that feature.
 
When I started converting from XP our main apps were, Internet, email, photos & financial.  Started with Ubuntu in 2006 and said I soon would completely convert.

Several years before we had converted to Firefox & Thunderbird in XP. And my wife like Picasa. So changing the the Ubuntu versions was easy as we were used to the software and the differences in Linux were minor. But Google worked with wine to make it work better or acceptably. Some now say the older versions of Quicken may work partially. 

For years I could not get any of the Linux apps working as well as  Quicken. Part to the issue was history as I had run Quicken since DOS.  And none of the Linux equivalents were as good. But several years ago a  new SSD which requires AHCI and XP does not work with AHCI pushed the  issues and I just converted to KMyMoney. Not as good as Quicken, but  good enough. I think if Quicken came out with a Linux version I would  have to think about it as part of the issue is all the old data or  history.

[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)
But if not at least gold, you will find it not worth using. Find the neared Linux app and you will be happier.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

 Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)
[http://www.linuxalt.com/](http://www.linuxalt.com/)

---

### Post by J Tinsby on 2014-05-01
> **Goten0007 said:**
> Word of caution though: In my case XP was first, win7 was 2nd and Ubuntu was 3rd in that order of installations (It wasn't planned but that was how it was and is  suppose to be). I've some people try it and ending up breaking their MBR, if that happens you will end up going through lot of loops. I suggest you ''carefully'' looking at some tut's or Youtube vids for this. You're not the first to try that and believe me you wont be last. If you're going to experiment, at least try to learn as much as possible from it. Then even if it is failure, you probably wont regret it. 

I used wine to run few of my favourites, but I eventually let go of it completely. It was not worth the effort.

Goten0007,

Fortunately as luck would have it my boot order is the same as you describe, minus of course Ubuntu. That page about multi-booting although outdated, still had a lot of information that was useful, if not applicable to my situation, due to upgrades of Linux and Grub. There is no rush to set this thing up, I can play with the install of LUBUNTU on the old machine while I am studying things here.

You were able to do it with not a lot of trouble or so it sounded, but I think that "chance favors the prepared mind" So I want to be prepared! :)

I'll look at YouTube and see if I find any more tutorials elsewwhere.

Thank you and I'll be in touch via the forum!

J T

---

### Post by J Tinsby on 2014-05-01
Hi oldfred,

Thanks for even more useful information, breaking the bonds of MS for me isn't easy, but as you can see I am willing to try. Win 7 64 is working like a charm, there's a long story to that I'm sure you don't want to hear, in the end it's fine.

The LUBUNTU on the older machine is working like a charm, so there's one less thing to worry about if the wife decides to go online for some reason, she won't be using XP. Really tho' there's nothing of value excapt the Os on that machine anyway but it's great as a test bed for me!

I don't do any finanaical stuff here as you do, mostly my time is taken editing music files or photos that I have taken or been given to enchance or repair.

I already like the simplicoty of Linuz and can see why more people use it.

Don't know how the multi-boot thing will work for me but intend to tread lightly, the url you gave me was informative. I never realized there were so many OTHER programs working to make an OS boot up, like so many others I thought it was just the MBR.

Thanks!

J T

---

### Post by oldfred on 2014-05-01
If your Windows 7 is working well one of the best things to do is a full image backup.

In Windows it is all one system. But Linux has many developers and each part is often developed separately and then has its own name. Boot loaders used to be lilo, then grub (now legacy), and now grub2. And I am sure there were (are) many others.

---

### Post by LastDino on 2014-05-02
> **J Tinsby said:**
> Goten0007,

Fortunately as luck would have it my boot order is the same as you describe, minus of course Ubuntu. That page about multi-booting although outdated, still had a lot of information that was useful, if not applicable to my situation, due to upgrades of Linux and Grub. There is no rush to set this thing up, I can play with the install of LUBUNTU on the old machine while I am studying things here.

You were able to do it with not a lot of trouble or so it sounded, but I think that "chance favors the prepared mind" So I want to be prepared! :)

I'll look at YouTube and see if I find any more tutorials elsewwhere.

Thank you and I'll be in touch via the forum!

J T

Well, I did have it easy. I only recently came to know what Grub is and what made my life easier was actually grub, so you can imagine.lol They do say that luck favours the brave. :P
Though my bravado came from me buying 1TB external back-up HD and I was more than willing to change things.

Tut's = Tutorials. You might find lot of step by step explained guides if you tried to search on google or Duckduckgo. I'm sure there are videos too.

---

### Post by J Tinsby on 2014-05-02
> **Goten0007 said:**
> Well, I did have it easy. I only recently came to know what Grub is and what made my life easier was actually grub, so you can imagine.lol They do say that luck favours the brave. :P
Though my bravado came from me buying 1TB external back-up HD and I was more than willing to change things.

Tut's = Tutorials. You might find lot of step by step explained guides if you tried to search on google or Duckduckgo. I'm sure there are videos too.

Hi Goten0007,

Some of the videos are very helpful and others are of such dreadful  quality they look like they were made during an earthquake! Makes me  sick to my stomach to watch them w/o taking some seasick medicine :(

I found a very interesting one on YouTube that shows a "non traditional" was of installing Linux, that lets the MBR of Windows alone and puts Grub on the /home partition.That way, according to the author, if Grub fails you still have the MBR to use or vice versa. Seemed to be a very clever way of preserving things if an update of some sort changes Grub or it gets corrupted. *I wonder if you have ever heard of or used this method?* 

Here's the link if you'd like to watch :  [https://www.youtube.com/watch?v=xlTgaWs9BD0](https://www.youtube.com/watch?v=xlTgaWs9BD0) ( I could find a lot of things to complain about in this one RE: the quality, but I found it easy to understand and ignored the focus problems etc.)

Like you I have a 1TB external drive that has all my partition backups on it it. So I guess I need to find the nerve to "just DO it!" I was advised by the Acronis forum NOT to use the "Try" mode for things that pertain to booting so I'm glad I asked that one.

Have to nip off now but will of course be here and keeping in touch. Tons more questions will ensue but I'll try and solve them and not be a problem child.

Cheers,

J T

---

### Post by J Tinsby on 2014-05-02
> **oldfred said:**
> If your Windows 7 is working well one of the best things to do is a full image backup.

In Windows it is all one system. But Linux has many developers and each part is often developed separately and then has its own name. Boot loaders used to be lilo, then grub (now legacy), and now grub2. And I am sure there were (are) many others.

Hi oldfred,

Yes I have multiple image backups of all 3 partitions so I'm just reading a lot and trying to learn how other folks have done it. If you look at my reply to Goten0007 you'll see a link that I found interesting. If the described method is good I wonder why it's not done commonly?  Looks like the triple boot can be done, I just need some quiet time,_ preferably without one of my Bengal cats sitting on my shoulders,_ to dive in and DO IT! :D

Always appreciate the info that you supply thanks!

Take care,

J T

---

### Post by LastDino on 2014-05-02
> **J Tinsby said:**
> Hi Goten0007,

Some of the videos are very helpful and others are of such dreadful  quality they look like they were made during an earthquake! Makes me  sick to my stomach to watch them w/o taking some seasick medicine :(

I found a very interesting one on YouTube that shows a "non traditional" was of installing Linux, that lets the MBR of Windows alone and puts Grub on the /home partition.That way, according to the author, if Grub fails you still have the MBR to use or vice versa. Seemed to be a very clever way of preserving things if an update of some sort changes Grub or it gets corrupted. *I wonder if you have ever heard of or used this method?* 

Here's the link if you'd like to watch :  [https://www.youtube.com/watch?v=xlTgaWs9BD0](https://www.youtube.com/watch?v=xlTgaWs9BD0) ( I could find a lot of things to complain about in this one RE: the quality, but I found it easy to understand and ignored the focus problems etc.)

Like you I have a 1TB external drive that has all my partition backups on it it. So I guess I need to find the nerve to "just DO it!" I was advised by the Acronis forum NOT to use the "Try" mode for things that pertain to booting so I'm glad I asked that one.

Have to nip off now but will of course be here and keeping in touch. Tons more questions will ensue but I'll try and solve them and not be a problem child.

Cheers,

J T

Lmao, well, get used to it as you'll find those same people making video's about all sorts of Linux related things and they are mostly same.

I haven't tried anything like that, and as my Windows days are over so I don't think there will be ever need to. But that sounds very informative, I'll bookmark that link, thanks ^^
I actually regret wasting my time and making my machine go through so much harassment just to keep Windows around.

---

### Post by oldfred on 2014-05-02
Some here have used EasyBCD and say it works.

But it requires you to install grub2 to a PBR, with old grub legacy that worked, but grub2 is a lot larger and does not fit. So it converts to blocklists which are hardcoded addresses. If any grub files moves on hard drive from update or even a fsck then you have to boot with Ubuntu repair and reinstall grub.

Windows is not a multi-boot system. It will multi-boot several Windows.
The EasyBCD solution actually uses grub4dos which is based on grub legacy to do a chain load to grub2 in PBR - partition boot sector.

Reinstalling a boot loader is very easy. But you need a Windows repair CD or flash drive for current version of Windows and Ubuntu live installer to add Boot-Repair into or other Linux repair drive. I have both Boot-Repair, Supergrub, gparted, parted-magic, knoppix and maybe a few others as ISO on repair flash drives.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by J Tinsby on 2014-05-05
> **Goten0007 said:**
> Lmao, well, get used to it as you'll find those same people making video's about all sorts of Linux related things and they are mostly same.

I haven't tried anything like that, and as my Windows days are over so I don't think there will be ever need to. But that sounds very informative, I'll bookmark that link, thanks ^^
I actually regret wasting my time and making my machine go through so much harassment just to keep Windows around.


I hope you get to read this, I tried to install Ubuntu today and was befuddled by the installer messages I got. 

I SHRANK a larger partition and made an unallocated 75GB partition on my drive, using Win 7, where I wanted to put Ubuntu.

I fully understand that I can't make a Linux partition using Windows.

When I got to the installing part, I chose "Something else" like I did in Lubuntu. I expected to see the various NTFS partitions and the 75 GB one that was unallocated. Instead I saw only the whole drive and kept getting messages that if I install the bootloader there, all other partitions will be gone! Grrrr! Not what I wanted to see. I thought, *wrongly so* that I'd get a chance to format the 75 GB new partition to ext4 and go from there but I couldn't find a way to do it.

What did I do wrong? I didn't know to start a new thread or keep going with this one, looks like a lot are reading it fwiw.

Thanks you Goten0007!

J T

---

### Post by oldfred on 2014-05-05
Please attach screen shots, not in line. Not everyone has high speed Internet and it can lock up a slow system.
You can easily attach with Go Advanced reply editor and paper clip icon in edit panel.

You do not create partitions with Windows. It cannot create Linux partitions and may convert to dynamic partitions which has no undo and does not work with Linux. Best to use Windows to shrink a NTFS partition. If you want to create partitions in advance use gparted.

Post this:
sudo parted -l

---

### Post by J Tinsby on 2014-05-05
> **oldfred said:**
> Please attach screen shots, not in line. Not everyone has high speed Internet and it can lock up a slow system.

You can easily attach with Go Advanced reply editor and paper clip icon in edit panel.

You do not create partitions with Windows. It cannot create Linux partitions and may convert to dynamic partitions which has no undo and does not work with Linux. Best to use Windows to shrink a NTFS partition. If you want to create partitions in advance use gparted. 

Post this:
sudo parted -l

Screen captures removed.

I_*** shrank***_ a larger partition into a 75 GB one that I wanted to format to ext4 using the UBUNTU installer, the same way I did when I installed LUBUNTU on my other machine. That installer found the second partition on that HD and allowed me the choose to format it as I needed to; using ext4.

 Are you now telling me that the very latest and greatest UBUNTU 14.04 LTS doesn't give me that option? I must use another program to format that 75 GB partition" Why does a lesser version of Ubuntu allow me to reformat a partition, from NTFS to EXT4 and the 'full' version won't? 

Makes no sense to me, sorry.

Tinsby

---

### Post by oldfred on 2014-05-05
You can use installer to reformat partition, if there are no errors created in system by your changes.

You may just need to run chkdsk as any change to the size of a NTFS partition requires a chkdsk to let Windows update itself to its new size. The Linux installer will not show a partition needing chkdsk as it cannot see it. The Linux NTFS drive does not mount NTFS partitions that need chkdsk or are hibernated to protect you from damaging a NTFS partition that chkdsk may not then fix.

But there is a long list of things that can be wrong with a partition table or hard drive that cause issues. The assumption is you know to fix those first or it assumes you just want to install to entire hard drive.

       Boot Issues from live Installer not showing partitions
Do you have Windows hibernated?  Or Windows 8 fastboot still on
Does NTFS need chkdsk? Even if it boots ok?
Was drive every part of RAID or RAID set in BIOS? or Intel SRT which uses RAID
SFS, Windows dynamic partitions or LDM on gpt drives
 backup GPT table is not at the end of the disk
Left over gpt data Windows leaves backup gpt data when converting to MBR.
Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by LastDino on 2014-05-05
What did you do to the leftover partition/space after you shrank the original one? Did you format it to NTFS or let it be  as unallocated space? I personally never faced this problem irrespective of the version of Ubuntu/Gparted used in installer. 

As Oldfred said, try to run Chkdsk.

---

### Post by J Tinsby on 2014-05-05
> **Goten0007 said:**
> What did you do to the leftover partition/space after you shrank the original one? Did you format it to NTFS or let it be  as unallocated space? I personally never faced this problem irrespective of the version of Ubuntu/Gparted used in installer. 

As Oldfred said, try to run Chkdsk.

Hi Goten0007 :D

I left the 75GB unformatted, no NTFS no nothing, thinking I'd be able to format it ext4 when I did the Ubuntu install. That of course never happened, the installer showed only one huge partition and I sure wasn't going to blow out 7 & XP! the installer for Lubuntu allowed me to format an NTFS partition, that's why I was dumbstruck when I couldn't do anything with it.

In fact I e x p a n d e d the partition back to the way it was and I ran chkdsk as advised, took long enough <sighs> and I haven't tried it since. btw it didn't find any errors. Looks like this isn't going to work after all.

J T

---

### Post by LastDino on 2014-05-05
Just shot in the dark, but when and if you shrink the partition again, try to format leftover to the NTFS as well.  Then when you go to installation process use Gparted to break that NTFS partition into required Linux partitions as you prefer and then format them to ext4

If you still can't see it, then run the Chkdsk and try again. Good luck!

---

### Post by oldfred on 2014-05-06
Do not create partitions with Windows.
If it converts to dynamic (logical) partitions it is very difficult to get it back to basic partitions.

You want the  typical 4 primary partitions where one primary partition can be an extended partition which can hold an unlimited number of logical partitions.

---

### Post by LastDino on 2014-05-06
> **oldfred said:**
> Do not create partitions with Windows.
If it converts to dynamic (logical) partitions it is very difficult to get it back to basic partitions.

You want the  typical 4 primary partitions where one primary partition can be an extended partition which can hold an unlimited number of logical partitions.

If this is true then you might give up on what I suggested. I've no clue as to how to approach situation beyond this, like I said, I've never personally faced it. Sorry.

---

### Post by mastablasta on 2014-05-06
if installer shows only one partition and if you have MBR partitioning then it means you have 4 primary partitions occupied. you can use the free mini partition wizzard tool to change one of the primary parittions into extended one (seocndary, logical). the empty disk space will then show up on installer. 

as for GRUB getting corrupted  - it hasn't happened yet to me, though i did have windows MBR corrupted 3 times (traced it to faulty hard disk cable). anyway just liek in windows booting from live CD and single command will reinstall it/repair it fast.

---

### Post by J Tinsby on 2014-05-06
> **Goten0007 said:**
> Just shot in the dark, but when and if you shrink the partition again, try to format leftover to the NTFS as well.  Then when you go to installation process use Gparted to break that NTFS partition into required Linux partitions as you prefer and then format them to ext4

If you still can't see it, then run the Chkdsk and try again. Good luck!

Hi Goten0007,

What you describe is exactly what I was intending to do, but of course I didn't format the 75GB partition. Since I can only draw from the install of Lubuntu, I was expecting the installer to show me the partitions and I could then choose the one I wanted to make the 3 smaller slices to use for Ubuntu. Of course for whatever reason it never happened that way.

I dunno :/

Thanks J T

---

### Post by oldfred on 2014-05-06
We all are talking around issues, but if you show your partitions we may know more.
From your installer in live mode, using terminal

sudo parted -l
 sudo fdisk -lu /dev/sda

---

### Post by J Tinsby on 2014-05-06
> **oldfred said:**
> We all are talking around issues, but if you show your partitions we may know more.
From your installer in live mode, using terminal

sudo parted -l
 sudo fdisk -lu /dev/sda

Hello oldfred,

Here is the info you requested I hope it's OK to paste it here as text and not as a .zip file.

ubuntu@ubuntu:~$ sudo parted -l
Error: Can't have overlapping partitions.                                 

Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xef5bef5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   157292414    78646176    7  HPFS/NTFS/exFAT
/dev/sda2       157292415   314584830    78646208    5  Extended
/dev/sda3       314584830  1250258943   467837057    7  HPFS/NTFS/exFAT
/dev/sda5       157292544   314583039    78645248    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 

Thanks,

J T

---

### Post by J Tinsby on 2014-05-06
Hi oldfred and Goten0007,

Here are some screenshots of both XP and Win 7 in the Admin | Computer Management | Disc Management area.

Probably no help since you now have the info from Ubuntu, but here they are anyway,plus the messages I got when trying to install the OS.

Thanks,

J T

---

### Post by oldfred on 2014-05-06
I think this is the issue.

 dev/sda2 157292415 [COLOR=#ff0000]314584830[/COLOR] 78646208 5 Extended
/dev/sda3 [COLOR=#ff0000]314584830[/COLOR] 1250258943 467837057 7 HPFS/NTFS/exFAT

Those should not be the same. or sda3 needs to start after sda2.
I would shrink sda2 by 1 or 2 sectors and then it should work.

It looks like sda5 has several hundred sectors so you only have to change the extended partition size.
If your Windows tools will work on it, then use that.

---

### Post by J Tinsby on 2014-05-07
> **oldfred said:**
> I think this is the issue.

 dev/sda2 157292415 [COLOR=#ff0000]314584830[/COLOR] 78646208 5 Extended
/dev/sda3 [COLOR=#ff0000]314584830[/COLOR] 1250258943 467837057 7 HPFS/NTFS/exFAT

Those should not be the same. or sda3 needs to start after sda2.
I would shrink sda2 by 1 or 2 sectors and then it should work.

It looks like sda5 has several hundred sectors so you only have to change the extended partition size.
If your Windows tools will work on it, then use that.

oldfred,

So I understand fully, I should resize the 2nd partition slightly so it's not the same as /dev/sda2 correct?

I don't know why it's showing that there are 5 partitions when I only have 3. If you look at the screenshots I posted it bears that out. Or maybe Ubuntu is seeing partitions that Windows can't see or ones that were there at one time and aren't now? Note that after I made the storage partition smaller, and the install failed, I then put the size back to what it was before I started. Could this be why it's showing 5 and Windoze says there are only 3? 

If I only show 3 partitions in Windows, I'm not sure how to change the 5th one, if it's not visible to me :/

Yes I can use the Win 7 tools to do the resizing with no trouble, I just don't want to misinterpret your instructions.

Thank you very much!

J T

---

### Post by bobmoyer on 2014-05-07
I have two machines that dual-boot ubuntu 12.04 and xp and they work fine, just remember to choose the dual boot option at install and you should be fine. I went and installed the gnome desktop "sudo apt-get install gnome-shell" and to make life easier remember that you can cut and paste commands to the terminal using control-c and control+shift+v to paste in

---

### Post by oldfred on 2014-05-07
You have three partitions.
It is the extended partition that is too large. The sda5 logical partition is not exactly the same size as the extended, so you can shrink the extended by a few sectors without changing sda5.

The extended partition always is just a container for the logical partitions and is counted as one of the 4 primary partitions, but You see it as the green line in your Windows around the logical partition. You currently only have one logical in the extended but can have as many as your want.

And logical partition always start at 5 or on drive sda as sda5. Any one primary can the the extended, but all primary partitions are numbered from 1 thru 4.

---

### Post by J Tinsby on 2014-05-07
> **bobmoyer said:**
> I have two machines that dual-boot ubuntu 12.04 and xp and they work fine, just remember to choose the dual boot option at install and you should be fine. I went and installed the gnome desktop "sudo apt-get install gnome-shell" and to make life easier remember that you can cut and paste commands to the terminal using control-c and control+shift+v to paste in

HI Bobmoyer,

thanks for the info. I am trying to make a triple-boot system with XP,  Win 7 64, and Ubuntu.

If you have read all my previous postings and questions you can see where I'm at right now.

thanks for the input, I'll take all I can get!

PS: I do have a dual boot XP and Lubuntu for my wife to use and it's working fine.

Regards,

J T

---

### Post by J Tinsby on 2014-05-07
> **oldfred said:**
> I think this is the issue.

 dev/sda2 157292415 [COLOR=#ff0000]314584830[/COLOR] 78646208 5 Extended
/dev/sda3 [COLOR=#ff0000]314584830[/COLOR] 1250258943 467837057 7 HPFS/NTFS/exFAT

Those should not be the same. or sda3 needs to start after sda2.
I would shrink sda2 by 1 or 2 sectors and then it should work.

It looks like sda5 has several hundred sectors so you only have to change the extended partition size.
If your Windows tools will work on it, then use that.

oldfred,

I have tried to resize both partitions as you suggested and when I run the LIve CD & the commands fo check the HD the results are EXACTLY the same as the original one was.IE: I first resized the Win 7 partition by 500MB and ran the Live CD and your commands. Result was the same as the first time. So I thought "Oh I should have done the partition that has XP on it." So I went back in and resized that one by 500MB, ran LIve CD and got the same results.

ubuntu@ubuntu:~$ sudo parted -l
Error: Can't have overlapping partitions.                                 

Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xef5bef5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156268414    78134176    7  HPFS/NTFS/exFAT
/dev/sda2       157292415   314584830    78646208    5  Extended
/dev/sda3       314584830  1250258943   467837057    7  HPFS/NTFS/exFAT
/dev/sda5       157292544   314580991    78644224    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 


As you can see from this fresh example the sda2 and sda3 lines have the same number in them as before.

Sorry but what am I missing here?

I am wondering: That shrinking the partition isn't really changing it's physical size but rather the amount of data that can be written to it. The apparent size may be changing but the original size isn't being modified and isn't that what we are looking for? Maybe I should be using a separate version of GParted to make this change?

Thank you as always,

J T

---

### Post by oldfred on 2014-05-07
I would try Windows third party tools. I know a way with Linux but it is pretty complex.

       EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

---

### Post by J Tinsby on 2014-05-07
> **oldfred said:**
> I would try Windows third party tools. I know a way with Linux but it is pretty complex.

       EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

oldfred,

I even made a new 40GB ntfs partition and the installer didn't find it. I also d/l GParted and ran it from the CD, with the same result as Ubuntu, it only shows the entire drive not any partitions.

I have used Easeus in the past with good luck but it won't allow formatting to ext4 only ext3. What is the difference if I resize the partitions using Win 7 or Easeus?

 If I choose to resize a partition am I really changing the original size of it or the 'apparent size?" IE: We have a 5 gallon bucket and we fill it with 2.5 gals of solid concrete. Even though the bucket will only hold 2.5 gals of water it's still a 5 gal container. If you get my meaning. We've changed the apparent size but the physical size is the same when it's all said and done. This resizing doesn't seem to affect the end product as witnessed by the sudo fdisk -lu /dev/sda information set.



[ATTACH=CONFIG]252962[/ATTACH]

Will explore Easeus again and the mini partition tool too!

Thanks I appreciate all your time and effort, it will be a real victory when we DO get it sorted, and I think we will. I seem to encounter problems that few if any others ever have so it's almost expected :D

J T

---

### Post by oldfred on 2014-05-07
Another possible choice is fixparts. It is not for overlapping issues but it loads partitions and recalculuates extended partition. So it may just fix the issue.

Easier to run from Linux, but may have a Windows version but commands are different.
       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

      
 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

You should just need to use p to review partitions and then w to write that info. use q if it does not look correct.

---

### Post by J Tinsby on 2014-05-08
> **oldfred said:**
> Another possible choice is fixparts. It is not for overlapping issues but it loads partitions and recalculuates extended partition. So it may just fix the issue.

Easier to run from Linux, but may have a Windows version but commands are different.
       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

      
 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

You should just need to use p to review partitions and then w to write that info. use q if it does not look correct.

oldfred,

Thanks for giving me yet another choice to possibly fix the issue I am faced with.

Since I have images of all 3 partitions I was considering reformatting the HD making 3 new primary partitions, of various sizes, then re-installing my images to that drive. That should clearly change the sector size shouldn't it?

 What I do not know is if the images contain information that would change the type of partition back to what it was when the image was created. IE: If I restore a logical extended partition image to a partition that is primary, does it change it to logical extended? 

Still ruminating on what to do!

Cheers,

J T

---

### Post by oldfred on 2014-05-08
I have never done a partition image restore, so I really do not know.
If planning on doing that try some of the other suggestions just to see if any work first. Worst case you then have to restore partitions.
But I think you would have to create partitions and just make sure they are large enough and since the partitions in the extended do not use all of the extended but only a few hundred sectors and your issue  is only one or two sectors, I would think a restore would work. But extended needs to be slightly smaller.

---

### Post by J Tinsby on 2014-05-08
> **oldfred said:**
>  But extended needs to be slightly smaller.

If I knew how to make it smaller I'd be all over it. It's clear that shrinking the partition using Win 7's tools doesn't work, yes it makes it smaller but doesn't change anything else. 

That program called FIXPARTS looks like it might do the trick but I am afraid to use it, too many unfamiliar commands needed, at least right now for me. If I don't know what I am looking for there's no sense even trying it, best way to muck things up!

J T

---

### Post by oldfred on 2014-05-08
But we like to muck things up just to see if we can fix them. :)
Of course good backups are required.

We spend days trying to resolve an issue, when you can reinstall Ubuntu in less than an hour. Restoring data can take some time.

---

### Post by LastDino on 2014-05-08
In theory, restoring partition images should work as long as they are being restored on same type and have enough space. You might need to be careful with boot/MBR though. Does that program of yours copy that as well? 

-Asking out of curiosity.

---

### Post by J Tinsby on 2014-05-09
> **LastDino said:**
> In theory, restoring partition images should work as long as they are being restored on same type and have enough space. You might need to be careful with boot/MBR though. Does that program of yours copy that as well? 

-Asking out of curiosity.

Hi LastDino,

Yes Acronis does allow me to restore the MBR when I restore an image. Oddly enough Acronis uses Linux to restore backups otherwise called .tib files. When you boot from the recovery disc, that you hopefully have, you are booting into a Linux environment. 

Have used it for years and through many versions with great success, it's saved my butt many times! 
There is an option called "Try & Decide" that allows you to install programs and try them and then revert the system back to it's original state before the test install. I was advised by the Acronis forum not to use the "Try" for things that pertain to booting up, rather just make images of all the partitions that way you know you have a way to go back.
J T

---

### Post by J Tinsby on 2014-05-09
oldfred,

I found an unused 250GB SATA drive that I can add to my machine for test purposes. I'll format the drive and make 4 primary partitions and install my images to that drive. I will unplug my main drive so there's no chance of messing it up, then we'll see if Ubuntu will install on the freshly formatted drive. It may be time consuming but I'm sure not getting anywhere this way.

J T

---

### Post by oldfred on 2014-05-09
If you want to go a bit more advanced and it will only be Ubuntu you can use gpt partitioning. Then there is no limit on the number of partitions.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

      
 If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

But since I may move drives to a new system soon, that would also be UEFI, I also am including an efi partition at beginning of drive.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by LastDino on 2014-05-09
@Oldfred, So, basically if GPT partition table is used then there can be more than 4 primary partitions since it doesn't really qualify them into primary or logical, just partitions. So, when and if Gparted is used, will it mark 4 partitions as primary and rest into logical again? 

What is difference between ''/boot'' and ''/boot efi''? I know what is stored in /Boot but I'm not sure if I understood what we need /boot efi for, and what files are stored there? 

Also, I'll take my own partition scheme as example>
[ATTACH=CONFIG]253024[/ATTACH]

Lets suppose; I'm to install one more Linux OS and use some of the space from sd5/ext4, will it be turned into primary as well?  If yes, then how does that arrangement work?

Sorry for asking too many things in someone else thread, but I think this should clear few doubts that I've with understanding of this whole thing.

---

### Post by oldfred on 2014-05-09
Gparted works with gpt partitioning. But you should also add gdisk. The standard fdisk currently is only for MBR partitions.

With gpt all partitions are the same. There is a soft limit of 128 as that is the size of the partition table. But the partition table size is also user adjustable. With MBR the 4 primary partitions are all that fit into the MBR. 

Most desktops do not need a separate /boot partition. But some with server type configurations using RAID or LVM may need a /boot. The /boot has more grub and kernels and cannot really be shared if installing two distributions.
The efi partition has .efi boot files, but the /boot is stil inside / or could be another partition. The efi partition replaces the MBR for initial boot and is somewhat like having many MBRs all on one drive that then can be used to boot from.

Gparted somewhat confuses the boot issue as it uses the boot flag setting in gpt partitioned drives to set the GUID code for an efi partition. Gdisk uses a code of ef00 for efi. But in the gpt partition it really is some long GUID that defines what the partition is used for. 
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

If you convert a drive from MBR to gpt that will normally erase drive. But gdisk can be used to convert, but really good backups required.

---

### Post by LastDino on 2014-05-09
> **oldfred said:**
> Gparted works with gpt partitioning. But you should also add gdisk. The standard fdisk currently is only for MBR partitions.

With gpt all partitions are the same. There is a soft limit of 128 as that is the size of the partition table. But the partition table size is also user adjustable. With MBR the 4 primary partitions are all that fit into the MBR. 

Most desktops do not need a separate /boot partition. But some with server type configurations using RAID or LVM may need a /boot. The /boot has more grub and kernels and cannot really be shared if installing two distributions.
The efi partition has .efi boot files, but the /boot is stil inside / or could be another partition. The efi partition replaces the MBR for initial boot and is somewhat like having many MBRs all on one drive that then can be used to boot from.

Gparted somewhat confuses the boot issue as it uses the boot flag setting in gpt partitioned drives to set the GUID code for an efi partition. Gdisk uses a code of ef00 for efi. But in the gpt partition it really is some long GUID that defines what the partition is used for. 
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

If you convert a drive from MBR to gpt that will normally erase drive. But gdisk can be used to convert, but really good backups required.

That was quite informative, thanks! 
So, if and when I do use GPT making ''/boot efi'' is compulsory, or did I get that mixed up? 

I remember Arch having gdisk but does Ubuntu also has it? Is it possible to access it while doing installation from GUI mode, if not, how do I access CLI temporarily if it allows use of gdisk? 


Now since that is out of the way, in case of MBR, if I'm to dual boot Linux in my partition scheme (posted on last page), how do I need to edit it or how will gparted read my partition schem?

---

### Post by oldfred on 2014-05-10
@LastDino
Better to start your own thread. Not sure if OP is that interested in gpt. 
I always partition in advance usually with gparted. not sure there is any way to specify gpt in the installer.
gdisk is in repository. sudo apt-get install gdisk from terminal. 
efi partition only required if booting in UEFI mode. suggested only if drive may later then be in a UEFI sysem. But Windows only boots from gpt drive with UEFI, so if older system it must be Ubuntu only if you want gpt now.

---

### Post by LastDino on 2014-05-10
> **oldfred said:**
> @LastDino
Better to start your own thread. Not sure if OP is that interested in gpt. 
I always partition in advance usually with gparted. not sure there is any way to specify gpt in the installer.
gdisk is in repository. sudo apt-get install gdisk from terminal. 
efi partition only required if booting in UEFI mode. suggested only if drive may later then be in a UEFI sysem. But Windows only boots from gpt drive with UEFI, so if older system it must be Ubuntu only if you want gpt now.

No, worries, I got all the answers I needed. Thank you for taking your time with this :3

---

### Post by J Tinsby on 2014-05-14
> **oldfred said:**
> @LastDino
Better to start your own thread. Not sure if OP is that interested in gpt. 
I always partition in advance usually with gparted. not sure there is any way to specify gpt in the installer.
gdisk is in repository. sudo apt-get install gdisk from terminal. 
efi partition only required if booting in UEFI mode. suggested only if drive may later then be in a UEFI sysem. But Windows only boots from gpt drive with UEFI, so if older system it must be Ubuntu only if you want gpt now.

Hi oldfred,

I now have 4 primary partitions on my HD, first is XP, then Win 7, then Ubuntu (not formatted to ext4 yet but will do before install) and the last is for storage. Also have GParted on a CD to partition with and yes it finds ALL my partitions ....NOW :D
I don't know about using the gpt method that you mentioned I may give it a miss for now, but it's nice to know there is a way to format that has no limit to the amount of partitions you may have.

Do you think installing Ubuntu will allow GRUB to handle the booting of all 3 OS's or will it want to boot to Ubuntu only and ignore the Windows entirely? Or maybe it won't boot at all?

Note I DO have EasyBCD installed on my XP system, There is a way to add GRUB to the boot sequence but I am not sure if that's the right way to go about it.

Thank you, feeling better now with good results so far, DR. very pleased, as I am.

J T

---

### Post by LastDino on 2014-05-15
I don't know about easy BCD but grub should be able to detect all 3. Also, why are you keeping storage drive as primary?

---

### Post by cub2 on 2014-05-15
Welcome to the dark side ;) 
dual / triple booting seems to be your problem. Try the LTS (long term release) version of ubuntu (14.04). Make sure you have your partitions sorted e.g where you want to put ubuntu.

The graphical install will sort out all your problems so don't worry about bios concerns :) 

The two most basic commands that got me through the first two years of ubuntu were 

```


sudo apt-get update 

sudo apt-get install

```

---

### Post by J Tinsby on 2014-05-15
> **LastDino said:**
> I don't know about easy BCD but grub should be able to detect all 3. Also, why are you keeping storage drive as primary?

Hey LastDino,

Well I had so much trouble with the way I had the original partitions set up I figured the easiest way was to just make 'em all primary.  What's the harm the way it is? Thank heavens its booting and running as before the major changes.

J T

---

### Post by J Tinsby on 2014-05-15
> **cub2 said:**
> Welcome to the dark side ;) 
dual / triple booting seems to be your problem. Try the LTS (long term release) version of ubuntu (14.04). Make sure you have your partitions sorted e.g where you want to put ubuntu.

The graphical install will sort out all your problems so don't worry about bios concerns :) 

The two most basic commands that got me through the first two years of ubuntu were 

```


sudo apt-get update 

sudo apt-get install

```

Hello cub2,

Really at the start of all this, the trouble was that GParted didn't' see my ntfs partitions because one was an extended with logical inside it. I had to redo them all and have primaries, now the install will run fine and all partitions are seen. I have 40GB set aside for 14.04 I hope that's enough room for it to run. I don't know what I'd end up adding to it so I was a bit stingy giving it some space.

I'm not worried about the BIOS, rather the MBR and Grub are what is puzzling me. I have yet to actually install the OS but expect to do so today so cross all your parts that it works!

Thanks for those commands I will notate them.

Just an update if you can find this. I finally got Ubuntu installed and working fine, triple boot as I wanted. Ended up using the already installed EasyBCD program to point to Grub which I did not install in the normal spot. All 3 systems working as planned. Thanks again! Now come MORE questions!! :D

Cheers

J T

---

### Post by oldfred on 2014-05-15
You do have to stay with MBR partitions as XP does not work with gpt.

Windows has all its boot files in one primary partition with the boot flag. So do not delete XP without reconfiguring/repairing Windows 7 to be bootable.
It is better to keep all Windows installs on primary partitions as it must boot from a primary. Second installs can be in a logical but you never can delete the primary it boots from nor directly boot it.

I prefer grub2 as it is designed as a boot manager. EasyBCD modifies Windows and uses grub4dos to chainload to a install of the grub boot loader to the PBR - partition boot sector of the Ubuntu install. Never install grub to the PBR of a NTFS partition. Better to have grub2 installed to the MBR of the hard drive and let it offer to boot your Windows. Since Windows boot files are only in one NTFS partition grub will only find one and from that you have to choose which Windows to boot. But you can repair the second install to add boot files and direct boot either Windows if desired.
Installing grub2's boot loader to a PBR is not recommended because it makes grub fragile. You may have to regularly reinstall as it has to convert to blocklists or hard code addresses for the rest of grub in the install. If any file gets moved due to a fsck or update then you have to reinstall grub as it will fail. 

I think you also can move boot flag and run repairs:
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by J Tinsby on 2014-05-15
> **oldfred said:**
> You do have to stay with MBR partitions as XP does not work with gpt.

Windows has all its boot files in one primary partition with the boot flag. So do not delete XP without reconfiguring/repairing Windows 7 to be bootable.
It is better to keep all Windows installs on primary partitions as it must boot from a primary. Second installs can be in a logical but you never can delete the primary it boots from nor directly boot it.

I prefer grub2 as it is designed as a boot manager. EasyBCD modifies Windows and uses grub4dos to chainload to a install of the grub boot loader to the PBR - partition boot sector of the Ubuntu install. Never install grub to the PBR of a NTFS partition. Better to have grub2 installed to the MBR of the hard drive and let it offer to boot your Windows. Since Windows boot files are only in one NTFS partition grub will only find one and from that you have to choose which Windows to boot. But you can repair the second install to add boot files and direct boot either Windows if desired.
Installing grub2's boot loader to a PBR is not recommended because it makes grub fragile. You may have to regularly reinstall as it has to convert to blocklists or hard code addresses for the rest of grub in the install. If any file gets moved due to a fsck or update then you have to reinstall grub as it will fail. 

I think you also can move boot flag and run repairs:
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

oldfred,

As it stands now I can boot XP or 7 I get the choice when I cold boot the machine.

So when I get to installing Ubuntu and am asked "Where do you want to install the bootloader?" I should choose the main HD itself and not another partition? That's what I am reading but maybe not fully understanding.IE" Don't put it on an NTFS partition of XP or Win 7 correct?

I know I need to have a / (root) & a /swap = to RAM in GiB and a /home anything else? I have 55GB of space on that partition to work with.

Don't know if I understand how to load Grub2 as you describe, I was going to use the version of Grub that comes with Ubuntu, I don't know what version that is.

Cheers,

J T

---

### Post by oldfred on 2014-05-15
Grub does not use PBR or partition boot sector. 
Computers only boot from MBR, so if you do not install grub to the MBR or sda's first sector you will not be able to boot. Windows uses PBR for more boot code, grub does not. 

While this is Windows it shows how BIOS booting works.
Shows Vista but applies to all BIOS Windows installs. Mentions old grub legacy at end, but now everyone uses grub2.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by J Tinsby on 2014-05-19
I now have XP, Win 7, and Ubuntu on my drive as I wanted. On bootup I have a choice of any of the 3 'OS's. I used EasyBCD, already on XP, to allow me to add Ubuntu to the boot sequence, it was dead easy once I took the bull by the horns and did it.

I found this guide to be extemely helpful along with all the advice in the forum: [http://khangyu.wordpress.com/2011/11/21/triple-boot-windows-7-xp-and-ubuntu-by-using-usb/](http://khangyu.wordpress.com/2011/11/21/triple-boot-windows-7-xp-and-ubuntu-by-using-usb/)

Hope that link helps someone else, this thread can be marked ***solved***.

Regards,

J T

---

### Post by LastDino on 2014-05-19
You can mark it as solved from thread tools at the top of the thread.

---


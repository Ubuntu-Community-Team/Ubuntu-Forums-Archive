---
title: "Advise best version for old XP laptop"
date: 2013-09-27
forum: Recurring Discussions
---

### Post by mawil10132 on 2013-09-27
I've changed my original post to a solutions post.

System Info on unit says; emachine 5414 X86 Family model 8 stepping 2 authentic amd ~1596 Mhz total phy. mem. 256 mb avail. phy. mem. 71.28 total virtual mem. 2 gb avail. virt. mem 1.96

emachine specs say; [http://support.gateway.com/emachines/Mobile/Gateway/5000Series/4645sp6.shtml](http://support.gateway.com/emachines/Mobile/Gateway/5000Series/4645sp6.shtml)
  
  
UPDATE 01; **[Ubuntu 4.10 (Warty Warthog)]("http://old-releases.ubuntu.com/releases/warty/") This does install on emachine5414**;  

A. There is an issue with network connection.  Select to continue without doing anything.
B. Select screen resolution 1280x800 when asked. Arrow down the selections until 1280x800 is in view then press enter.
C. The screen writing is split and awkward to view. There is one function where you might not see two selections, one for yes, the other for no, left arrow over press enter.

UPDATE 02; **[Ubuntu 5.04 (Hoary Hedgehog)]("http://old-releases.ubuntu.com/releases/hoary/")** **This does install on emachine 5414 **

A. There wasn't a network connection issue, it went right through automatically.
B. Same as B above.
C. Same as C above.

UPDATE 03; _**xubuntu-6.06.1-desktop-i386**_ **This does install on emachine 5414**

There no issues during install, all worked better than previous so far.

UPDATE 04;  [Ubuntu 7.10 (Gutsy Gibbon)]("http://old-releases.ubuntu.com/releases/gutsy/")  **This does install on emachine 5414 !**

There were no issues during install, install went smoothly, this was the first version which seems to recognize the Linksys WUSB600n wireless thumb drive but for now I cannot enable 'Broadcom 43xx chipset family', I go to System , administration, restricted drivers, then the list pops up but when I select Enable, I get this message; the software source for package, bcm 43xx-fwcutter is not enabled.  

LAST UDATE: Had problems getting any version to install, I found out that the hard drive was the proble, so to fix, I used an older version, say down in the 8 range and that will fix the HD, do a full install using the ENTIRE HD, then you can load virtually any version, BUT this version of XUBUNTU will load, regardless of whatever errors are thrown up, just let it run through and it will load, ALSO it is the first version that will locate any and all wifi even if configured for hidden, there it is the easiest to use wifi on unless you already know how to configure hidden wifi manually. 

[http://iso.linuxquestions.org/xubuntu/xubuntu-10.10/](http://iso.linuxquestions.org/xubuntu/xubuntu-10.10/)

Other older versions show a partial screen during install, do not despair, simply arrow down untill you see what need then arrow up will bring highlight up to what you need, then hit enter, only one screen is a bugger and that is the finial message about do you want to erase entire HD, use the entire HD, you cannot see the yes or know, the No is automatically highlighted and it is to the right, soo, arrow over left then hit enter, you won't be able to see what you did but it will work.

Even the xubuntu have extra software such as games and office stuff, delete them to free up HD space or go and buy and install the 2GB max memory for the emachine 5414!

Anyone have questions email me,


Michael

---

### Post by papibe on 2013-09-27
Hi mawil10132.

As is, with only 256Mb of RAM, I'd recommend [Lubuntu]("http://www.lubuntu.net/").

I'm not very familiar with that AMD processor, but if it is closer to the performance of a P4, you may be able to get a nicer experience running [Xubuntu]("http://xubuntu.org/") (if you upgrade the RAM to, say, 1Gb).

Just a thought.
Regards.

---

### Post by mawil10132 on 2013-09-27
> **papibe said:**
> Hi mawil10132.

As is, with only 256Mb of RAM, I'd recommend [Lubuntu]("http://www.lubuntu.net/").

I'm not very familiar with that AMD processor, but if it is closer to the performance of a P4, you may be able to get a nicer experience running [Xubuntu]("http://xubuntu.org/") (if you upgrade the RAM to, say, 1Gb).

Just a thought.
Regards.

I found the Lubuntu download page but there are these, are they newer and older versions, if so, whats newest version?


[LIST]
[*][lucid]("http://packages.ubuntu.com/lucid/lubuntu-desktop") (metapackages): 	Lubuntu Desktop environment [**multiverse**]             
0.13: amd64 i386
[*][precise]("http://packages.ubuntu.com/precise/lubuntu-desktop") (metapackages): 	Lubuntu Desktop environment [**universe**]             
0.38: amd64 i386
[*][quantal]("http://packages.ubuntu.com/quantal/lubuntu-desktop") (metapackages): 	Lubuntu Desktop environment [**universe**]             
0.45: amd64 i386
[*][raring]("http://packages.ubuntu.com/raring/lubuntu-desktop") (metapackages): 	Lubuntu Desktop environment [**universe**]             
0.48: amd64 i386
[*][saucy]("http://packages.ubuntu.com/saucy/lubuntu-desktop") (metapackages): 	Lubuntu Desktop environment [**universe**]             
0.52: amd64 i386
[/LIST]

---

### Post by Bashing-om on 2013-09-27
mawil10132; Hi !
^+1 .. We are running Lubuntu quite nicely on an old AMD sempron processor machine.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-27
mawil10132; Hi ! again.

Here is the better guide, choose the AMD64 version 13.04 Standard PC.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by mawil10132 on 2013-09-27
Does anyone know what version had a logo of a rat?  I had that years ago on this same machine, just for curiosity.

Also, thought I'd try Xubuntu first but the it starts but screen goes black eventually.

Michael

---

### Post by mawil10132 on 2013-09-27
> **Bashing-om said:**
> mawil10132; Hi !
^+1 .. We are running Lubuntu quite nicely on an old AMD sempron processor machine.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


It won't run.

---

### Post by mawil10132 on 2013-09-27
> **papibe said:**
> Hi mawil10132.

As is, with only 256Mb of RAM, I'd recommend [Lubuntu]("http://www.lubuntu.net/").

I'm not very familiar with that AMD processor, but if it is closer to the performance of a P4, you may be able to get a nicer experience running [Xubuntu]("http://xubuntu.org/") (if you upgrade the RAM to, say, 1Gb).

Just a thought.
Regards.

It won't run.

---

### Post by Bashing-om on 2013-09-27
mawil10132;
> 
It won't run.
Does not tell us much with which to help you with.
Can you boot the liveCD into "try ubuntu" mode ?
No ? Then how far do you progress in the boot process ? What do you see if the boot is halted ?

OR

Have you "tried ubuntu" and installed .. what is the status of the install ? If installed do you boot to 'buntu ?
No ?  Then how far do you progress in the boot process ? What do you see if the boot is halted ?
yes ? can you boot to the GUI ?

[INDENT][INDENT]help us to help you
[/INDENT][/INDENT]

---

### Post by mawil10132 on 2013-09-27
[QUOTE=Bashing-om;12801036]mawil10132;

Does not tell us much with which to help you with.
Can you boot the liveCD into "try ubuntu" mode ?
No ? Then how far do you progress in the boot process ? What do you see if the boot is halted ?

OR

Have you "tried ubuntu" and installed .. what is the status of the install ? If installed do you boot to 'buntu ?
No ?  Then how far do you progress in the boot process ? What do you see if the boot is halted ?
yes ? can you boot to the GUI ?
[INDENT][INDENT]help us to help you
[/INDENT]
[/INDENT]
[/QUOTE


I downloaded both L and X ubuntu to another PC/Win7, right clicked on downloads and burned to DVD, put DVD into emachine, booted, I could tell they were strating install but got errors and blank screen before any menus.  ubuntu is too big, way back I tried 10.1 and it would not install, only the rat ?Xubuntu? what ever version number, cannot remember would install. I remember someone telling me it was a stripped down version.

---

### Post by Bashing-om on 2013-09-27
mawil10132;

Yes there are stripped down versions, however it does take a bit of know how to get the install set up.

Let's see what can be done to get 'buntu installed.
1. Did you verify the download integrity of the .iso images ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2. Is the disk burned as an "image" ?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3. There will be no install action taken until you select "install"
4. Have you set in bios to boot the DVD drive as 1st boot priority ?

We must conclude that the liveDVD is not booting.

When you boot the installDVD, as soon as the bios screen clears depress and hold the shift key -> language screen; escape key to accept the default -> Boot options menu screen .

Can you boot to this point ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by sanderj on 2013-09-28
> **mawil10132 said:**
> System Info on unit says; emachine 5414 X86 Family model 8 stepping 2 authentic amd ~1596 Mhz total phy. mem. 256 mb avail. phy. mem. 71.28 total virtual mem. 2 gb avail. virt. mem 1.96

emachine specs say; [http://support.gateway.com/emachines/Mobile/Gateway/5000Series/4645sp6.shtml](http://support.gateway.com/emachines/Mobile/Gateway/5000Series/4645sp6.shtml)

I will be making a full install so full memory will be available for whatever version you folks might suggest!


Based on:
1) 256MB RAM
2) SIS GPU (according to [http://ubuntuforums.org/showthread.php?t=1150888&p=7246787#post7246787](http://ubuntuforums.org/showthread.php?t=1150888&p=7246787#post7246787) and [http://support.gateway.com/emachines/Mobile/Gateway/5000Series/4645sp6.shtml](http://support.gateway.com/emachines/Mobile/Gateway/5000Series/4645sp6.shtml))

I would advice Windows XP. Certainly no Linux Desktop because of the two above reasons. SiS GPU's are a nightmare under Linux; I once bought a laptop with a SiS GPU, so I have experience with this. 
Linux Server (without GUI) could run, but you don't specify what you need. 

Hope this helps.

---

### Post by mörgæs on 2013-09-28
Yes, first of all you should try to get some more RAM if you want to run a desktop environment (DE).

After that you may or may not be lucky to get a DE running on the SIS graphics.

Don't try the AMD64 ISO mentioned above.

Yes, the rat means Xubuntu.

---

### Post by mawil10132 on 2013-09-28
> **sanderj said:**
> Based on:
1) 256MB RAM
2) SIS GPU (according to [http://ubuntuforums.org/showthread.php?t=1150888&p=7246787#post7246787](http://ubuntuforums.org/showthread.php?t=1150888&p=7246787#post7246787) and [http://support.gateway.com/emachines/Mobile/Gateway/5000Series/4645sp6.shtml](http://support.gateway.com/emachines/Mobile/Gateway/5000Series/4645sp6.shtml))

I would advice Windows XP. Certainly no Linux Desktop because of the two above reasons. SiS GPU's are a nightmare under Linux; I once bought a laptop with a SiS GPU, so I have experience with this. 
Linux Server (without GUI) could run, but you don't specify what you need. 

Hope this helps.

If your suggesting go back to XP because linux won't run on this laptop, your incorrect, I know this because it did, at one time, run on a version of ubuntu.

---

### Post by mawil10132 on 2013-09-28
> **mörgæs said:**
> Yes, first of all you should try to get some more RAM if you want to run a desktop environment (DE).

After that you may or may not be lucky to get a DE running on the SIS graphics.

Don't try the AMD64 ISO mentioned above.

Yes, the rat means Xubuntu.


I have found and downloaded xubuntu 6.06.1-desktop-i386, I tried running it and it did get to the point of asking what I wanted to do, and started instal but stalled at unpacking, as I left it run over night, so right now I running all the test available upon start up menu. I think this is the one I used in the past. I'm wondering does the install erase HD first?

---

### Post by mawil10132 on 2013-09-28
> **Bashing-om said:**
> mawil10132;

Yes there are stripped down versions, however it does take a bit of know how to get the install set up.

Let's see what can be done to get 'buntu installed.
1. Did you verify the download integrity of the .iso images ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2. Is the disk burned as an "image" ?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3. There will be no install action taken until you select "install"
4. Have you set in bios to boot the DVD drive as 1st boot priority ?

We must conclude that the liveDVD is not booting.

When you boot the installDVD, as soon as the bios screen clears depress and hold the shift key -> language screen; escape key to accept the default -> Boot options menu screen .

Can you boot to this point ?
[INDENT][INDENT]just try'n to help
[/INDENT]
[/INDENT]


I downloaded all ISO, then using a machine running Win7, right click on icon to burn ISO to a DVD, with the option; verify after burn. They all started to install but never get to the initial menu.

---

### Post by mawil10132 on 2013-09-28
I have a dysfunctional WinOS on an old emachine 5414 which came with XP.

I'm trying to do a full install of xubuntu, my question, do I need to prepare my HD before ahead of time to ensure all HD space and memory is available for xubuntu? OR, will xubuntu do all that for me?   I downloaded xubuntu and burned the ISO to a DVD using verify after burn.

---

### Post by Bucky Ball on 2013-09-28
No. Xubuntu will do that for you. If you want control of how the hard drive is partitioned, choose 'Something Else' when you get to the partitioning section of the install and partition it manually rather than let Xubuntu slice it up 'automagically'. 

Leave as is or wipe the drive first, up to you, but DON'T bother creating any partitions for Linux: *buntu uses EXT* partitions which Win knows nothing about (can't create, read/write to, or recognise). 

Hope that helps. ;)

Note: Sounds like you're pretty well good to go. When you get to the options hit 'Try Xubuntu' and see how it runs. You can then choose the install option from the desktop. If you have any further issues (not related to the question here) please start a new thread with a descriptive title for clarity and to increase your chances of help. Good luck!

---

### Post by mörgæs on 2013-09-28
Threads merged. Please don't create multiple threads on the same or closely related topics.

---

### Post by Bucky Ball on 2013-09-28
*Thread moved to **Recurring Discussions**.*

---

### Post by sudodus on 2013-09-28
Knoppix is a linux distro, that is known to work well with many old computers. I suggest that you download it from

[http://www.knoppix.org/](http://www.knoppix.org/)

and try it. Knoppix is not installed like the Ubuntu flavours. Instead it runs more like a live or persistent live system.

---

### Post by mawil10132 on 2013-09-28
> **mörgæs said:**
> Threads merged. Please don't create multiple threads on the same or closely related topics.

Oops! Sorry!

---


---
title: "broken packages"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by aprilm on 2012-08-28
Hi guys.

I am new to ubuntu (well sort of, I have had it a year but I am still lost). I attempted to upgrade to 12.04 the other day and my toddler x'd out of it when it was partially done. I think this caused a major problem because after that I tried to do a system update and it said I had broken packages. It didn't say which packages were broken but it told me to use the filter to find out what packages were broken. I tried to use the filter, but it isn't working. It has a bunch of options to select with boxes next to them And I selected all of them just to check everything and nothing happens. I don't know if this makes sense or not. But it seems to me like the filter to find what packages are broken isn't working. I don't know any ubuntu vocabnulary really so the solution to this would have to be spelled out step by step. I googled it and I found things that said to enter codes but I don't know where to go to even enter a code. Also I just bought my son minecraft and it is sooooo slow that he can't even play it :( any ideas on how to speed the game up so he can enjoy it? He was so excited about playing it and this was a real letdown. I believe I have ubuntu 10 or 11. Idk. I need to upgrade and everything is broken. Its bumming me out. 

Thanks!!!

---

### Post by Bashing-om on 2012-08-28
aprilm;

  This is fixable (as all things are in ubuntu).

  Not knowing what version you are running I can not tell you how to get to the command line terminal(CLI)// In 12.04 from the dash search for "terminal"

earlier versions terminal is Applications=>Accessories=>terminal.

get a cli (command line interface) and copy paste the following codes, one code line at a time, awaiting and noting any errors at each input if needed for further assist.
```
sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a --force-all
sudo apt-get -f install

```be aware the use of sudo requires your password; when entering the password will get no echo back to the terminal (security reasons).[INDENT]kindest regards <==BDQ
[/INDENT]

---

### Post by aprilm on 2012-08-28
Ok great! Thanks so much for responding.

I did what you said and I got a whole bunch of things that say w: failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/sources.gz) somethingwicked happened resolving 'us archive.ubuntu.com:http' (-5 - no adress associated with host name.

It just says this over and over and then it says "E:some index files failed to download, they have been ignored, or old ones used inste

I don't know what "something wicked happened"means but I think its so funny! Hahaha.

Also can you tell me how to find out which version I have?

Sorry if I seem dumb. I respect all you experts so much. This is a whole different language to me.

I would copy and paste the failure message but my husband is tying up the wifi and I can only use my phone right now to get on this forum.

---

### Post by aprilm on 2012-08-28
The second and third codes you gave me did nothing. Just oppened up a new thing to enter a code below it. 

The last code gave me this:

Correcting dependancies failed
The following packages have unmet dependancies
Libc6: depends:libc-bin (=2.11.1-0ubuntu7.10) but 2.15-0ubuntu10 is intalled

Recomends libc6-i686 python -louis:depends liblouis0 (>=1.70-2) but it is not installable
Ubuntu minimal depends libc6i686
E:error, pkgproblemresolver: :resolve generated breaks this may be caused by the ld packages
Unable to correct dependancies

Sad face.

---

### Post by critin on 2012-08-28
>  [aprilm]("http://ubuntuforums.org/member.php?u=1724928")   . I attempted to upgrade to 12.04 the other day and my toddler x'd out  of it when it was partially done. I think this caused a major problem I hate to say it, but the simplest and surest way to get a stable system is to reinstall and guard it until it's finished.

You might go into synaptic package manager and repair broken packages, but you've already tried other methods and they didn't work.  Apparently, the iso wasn't installed completely.

---

### Post by aprilm on 2012-08-28
Ok so I can just re do the install of 12.04 and forget the rest? I guess that makes sense. Duh. I can't believe I didn't think of that. For some reason I was convinced I needed to do a system update to fix what was broken. Ok. I will just re install the 12.04. How many hours does it take? When I first did it, it said something like "this will take several hours"

I guess what I was trying to do was just clean up the system and do an update to see if that would make my sons game go faster without having to wait "several hours".

---

### Post by critin on 2012-08-29
> **aprilm said:**
> Ok so I can just re do the install of 12.04 and forget the rest? I guess that makes sense. Duh. I can't believe I didn't think of that. For some reason I was convinced I needed to do a system update to fix what was broken. Ok. I will just re install the 12.04. How many hours does it take? When I first did it, it said something like "this will take several hours"

I guess what I was trying to do was just clean up the system and do an update to see if that would make my sons game go faster without having to wait "several hours".

You will need to download an iso image from ubuntu.com if you updated from a previous version via the update/upgrade application.

Download and burn it to a cd or copy to a usb via unetbootin.  You will need to download unetbootin if you don't have it already.  If you can get to software center, you can get it there.  The iso will be at ubuntu.com

It depends on your internet speed on how long it takes to download.  It will install in about 20 minutes after you've burned it.

---

### Post by NikTh on 2012-08-29
Hi , 
yes the simplest way is to reinstall. After all re-installation of Ubuntu is a about , what ? 15 minutes ? 

But if you want to try solve your problem with your current install , open a terminal and provide some info.. 
You can open a terminal with Ctrl+alt+t combination. 

Copy-paste from here to terminal below commands , one line at time. 
```
cat /etc/lsb-release && uname -r 
ls /etc/apt/sources.list.d/ 
cat -n /etc/apt/sources.list 
dpkg -l | grep linux-image  
sudo apt-get update
``` 

put the results between ```
 brackets . [noparse][code]The Results Here
```[/noparse]

Thank you

---

### Post by aprilm on 2012-08-29
Ok great thanks. I will try both of your suggestions tonight and update you with the results. Hopefully I can figure it out.

---

### Post by aprilm on 2012-08-29
So I dont know how to burn things, and I dont know what and iso is. I also dont know what you meant by putting the "results" in betweeen two codes with brackets. But I did do the codes in the terminal and I got this. Also, it is telling me I cant just re upgrade until I do a system update, which I cannot do due to the broken packages that I cannot repair.


-desktop:~$ cat /etc/lsb-release && uname -r 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
2.6.32-41-generic
-desktop:~$ ls /etc/apt/sources.list.d/ 
google-chrome.list              google-talkplugin.list
google-chrome.list.distUpgrade  google-talkplugin.list.distUpgrade
google-chrome.list.save         google-talkplugin.list.save
-desktop:~$ cat -n /etc/apt/sources.list 
     1	# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
     2	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3	# newer versions of the distribution.
     4	
     5	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     6	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    11	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    17	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    18	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    19	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    27	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    28	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    29	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    30	
    31	## Uncomment the following two lines to add software from the 'backports'
    32	## repository.
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
    39	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
    46	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    47	
    48	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    49	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    50	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    51	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    52	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    53	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
-desktop:~$ dpkg -l | grep linux-image  
ii  linux-image-2.6.32-21-generic         2.6.32-21.32                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-24-generic         2.6.32-24.43                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-25-generic         2.6.32-25.45                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-26-generic         2.6.32-26.48                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-27-generic         2.6.32-27.49                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-28-generic         2.6.32-28.55                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-29-generic         2.6.32-29.58                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-30-generic         2.6.32-30.59                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-31-generic         2.6.32-31.61                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-36-generic         2.6.32-36.79                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-41-generic         2.6.32-41.90                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic                   2.6.32.41.48                                    Generic Linux kernel image
-desktop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main Translation-en_US        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [776B]                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198B] 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Packages           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6kB]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Packages         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources          
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Packages [162kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Packages [3,968B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [41.0kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Packages [41.6kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [12.1kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Packages [2,369B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386B]
Fetched 318kB in 1s (161kB/s)                               
Reading package lists... Done
:~$

---

### Post by Bashing-om on 2012-08-29
No sweat.... we have installed so many times we forget what the first times were like.... down load the .iso image, BURN it to CD (or usb device), verify the integrity of the disk, reboot with install cd (bios set to boot cd first), follow the prompts .... if you want one can get choosy about the partitioning (and if the real need exist) ...other wise ..use the entire disk to install to and let the installer do it's thing..if you only have one disk on your system, this is all there is to it.
 We are here if you need further assistance !

[INDENT]BDQ
[/INDENT]

---

### Post by NikTh on 2012-08-29
Hi , 
Ok ! You have a completely messed up system . 
First of all, it seems that the Upgrade to 12.04 never happened. You still have Ubuntu 10.04 Lucid.
Second , you have a messed up sources.list with both versions sources , precise (12.04) and lucid (10.04).

I think the best way to proceed would be a new fresh install of Ubuntu 12.04.1 (we are now in 12.04**.1** version )

So 
1st download the .iso from here : [http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/) , Desktop .iso , 32 or 64 bits (depends on your CPU). 

2nd Backup all your important files to external hdd . 

3rd , burn the .iso either to CD or Usb (usb is better I.M.O) 

4th boot from CD / Usb and install. 

If you want assistance on how to burn the .iso to Usb , look here : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Thanks

---

### Post by aprilm on 2012-08-29
Ugh. This may as well be Swahili. I dont understand half the terms you guys use. I feels so stupid. But I think I know what I need to do. I will go buy a usb and download the link you gave me and give it a shot. Will update tomorrow. Thanks again. I want to stick with ubuntu and continue to learn the language. I do like this os and all its little perks.I really want to get my sons minecraft going for him. Hoping it happens after all this work.. Thanks so much, smart people! Cheers.

---

### Post by NikTh on 2012-08-30
Hi , 
of course you can post back here for any assistance - query -help , anything about installing Ubuntu. 
Thanks and welcome on board !

---

### Post by Petro Dawg on 2012-08-30
1st of all, don't feel stupid.  If you don't understand, its mostly because many of us have forgotten how it was when we got started getting involved in computers.  When we offer help, we just assume everyone knows what we know, and it comes off as "shop talk" to people who do not yet have experience with the behind the scenes operations of computing.

An "ISO image" is just the file type that downloads from the [Ubuntu website]("http://www.ubuntu.com/") when you select to install from a CD.  Its really no different than downloading a picture file or any other file type you might find on the internet.  An ISO image is a special file that has all the information required to make a "Copy" of a CD (like an Ubuntu installation CD for example).  When you save the ISO image on to a writable disk, it turns the writable disk into a copy of the Ubuntu installation Disk. 

Its like painting a picture; you start with a blank canvas, then you apply paint to the canvas to make into something valuable.  Except in this case, your "canvas" is a blank disk, and the "paint" is the ISO image.

I would give you a simple tutorial in how to Burn the image to a disk, but I assume if are not familiar with "Burning", you probably do not have blank writable disks laying around, and possibly no disk drive with a burner. 

Keep in mind that installing from a USB can be tricky in some cases and don't get discouraged if you have problems with it.  Most of us have failed doing installations at some point in the past, and its the failures that teaches us how to do things correctly.  So those of us that know the most, have probably failed the most as well.

---

### Post by Bashing-om on 2012-08-30
+1 for petro dawg's advice. well said.

re-numeration: someone is here to assist.

[INDENT]BDQ
[/INDENT]

---

### Post by critin on 2012-08-30
> **aprilm said:**
> Ugh. This may as well be Swahili. I dont understand half the terms you guys use. I feels so stupid. But I think I know what I need to do. I will go buy a usb and download the link you gave me and give it a shot. Will update tomorrow. Thanks again. I want to stick with ubuntu and continue to learn the language. I do like this os and all its little perks.I really want to get my sons minecraft going for him. Hoping it happens after all this work.. Thanks so much, smart people! Cheers.

Since you have a toddler to deal with, find a friend who knows how to create the usb.  I'd bet someone you know could do it for you.   It's not hard but it is complicated and must be done correctly  or it won't work.  There are tutorial How-To's on the web if you have time to study.

---

### Post by aprilm on 2012-09-13
Ok so I bought a usb, dowloaded the iso. I think i put the iso on the usb but I am not sure. Here is a screenshot of where I am at. I cant get it to launch. Do I right click or something? I made it executable. Can anyone give me a list of steps on the usb iso mystery so I can install 12.04. I don't care about my files. So i have nothing to save.

[[IMG]http://imageshack.us/a/img803/8007/screenshot4fs.png[/IMG]](http://imageshack.us/photo/my-images/803/screenshot4fs.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by ChinaJustin on 2012-09-14
Unfortunately, it's not so easy as just copying the .iso file to the USB  disc and making it executable (after all, that would be TOO easy,  right? :wink: )

You have two choices available to you to get the .iso set up so your  computer will be able to read it and install it. Both are small programs  you can download from the internet: unetbootin and LiLi USB Creator.

**(EDIT:** Actually, there's a third option (I think) on Ubuntu: an actual image writing program (putting the paint on the canvas), where it will do the same thing as I outline below, but is already installed on Ubuntu. I'll be honest: I'm using a different version of Linux that's based on Ubuntu, not Ubuntu itself. Which means I don't know the exact name of the already installed program on Ubuntu; on my version, it's called "ImageWriter" and is under my "Accessories" sub-menu, but, again, it may be different from yours. I've just always used the program below, because that's how I started getting Linux on a computer, and I've just stuck with it.)

LiLi is only on Windows, while unetbootin has a Linux version as well as a Windows version. How comfortable are you with installing something on Linux? Or would you rather do something in Windows?

Here are the instructions for LiLi if you decide to use that. If you are fine with Linux (or don't have access to a Windows computer), let us know, and we'll walk you through it.

 I  recommend LiLi (short for Linux Live) as it's pretty straightforward...  and it's also the only one I've used. Hehe.

1) Go here [http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download) to download LiLi. Just click on the big red "download" button.
2) Once it's done, run the program you just downloaded.
 - Choose your preferred language (I'm assuming English here ;-) ) and click OK.
 - Click "Next".
 - Click "Install".
 - When it's completed and the green install progress bar is green, click "Next".
 - Now, click "Finish", making sure the "Run LinuxLive USB Creator" box has a checkmark in it.
3) The program will load and you'll see the program has five different "Steps".
 -  Step 1 is to choose your USB key. If it's not plugged in already, plug  it in now. Then choose the drive that is your USB key; it should be the  only one that you see, assuming there are no other USB drives (external  hard discs, external DVD/CD-ROM drives, or other USB keys) plugged in.
 -  Step 2 is to "Choose a Source". This is where you need to choose the  .iso you downloaded. If you MOVED the .iso from your computer to the USB  key (so the USB key has the only copy), then you need to move it back  to your computer, putting it somewhere easy to remember (your Desktop,  Documents folder, Downloads folder, etc.,); if you COPIED it to your USB  key (so there's a copy of the .iso on your USB key AND on your computer  where you downloaded it originally), you don't need to do anything.  Either way, Click on "ISO / IMG/ ZIP" and navigate your way to the .iso  that's on your computer. It will now check the integrity of the .iso  file; this is good, because if something messed up with your download,  it will prompt you and save you a headache during the reinstall (bad  downloads = corrupted/missing pieces in the download = another messed up  install)
 - Step 3 is "Persistence" and doesn't need to be changed. Just skip it.
 -  Step 4 is "Options". I always like to choose the second option "Format  the key in FAT32 (this will erase your data!!)". It does just what it  says; since you just bought this USB key, it shouldn't be an issue,  because there's no important data on there. Make sure the other two boxes are empty.
 -  Step 5: "Create"! Just click the lightning bolt, sit back, and in a few  minutes your USB key is ready to use with a readable copy of the  install .iso file. Also, when it's done, LiLi will start your web  browser up with a web page telling you it's completed; don't worry, your  computer hasn't been hijacked!
4) When it's finished, plug the USB key into the computer you're needing to install Linux onto.

Now, assuming everything is working right, your computer *should* read the USB key and begin the installation. If not, and it starts up as normal into the old version of Ubuntu, we need to get a bit more technical and change your computer to read the USB key FIRST. Not difficult at all, just a bit more than the novice user ever has to deal with.

---

### Post by aprilm on 2012-09-14
I dont have windows, so I would need the untebootin. Man this is complicated!!!! lol!

---

### Post by aprilm on 2012-09-14
Ok I started the unetbootin process and I got this. I dont know what to do now. Thank you guys. I am hoping to get this ball rolling tonight with the 12.04 so my kiddo can play minecraft and my computer will run better. Otherwise, I am just going to take it into the shop where I got it and have the ubuntu genius there instal it for me. I am trying to do it myself though because I want to learn.

[[IMG]http://imageshack.us/a/img27/7485/screenshot6kl.png[/IMG]](http://imageshack.us/photo/my-images/27/screenshot6kl.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by NikTh on 2012-09-14
> **aprilm said:**
>  I am trying to do it myself though because I want to learn.

Hi , 

Learn lesson 1 : How to burn an .iso image with unetbootin. Tutorial with images.
[http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install)
not exactly the same images , but you will figure it out. 
**Tip: **Before you open Unetbootin is better to have the USB attached already.

Learn Lesson 2 : How to install Ubuntu. Short Video Tutorial :
[http://www.youtube.com/watch?v=ba9Wv-XU_4M](http://www.youtube.com/watch?v=ba9Wv-XU_4M)

**Tip: **To boot from USB (and not HDD) you must configure your BIOS , so the first boot device will be USB device. 
OR
Press "One Boot Key" during PC boot (in my laptop is F2) for the menu comes up and choose what device you want to boot from. You must have the USB already attached of course.

Thanks

---

### Post by aprilm on 2012-09-28
Omg I think I broke my computer. I downloaded untebooten and it made me reboot and now my computer is totally stuck on a boot screen and it says automatic boot and just keeps counting down from 10 over and over even if I restart the computer. Its completely broken. Help :(

---

### Post by Bashing-om on 2012-09-29
Hi ! Again //
Ain't broke, just needs a bit of fixing.
ubuntu -> all things are fixable.

You got the first prerequisite -> install cd ?
no ?
Can you get the grub menu (hold shift down after bios screen clears) ?

[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by aprilm on 2012-09-29
Ummm... I don't know what "install cd means. I put a usb in the computer and downloaded untebootin and then ran it and when it had to reload, I get a blue screen that just keeps counting down from 10 over and over. And I also don't know what a grub menu or a bio screen are. Yikes. This really sucks.

---

### Post by aprilm on 2012-09-29
This has been going on for so long without resolve and I am really upset because the computer shop I got it from was staffed by ubuntu geniuses and I took the computer by there so they could look at it for me and the stupid place had turned into a dumb yoga studio and now I can't find anyone in this town that knows anything about ubuntu. Maybe its time to give up and get a new toy. Like a nice little laptop :)

---

### Post by Bashing-om on 2012-09-29
Nay on other toys (my advise)...This is a small matter of coordination ..and a lack of knowledge of usb on my part. I have never attempted an install other than the my tried and true method via .iso burned to cd.

 I know this is aggravating and frustrating, but, hang in there and you will master your machine!

Back on topic: Blue screen ? At what point in the booting process do you get to this "blue screen" ...Do you boot as far as the grub menu ? (try holding down the shift key after the bios screen clears).

Another thought: Have you ever been able to boot up ubuntu in the "try ubuntu" mode ?

If we can identify the issue, we can advise on some boot options.

[INDENT]My Regards <==BDQ

[/INDENT]

---

### Post by aprilm on 2012-10-03
Right after I downloaded untebooten it asked me if I wanted to reboot now and I clicked yes. Now I have a booting screen that is blue and counts down from ten over and over to infinity even if I try turn the computer off and turn it on again. I do not know what bios means. I tried pushing tab for menu options and it gives me a thing like to put a code in but I don't know what to put. I also tried to push shift and it just scrolls down unintelligable letters and numbers. I am thinking my computer has officially crashed unless there is some type of code to type in after I push tab and get the thing where I am supposed to put a code it (you know with the colon at the end)

---

### Post by aprilm on 2012-10-03
Also I have no idea what you mean about the "try ubuntu" thing. Thanks for responding. Is there a code I can use to get out of this blue thing? I think I have ubuntu 10.04 if that helps.

---

### Post by Bashing-om on 2012-10-03
aprilm ...

I am looking and thinking ..get back with you soonest.

[INDENT]BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-10-03
aprilm;

Let's see what we can do.
ok I need to know that in bios (basic input/output system) you have set the option to boot the usb as 1st boot priority.

bios => the first step in booting up a operating system, see this article for a good explanation:
[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

When you are booting into ubuntu from the usb device, at the blue screen depress the enter key. At this point what is the result ?

[INDENT]Try'n to Help <==BDQ

[/INDENT]

---

### Post by aprilm on 2012-10-12
Ok. Here is what I see, exactly.

There is a large blue box. Rectangular in shape. Surrounded by black. In the top of the blue triangel, it says UNetbooten. Then right under that is a grey small long rectangle that has black letters that say Default. Under the blue box, in red letters, it says Press[tab] to edit options. Below that are the white letters that say Automatic boot in ___ seconds. The ____ is where it is counting down from 10 over and over to infinity. Does that help? Thanks sooooo much if you can help me I will send you flowers. Or something lol !!!!!

---

### Post by aprilm on 2012-10-12
Dang it. Not triangle. Blue RECTANGLE in the top of the screen takes up about 3 4ths of the screen. Mehhhhh.

---

### Post by aprilm on 2012-10-12
Also to answer your question, I am trying to do ubuntu 12.04 I guess. I was actually just trying to do a system update and it crashed. Also when I depress the enter key, nothing happens at all except static type lines on the entire screen.

---

### Post by aprilm on 2012-10-12
As for the usb studf, I don't know. I just put in the usb, downloaded uetibooten and then this happened. I am starting to think I am too stupid for this OS. It 'sucks!

---

### Post by Bashing-om on 2012-10-12
Don't be so hard on yourself !...This is an abnormal situation, that has a solution. I feel bad that I do not have the experience/knowledge to assist you in unetbooten as I also have never experienced it.

What I will suggest till better help arrives is take the usb drive to another computer and see if ubuntu will boot up. If the other system boots, that proves you have a good install medium, else maybe a bad usb install medium.

As I have no boot experience other than cd and hard drive, at this time I am not able to assist you //When You can boot up to grub or beyond, yes!

As of now we are waiting on persons with unetbooten experience to respond to this thread.
[INDENT]life is not so good computerless <==BDQ

[/INDENT]

---

### Post by aprilm on 2012-10-14
Thanks so much. I just need a code to get out of the boot screen I think. I don't know what grub is. I don't have another computer. This one was getting old anyway. I am just thinking maybe ubuntu is more for people that know more about computers. I have tried to understand it but it never clicks. I wish it worked though. It was great before I started to try and clean it up a bit to get it to run faster. I don't know. I'm really frustrated. Its my daughters birthday today and I can't even upload pictures except from my phone. And I paid 30 dollars for minecraft and my son can't even play it.  But thanks for trying to help me. I will keep checking back for awhile. Then I will just buy a new one if I can't solve this.

---

### Post by aprilm on 2012-10-14
[http://ubuntuforums.org/showthread.php?t=1532238](http://ubuntuforums.org/showthread.php?t=1532238)

Here is a link to a thread that I found that has my exact problem if that will help you guys.

---

### Post by critin on 2012-10-14
> **aprilm said:**
> Right after I downloaded untebooten it asked me if I wanted to reboot now and I clicked yes. Now I have a booting screen that is blue and counts down from ten over and over to infinity even if I try turn the computer off and turn it on again. I do not know what bios means. I tried pushing tab for menu options and it gives me a thing like to put a code in but I don't know what to put. I also tried to push shift and it just scrolls down unintelligable letters and numbers. I am thinking my computer has officially crashed unless there is some type of code to type in after I push tab and get the thing where I am supposed to put a code it (you know with the colon at the end)

The poster in the link you gave only had to download a fresh iso as his was corrupted.  I suggest you try that.

There are a few steps missing here.  unetbootin will **not** ask you to reboot if you've only downloaded it.

I suspect you have a bad iso because if you inserted the usb stick, opened unetbootin, browsed to the downloaded iso on your computer, highlighted it by clicking it once with the mouse and  saw it in unetbootin's window, all you'd have to do is start unetbootin at the start button.  When it finished installing the iso is when it would ask you to reboot or exit.

If the iso is to be installed in another computer, you 'remove hardware safely', remove the usb and insert it in the other computer.  Boot from it and choices of DEFAULT, TRY, INSTALL, would show.  Choose TRY to check it out.

Again, I'd download a fresh iso and follow a tutorial to install it to usb and then to computer.

If unetbootin doesn't work for you, there are others.  Rufus is very good, for instance.   
Perhaps downloading a fresh unetbootin would work, it also may be corrupted.

---

### Post by critin on 2012-10-14
> **aprilm said:**
> As for the usb studf, I don't know. I just put in the usb, downloaded uetibooten and then this happened. I am starting to think I am too stupid for this OS. It 'sucks!

Did you download unetbootin to the USB?  You don't do that.    unetbootin is the app that allows you to install the ubuntu image to a usb flash stick.  Once the image is installed to the usb flash, you're finished with unetbootin.

You download unetbootin to the computer desktop.  If you already have a good iso image, insert the usb stick in the computer, THEN open unetbootin, browse to the iso wherever it is stored on the computer, highlight it, make sure the name shows in unetbootin's window (at the bottom) and click start.

---

### Post by critin on 2012-10-14
> **aprilm said:**
> Ok I started the unetbootin process and I got this. I dont know what to do now. Thank you guys. I am hoping to get this ball rolling tonight with the 12.04 so my kiddo can play minecraft and my computer will run better. Otherwise, I am just going to take it into the shop where I got it and have the ubuntu genius there instal it for me. I am trying to do it myself though because I want to learn.

[[IMG]http://imageshack.us/a/img27/7485/screenshot6kl.png[/IMG]]("http://imageshack.us/photo/my-images/27/screenshot6kl.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

You must have the usb stick already plugged in or unetbootin won't find it.  I see you don't or the drive letter would be showing here.

Okay, see where it says DISK IMAGE?  Click the circle.  Go to the browse box, far right in same line.  It has tiny dot line inside.    It will open files so you can find the iso image.  Highlight the iso by clicking on it one time.    Do NOT open it with your mouse.  Choose open from the bottom of the page.

Look in the empty box after the text ISO.  Is your image name there?

Ignore the SPACE line--nothing goes there.

Make sure the drive is correct for the usb by knowing which drive letter before beginning.   It will be correct though, if you don't have any other usb device plugged in.  USB Mouse/keyboard don't count as drives.  Don't worry about those.

Click OK.  Let it install.  When it is done,  choose reboot, hit the correct boot key that will show on the first page that opens after the restart, the bio page.  Hit the key before the bio page goes away, choose boot from usb, flash, or it may show the name of the usb (sandisk) etc.

---

### Post by aprilm on 2012-10-18
> **critin said:**
> You must have the usb stick already plugged in or unetbootin won't find it.  I see you don't or the drive letter would be showing here.

Okay, see where it says DISK IMAGE?  Click the circle.  Go to the browse box, far right in same line.  It has tiny dot line inside.    It will open files so you can find the iso image.  Highlight the iso by clicking on it one time.    Do NOT open it with your mouse.  Choose open from the bottom of the page.

Look in the empty box after the text ISO.  Is your image name there?

Ignore the SPACE line--nothing goes there.

Make sure the drive is correct for the usb by knowing which drive letter before beginning.   It will be correct though, if you don't have any other usb device plugged in.  USB Mouse/keyboard don't count as drives.  Don't worry about those.

Click OK.  Let it install.  When it is done,  choose reboot, hit the correct boot key that will show on the first page that opens after the restart, the bio page.  Hit the key before the bio page goes away, choose boot from usb, flash, or it may show the name of the usb (sandisk) etc.

I can't do this because I can't even get out of this blue screen that is counting down from 10. I am totally stuck in the blue unetbooten screen that says automatic boot or whatever. Even if I unplug the usb. Even if I unplug and plug the computer back in. There is no mouse arrow because it is totally frozen in the rebooting thing no matter what I do. I would have done this whole unetbooten thing with a disk, but I don't think my desktop burns disks. I am totally illiterate with this operating system. I do not understand anything about it at all. If there I s any possible way to get out of the blue screen, I may be able to move forward and try again with untebooten or whatever I need in order to get 12.04. I don't know guys. I think its over. I think I am going to give up on it. I may just call the geek squad and get windows. Or just buy a new computer and call it a day. If I can get out of this booting screen, I will have a chance. But I don't know how.

---

### Post by Bashing-om on 2012-10-18
I ain't over...As I know nothing of  unetbootin, again, can not help you there.
however, have you considered purchasing the cd ( i Think about $3.00)//this link:
[http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17)

there are other sources (google: purchase ubuntu cd)

hopefully critin will respond again (or others).

[INDENT]where there is a will, there is a way ! <==BDQ

[/INDENT]

---

### Post by aprilm on 2012-10-18
Wow I can definately afford 3 dollars. Not sure if putting this disk in would do anything though now that I am stuck here in the endless countdown from hell. Thanks for your continued help. I appreciate the time you have taken to try and help me figure it out.

---

### Post by Bashing-om on 2012-10-18
Well, disallowing a bios problem. Install from the cd should be a piece of cake -compared to what you have been through- : chocolate cake!
set in bios the cd as 1st boot priority, insert cd into cd drive, wait for it to boot->suggest the "try ubuntu" option to see that all functions with 12.04.1//like it; back on the desktop, choose "install ubuntu" let the install wizard do it's thing answering minimal questions and done. ==> happy ubuntu'n

still try'n to help <==BDQ

---

### Post by critin on 2012-10-19
> **aprilm said:**
> I can't do this because I can't even get out of this blue screen that is counting down from 10. I am totally stuck in the blue unetbooten screen that says automatic boot or whatever. Even if I unplug the usb. Even if I unplug and plug the computer back in. There is no mouse arrow because it is totally frozen in the rebooting thing no matter what I do. I would have done this whole unetbooten thing with a disk, but I don't think my desktop burns disks. I am totally illiterate with this operating system. I do not understand anything about it at all. If there I s any possible way to get out of the blue screen, I may be able to move forward and try again with untebooten or whatever I need in order to get 12.04. I don't know guys. I think its over. I think I am going to give up on it. I may just call the geek squad and get windows. Or just buy a new computer and call it a day. If I can get out of this booting screen, I will have a chance. But I don't know how.

Wowee, even unplugging don't work?    As for this issue, it isn't the OS, it's installing unetbootin in the wrong place, I think.  I wonder if it's installed in Ram?  It's still there with the usb removed, right?

What I would do at this point is upplug the computer, open the computer and remove the battery.  (I didn't go back to first post and don't remember if it's a desktop or laptop),  you might not can do this on a laptop.  I'm not talking of the power battery on laptop, but the tiny round battery located in the MB.  Plug the power in and push the power button for a few seconds.  

Replace the battery & side cover and start the machine without the usb.  Hopefully, the unetbootin screen will be gone.   Then install from a purchased CD/DVD as suggested by  Bashing-om.  Your local library might have one, or local computer shop might make you one for the price of the cd.  They might install the iso on your usb.  Installing with a usb is just as easy as a CD, but your situation is one I haven't seen before--unique.  

Removing the battery might not fix it but it won't do a desktop any harm.  I don't have a laptop, but I don't think it's as easy to work on.    Don't forget to clean the usb before trying to use it again.  Formatting will erase it, but let it format to whatever it is already formatted to--don't change that. 

This is a hardware problem of the mysterious kind.

---

### Post by Bashing-om on 2012-10-19
critin,  your input sure makes me feel better !

---

### Post by aprilm on 2012-10-19
Great! I will try this today when I get home. It is a desktop. My husband will be able to show me where the batery is. And yes I had the usb in when I did unetbooten. I guess I missed a step or something. I am going to watch the tutorials again that were posted on this thread so that I can learn and do it right next time. My ultimate goal is to get the dang thing running at a decent speed. Get it cleaned up. I don't have anything important on it so I don't care if I wipe everything out completely and just start over. All I use this computer for is typing stuff up, my son playing minecraft, and sharing pictures. I am really boring. I also have all my pictures and stuff on a cloud, so I don't care if they get erased. I am going to stop by a small computer shop by my house today and ask if they have the ubuntu disk, and if they don't I will just get it online. Will update later after I disect my machine. Thanks a bunch. If this blue screen goes away, I may need more help trying to figure out what to do next as far as cleaning up my system. The system updates have given me problems since day 1.

---

### Post by Bashing-om on 2012-10-19
sounds like a great plan of action to me ...->
We are here and more than willing to help in any way we can (so you have found out!)

[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by aprilm on 2012-10-20
Hi guys. I love you. It worked. Thank you so much. I am typing this from my desk top. Now onto the next thing.... I dont even mind keeping the 10.04, so long as I can just get it cleaned up and running at a speed that makes playing minecraft possible. When my son tries to play it, it is sooooo slow its not even play able.

Here are a few screenshots of what I get when I attempt a system update.

[[IMG]http://imageshack.us/a/img17/1340/screenshot7ls.th.png[/IMG]](http://imageshack.us/photo/my-images/17/screenshot7ls.png/)

[[IMG]http://imageshack.us/a/img21/3081/screenshot8yl.th.png[/IMG]](http://imageshack.us/photo/my-images/21/screenshot8yl.png/)

My question is, what is the easiest way to get it running nicely? I don't think I have been doing the system updates right. How often should I do them. Is there a way to get 12.04 easily? I don't know how to burn disks. I think my computer can burn a disk, but I am not sure. What do you guys suggest to get the best out of my machine?

**[SIZE="4"][COLOR="DeepSkyBlue"][COLOR="Blue"]THANK YOU SO MUCH FOR GIVING MY COMPUTER BACK TO ME!!!!![/COLOR][/COLOR][/SIZE]**:guitar:

---

### Post by aprilm on 2012-10-20
....will this help with figuring out my broken package problem?

```
Considering libnepomuk4 1 as a solution to libnepomukquery4a 1
  Holding Back libnepomukquery4a rather than change libnepomuk4
Investigating libnepomukdatamanagement4
Package libnepomukdatamanagement4 has broken Depends on libnepomuk4
  Considering libnepomuk4 1 as a solution to libnepomukdatamanagement4 0
  Holding Back libnepomukdatamanagement4 rather than change libnepomuk4
Investigating libkimproxy4
Package libkimproxy4 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libkimproxy4 0
  Holding Back libkimproxy4 rather than change libkio5
Investigating ubuntu-desktop
Package ubuntu-desktop has broken Depends on xorg
  Considering xorg 46 as a solution to ubuntu-desktop 0
  Re-Instated libatspi2.0-0
  Re-Instated at-spi2-core
  Re-Instated libgdict-common
  Re-Instated libgdict-1.0-6
  Re-Instated gnome-dictionary
  Re-Instated gnome-screenshot
  Re-Instated gnome-search-tool
  Re-Instated gnome-system-log
  Re-Instated gnome-utils
  Re-Instated baobab
  Re-Instated checkbox
  Re-Instated checkbox-qt
  Re-Instated foomatic-db-compressed-ppds
  Re-Instated gnome-font-viewer
  Re-Instated language-selector-common
  Re-Instated language-selector
  Re-Instated language-selector-gnome
  Re-Instated at-spi
  Re-Instated libatk-adaptor
  Re-Instated libatk-adaptor-schemas
  Re-Instated libnotify-bin
  Re-Instated lightdm
  Re-Instated pnm2ppa
  Re-Instated printer-driver-pnm2ppa
  Re-Instated rfkill
  Re-Instated ubuntu-extras-keyring
  Re-Instated libdconf-dbus-1-0
  Re-Instated libdconf-qt0
  Re-Instated libqtbamf1
  Re-Instated libqtgconf1
  Re-Instated libqtdee2
  Re-Instated libunity-2d-private0
  Re-Instated unity-2d-common
  Re-Instated unity-2d-panel
  Re-Instated unity-2d-spread
  Re-Instated unity-2d-shell
  Re-Instated metacity-common
  Re-Instated metacity
  Re-Instated unity-2d
  Re-Instated liblightdm-gobject-1-0
  Re-Instated unity-greeter
  Re-Instated x11-common
  Re-Instated xdiagnose
    Reinst Failed because of xorg
  Removing ubuntu-desktop rather than change xorg
Investigating libkatepartinterfaces4
Package libkatepartinterfaces4 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libkatepartinterfaces4 0
  Holding Back libkatepartinterfaces4 rather than change libkio5
Investigating libkde3support4
Package libkde3support4 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libkde3support4 0
  Holding Back libkde3support4 rather than change libkio5
Investigating libkdewebkit5
Package libkdewebkit5 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libkdewebkit5 0
  Holding Back libkdewebkit5 rather than change libkio5
Investigating kdoctools
Package kdoctools has broken Depends on libkio5
  Considering libkio5 1 as a solution to kdoctools 0
  Holding Back kdoctools rather than change libkio5
Investigating libkrossui4
Package libkrossui4 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libkrossui4 0
  Holding Back libkrossui4 rather than change libkio5
Investigating katepart
Package katepart has broken Depends on libkatepartinterfaces4
  Considering libkatepartinterfaces4 0 as a solution to katepart 0
  Holding Back katepart rather than change libkatepartinterfaces4
Investigating libnepomukutils4
Package libnepomukutils4 has broken Depends on libnepomuk4
  Considering libnepomuk4 1 as a solution to libnepomukutils4 0
  Holding Back libnepomukutils4 rather than change libnepomuk4
Investigating libkmediaplayer4
Package libkmediaplayer4 has broken Depends on libkparts4
  Considering libkparts4 1 as a solution to libkmediaplayer4 0
  Holding Back libkmediaplayer4 rather than change libkparts4
Investigating libnepomuksync4
Package libnepomuksync4 has broken Depends on libnepomuk4
  Considering libnepomuk4 1 as a solution to libnepomuksync4 0
  Holding Back libnepomuksync4 rather than change libnepomuk4
Investigating libknotifyconfig4
Package libknotifyconfig4 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libknotifyconfig4 0
  Holding Back libknotifyconfig4 rather than change libkio5
Investigating kdelibs5-plugins
Package kdelibs5-plugins has broken Depends on libkde3support4
  Considering libkde3support4 0 as a solution to kdelibs5-plugins 0
  Holding Back kdelibs5-plugins rather than change libkde3support4
Investigating libkutils4
Package libkutils4 has broken Depends on libkprintutils4
  Considering libkprintutils4 1 as a solution to libkutils4 0
  Holding Back libkutils4 rather than change libkprintutils4
Investigating telepathy-butterfly
Package telepathy-butterfly has broken Depends on python-papyon
  Considering python-papyon 1240 as a solution to telepathy-butterfly -1
  Removing telepathy-butterfly rather than change python-papyon
Investigating libasound2
Package libasound2 has broken Breaks on libasound2-plugins
  Considering libasound2-plugins 11 as a solution to libasound2 114
  Upgrading libasound2-plugins due to Breaks field in libasound2
Investigating kdelibs5
Package kdelibs5 has broken Depends on kdelibs5-plugins
  Considering kdelibs5-plugins 0 as a solution to kdelibs5 75
  Removing kdelibs5 rather than change kdelibs5-plugins
Investigating libplasma3
Package libplasma3 has broken Depends on libkdewebkit5
  Considering libkdewebkit5 0 as a solution to libplasma3 30
  Removing libplasma3 rather than change libkdewebkit5
Investigating ppp
Package ppp has broken Breaks on network-manager
  Considering network-manager 5 as a solution to ppp 26
  Upgrading network-manager due to Breaks field in ppp
Package ppp has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to ppp 26
  Upgrading network-manager-pptp due to Breaks field in ppp
Investigating plasma-scriptengine-javascript
Package plasma-scriptengine-javascript has broken Depends on libkio5
  Considering libkio5 1 as a solution to plasma-scriptengine-javascript 23
  Removing plasma-scriptengine-javascript rather than change libkio5
Investigating gnome-control-center
Package gnome-control-center has broken Depends on libnm-gtk0
  Considering libnm-gtk0 10 as a solution to gnome-control-center 17
  Removing gnome-control-center rather than change libnm-gtk0
Investigating nautilus
Package nautilus has broken Breaks on gnome-bluetooth
  Considering gnome-bluetooth 3 as a solution to nautilus 11
  Upgrading gnome-bluetooth due to Breaks field in nautilus
Investigating libasound2-plugins
Package libasound2-plugins has broken Depends on libjack-jackd2-0
  Considering libjack-jackd2-0 0 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-jackd2-0
Package libasound2-plugins has broken Depends on libjack-0.116
  Considering libjack0 9 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-0.116
  Or group keep for libasound2-plugins
Investigating indicator-power
Package indicator-power has broken Depends on gnome-control-center
  Considering gnome-control-center 17 as a solution to indicator-power 9
  Holding Back indicator-power rather than change gnome-control-center
Investigating network-manager-pptp
Package network-manager-pptp has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-pptp 7
  Holding Back network-manager-pptp rather than change libnm-glib-vpn1
Investigating network-manager
Package network-manager has broken Breaks on network-manager-gnome
  Considering network-manager-gnome 4 as a solution to network-manager 5
  Upgrading network-manager-gnome due to Breaks field in network-manager
Package network-manager has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to network-manager 5
  Holding Back network-manager rather than change network-manager-pptp
Investigating kdepimlibs5
Package kdepimlibs5 has broken Depends on kdelibs5
  Considering kdelibs5 75 as a solution to kdepimlibs5 5
  Removing kdepimlibs5 rather than change kdelibs5
Investigating libmetacity-private0
Package libmetacity-private0 has broken Depends on metacity-common
  Considering metacity-common 12 as a solution to libmetacity-private0 5
  Re-Instated libmetacity-private0
Investigating network-manager-gnome
Package network-manager-gnome has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-gnome 4
  Holding Back network-manager-gnome rather than change libnm-glib-vpn1
Investigating gnome-bluetooth
Package gnome-bluetooth has broken Depends on gir1.2-gnomebluetooth-1.0
  Considering gir1.2-gnomebluetooth-1.0 1 as a solution to gnome-bluetooth 3
  Holding Back gnome-bluetooth rather than change gir1.2-gnomebluetooth-1.0
Investigating python-pyatspi
Package python-pyatspi has broken Depends on at-spi
  Considering at-spi 4 as a solution to python-pyatspi 2
  Re-Instated gir1.2-atspi-2.0
  Re-Instated python-pyatspi2
  Re-Instated python-pyatspi
Investigating libksane0
Package libksane0 has broken Depends on kdelibs5
  Considering kdelibs5 75 as a solution to libksane0 1
  Re-Instated libksane-data
  Re-Instated libksane0
Investigating libkemoticons4
Package libkemoticons4 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libkemoticons4 1
  Holding Back libkemoticons4 rather than change libkio5
Investigating checkbox-gtk
Package checkbox-gtk has broken Depends on checkbox
  Considering checkbox 2 as a solution to checkbox-gtk 1
  Re-Instated checkbox-gtk
Investigating libkworkspace4
Package libkworkspace4 has broken Depends on kdelibs5
  Considering kdelibs5 75 as a solution to libkworkspace4 1
  Removing libkworkspace4 rather than change kdelibs5
Investigating libknewstuff2-4
Package libknewstuff2-4 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libknewstuff2-4 1
  Holding Back libknewstuff2-4 rather than change libkio5
Investigating libkfile4
Package libkfile4 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libkfile4 1
  Holding Back libkfile4 rather than change libkio5
Investigating libknewstuff3-4
Package libknewstuff3-4 has broken Depends on libkio5
  Considering libkio5 1 as a solution to libknewstuff3-4 1
  Holding Back libknewstuff3-4 rather than change libkio5
Investigating indicator-datetime
Package indicator-datetime has broken Depends on gnome-control-center
  Considering gnome-control-center 17 as a solution to indicator-datetime 1
  Holding Back indicator-datetime rather than change gnome-control-center
Investigating libsolidcontrol4
Package libsolidcontrol4 has broken Depends on kdelibs5
  Considering kdelibs5 75 as a solution to libsolidcontrol4 1
  Removing libsolidcontrol4 rather than change kdelibs5
Investigating libmarble4
Package libmarble4 has broken Depends on kdelibs5
  Considering kdelibs5 75 as a solution to libmarble4 0
  Removing libmarble4 rather than change kdelibs5
Investigating foomatic-db-compressed-ppds
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db
  Considering foomatic-db 10 as a solution to foomatic-db-compressed-ppds 0
  Holding Back foomatic-db-compressed-ppds rather than change foomatic-db
Investigating libasound2
Package libasound2 has broken Breaks on libasound2-plugins
  Considering libasound2-plugins 11 as a solution to libasound2 114
  Upgrading libasound2-plugins due to Breaks field in libasound2
Investigating ppp
Package ppp has broken Breaks on network-manager
  Considering network-manager 5 as a solution to ppp 26
  Upgrading network-manager due to Breaks field in ppp
Package ppp has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to ppp 26
  Upgrading network-manager-pptp due to Breaks field in ppp
Investigating gnome-panel
Package gnome-panel has broken Depends on gnome-control-center
  Considering gnome-control-center 17 as a solution to gnome-panel 21
  Added gnome-control-center to the remove list
  Fixing gnome-panel via keep of gnome-control-center
 Try to Re-Instate gnome-control-center
Investigating gnome-control-center
Package gnome-control-center has broken Depends on capplets-data
  Considering capplets-data 0 as a solution to gnome-control-center 21
  Added capplets-data to the remove list
Package gnome-control-center has broken Depends on capplets-data
  Considering capplets-data 0 as a solution to gnome-control-center 21
  Added capplets-data to the remove list
  Fixing gnome-control-center via keep of capplets-data
  Fixing gnome-control-center via keep of capplets-data
Investigating gnome-control-center-data
Package gnome-control-center-data has broken Conflicts on capplets-data
  Considering capplets-data 21 as a solution to gnome-control-center-data 15
  Holding Back gnome-control-center-data rather than change capplets-data
Investigating nautilus
Package nautilus has broken Breaks on gnome-bluetooth
  Considering gnome-bluetooth 3 as a solution to nautilus 11
  Upgrading gnome-bluetooth due to Breaks field in nautilus
Investigating libasound2-plugins
Package libasound2-plugins has broken Depends on libjack-jackd2-0
  Considering libjack-jackd2-0 0 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-jackd2-0
Package libasound2-plugins has broken Depends on libjack-0.116
  Considering libjack0 9 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-0.116
  Or group keep for libasound2-plugins
Investigating network-manager-pptp
Package network-manager-pptp has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-pptp 7
  Holding Back network-manager-pptp rather than change libnm-glib-vpn1
Investigating network-manager
Package network-manager has broken Breaks on network-manager-gnome
  Considering network-manager-gnome 4 as a solution to network-manager 5
  Upgrading network-manager-gnome due to Breaks field in network-manager
Package network-manager has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to network-manager 5
  Holding Back network-manager rather than change network-manager-pptp
Investigating network-manager-gnome
Package network-manager-gnome has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-gnome 4
  Holding Back network-manager-gnome rather than change libnm-glib-vpn1
Investigating gnome-bluetooth
Package gnome-bluetooth has broken Depends on gir1.2-gnomebluetooth-1.0
  Considering gir1.2-gnomebluetooth-1.0 1 as a solution to gnome-bluetooth 3
  Holding Back gnome-bluetooth rather than change gir1.2-gnomebluetooth-1.0
Investigating gnome-font-viewer
Package gnome-font-viewer has broken Breaks on capplets-data
  Considering capplets-data 21 as a solution to gnome-font-viewer 0
  Holding Back gnome-font-viewer rather than change capplets-data
Investigating libglib2.0-0
Package libglib2.0-0 has broken Breaks on gnome-control-center
  Considering gnome-control-center 21 as a solution to libglib2.0-0 2925
  Upgrading gnome-control-center due to Breaks field in libglib2.0-0
Investigating libasound2
Package libasound2 has broken Breaks on libasound2-plugins
  Considering libasound2-plugins 11 as a solution to libasound2 114
  Upgrading libasound2-plugins due to Breaks field in libasound2
Investigating ppp
Package ppp has broken Breaks on network-manager
  Considering network-manager 5 as a solution to ppp 26
  Upgrading network-manager due to Breaks field in ppp
Package ppp has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to ppp 26
  Upgrading network-manager-pptp due to Breaks field in ppp
Investigating gnome-control-center
Package gnome-control-center has broken Depends on libnm-gtk0
  Considering libnm-gtk0 10 as a solution to gnome-control-center 21
  Holding Back gnome-control-center rather than change libnm-gtk0
Investigating nautilus
Package nautilus has broken Breaks on gnome-bluetooth
  Considering gnome-bluetooth 3 as a solution to nautilus 11
  Upgrading gnome-bluetooth due to Breaks field in nautilus
Investigating libasound2-plugins
Package libasound2-plugins has broken Depends on libjack-jackd2-0
  Considering libjack-jackd2-0 0 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-jackd2-0
Package libasound2-plugins has broken Depends on libjack-0.116
  Considering libjack0 9 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-0.116
  Or group keep for libasound2-plugins
Investigating network-manager-pptp
Package network-manager-pptp has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-pptp 7
  Holding Back network-manager-pptp rather than change libnm-glib-vpn1
Investigating network-manager
Package network-manager has broken Breaks on network-manager-gnome
  Considering network-manager-gnome 4 as a solution to network-manager 5
  Upgrading network-manager-gnome due to Breaks field in network-manager
Package network-manager has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to network-manager 5
  Holding Back network-manager rather than change network-manager-pptp
Investigating network-manager-gnome
Package network-manager-gnome has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-gnome 4
  Holding Back network-manager-gnome rather than change libnm-glib-vpn1
Investigating gnome-bluetooth
Package gnome-bluetooth has broken Depends on gir1.2-gnomebluetooth-1.0
  Considering gir1.2-gnomebluetooth-1.0 1 as a solution to gnome-bluetooth 3
  Holding Back gnome-bluetooth rather than change gir1.2-gnomebluetooth-1.0
Investigating libglib2.0-0
Package libglib2.0-0 has broken Breaks on gnome-control-center
  Considering gnome-control-center 21 as a solution to libglib2.0-0 2925
  Upgrading gnome-control-center due to Breaks field in libglib2.0-0
Investigating libasound2
Package libasound2 has broken Breaks on libasound2-plugins
  Considering libasound2-plugins 11 as a solution to libasound2 114
  Upgrading libasound2-plugins due to Breaks field in libasound2
Investigating ppp
Package ppp has broken Breaks on network-manager
  Considering network-manager 5 as a solution to ppp 26
  Upgrading network-manager due to Breaks field in ppp
Package ppp has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to ppp 26
  Upgrading network-manager-pptp due to Breaks field in ppp
Investigating gnome-control-center
Package gnome-control-center has broken Depends on libnm-gtk0
  Considering libnm-gtk0 10 as a solution to gnome-control-center 21
  Holding Back gnome-control-center rather than change libnm-gtk0
Investigating nautilus
Package nautilus has broken Breaks on gnome-bluetooth
  Considering gnome-bluetooth 3 as a solution to nautilus 11
  Upgrading gnome-bluetooth due to Breaks field in nautilus
Investigating libasound2-plugins
Package libasound2-plugins has broken Depends on libjack-jackd2-0
  Considering libjack-jackd2-0 0 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-jackd2-0
Package libasound2-plugins has broken Depends on libjack-0.116
  Considering libjack0 9 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-0.116
  Or group keep for libasound2-plugins
Investigating network-manager-pptp
Package network-manager-pptp has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-pptp 7
  Holding Back network-manager-pptp rather than change libnm-glib-vpn1
Investigating network-manager
Package network-manager has broken Breaks on network-manager-gnome
  Considering network-manager-gnome 4 as a solution to network-manager 5
  Upgrading network-manager-gnome due to Breaks field in network-manager
Package network-manager has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to network-manager 5
  Holding Back network-manager rather than change network-manager-pptp
Investigating network-manager-gnome
Package network-manager-gnome has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-gnome 4
  Holding Back network-manager-gnome rather than change libnm-glib-vpn1
Investigating gnome-bluetooth
Package gnome-bluetooth has broken Depends on gir1.2-gnomebluetooth-1.0
  Considering gir1.2-gnomebluetooth-1.0 1 as a solution to gnome-bluetooth 3
  Holding Back gnome-bluetooth rather than change gir1.2-gnomebluetooth-1.0
Investigating libglib2.0-0
Package libglib2.0-0 has broken Breaks on gnome-control-center
  Considering gnome-control-center 21 as a solution to libglib2.0-0 2925
  Upgrading gnome-control-center due to Breaks field in libglib2.0-0
Investigating libasound2
Package libasound2 has broken Breaks on libasound2-plugins
  Considering libasound2-plugins 11 as a solution to libasound2 114
  Upgrading libasound2-plugins due to Breaks field in libasound2
Investigating ppp
Package ppp has broken Breaks on network-manager
  Considering network-manager 5 as a solution to ppp 26
  Upgrading network-manager due to Breaks field in ppp
Package ppp has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to ppp 26
  Upgrading network-manager-pptp due to Breaks field in ppp
Investigating gnome-control-center
Package gnome-control-center has broken Depends on libnm-gtk0
  Considering libnm-gtk0 10 as a solution to gnome-control-center 21
  Holding Back gnome-control-center rather than change libnm-gtk0
Investigating nautilus
Package nautilus has broken Breaks on gnome-bluetooth
  Considering gnome-bluetooth 3 as a solution to nautilus 11
  Upgrading gnome-bluetooth due to Breaks field in nautilus
Investigating libasound2-plugins
Package libasound2-plugins has broken Depends on libjack-jackd2-0
  Considering libjack-jackd2-0 0 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-jackd2-0
Package libasound2-plugins has broken Depends on libjack-0.116
  Considering libjack0 9 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-0.116
  Or group keep for libasound2-plugins
Investigating network-manager-pptp
Package network-manager-pptp has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-pptp 7
  Holding Back network-manager-pptp rather than change libnm-glib-vpn1
Investigating network-manager
Package network-manager has broken Breaks on network-manager-gnome
  Considering network-manager-gnome 4 as a solution to network-manager 5
  Upgrading network-manager-gnome due to Breaks field in network-manager
Package network-manager has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to network-manager 5
  Holding Back network-manager rather than change network-manager-pptp
Investigating network-manager-gnome
Package network-manager-gnome has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-gnome 4
  Holding Back network-manager-gnome rather than change libnm-glib-vpn1
Investigating gnome-bluetooth
Package gnome-bluetooth has broken Depends on gir1.2-gnomebluetooth-1.0
  Considering gir1.2-gnomebluetooth-1.0 1 as a solution to gnome-bluetooth 3
  Holding Back gnome-bluetooth rather than change gir1.2-gnomebluetooth-1.0
Investigating libglib2.0-0
Package libglib2.0-0 has broken Breaks on gnome-control-center
  Considering gnome-control-center 21 as a solution to libglib2.0-0 2925
  Upgrading gnome-control-center due to Breaks field in libglib2.0-0
Investigating libasound2
Package libasound2 has broken Breaks on libasound2-plugins
  Considering libasound2-plugins 11 as a solution to libasound2 114
  Upgrading libasound2-plugins due to Breaks field in libasound2
Investigating ppp
Package ppp has broken Breaks on network-manager
  Considering network-manager 5 as a solution to ppp 26
  Upgrading network-manager due to Breaks field in ppp
Package ppp has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to ppp 26
  Upgrading network-manager-pptp due to Breaks field in ppp
Investigating gnome-control-center
Package gnome-control-center has broken Depends on libnm-gtk0
  Considering libnm-gtk0 10 as a solution to gnome-control-center 21
  Holding Back gnome-control-center rather than change libnm-gtk0
Investigating nautilus
Package nautilus has broken Breaks on gnome-bluetooth
  Considering gnome-bluetooth 3 as a solution to nautilus 11
  Upgrading gnome-bluetooth due to Breaks field in nautilus
Investigating libasound2-plugins
Package libasound2-plugins has broken Depends on libjack-jackd2-0
  Considering libjack-jackd2-0 0 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-jackd2-0
Package libasound2-plugins has broken Depends on libjack-0.116
  Considering libjack0 9 as a solution to libasound2-plugins 11
  Holding Back libasound2-plugins rather than change libjack-0.116
  Or group keep for libasound2-plugins
Investigating network-manager-pptp
Package network-manager-pptp has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-pptp 7
  Holding Back network-manager-pptp rather than change libnm-glib-vpn1
Investigating network-manager
Package network-manager has broken Breaks on network-manager-gnome
  Considering network-manager-gnome 4 as a solution to network-manager 5
  Upgrading network-manager-gnome due to Breaks field in network-manager
Package network-manager has broken Breaks on network-manager-pptp
  Considering network-manager-pptp 7 as a solution to network-manager 5
  Holding Back network-manager rather than change network-manager-pptp
Investigating network-manager-gnome
Package network-manager-gnome has broken Depends on libnm-glib-vpn1
  Considering libnm-glib-vpn1 6 as a solution to network-manager-gnome 4
  Holding Back network-manager-gnome rather than change libnm-glib-vpn1
Investigating gnome-bluetooth
Package gnome-bluetooth has broken Depends on gir1.2-gnomebluetooth-1.0
  Considering gir1.2-gnomebluetooth-1.0 1 as a solution to gnome-bluetooth 3
  Holding Back gnome-bluetooth rather than change gir1.2-gnomebluetooth-1.0
Done

Broken packages 

Your system contains broken packages that couldn't be fixed with this 
software. Please fix them first using synaptic or apt-get before 
proceeding. 


Preparing the upgrade failed 

Preparing the system for the upgrade failed. Please report this as a 
bug against the 'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report.
```

---

### Post by critin on 2012-10-20
Run the code given in the error message in the screenshot you posted.  The software index is broken and nothing can be done until that is fixed.  Copy/paste the code into the terminal and run it.  It may take a while so be patient.  

Are you updating the 10.04?   I wouldn't try to upgrade to 12.04 until you get a disk  or usb.  Fresh installs are better for most older machines, at least for me.  Consider a lighter version of 12.04 instead of ubuntu 12.04, I think it will be easier to maintain.  Of course that would mean a new install, but it should be easier this time.  lol

Do you still have your copy of 10.04?  If so, why not just reinstall it and get rid of all these broken packages with a fresh install?   Because they will still be there and have to be dealt with after fixing the software index as noted in your posting above.

> 
Your system contains broken packages that couldn't be fixed with this 
software. Please fix them first using synaptic or apt-get before 
proceeding. 

Oh, and I'm very happy that you've fixed it!!  At least that part.    Good job!

---

### Post by aprilm on 2012-10-20
The 10.04 was put on there at the shop that refurbished the computer, so no I dont have it. Thanks for your input! I will try the code in the error message. I think I did that and it didnt work for some reason. I will get back to you.

---

### Post by aprilm on 2012-10-20
Here is what I get. And is it just me or did I somehow downgrade on my ubuntu??? It says ubuntu 10 here. I thought I had 10.04.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.10) but 2.15-0ubuntu10 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by aprilm on 2012-10-20
I know what I did. I deleted all my downloads.I didn't realize I would be deleting my 10.04.  CRAP. CRAP CRAP!!!!

omg smh smh i cannot believe i did that.

---

### Post by aprilm on 2012-10-20
I thought my downloads were just all my pictures and stuff so I just deleted everything to try and get it all out of the way. Man. This is unreal. everything still looks the same though and it is running fine...

---

### Post by Bashing-om on 2012-10-20
aprilm, looking good, you doing good work !

lost updates can be got back, if system is now intact. ..but 10.04 is near End Of Life support ...It does behoove you to move up to 12.04 ....
as critin suggest, might consider a lighter distro ...as 12.04 ubuntu can be laggy on older hardware. (lubuntu 12.04 screams on an older AMD system here) ==> clean install from cd highly recommended.

It is not recommended to upgrade via update manager from 10.04 to 12.04 ...too many changes to the systems in between ...too much can go wrong. From what I have observed on the forums, a successful upgrade from 10.04 to 12.04 is rare. That is not to say you can not try it...the clean up of resulting problems can be a real trial (good experience !).

oh! by the way ...here is the 12.04 precise guide:
[http://ubuntuguide.org/wiki/Ubuntu_Precise](http://ubuntuguide.org/wiki/Ubuntu_Precise)
[INDENT]standing by ==> BDQ

[/INDENT]

---

### Post by critin on 2012-10-22
> **aprilm said:**
> I thought my downloads were just all my pictures and stuff so I just deleted everything to try and get it all out of the way. Man. This is unreal. everything still looks the same though and it is running fine...

Are you talking about the Download Folder?    Nothing is there except apps you've downloaded to install.    Your updates are not stored there.

Check your trash, they might still be there to restore.  I don't believe trash empties itself.


Did you ever open Synaptic Package Manager and check for broken packages, choosing "Fix Broken" under the Edit tab?

You say it's working fine now, and the report above seems to have substituted a lot that it couldn't fix.  But you can still fix those that weren't fixed in Synaptic according to this report.

> Broken packages   Your system contains broken packages that couldn't be fixed with this  software. Please fix them first using synaptic or apt-get before  proceeding. 

---

### Post by critin on 2012-10-22
> **Bashing-om said:**
> aprilm, looking good, you doing good work !

lost updates can be got back, if system is now intact. ..but 10.04 is near End Of Life support ...It does behoove you to move up to 12.04 ....
as critin suggest, might consider a lighter distro ...as 12.04 ubuntu can be laggy on older hardware. (lubuntu 12.04 screams on an older AMD system here) ==> clean install from cd highly recommended.

It is not recommended to upgrade via update manager from 10.04 to 12.04 ...too many changes to the systems in between ...too much can go wrong. From what I have observed on the forums, a successful upgrade from 10.04 to 12.04 is rare. That is not to say you can not try it...the clean up of resulting problems can be a real trial (good experience !).

oh! by the way ...here is the 12.04 precise guide:
[http://ubuntuguide.org/wiki/Ubuntu_Precise](http://ubuntuguide.org/wiki/Ubuntu_Precise)[INDENT]standing by ==> BDQ

[/INDENT]

Bashing-om, a question.

Could she go into synaptic and install another desktop?  Either the same or a different version?  xubuntu?  ubuntu?  Would that work in her situation?  Or would these broken packages still affect the system?

---

### Post by Bashing-om on 2012-10-23
broken packages must be repaired first ! Until the lower level dpkg (manager) is happy, no one is happy !

 I am absorbed presently on another issue //me with my tunnel vision, have not paid the attention here that is proper.. I will soon require a break from it and be back here soonest.

'nother thing - winter is coming on - getting the rest of my fire wood up and split is getting to be a high priority (weather permitting) and getting our habitat winterized !


Errors: your suggestion to use Synaptic is a good place to start, then progress lower to apt-get's fix'in, anything left over.... dpkg should handle .
[INDENT][INDENT]I'll Be Back ==> BDQ

[/INDENT][/INDENT]

---

### Post by Bashing-om on 2012-10-23
aprilm, I am back.

ok... So what do you want to do ???
1. Update and use the present 10.04 ?[INDENT]No big deal, some time and effort ..will fix if want to
let me see updated errors from 
```
sudo apt-get update
```[INDENT]OR
[/INDENT][/INDENT][LEFT]2. Upgrade to 12.04 /12.10[INDENT]as 10.04 is approaching EOL ..my suggestion still
-with all the hassles of obtaining an install medium-
my current suggestion is purchase the install cd//
However if ya want to do the download burn we try that too (will verify first that the brasereo utility on 10.04 burns to disk with your cd device)

[/INDENT]Panic not. Just proceed in a calm and orderly fashion.  <==BDQ

[/LEFT]

---

### Post by critin on 2012-10-24
> **Bashing-om said:**
> broken packages must be repaired first ! Until the lower level dpkg (manager) is happy, no one is happy !

 I am absorbed presently on another issue //me with my tunnel vision, have not paid the attention here that is proper.. I will soon require a break from it and be back here soonest.

'nother thing - winter is coming on - getting the rest of my fire wood up and split is getting to be a high priority (weather permitting) and getting our habitat winterized !


Errors: your suggestion to use Synaptic is a good place to start, then progress lower to apt-get's fix'in, anything left over.... dpkg should handle .[INDENT][INDENT]I'll Be Back ==> BDQ

[/INDENT][/INDENT]

Thanks, that's what I thought because it makes sense, but sometimes the illogical works too.  lol  Thought she might save a little stress.

You're so lucky to be able to burn firewood!  I miss it...

---

### Post by Bashing-om on 2012-10-24
off topic; conversation:
I have used fire wood the majority of my adult life...a few years back our stove burned out and we went to propane for heating..uh uhh..I missed that warm your bones feeling from wood heat ! Anyway, this year we finally got a new stove/ all the new technologies incorporated ...I did the initial 1st burn yesterday...let me tell you ---I was impressed with it's functioning !

still off topic: I have never expressed how much I enjoy working with you ! *In other threads I peruse* I pay attention to how you proceed and the thought process employed.

OK on topic: @ aprilm....-> It is your system...to do with as you prefer...We are here to assist and guide you.
[INDENT]we await your pleasure ==> BDQ
 
[/INDENT]

---

### Post by critin on 2012-10-24
Quick OT:  Thank you, I appreciate your encouraging words as I'm "just another newbie" who tries hard.  lol
With Calif's restrictive laws & 'burn days', we can't enjoy the heat and aroma of wood any longer.  bah  I'm an Arkie by birth and disposition, a prune picker by circumstances.

---

### Post by Bashing-om on 2012-10-24
while we are waiting---> har har...
I spent may years in Ca. ...long story short-in process there of buying a house, 30+ years to pay for it --I had a house here promised to me ...I going to work for 30 years for a house ...hummmmm...I came back to Ark. !

  I broadly expanded my computer horizons in California (silicon valley); I came back here --20 years behind -- sure did miss that atmosphere ... I managed to progress in other areas. And here I am talking to you today!

---


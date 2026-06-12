---
title: "An Idea to solve a problem"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Teamgai on 2008-09-25
Earlier this week, I made the mistake of trying to uninstall Ubuntu (gOS Linux) with Vista's disk management, making it impossible to boot into Vista, leading me to completely reformat, coming to the same GRUB problem (error 22).  

Deciding to just stick with Linux, I installed it again, making everything (cept Vista) work again, though I installed over Vista (what was left from the "recovery").  Everything is all nice and pretty, but I'm having such trouble with installing Java and/or other programs (haven't even gotten to anything else yet), I really would like to be ABLE to go back to Vista.

I was thinking, could I just use the Vista recovery disk to reformat, then install Linux (not using the WHOLE hard drive) then be able to dual boot?

I'm worried because my mom is skeptical about having anything other than Windows, and there's the fact that I don't have any of my pictures (I saved my music on another computer a long time ago), and Linux is hard to get used to.

First I was thinking of just sticking with Vista, putting all the pretty stuff I found in gOS on Vista (or whatever I can find), and somehow go on with life.

Then I thought about sticking with Linux because it's already on here and won't require another reformat to be installed.

But.. overall, I'd be nice to have the speedy Linux with the compatible (and easier to install/uninstall programs) Vista together on one computer...

Can someone help me? I hate that manufacturers only give the recovery disk and not a full install disk (which I've heard from many sources has a boot recovery option to get rid of GRUB altogether).

Many thanks in advance!

---

### Post by adult swim on 2008-09-25
teamgai, if you havent overwritten your vista install, and you just cant boot it, dont worry, all can be recovered.  first things first, go to a terminal (applications>accessories>terminal) and type in ```
sudo fdisk -l
``` it will ask you for your password, type that in and hit enter.  now post back what it returns to you here.

---

### Post by Teamgai on 2008-09-25
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb21d0910

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris


I'm pretty sure I overwrote what little vista there was.... >.> Thanks for replying :P I thought I was alone.

---

### Post by adult swim on 2008-09-25
im sorry to tell you but your windows is gone.  if you are trying to get java to work in ubuntu, open a terminal (applications>accessories>terminal) and type in ```
sudo apt-get install openjdk-6-jre
```
i understand that you are in new places with your computer, the first time i installed ubuntu and didnt have windows ariound i panicked and reinstalled windows within a day.  what programs are you looking for?  if you want to reinstall vista and have that as your only os we can tell you how to do that to.  there is no need to feel ashamed for using windows, i see that alot here.  whatever you need your computer to do, it can do. just ask!

---

### Post by Teamgai on 2008-09-25
O.O... How'd... you make that so easy!?!?!?

EDIT: How do I enable it in Firefox 3?

Thank you soooooooo much! Next I wanted to get games on here (I had 6 MMORPGS on Vista, so I'm a little deprived here with solitaire and the like).  None of the one's I played were very mainstream (not as much hype as WoW, but they had great graphics, so... *shrug*)

I've read a lot about Wine and how much you can do with it, but I have no clue how to use it. I wanted to download Cedega or CXgames, but that would require another install I couldn't understand :P

---

### Post by eeeandrew on 2008-09-25
> sudo apt-get install wine

It will ask you for your password, enter it and it will install wine for you. Next thing to do is go to [http://appdb.winehq.org/](http://appdb.winehq.org/) and search for the game you want to run. You should then browse through the most recent and relevant test results for your install. If the test result is "garbage" then the game won't run. 

You also need to configure wine, on my laptop I need to have it emulate a virtual desktop in order to get games to run.

Can I also suggest you read the help files on installing programs under the "help and support" link under the system menu on your desktop. This will take you through the apt-get and apt-cache commands as well as unpacking tarballs and .deb for a manual install. If you have any problems post back here and someone will help.

Hope this is useful,
Andrew

---

### Post by adult swim on 2008-09-25
as far as solitaire goes, if you go to applications>games>aisle riot, there is solitaire.  im sure most of the games you are used to in windows play a bit different in ubuntu.  WINE is "not a windows emulator" but it basically emulates windows inside of linux, so you can run "some" programs that you use in windows.  you dont need to reinstall to use WINE.  some programs work, and some do not.  to check and see if you can run the program you are after with WINE, search this page [http://appdb.winehq.org/](http://appdb.winehq.org/) 
if you absolutely need to run some windows programs, or are missing windows solitaire, you can run windows on a virtual machine, which is basically booting windows from inside ubuntu.  you can do this (if you have a cd to install windows with) by installing virtualbox (the easiest way is to go to a terminal and type in "sudo apt-get install virtualbox-ose virtualbox-ose-source virtualbox-ose-modules-generic")  once you do this, follow this guide [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) (you'll need to scroll down to the first run section)
and again, if you want to dual boot windows and linux, that is still do-able.  just let us know if thats what you want!

---

### Post by WWSmith36 on 2008-09-25
Also there are quite a few game that will run natively in linux (quake, doom, unreal tournament).  Pretty much any openGL will run that way.

I would also recommend reinstalling vista to dual boot.  That way any games that are not supported in Wine can be played there.

---

### Post by Teamgai on 2008-09-25
lol Okay I give up, I do want to dual boot.. But I'm sure it's going to be difficult seeing as I only have a recovery disk and not an actual installer; though I'm sure you guys could find a way to work around it.

:)

---

### Post by WWSmith36 on 2008-09-25
If you computer came from Dell they no longer provide installation disk.  You have to go to their website and request one for reinstallation.  The good news is they are quick.  You will receive it the following day.

They main thing should be thinking about until you do get the install disks is ¨How do you want to partition your 160Gig Drive.¨

---

### Post by mkvnmtr on 2008-09-25
Do a search here on the forums on how to enable more repositories. You will find a lot more games. Then there is a pure games site where you can download some good games. Go slow and try to understand something before you do it. But remember anything you mess up can be fixed. Most of it is pretty easy you just have to ask here and somebody can help you.

---

### Post by Teamgai on 2008-09-25
I just thought about it... I should install Vista before Linux so that I can at least get one OS set up completely how I want it, then get started on Linux. This is a whole new world to explore, and I'm not going to have a lot more time with the installation disk...

How do I get GRUB to uninstall along with Linux so that I can get a clean install of Vista and Linux together?

---

### Post by eeeandrew on 2008-09-25
It is. It may be lengthly though. I was in this situation one year ago, at the beginning of this week I took vista off and installed 8.04 so things do work out. Bear in mind its a year since I did this but hopefully this helps. I would suggest going to [www.google.co.uk/linux](www.google.co.uk/linux) and search for dual boot guides to get a better idea but this is the basic procedure as I remember it 

First use the Vista disk to reinstall Vista.

Next find the vista partition editor and select the "shrink" option. That should reduce the size of the Vista partition by about 40-50%

Next reinsert the linux disk and install it on that blank space. The linux boot disks have guided options and you should be able to select something like "guided: using largest free space"

I remember I also had to edit the grub file to allow vista to boot.

A bit of googling turned up the guide I used but this may be out of date. If theres anything you don't understand then ask first and make sure your clear on the procedure. As always backup your important data before any repartitioning and if you have any problems then we're all here to help.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Who Dares Wins,
Andrew

---

### Post by Teamgai on 2008-09-25
> **eeeandrew said:**
> It is. It may be lengthly though. I was in this situation one year ago, at the beginning of this week I took vista off and installed 8.04 so things do work out. Bear in mind its a year since I did this but hopefully this helps. I would suggest going to [www.google.co.uk/linux](www.google.co.uk/linux) and search for dual boot guides to get a better idea but this is the basic procedure as I remember it 

First use the Vista disk to reinstall Vista.

Next find the vista partition editor and select the "shrink" option. That should reduce the size of the Vista partition by about 40-50%

Next reinsert the linux disk and install it on that blank space. The linux boot disks have guided options and you should be able to select something like "guided: using largest free space"

I remember I also had to edit the grub file to allow vista to boot.

A bit of googling turned up the guide I used but this may be out of date. If theres anything you don't understand then ask first and make sure your clear on the procedure. As always backup your important data before any repartitioning and if you have any problems then we're all here to help.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Who Dares Wins,
Andrew

I only have one problem with this. I only have a RECOVERY DISK from Asus (my laptop brand).  It doesn't directly install Vista, it's only use is to recover back to factory settings.  What I need to know how to do is get Linux completely deleted (along with GRUB) and then get Vista, then reinstall Linux.

Thank you so much for the guides, they're very detailed and would help very much if that was my situation.

---

### Post by egalvan on 2008-09-25
> **Teamgai said:**
> I only have one problem with this. I only have a RECOVERY DISK from Asus (my laptop brand).  It doesn't directly install Vista, it's only use is to recover back to factory settings.  What I need to know how to do is get Linux completely deleted (along with GRUB) and then get Vista, then reinstall Linux.

Thank you so much for the guides, they're very detailed and would help very much if that was my situation.

Your recovery disk should have an option to "Recover to Factory Settings"

That means that it will wipe the drive clean (ok, it's really a windows format), then reinstall Vista.

Remember, your Vista computer came from the factory with Vista, and not Ubuntu.

In extreme cases, I suggest 'Darik's Boot and Nuke'

[www.dban.org](www.dban.org)

This will wipe clean any drive.

Use Vista to shrink the Vista installation.

Also, I suggest using PartED Magic LiveCD to partition your drive.
I find it a bit easier to use than Ubuntu's LiveCD.
My opinion, yours may vary.

[http://partedmagic.com/](http://partedmagic.com/)


ErnestG

---


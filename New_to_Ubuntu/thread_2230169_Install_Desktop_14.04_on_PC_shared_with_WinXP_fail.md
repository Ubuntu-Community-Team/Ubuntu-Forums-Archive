---
title: "Install Desktop 14.04 on PC shared with WinXP fails"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by Christopher_Ward on 2014-06-17
Processor: Intel Core 2 Duo E6400 @ 2133MHz
Video: NVIDIA GeForce 7900 GT/GTO
Motherboard: MSI MS-7246
RAM: 4GB DDR2-SDRAM
4 * ATA Hard Drives 2 * USB Hard Drives
Monitors: 2 * HannsStar HX191D (1280 x 1024 pixels @ 60Hz 32-bit)
MS Windows-XP SP3 (Home Edition)
Ubuntu Desktop 14.04

Attempted to install Ubuntu Desktop 14.04 on the above PC, shared with WinXP. Failed (locked-up).
Note, successfully installed (from same CD) on a different PC where Ubuntu is the only OS and the system only has 1 hard drive.

So, from within Windows, ran wubi.exe ( have tried this twice now - second time recognised that Ubuntu was previously installed and wiped it).
This downloads Ubuntu and installs to the allocated hard drive (Drive M in this case [1TB, only Ubuntu on it]).
Rebooted the PC when prompted.
On reboot, choice of start-up offered (XP or Ubuntu). Ubuntu Selected.
Ubuntu continues install, the progress bar reaches approx 80% completion and then the system re-starts.
Choice of start-up offered (XP or Ubuntu). Ubuntu Selected.
Ubuntu screen (with the progress dots) is displayed.
Error message is displayed: Serious errors were found while checking the disk drive for /. Press I to ignore, S to Skip, M for Manual Recovery.

So, losing the will to live! :P

---

### Post by Mark Phelps on 2014-06-17
Wubi has been discontinued-- if it works, that is an exception, but regardless, it's not supported anymore.

---

### Post by Christopher_Ward on 2014-06-17
...not very encouraging then, given that 14.04 is the latest and greatest, why is wubi included if it is discontinued?
Is there a magical method of installing Ubuntu successfully alongside Windows XP, or is it just not viable?

---

### Post by squakie on 2014-06-17
+1 on NOT using wubi.  It's not just not supported in the forums, it's no longer supported by Canonical.

So......

When you tried to install for dual boot, did it actually lock up, or did you have a blank screen and nothing responded? 

What I would do (and this is just me - others may have better ideas):

- download and burn the 14.04 ISO (presumably the 32-bit version given you are running XP) 
- boot this newly created install media and select "Try Ubuntu"

Does this boot to the GUI, or does it appear as a black screen as well?  Do you get any error messages?

- install 14.04 for dual-boot, NOT wubi
- try booting again

If you get any error messages please post them back here.

If you get a black screen, try ctrl/alt/F1 and see if you get a text-based login window.  If so, log in using your normal userid and password.  The password is not echoed to the screen so it looks like it isn't doing anything but it is - just press enter when you have finished typing your password.  At this text-based window, type:

startx <press enter>

Do you get any error messages?  If not, try ctrl/alt/F7 and see if a GUI'd screen now shows.  You can switch back and forth between the text and GUI'd screen (or at least the attempt to get a GUI'd screen) via ctrl/alt/F1 and ctrl/alt/F7.

Please post back any and all results.  If you run into any problems - stop and post back here with the problem and the error messages.

---

### Post by Christopher_Ward on 2014-06-17
Hello Squakie. I wiped the drive and tried the DVD. It is just locking-up on the first Ubuntu screen, where the 5 dots change from white to red in sequence. Left it like that for 20mins, nothing happens. I'm sure, by hook or by crook, there will be a way that I can get it to work, but frankly I'm not interested if this represents the quality on offer - the install really should be rock-solid. I going to try other Linux flavours instead. Mint and Mageias next on the list :)

---

### Post by Christopher_Ward on 2014-06-17
oh - just discovered that Mint 17 is based on Ubuntu. :( They do seem to have a handle on installation faults though, in particular PCs with nVIDIA GForce cards can be an issue (sounds like it fits my experience), and there is a fix: [http://www.linuxmint.com/rel_qiana_mate.php](http://www.linuxmint.com/rel_qiana_mate.php)

---

### Post by squakie on 2014-06-17
nomodeset, etc., are well known and suggested here as well.  Wanted to try going a step at a time with Ubuntu.  You can specify nomodeset, etc., in the boot from the live media before you "Try Ubuntu" or "Install Ubuntu".  That is one of the things I would have you try next.  If you have problems figuring out how to do that just post back.  It's been a while since I did that on a live media boot, but I know it's very simple.  I would always recommend trying to work these things out prior to jumping to another distribution, but that's just me - I like the challenge ;)  Have you tried lubuntu or xubuntu?

---

### Post by squakie on 2014-06-18
Sorry - please ignore this empty post.  I posted something meant for a different thread.

Sorry!

---

### Post by mörgæs on 2014-06-18
There's a hardware list in original post. 

Christopher, you computer is good for all of the Buntus. A 64 bit install is your best option.

Installing from USB is better than from CD / DVD.

---

### Post by oldfred on 2014-06-18
I have a slightly newer nVidia card 9600GT and have to use nomodeset on every boot of live installer or boot after install until I install the nVidia proprietary driver from system settings. Do not install a nVidia drive from nVidia. Not required and complicates it greatly.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

With 14.04 it booted by default in low resolution and made it difficult to get to system settings, but it is possible.

---

### Post by Christopher_Ward on 2014-06-18
Hello mörgæs, thanks for your advice, I hadn't thought of 64bit. It has not made a difference though, as the install is just locking-up as I described before.
This is what I did (might help others).
1) Downloaded Ubuntu 14.04LTS to a hard drive on my WindowsXP PC.
2) Downloaded Universal-USB-Installer from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
3) Used Universal-USB-Installer to make Ubuntu bootable from a USB stick.
4) Shut-down the PC (reset is not enough).
5) Started the PC and via the BIOS menu, selected the USB stick as the drive to boot from.


The above worked, so far as getting the Ubuntu screen to display (The 'five dots progress screen') but it just locks-up on that screen.

Hello oldfred, very useful info thank you. I found some Linux Mint notes that cited nVidia G-Force cards as an issue. Considering there are millions of them still in service, I do find it surprising that the installer can't handle it without manual intervention.

Re your link, which shows this is a fairly old fault (2010), I didn't realise the keyboard logo on the Ubuntu screen meant I could press a key to open a menu! If you ask me, most newbies would not realise.

So, I don't know why but I'm going to give it one more try. I'm just pretending to myself that I have the time :D

---

### Post by mörgæs on 2014-06-18
Did you try nomodeset?

---

### Post by squakie on 2014-06-19
OOPPPSSS - the post I made about the hardware was meant for a different thread - sorry!  I'm editing it so it can be ignored.

---

### Post by squakie on 2014-06-19
And hence why I mentioned nomodeset way back in this thread......   Never got a response from the OP on that.

---

### Post by Christopher_Ward on 2014-06-19
Hello all, thank you for your info. No, I have not used nomodeset because (a) The Ubuntu screen locked-up (as reported earlier in the post) and (b) I didn't know that I could get a menu up from that locked up screen (as reported earlier in the post).

I am also too pushed for time, I have a lot of work on at the moment so although I'd normally relish the challenge, I have to leave it for now.

Armed with the info that the very strange image of a keyboard and a figure with out-stretched arms actually means 'hit any key for a menu' (or something) (that image to me suggests 'hands free' or 'don't touch the keyboard' :D). I tried a USB Stick boot again, got to the locked-up screen, tried various keyboard keys - nothing. Tried the F6 key (was mentioned somewhere) - got a black screen with a repeating message thus: [COLOR=#0000cd]STD IN: NOT A TYPEWRITER[/COLOR]

Given that something about the USB stick set-up could possibly add it's own issue, I tried a DVD again (14.04LTS 32bit). The screen didn't lock this time and I was able to select 'try Ubuntu', which worked (fast) (last time I saw that screen I chose 'install', which failed as per original post). :D

Side note - a handy window listing key combinations is displayed. However, a lot of those refer to the 'super' key. I have no idea what key that is!

So, poked around a little bit, copied an existing folder and files from one drive to another (very fast).

Ubuntu created an icon for every logical partition and used the existing naming convention I use in MS Windows (partition letter plus manufacturer device id e.g. 'C on ST3320620AS', 'M on ST2000DM001' etc). 

On the Ubuntu desktop there is an install icon - so naturally I thought, got to give it a go!

In the earliest install window though, there is info that is meaningless to 101% of MS Windows Users - I got a pop-up message: [COLOR=#0000cd]'/sdd has mounted partitions'[/COLOR] -now, I understand what that is about from my Unix experience (donkeys years ago), but that message alone would put off most MS Windows Users forever!

Got to the Window where one can choose how/where to install. I did not want to allow it to install blindly for fear of something on the MS Windows side being over-written. There is an option to choose to 'do something else', so I picked it. This presents a Window listing all partitions - but alas, unlike the Desktop icons, the partitions are identified as /dev/sdd, /dev/sdd5 and so on. At this point, most MS Windows Users would be electing to poke sharpened forks in their eyes rather than continue to install Ubuntu - the point is, without any correlation to the Windows partition labels, the User does not know which of the partitions can be safely used.

As it happens, I was lucky here because I had a drive (with some unimportant temporary files on it) that I could identify by it's size and amount of free space available. So, selected that drive (2TB) and got another pop-up msg: [COLOR=#0000cd]'NO ROOT FILE SYSTEM. PLEASE CORRECT THIS FROM THE PARTITION MENU [OK]. [/COLOR]

Oh dear, that's fine(ish) in principle, but where the hell is that menu? So, I cancelled install and tried to find the menu via the desktop icons. About 5 minutes into that hunt, Ubuntu crashed right off the screen.

So, ran the CD again. Locked-up screen again - but this time hitting a keyboard key took me to a black screen with a repeating 'report', as follows:
[COLOR=#0000ff][  64.080000] BUG : soft lockup - CPU#1 stuck for 22s! [systemd-udevd : 108]
[  64.080000] CPU : 1 PID : 108 COM systemd-udevd Tainted : G   W 3.13.0-24 -generic #46-Ubuntu
[  64.080000] Hardware name : /MS-7246, BIOS v7.40 01/24/2007
[  64.080000] task : f7448000 ti : f7606000 task.ti : f7606000
[  64.080000] stack :
[  64.080000] Call Trace:
[  64.080000] Code : f0 8b 46 04 89 5e 04 89 33 89 43 04 89 18 89 f8 e8 00 41 59.........etc
[/COLOR]
So, I have really run out of time - now where did I put those sharpened forks? ](*,)

---

### Post by yancek on 2014-06-19
> This presents a Window listing all partitions - but alas, unlike the  Desktop icons, the partitions are identified as /dev/sdd, /dev/sdd5 and  so on.

 Learning Linux naming conventions is pretty simple and there are countless tutorials expalining this.    The installer lists the Filesystem Type on the page you are referring to and anything in that column with ntfs is a windows partition.  sda equals first hard drive, sda1 first hard drive and first partition, sdb second hard drive, sdb2 second hard drive second partition.

> In the earliest install window though, there is info that is meaningless to 101% of MS Windows Users - I got a pop-up message: [COLOR=#0000cd]'/sdd has mounted partitions'[/COLOR]  -now, I understand what that is about from my Unix experience (donkeys  years ago), but that message alone would put off most MS Windows Users  forever!

The primary reason for that is that windows generally overwrites everything and assumes it will be the only OS.  Rather than poking sharpened forks in there eyes, they could read a little in advance as there are numerous tutorials explaining in detail how to install as well as the naming conventions used in Linux for drives/partitions.

You need to select one of the partitions for root.  In the installer window, click on one of the partitions in the main window (not an ntfs) and then click the Change tab below where you get a new window with several options.

---

### Post by sudodus on 2014-06-19
> **Christopher_Ward said:**
> Hello all, thank you for your info. No, I have not used nomodeset because (a) The Ubuntu screen locked-up (as reported earlier in the post) and (b) I didn't know that I could get a menu up from that locked up screen (as reported earlier in the post).


Please try the boot option **nomodeset** running a live session 'Try Ubuntu'

See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by oldfred on 2014-06-19
One of the new issues with Ubuntu is that it will be like Windows and overwrite the entire drive. And bug reports say that is a feature and how it is supposed to work so there is nothing to fix. We have before had major issues that better explanation up front would resolve but they refuse to change descriptions, but often fix real bugs. 

In the old alternative installer with 12.04, LVM was always labelled as a full drive install. Now it says easy to partition so many new users think it is a good way to install. LVM is more complicated and still is a full drive install, it does not mention it will erase everything.

And now Windows 8 is always hibernated, the Linux NTFS driver does not mount NTFS with either chkdsk or hibernation flags set. So installer does not see Windows so the auto install just does not mention it will overwrite what it does not see. So the auto install side by side or into unallocated space is not really working.

It is just about that Something Else is the only safe way to install. But as you have found out, users do not understand drives & even what a partition really is. Windows historically has confused the issue as everything is a drive. Drive d: could be a second partition like sda2 on same drive or could be another entire phyical drive like sdb and first partition on sdb is sdb1.

Default install of Ubuntu is / (root) and swap using its auto sizing. But I never liked any system that automatically does its thing and want control, so I learned (but really knew as I created partitions in Windows before) about partitions and only use Something Else. But its not the easy to try that is was and as you say many new users will be put off. See this for ways to try Ubuntu before installing:
       Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

As long as I use nomodeset with my dual core & nVidia system, I have no boot issues of live installer or first boot. And once nVidia driver is installed it works well. 

Also if drive is 2TB the auto install creates too large of a / . with just / & swap you end up with almost 2TB of / and files in ext4 are scattered across a partition. Or even just to boot it may have to jump all over drive. Much better to create a 25GB / (root) partition and use rest of drive a /home or data partitions.

      
 Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

With a second drive Something else is always recommended as that is the only way you get to choose which drive to install boot loader. Any Something else install is otherwise the same.
      
 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb or second drive (if applicable), but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)

---

### Post by Christopher_Ward on 2014-06-19
> The installer lists the Filesystem Type on the page you are referring to  and anything in that column with ntfs is a windows partition.  sda  equals first hard drive, sda1 first hard drive and first partition, sdb  second hard drive, sdb2 second hard drive second partition.
Hello Yancek. That is understood, but it is simply not practical in a situation where you are adding Ubuntu to a PC where MS Windows already exists. In the MS Windows World, there is no 1st drive/1st partition/2nd partition, 2nd drive/1st partition etc - you just have a smorgasbord of partitions and they are all (foolishly) referred to as drives. So, the list presented to the User to choose from does not present the information in a way that a safe choice can be made.

Hello sudodus. Thank you for the link. The snag is, it can't be done. I can make the changes using the 'Try Ubutu' mode, but as the link says: [COLOR=#006400]'Changes made during the session are not persistent. Any changes made will be lost when the user exits Ubuntu.'[/COLOR] If I try to install from the DVD (or USB), the link says: [COLOR=#006400]'As the CD boots, the user can gain access to the advanced page and its  options by pressing any key when the small logo appears at the bottom of  your screen'[/COLOR] - but that simply does not happen, no matter what key is pressed.

I think Ubuntu looks great for a single OS PC, but there are too many issues to trust it to share the PC with MS Windows. It seems a pity that Ubuntu is reaching out to other devices without really getting it right for Desktop PCs in a shared scenario that, in my view, would be the most attractive to MS Windows Users - like it not, they are the folks that Ubuntu needs to attract.

**Edit:** I forgot to say that I think it's a shame Wubi.exe can no longer be used as it is simple and, being on the MS Windows side of the equation, easy for MS Windows Users to understand.

---

### Post by sudodus on 2014-06-19
Maybe you are at a dead end street now. Please boot into Windows and uninstall Ubuntu (the WUBI installation). See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]
Forums Staff recommendations on WUBI[/URL]

Then try Ubuntu along another street (or maybe a flavour with a lighter desktop environment, but standard Ubuntu should work well with your hardware). Try it before installing anything into your internal drive. See this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

It is way too early to give up :-)

---

### Post by yancek on 2014-06-19
> Hello Yancek. That is understood, but it is simply not practical in a  situation where you are adding Ubuntu to a PC where MS Windows already  exists. In the MS Windows World, there is no 1st drive/1st partition/2nd  partition, 2nd drive/1st partition etc - you just have a smorgasbord of  partitions and they are all (foolishly) referred to as drives. So, the  list presented to the User to choose from does not present the  information in a way that a safe choice can be made.

I'm not sure I understand what you are trying to say.  If you are installing Ubuntu on a drive(s) with windows, then you would want to know how Ubuntu identifies drives/partitions.  Using the Something Else option, which is called Expert or Manual on other system and also on early version of Ubuntu, gives the user a lot more control and adds to the users knowledge.   I've read various artilces about the Ubuntu installer and I would have to agree with this statement that the only safe method is "Something Else".  The Alongside option seems like it should be called something like "Cross your finger and hope for the Best".  I've always used that option or the Manual option to install and have not yet overwritten a windows partition. 

Good luck with it.

---


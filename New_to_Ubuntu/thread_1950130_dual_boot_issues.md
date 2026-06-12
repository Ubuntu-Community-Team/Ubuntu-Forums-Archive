---
title: "dual boot issues"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by airtime82 on 2012-03-31
Hi, I'm as close to a total newb as you get. I installed Ubuntu 11.10 alongside my current OS(windows 7). I didn't know I should first partition my windows,and thought it would be okay to just use the installer partitioning tool where you just slide it back and forth to where you want. After the install(went very smooth) Ubuntu came up looked great, I set up my cloud and email and decided it was time to restart and make sure I could boot windows. I couldn't get a boot menu that showed windows and it would automatically boot Ubuntu. Weird thing was there was an extra black screen which lasted about 5 seconds after my splash screen. Now through messing around and some Google I figured out that this was my menu to select OS but for some reason it was blacked out. So when it came on I pushed down arrow a few times and hit enter, boom windows rec menu(made a backup quick) now I just had to figure out how many times I had to arrow down to boot windows 7. So I let Ubuntu boot, opened terminal and typed sudo update-grub. This showed windows 7 as fourth on the list so I rebooted, waited for black mystery screen, arrowed down four times, hit enter and bingo windows 7 boots. Great however now I have no more black screen it boots right to windows and since I just used the tool in the wubi installer for the partition windows still shows it as one big partition with no sign of Ubuntu anywhere. How can I have the option to boot into Ubuntu? Or is there a way to delete/uninstall so I can start over and do correctly?

---

### Post by kc1di on 2012-03-31
Hi and welcome to Ubuntu,

Here what you need to do to show the boot screen.

Open a terminal >the ubuntu log on the upper left if your using unity.  type term and click on the terminal when it comes up 
type the following at the prompt

```
sudo gedit
```
this will bring up geditor in root mode so be very careful what you change.

click on Open navigate to /etc/default/grub
when you get that file up look for the line that looks like this:

```
#GRUB_TERMINAL=console
```
delete the # sign from in front of that line
save the file exit gedit
no again in the terminal type the following
```
sudo update-grub
```
when that finishes reboot you should now be able to see the boot list when it boots up.
if you want to make windows the default go to the page which explains how to do that. 
[http://askubuntu.com/questions/82928/how-to-make-windows-boot-first]("http://askubuntu.com/questions/82928/how-to-make-windows-boot-first")

Also you may want to look at boot repair here:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")


I might add the reason this happen most often is that grub does not have the correct resolution for your video card.  you can also adjust this parameter to fix the problem.

---

### Post by critin on 2012-03-31
>  in the wubi installer for the partition windows still shows it as one  big partition with no sign of Ubuntu anywhere. How can I have the option  to boot into Ubuntu? Or is there a way to delete/uninstall so I can  start over and do correctly?You can probably fix the boot screen issue following advice given by others.   If this is a true Wubi install, you can remove it through the Windows Add/Remove programs.  There is no separate partition with Wubi since it installs* inside* Windows as a program.
> 
 I didn't know I should first partition my windows

You Don't with Wubi.

If you're wanting a true dual install, download your preferred version iso, burn to disk/flash drive, boot and follow instructions there.  Use particular care in partitioning Windows.

---

### Post by airtime82 on 2012-03-31
You said delete # and save the file. How do yo save? Just hit enter or do I need to type some kind of save command?

---

### Post by airtime82 on 2012-03-31
How do I know if it was a "true" wubi install? When I used my live disc it popped up option to install using wubi and that's what I clicked.

---

### Post by critin on 2012-03-31
> **airtime82 said:**
> How do I know if it was a "true" wubi install? When I used my live disc it popped up option to install using wubi and that's what I clicked.

You said there was only one large partition with Windows.  
Look in your Add/Remove programs (Windows) and see if Ubuntu or Wubi is listed there.

---

### Post by kc1di on 2012-03-31
> **airtime82 said:**
> You said delete # and save the file. How do yo save? Just hit enter or do I need to type some kind of save command?
in gedit go to the top menu and one of options will be save.

---

### Post by airtime82 on 2012-03-31
> **critin said:**
> You said there was only one large partition with Windows. 
Look in your Add/Remove programs (Windows) and see if Ubuntu or Wubi is listed there.
 
In windows 7 it is no longer add/remove programs, now its programs and features > uninstall or change program. There is no sign of either in there. Also It has to be somewhere because in the midst of the confusion with the black screen it was booting ubuntu without the disc so it must be on the drive somewhere right???

---

### Post by airtime82 on 2012-03-31
> **kc1di said:**
> Hi and welcome to Ubuntu,
 
Here what you need to do to show the boot screen.
 
Open a terminal >the ubuntu log on the upper left if your using unity. type term and click on the terminal when it comes up 
type the following at the prompt
 
```
sudo gedit
```
this will bring up geditor in root mode so be very careful what you change.
 
click on Open navigate to /etc/default/grub
when you get that file up look for the line that looks like this:
 
```
#GRUB_TERMINAL=console
```
delete the # sign from in front of that line
save the file exit gedit
no again in the terminal type the following
```
sudo update-grub
```
when that finishes reboot you should now be able to see the boot list when it boots up.
if you want to make windows the default go to the page which explains how to do that. 
[http://askubuntu.com/questions/82928/how-to-make-windows-boot-first](http://askubuntu.com/questions/82928/how-to-make-windows-boot-first)
 
Also you may want to look at boot repair here:
 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
 
I might add the reason this happen most often is that grub does not have the correct resolution for your video card. you can also adjust this parameter to fix the problem.
 
If this is followed to the letter is there any chance to screw my computer up? I cant down this computer as its the only one in the house and I dont feel like sleeping in the doghouse. Also what you said at the end has something to do with it because after black mystery screen would time out it would then be a darker black screen where I would get a grey box in the middle of the screen saying screen needs to be ###x####(cant remember the numbers) it would pause, auto set itself somehow and ubuntu would boot.

---

### Post by oldfred on 2012-03-31
If this is the only computer you have make some repair disks and a bootable Ubuntu liveCD or USB.

And since this is backup day:

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by kc1di on 2012-03-31
>  with it because after black mystery screen would time out it would then be a darker black screen where I would get a grey box in the middle of the screen saying screen needs to be ###x####(cant remember the numbers) it would pause, auto set itself somehow and ubuntu would boot.

If you follow the recommendations there if very little chance of messing it up.  the numbers your seeing on the blank screen is the resolution the screen is looking for.

---

### Post by airtime82 on 2012-03-31
> **oldfred said:**
> If this is the only computer you have make some repair disks and a bootable Ubuntu liveCD or USB.
 
And since this is backup day:
 
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
 
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
 
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
 
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
 
when I was trying to boot windows from the "black screen" I accidentally ended up in the windows recovery menu once, in here I decided to select "backup" it then went on to check every file on the computer and then burn all files to cd(four cds actually). So doesnt this mean I already made a recovery???

---

### Post by airtime82 on 2012-03-31
> **kc1di said:**
> If you follow the recommendations there if very little chance of messing it up. the numbers your seeing on the blank screen is the resolution the screen is looking for.
 
I understand that but what is the problem it has with resolution and what does it do to the menu. If my first theory was right about the menu I couldnt see was this a "grub menu"?

---

### Post by oldfred on 2012-03-31
There is a vendor recovery which I thought was more like 4 DVDs. That is just an image of the hard drive as purchased. That does not include any of your data nor all the updates and housecleaning you have done since you bought system. 

Worthwhile to have vendor recovery DVDs, system repairCD and a third party full backup of your system (or USB flash drive(s)). But a Ubuntu liveCD will allow you to boot and get on the Internet and use system. Plus you need the current liveCD to make repairs.

---

### Post by kc1di on 2012-03-31
> **airtime82 said:**
> I understand that but what is the problem it has with resolution and what does it do to the menu. If my first theory was right about the menu I couldnt see was this a "grub menu"?

yes when you install ubuntu it installs a grub menu over the old one.  So the new grub boot loader can't find the right resolution for your video card & Monitor.  that's why it show as a black screen.  if you follow my instruction you'll get a grub terminal screen but you will be able to see all the boot entries and be able to scroll to the one you want to boot into.

There are settings that can be changed in the grub file to try different resolutions but lets get it up and running before we try those.

---

### Post by airtime82 on 2012-03-31
> **kc1di said:**
> yes when you install ubuntu it installs a grub menu over the old one. So the new grub boot loader can't find the right resolution for your video card & Monitor. that's why it show as a black screen. if you follow my instruction you'll get a grub terminal screen but you will be able to see all the boot entries and be able to scroll to the one you want to boot into.
 
There are settings that can be changed in the grub file to try different resolutions but lets get it up and running before we try those.
 
 
Do I need to use the iso disc I burned to get into a "live" session of ubuntu and start these commands or can I get there right off the ubuntu site?

---

### Post by airtime82 on 2012-03-31
Also if im just in a "live" session will the commands im typing have the correct affect and not screw things up since im not really in the one installed on my computer?

---

### Post by kc1di on 2012-03-31
> **airtime82 said:**
> Also if im just in a "live" session will the commands im typing have the correct affect and not screw things up since im not really in the one installed on my computer?

you do it right in ubuntu when it boots up. just reboot and let it go to ubuntu then follow the instructions.

---

### Post by airtime82 on 2012-03-31
> **kc1di said:**
> you do it right in ubuntu when it boots up. just reboot and let it go to ubuntu then follow the instructions.
 
My computer boots right to windows 7. Are you saying put in the cd and reboot?

---

### Post by airtime82 on 2012-03-31
> **kc1di said:**
> yes when you install ubuntu it installs a grub menu over the old one. So the new grub boot loader can't find the right resolution for your video card & Monitor. that's why it show as a black screen. if you follow my instruction you'll get a grub terminal screen but you will be able to see all the boot entries and be able to scroll to the one you want to boot into.
 
There are settings that can be changed in the grub file to try different resolutions but lets get it up and running before we try those.
 
If there was a grub menu on the black screen where did it go now that the computer boots right to windows and has no more black screen?

---

### Post by airtime82 on 2012-03-31
Sorry if the questions seem redundant but I want to know as much as possible before doing this.
 
Thanks again for all the help

---

### Post by critin on 2012-03-31
> **airtime82 said:**
> In windows 7 it is no longer add/remove programs, now its programs and features > uninstall or change program. There is no sign of either in there. Also It has to be somewhere because in the midst of the confusion with the black screen it was booting ubuntu without the disc so it must be on the drive somewhere right???

Did you ever look at the disk through windows?  Does it show a 2nd partition of ext 3 or 4, or is it still one windows partition?   If there is no separate partition,  and it isn't in the remove/change programs, ubuntu is not installed.  You have just the one hdd?

---

### Post by airtime82 on 2012-03-31
> **critin said:**
> Did you ever look at the disk through windows? Does it show a 2nd partition of ext 3 or 4, or is it still one windows partition? If there is no separate partition, and it isn't in the remove/change programs, ubuntu is not installed. You have just the one hdd?
 
not sure what you mean by "look at the cd through windows". Also yes just one hdd.

---

### Post by airtime82 on 2012-03-31
?

---

### Post by oldfred on 2012-03-31
From Ubuntu or a Ubuntu liveCD terminal, post this:
```

sudo fdisk -lu
```

---

### Post by critin on 2012-03-31
> not sure what you mean by "look at the cd through windows". Also yes just one hdd.Not the cd, the hard drive.  I don't know Win7, but look at disk management (or whatever its called).  Find your hard drive and see if it's has another partition.

Did you attempt to boot into ubuntu again?  If windows is line 4 on the dark screen, ubuntu should be line 1.  But if windows is booting automatically, it may be booting as the last os used.  Maybe arrow down one time and see what happens.  It should be ubuntu recover at that point.  Normally---

If you can get back in, I suggest doing what post 2 advises.  You need to update grub.  
Or simply boot the live cd and reinstall ubuntu on the same partition as before.  

Still not clear if it's a Wubi or not,  Look at your hard disk drive.

**Follow OldFred's instructions, He posted while I was writing.**

---

### Post by airtime82 on 2012-04-01
> **oldfred said:**
> From Ubuntu or a Ubuntu liveCD terminal, post this:
```

sudo fdisk -lu
```

What will this do?

---

### Post by airtime82 on 2012-04-01
After some Google I see this command shows me my hdd partitions but let's get to my first problem at hand that nobody has given me a solution to.....I can't boot into Ubuntu, there is no more  mystery grub screen, if I can't get into it how can I even try the update grub stuff to.get my menu back?

---

### Post by critin on 2012-04-01
> **airtime82 said:**
> [COLOR=Red]**What will this do?**[/COLOR]

> **airtime82 said:**
> [COLOR=Red]After some Google I see this command shows me my hdd partitions **but let's get to my first problem at hand that nobody has given me a solution to.....I can't boot into Ubuntu, **[/COLOR]there is no more  mystery grub screen, if I can't get into it how can I even try the update grub stuff to.get my menu back?

They're trying to get to the solution.  If you're afraid to follow instructions you will never find the solution.  

Theyl have to see how the hdd is partitioned and they must do it with your help.
This command will not change anything on your comp., it will simply show what is there.

---

### Post by airtime82 on 2012-04-01
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   600760319   300276736    7  HPFS/NTFS/exFAT
/dev/sda4       600760320   625139711    12189696    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$

---

### Post by airtime82 on 2012-04-01
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$

---

### Post by oldfred on 2012-04-01
ubuntu@ubuntu is the liveCD. You cannot update grub from the liveCD. You can reinstall grub but have to mount the Linux partition where grub is installed first. 

But you have no Linux partitions.

Is this a wubi install where Ubuntu is just a file inside your Windows NTFS partition?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi only boots thru the Windows boot loader in the MBR. Installing grub to MBR would prevent booting Windows which you do not want.

---

### Post by critin on 2012-04-01
When you installed ubuntu, did the Wubi installer look like this one?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Delete all references of ubuntu/wubi from the comp.  Do a search and delete the file folders.
Then download the installer from this link and install it again.  If it still says there is a previous version, you didn't delete them all.

---

### Post by airtime82 on 2012-04-01
> **oldfred said:**
> ubuntu@ubuntu is the liveCD. You cannot update grub from the liveCD. You can reinstall grub but have to mount the Linux partition where grub is installed first. 

But you have no Linux partitions.

Is this a wubi install where Ubuntu is just a file inside your Windows NTFS partition?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi only boots thru the Windows boot loader in the MBR. Installing grub to MBR would prevent booting Windows which you do not want.

Line 1; this cd is the only way I knew of to use terminal as I no longer have a way to get to ubuntu that I "installed" on my windows partition.

Line 2; Yes it doesnt show in windows either, I could do a screen shot of the windows disk manager showing partitions if you need it.

Line 3; After I made my boot cd using windows image burner the two options it gave me when the cd was inserted were (a) run wubi.exe install ubuntu with wubi(which I did and (b) explore files contained in iso image on disc.

Line 4; No I dont want to screw up windows being able to boot, I want to find a way to have the option to boot into either OS.

---

### Post by airtime82 on 2012-04-01
> **critin said:**
> When you installed ubuntu, did the Wubi installer look like this one?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Delete all references of ubuntu/wubi from the comp.  Do a search and delete the file folders.
Then download the installer from this link and install it again.  If it still says there is a previous version, you didn't delete them all.

This is very helpful. It did not look like this at all. It was just the ubuntu installer where everything is ubuntu themed. I will try your suggestion.

---

### Post by airtime82 on 2012-04-01
[attach]215258[/attach]

[attach]215259[/attach]

[attach]215260[/attach]

---

### Post by critin on 2012-04-01
If you use the Wubi installer shown in the link, you will not need to burn a cd, it downloads and installs.  Much easier and error-proof.

I suggest you do a defrag before installing again.

---

### Post by kc1di on 2012-04-01
Ok now that we see your drive.  there is no linux partition to boot to.  booting to the live cd and run install.  Not the WUBI one the regular install.  Allow Ubuntu partition manager in the install to re partition your drive [COLOR="Red"](NOTE: if you have anything important on your window install back it up first.)[/COLOR]

Then install Ubuntu -- allow it to finish then reboot into Ubuntu.
When you get to that point I'll or others will help you set it up to dual boot with windows and set up grub so you won't get the black screen.  

[COLOR="red"]Make sure in the installer you check the option that says install along side of windows.[/COLOR]

Let us know when you've done that :)

---

### Post by airtime82 on 2012-04-01
> **kc1di said:**
> Ok now that we see your drive. there is no linux partition to boot to. booting to the live cd and run install. Not the WUBI one the regular install. Allow Ubuntu partition manager in the install to re partition your drive [COLOR=red](NOTE: if you have anything important on your window install back it up first.)[/COLOR]
 
Then install Ubuntu -- allow it to finish then reboot into Ubuntu.
When you get to that point I'll or others will help you set it up to dual boot with windows and set up grub so you won't get the black screen. 
 
[COLOR=red]Make sure in the installer you check the option that says install along side of windows.[/COLOR]
 
Let us know when you've done that :)
 
Okay but first you say "Allow Ubuntu partition manager in the install to re partition your drive" what does that mean? The first time it just brought me to the screen where the partition line slides back and forth between your windows and ubuntu. I want to allow sufficient room for things to be added to ubuntu because I would like to use it mostly and learn so I can maybe use it instead of windows.What do you think is a good amount of space for ubuntu? The first time I left 65 gb to ubuntu and like 180 gb to win7.

---

### Post by kc1di on 2012-04-01
Ok you must still be installing with wubi that's I don't remember how big your drive is but if you have the room give yourself say 80gb more if you can afford it.  Follow the instruction in wubi wiki. Good luck I was talking about a cd install.

---

### Post by airtime82 on 2012-04-01
that was in the cd install.

---

### Post by kc1di on 2012-04-01
here is a page that makes it about as easy as I've seen maybe it will be of help to you.

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by critin on 2012-04-01
> **airtime82 said:**
> Okay but first you say "Allow Ubuntu partition manager in the install to re partition your drive" what does that mean? The first time it just brought me to the screen where the partition line slides back and forth between your windows and ubuntu. I want to allow sufficient room for things to be added to ubuntu because I would like to use it mostly and learn so I can maybe use it instead of windows.What do you think is a good amount of space for ubuntu? The first time I left 65 gb to ubuntu and like 180 gb to win7.

> **airtime82 said:**
> [COLOR=Red]**that was in the cd instal**[/COLOR]l.

Airtime82, If it was me, and I did as a new user, I would use the Wubi as seen in the Wiki link.  Not the same install as you tried before.  Partitioning Windows is not an easy task unless you have studied a few tutorials or someone goes through it step-by-step with you.

Yes, you used a cd but it was still Wubi installed--*inside of Windows.*  Wubi is a virtual machine.  That's different from a cd installed to a hdd.  Two different animals.

After you use ubuntu awhile and have read and studied it,  you can always either learn how to move the Wubi install to a separate partition or install ubuntu fresh to its own.

If the dark screen issue comes up again, you can get help with the graphics at that point.  There is also
help on that wiki page.    

If you decide to partition and install to the hdd please study some tutorials first for your own sake.

---

### Post by airtime82 on 2012-04-02
> **kc1di said:**
> here is a page that makes it about as easy as I've seen maybe it will be of help to you.
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
 
everything on that page is exactly the way I installed to the T and there is nothing I can find on my pc regarding ubuntu after the black screen windows boot. I guess I will just have to try to reinstall but first make my own partition in windows and check something else in the install instead of using the partition slider.

---


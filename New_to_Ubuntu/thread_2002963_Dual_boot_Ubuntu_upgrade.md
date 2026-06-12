---
title: "Dual boot Ubuntu upgrade"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by blackhill on 2012-06-13
I have a dual boot system, Win XP on disk 0 & ubuntu on disk 1.
On attempting to upgrade from 10.10 to 12.04 I lost access to ubuntu but not Win XP
I suspect the problem relates to an incorrectly set up of Grub2 preventing correct boot.
However, it does still boot to the Grub2 menu.
Any help would be much appreciated

---

### Post by mapes12 on 2012-06-13
From 10.10 to 12.04 you either have to upgrade through every version 11.04>11.10 or do a fresh install. In my experience a fresh install wins every time.

How did you approach it?

---

### Post by wilee-nilee on 2012-06-13
10.10 is end of life did you use the correct method to upgrade a EOL.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You can't go from 10.10 to the long term release as well and expect it to just work.

You may have to just pull out what you can with a live cd and reinstall.

---

### Post by kansasnoob on 2012-06-13
I'm also curious what procedure you followed to upgrade?

---

### Post by afixane on 2012-06-13
> **kansasnoob said:**
> I'm also curious what procedure you followed to upgrade?

I always use fresh install

---

### Post by oldfred on 2012-06-14
To see status of where you are at, post the Boot Info link from this, you can run it from Ubuntu liveCD or download it as a bootable liveCD.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by kansasnoob on 2012-06-14
Hi oldfred. Glad to see you're on this :D

Quite a history of boot issues with that computer:

[http://ubuntuforums.org/showthread.php?t=1364928](http://ubuntuforums.org/showthread.php?t=1364928)

[http://ubuntuforums.org/showthread.php?t=1761814](http://ubuntuforums.org/showthread.php?t=1761814)

I'm very rusty with boot problems but from a couple of PM's it sounds like Windows is still booting from grub, not sure what type of errors appear when trying to boot Ubuntu ;)

Just looked at that first PM recieved:

> Lance
You were kind enough to help me in 2010 to overcome a problem
during upgrade of Ubuntu  to 10.04 and all has been fine until I tried
to upgrade to 12.04.

My system is dual boot Win XP on sda and ubuntu
on sdb. The previous problem related to Grub looking in the wrong
initial location and you provided me with the solution.

I suspect that
a similar problem has arisen this time. [B]I used a live version of 12.04
on a USB stick and the option offered to upgrade from 11.04 to 12.04.
All appeared to go well. I could run 12.04 from the stick and after
supposed installation and reboot, the Grub menu offered options to boot
into 12.04 or Windows. The Windows option works but Ubuntu goes into an
unending loop,[/B]

I tried to use the new Grub2 basics and
Grub2/Troubleshooter webpages to understand what is wrong but I am not
sure where to start. I suspect that as last time,Grub is looking for
Ubuntu on the wrong partition/disk.

I am uncertain what to do. I would
like to avoid this type of problem in any future upgrades. I would also
be happy to say goodbye to Windows and my Windows associated data is
well backed up. I am therefore tempted to use the 12.04 stick to re-
format sda and do a new install of 12.04 on sda. I could then re-format
the partition on sdb which currently has ubuntu 10.04 on it and recover
useful disc space.

However, the Windows installation is the only one
on the computer which currently still works which makes me doubtful
about removing it

The alternative would seem to be to edit Grub2 to
direct the ubuntu link to the correct location on sdb. This process is
what you led me through in 2010. However, the Grub information seems to
have changed during the last two years and I can not relate my notes of
what you suggested then to the new descriptions in the Grub2 basics and
Grub2/troubleshooter webpages

So that may answer my earlier question :oops:

---

### Post by oldfred on 2012-06-14
With multiple drives, it may just be a case of grub reinstalling to one drive when BIOS is booting from the other.

The Boot-Repair runs the same bootinfoscript you have run before (which you can run instead if you like), but also can make many repairs, reinstall of grub etc from a gui.

---

### Post by kansasnoob on 2012-06-16
Received another PM :(

> Sorry for the delayed reply but::-

This is a second attempt to reply as the last one a few minutes ago seemed to fail when submitted

I downloaded boot-repair-disk using Windows & burned it to CD using Nero Burn Image to Disk
On booting with the CD in place and as primary boot source it was either ignored or on one occasion boot faiIed

I understood from the program description that the program could be put on USB stick and run from there but again it was ignored and the grub? menu appears offering either windows or ubuntu.
Windows works normally but selecting ubuntu results in an endless looping to the initial screen of cycling dots.

I have also downloaded Super Grub 2 iso file which would not run from a USB stick.
Does the iso file need processing before loading to the stick?

In all cases the boot menu offers a choice of windows or ubuntu & the former works but not ubuntu yet the same ubuntu file on a stick upgraded my portable without serious problem .
The only difference that I know is the the portable had 10.04 on it while the PC had been upgraded to 10.10

Sorry to be so troublesome but I do not know what to do next

I'll PM back asking that we continue the conversation here.

But I can already tell from this "selecting ubuntu results in an endless looping to the initial screen of cycling dots" it's more likely a graphics issue than a grub issue.

So there's probably no need to recreate a Boot Repair USB properly. BTW Nero sucks ;)

I'd guess we need to know some graphics info so use whatever live Ubuntu CD/USB works and post the output of:

```
lspci | grep VGA
```

We'll figure it out ;)

---

### Post by kansasnoob on 2012-06-16
Oh, and no more PM's please :)

Posting here on the open forum is much more likely to get you a desirable result.

---

### Post by kansasnoob on 2012-06-17
While sipping my morning coffee I was thinking about this:

> selecting ubuntu results in an endless looping to the initial screen of cycling dots

The first thing I would do is reboot, use the arrow keys to select Ubuntu in the grub menu, but instead of pressing enter press the "e" key. This will allow you to temporarily edit the boot info grub is using.

Use the arrow keys to move the cursor just past the end of the words **quiet splash**, then use the backspace key to remove only those two words. Next press the F10 key to try and boot.

You'll see a lot of scrolling text and the last lines of text appearing on the screen may help us trouble shoot this. It's generally a lot to try and write down so a digital camera or cell phone camera is handy to post a screen-grab if you have one available :)

Also, do you still have the bootable USB of 12.04 that you installed with? If so I'd try booting it again but as soon as the two small graphics appear at the bottom of the screen press enter (or any key). That will display the boot menu (not grub), and from that select Check disc for defects. That generally takes a few minutes to complete.

If it says "no defects found" then we can rule out faulty installation media, and that Live USB could also be used to run the boot info script using Boot Repair:

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

No need to create a separate disc or USB :)

---

### Post by blackhill on 2012-06-17
> **kansasnoob said:**
> Oh, and no more PM's please :)

Posting here on the open forum is much more likely to get you a desirable result.
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
ubuntu@ubuntu:~$ lspci > grep VGA


The above is the output from lspc > grep VGA

Note that the bar symbol on my keyboard yields > rather than a bar.
Is this the output you wanted or will I try to find a bar symbol in the computers symbol table

---

### Post by blackhill on 2012-06-17
Found correct key for bar symbol. output shown below



ubuntu@ubuntu:~$ lspci | grep VGA  
 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)  
 ubuntu@ubuntu:~$

---

### Post by kansasnoob on 2012-06-17
> **blackhill said:**
> Found correct key for bar symbol. output shown below



ubuntu@ubuntu:~$ lspci | grep VGA  
 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)  
 ubuntu@ubuntu:~$

I'm not finding any known issues related to that graphics chip and 12.04 so move on to what I suggested in post #11.

Hopefully the text displayed w/o "quiet splash" will provide a clue.

---

### Post by blackhill on 2012-06-18
I followed the instructions - grub menu, e, removed quiet splash, F10
The last line of the text was
Running /scripts/init-bottom.........done

Run from 12.04 USB boot menu reported no disk defects

Tried to use Boot Repair from forum item 1821980 but (stupid in retrospect) I hit the repair button instead of the script button

A big mistake! now when I try to boot from the hard disk, all I get is a prompt  "grub rescue"
and no grub menu

Any suggestions?

---

### Post by blackhill on 2012-06-18
Forgot to add that the computer will still boot from the 12.04 stick.

---

### Post by kansasnoob on 2012-06-19
Well now we certainly need to see the results of the Boot Info Script.

---

### Post by oldfred on 2012-06-19
Since booting is now an issue and things may have changed, post the lasted run of the bootinfo report or link to it.

I have Intel 915 on a laptop and 12.04 boots fine. I think I have built in the nomodeset parameter as I need it to boot on my Desktop and the only 12.04 I have tested on the laptop is on a USB flash drive that was created with my desktop. Or try the nomodeset parameter to see if that helps.

---

### Post by blackhill on 2012-06-19
At present booting from the hard disk only yields the Grub Rescue prompt and I have not found any way to progress beyond this.

However, it will boot normally from my 12.04 USB stick.

Can I obtain a copy of the Boot Info Script.for the computer using commands from the stick?

---

### Post by YannBuntu on 2012-06-19
Hello
> **blackhill said:**
> Can I obtain a copy of the Boot Info Script.for the computer using commands from the stick?

Yes you can: boot on your live-USB then follow this: [http://ubuntuforums.org/showpost.php?p=11136267&postcount=1](http://ubuntuforums.org/showpost.php?p=11136267&postcount=1)

---

### Post by kansasnoob on 2012-06-19
> **blackhill said:**
> At present booting from the hard disk only yields the Grub Rescue prompt and I have not found any way to progress beyond this.

However, it will boot normally from my 12.04 USB stick.

Can I obtain a copy of the Boot Info Script.for the computer using commands from the stick?

You know I already linked to that:

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

Also, back in post #11 I specifically said, "You'll see a lot of scrolling text and the last **[COLOR="Red"]lines[/COLOR]** of text appearing on the screen may help us trouble shoot this. It's generally a lot to try and write down so a digital camera or cell phone camera is handy to post a screen-grab if you have one available".

**[COLOR="Red"]Lines[/COLOR]** is plural! Did you not have a way of taking a picture of that screen when things froze?

I'm sorry if I seem a bit gruff but you're making it nearly impossible for anyone to effectively help you :(

---

### Post by blackhill on 2012-06-19
"Yes you can: boot on your live-USB then follow this: [http://ubuntuforums.org/showpost.php...67&postcount=1]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") 		                   		  		  		 		 			 				________________"

Followed the above and obtained the following web address which I presume contains the boot-repair script

[http://paste.ubuntu.com/1049574](http://paste.ubuntu.com/1049574)

---

### Post by SilentMute on 2012-06-19
I had the same problem except that I lacked enough internal disk space on my Ubuntu partition to upgrade 10.04, but I used Wubi, wiped the ubuntu partition and got a fresh install and it's been working great

---

### Post by YannBuntu on 2012-06-19
**@blackhill:** You have no more GRUB packages in your system. You need to reinstall them, eg by clicking the "Recommended repair" of Boot-Repair. If still not good, please indicate the new URL that will appear.

---

### Post by blackhill on 2012-06-19
> **YannBuntu said:**
> **@blackhill:** You have no more GRUB packages in your system. You need to reinstall them, eg by clicking the "Recommended repair" of Boot-Repair. If still not good, please indicate the new URL that will appear.

My humble apologises to all

I miss-read the question whether the sb2 was removable as referring to the USB stick
rather than as it clearly does to my second hard drive

I have re-run the program and the correct script  is at

[http://paste.ubuntu.com/1049695](http://paste.ubuntu.com/1049695)

I do appreciate all the help I have been given. Please do not abandon me now.

---

### Post by kansasnoob on 2012-06-19
Both of those boot info results show there are no grub packages installed in Ubuntu. I also notice that it's still identified as Ubuntu 11.10, not 12.04 :(

Am I correct that you used a Precise Live USB to upgrade from Oneiric similar to this:

[ATTACH]219958[/ATTACH]

If so did you get any error warnings during the process?

I'm guessing that the first time you ran "boot repair" it purged the grub files with the intention of reinstalling the grub files, but then encountered a package installation problem. Like the packages are just not available, maybe broken repositories due to a failed upgrade/installation. I need to think about this a little ;)

---

### Post by kansasnoob on 2012-06-19
I want you to try something using your live USB. I assume you know how to open the terminal by now, so just boot the live USB, open the terminal, then [copy-n-paste]("http://ubuntuforums.org/showpost.php?p=11459388&postcount=160") these commands. They are terribly long commands so don't try just typing them:

```
sudo mount /dev/sdb7 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
apt-get update
```

If you have broken repos as I expect that'll show a lot of errors, regardless I really need you to copy all of that text and post it here.

But you may as well also try:

```
apt-get install grub-pc
```

```
update-grub
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

Of course I need to know about any errors shown but **I absolutely must see the output of**:

```
df -H
```

After you have that info copied then you can exit the chroot:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Don't worry about errors from that last command, just post that info here so I can see it.

---

### Post by YannBuntu on 2012-06-20
> **blackhill said:**
> My humble apologises to all

I miss-read the question whether the sb2 was removable as referring to the USB stick
rather than as it clearly does to my second hard drive

I have re-run the program and the correct script  is at

[http://paste.ubuntu.com/1049695](http://paste.ubuntu.com/1049695)

I do appreciate all the help I have been given. Please do not abandon me now.

You have clicked the "Create BootInfo" button instead of the "Recommended repair" one.
Please click the "Recommended repair" button and indicate the new URL that will appear.
It will do in 1 click what Kansasnoob suggested:
> =================== Default settings
recommendedrepair
This setting would purge and reinstall the grub2 of sdb7  into the MBRs of all disks (except USB without OS).

---

### Post by kansasnoob on 2012-06-20
> **YannBuntu said:**
> You have clicked the "Create BootInfo" button instead of the "Recommended repair" one.
Please click the "Recommended repair" button and indicate the new URL that will appear.
It will do in 1 click what Kansasnoob suggested:

Did you notice where I said:

> I'm guessing that the first time you ran "boot repair" it purged the grub files with the intention of reinstalling the grub files, but then encountered a package installation problem. Like the packages are just not available, maybe broken repositories due to a failed upgrade/installation.

That's why I specifically want to see the terminal output of "apt-get update" in a chroot. I suspect the packages are simply not available due to borked repos, and I also requested a free space check (df -H) to rule out a lack of free space as the cause of the failed upgrade/installation :)

If you go clear back to post #9 I posted the content of a PM where blackhill said:

> Windows works normally but selecting ubuntu results in an endless looping to the initial screen of cycling dots.


But then in post #15 blackhill said:

> I followed the instructions - grub menu, e, removed quiet splash, F10
The last line of the text was
Running /scripts/init-bottom.........done

Run from 12.04 USB boot menu reported no disk defects

Tried to use Boot Repair from forum item 1821980 but (stupid in retrospect) I hit the repair button instead of the script button

A big mistake! now when I try to boot from the hard disk, all I get is a prompt "grub rescue"
and no grub menu


That's why I assume the boot repair disc purged but was then unable to reinstall the grub packages ;)

So the boot repair disc took us from:

> Windows works normally but selecting ubuntu results in an endless looping to the initial screen of cycling dots. 

To:

> now when I try to boot from the hard disk, all I get is a prompt "grub rescue"
and no grub menu 

Then there is the greater issue of why the boot info results show Ubuntu 11.10 even though blackhill says:

> I used a live version of 12.04
on a USB stick and the option offered to upgrade from 11.04 to 12.04.
All appeared to go well. I could run 12.04 from the stick and after
supposed installation and reboot, the Grub menu offered options to boot
into 12.04 or Windows. The Windows option works but Ubuntu goes into an
unending loop,

Great confusing stuff, eh :)

It would be great to see some of the logs, and that's certainly one of the things I'd look at if the puter was right in front of me, but based on the links I included in post #7 this may well date back to Karmic so it could take days or even weeks to obtain the proper logs at this rate ............ and why it's borked isn't as important as what is borked.

---

### Post by YannBuntu on 2012-06-20
**@kansasnoob:** thanks. I agree with your analysis. I also think that boot repair disc purged but was then unable to reinstall the grub packages (this may be due to bad network, or bad sources.list, or apt/dpkg problem).
I asked the URL resulting of the "Recommended repair" because it will show all what you asked (output of "apt-get update" in a chroot, "df -H", and outputs of all the post#27 procedure commands) and more.

**@blackhill:** in addition to the "Recommended repair" URL, please could you attach your logs history to your reply (run Boot-Repair, click "Advanced options", click "Backup partition tables..", save the ZIP file somewhere, and attach it to your reply in this thread). This will help us understand why Boot-Repair purged GRUB.

---

### Post by kansasnoob on 2012-06-20
> I asked the URL resulting of the "Recommended repair" because it will show all what you asked (output of "apt-get update" in a chroot, "df -H", and outputs of all the post#27 procedure commands) and more.


Aha, I didn't know that. I'll have to play more thoroughly with Boot Repair when I find time ;)

I also hadn't thought about a network problem but that could explain a great deal of the problem(s).

---

### Post by blackhill on 2012-06-21
[I]I have had several attempts to follow YannBuntu's post  no. 30

I tried to combine the Recommended repair function with the Advanced options with no success so I finally concluded that they should be run separately - correct?

The Rec. Repair gave the following output:-[/I]

  	 	 	 	 	 	   Please open a terminal then type the following commands:-
 

 sudo chroot "/mnt/boot-sav/sdb7" apt-get install -fy  
 sudo chroot "/mnt/boot-sav/sdb7" dpkg --configure -a  
 sudo chroot "/mnt/boot-sav/sdb7" apt-get install -y --force-yes grub-pc
 

 If a menu similar to the one below appears , use Tab, Space and Enter keys in order to install
 GRUB in the disk you wish


*This was followed by  a screen image  containing commands which appear to be intended to redirect Grub to an alternative location but I do not understand the commands sufficiently to risk attempting to use  them without advice.*


*I have on disk, the  zip file produced by the advance option of Boot-Repair but I could not find how to attach it to this post. The attachment option seemed to require  an http address. I  could possibly expand the file but it would be very substantial and I doubt  if would comply with the restriction on posting*


[I]Please could you suggest how to procede
[/I]

---

### Post by YannBuntu on 2012-06-21
> **blackhill said:**
> I tried to combine the Recommended repair function with the Advanced options with no success so I finally concluded that they should be run separately - correct?

The "Recommended repair" button is equivalent to clicking "Advanced options", then "Apply" without changing the default settings.
> **blackhill said:**
> sudo chroot "/mnt/boot-sav/sdb7" apt-get install -fy  
 sudo chroot "/mnt/boot-sav/sdb7" dpkg --configure -a  
 sudo chroot "/mnt/boot-sav/sdb7" apt-get install -y --force-yes grub-pc

These commands will fix frequent package problems, then reinstall your GRUB.
 
> **blackhill said:**
> *I have on disk, the  zip file produced by the advance option of Boot-Repair but I could not find how to attach it to this post. The attachment option seemed to require  an http address. I  could possibly expand the file but it would be very substantial and I doubt  if would comply with the restriction on posting*

I don't know if there are any restrictions for forum attachment, maybe Oldfred can tell us more about it. Please could you send me the ZIP file by email (yannubuntu ATT gmail DOTT com)?

---

### Post by kansasnoob on 2012-06-21
I'd suggest that "Boot Repair" is still alpha or beta quality and it would be best to follow my suggestions. I don't mean to say that "I know better" but I do absolutely know how to instruct someone using my procedure :)

Once again I'd point out that this was a failed upgrade using a live USB, grub was NOT the problem, so all "Boot Repair" did was create a new problem :(

Given the fact that BIS shows it's still 11.10 when it should be 12.04 I think we need to look at what failed in the upgrade, very specifically finding out how much free space exists!

But we've now turned this into troubleshooting "Boot Repair". Sometimes a human brain is just required to work through the intricacies of boot problems ;)

Remember I spent a few moments to look back at other boot problems with this puter:

[http://ubuntuforums.org/showthread.php?t=1364928](http://ubuntuforums.org/showthread.php?t=1364928)

[http://ubuntuforums.org/showthread.php?t=1761814](http://ubuntuforums.org/showthread.php?t=1761814)

This was NOT a grub problem until "Boot Repair" made it one! So maybe that app needs a sanity check to see if apt will allow re-installation of grub packages before purging them.

---

### Post by blackhill on 2012-06-21
Speaking from the fullness of my ignorance, it strikes me  that 12.04 is working consistently from my USB stick.

Also each time I load it from the stick, it still offers  the option to install ubuntu 12.04

Would there be any possible benefit in trying a re-installtion from the stick or is that just likely to completely muck things up.

---

### Post by kansasnoob on 2012-06-21
> **blackhill said:**
> Speaking from the fullness of my ignorance, it strikes me  that 12.04 is working consistently from my USB stick.

Also each time I load it from the stick, it still offers  the option to install ubuntu 12.04

Would there be any possible benefit in trying a re-installtion from the stick or is that just likely to completely muck things up.

I first need to know why it failed the first time. Very specifically if there's a free space issue.

That's why I requested that info :D

---

### Post by blackhill on 2012-06-21
I would be happy to run any commands that give the information requested regarding free space but
having looked back through the posts I am uncertain which commands should be run and the last thing I want is to mess things up further by an inappropriate action.

Could you repeat the command for point me to the relevant previous post. Thanks.

---

### Post by blackhill on 2012-06-21
Having gone back again over previous posts, I suspect that I should follow the suggests listed previously in post 27.

Is this still appropriate? If so. I will try to work my way through them and report back.

---

### Post by kansasnoob on 2012-06-22
> **blackhill said:**
> Having gone back again over previous posts, I suspect that I should follow the suggests listed previously in post 27.

Is this still appropriate? If so. I will try to work my way through them and report back.

Yes. Not much work to it, just copy-n-paste those commands into the terminal and also copy-n-paste the terminal output into a reply box here.

---

### Post by blackhill on 2012-06-22
ubuntu@ubuntu:~$ sudo mount /dev/sdb7 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic InRelease                              
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports InRelease                    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                         
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease             
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports Release.gpg        
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]           
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]            
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports Release                      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg [198 B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release [40.8 kB]                      
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/main TranslationIndex        
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/multiverse TranslationIndex  
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/restricted TranslationIndex  
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/universe TranslationIndex    
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release [40.8 kB]              
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner TranslationIndex               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release [40.8 kB]             
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources [877 kB]                  
Err [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/main i386 Packages           
  404  Not Found [IP: 91.189.92.176 80]
Err [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/restricted i386 Packages     
  404  Not Found [IP: 91.189.92.176 80]
Err [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/universe i386 Packages     
  404  Not Found [IP: 91.189.92.176 80]
Err [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/multiverse i386 Packages   
  404  Not Found [IP: 91.189.92.176 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/main Translation-en_US     
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/main Translation-en          
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US 
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/multiverse Translation-en    
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/restricted Translation-en_US 
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en                 
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/restricted Translation-en    
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/universe Translation-en_US   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) karmic-backports/universe Translation-en      
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources [5,351 B]           
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources [4,677 kB]           
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources [149 kB]           
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]         
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B]    
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages [4,468 kB]     
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources [143 kB]         
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources [3,347 B]  
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources [56.1 kB]    
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources [3,666 B]  
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages [359 kB]   
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages [6,631 B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages [121 kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,371 B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]  
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [72 B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources [41.8 kB]       
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources [1,959 B] 
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources [18.6 kB]   
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources [1,641 B] 
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages [129 kB]  
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages [3,939 B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages [43.0 kB]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages [3,380 B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex [73 B] 
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex [71 B]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en        
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en [72.8 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en       
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en [29.6 kB]
Fetched 12.7 MB in 1min 50s (115 kB/s)                                         
W: Failed to fetch [http://im.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages](http://im.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch [http://im.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages](http://im.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch [http://im.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages](http://im.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch [http://im.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages](http://im.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.176 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ubuntu:/# apt-get install grub-pc
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ubuntu:/# update-grub
Generating grub.cfg ...
cat: /boot/grub/video.lst: No such file or directory
Found linux image: /boot/vmlinuz-3.0.0-20-generic
Found initrd image: /boot/initrd.img-3.0.0-20-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found Windows NT/2000/XP (loader) on /dev/sda2
done
root@ubuntu:/# grub-install /dev/sdb
Installation finished. No error reported.
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb7               88G    56G    28G  67% /
udev                   1.1G    13k   1.1G   1% /dev
tmpfs                   88G    56G    28G  67% /run
df: `/run/lock': No such file or directory
df: `/run/shm': No such file or directory
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
ubuntu@ubuntu:~$

---

### Post by kansasnoob on 2012-06-22
Wow, what a freaking mess :(

You clearly have both Oneiric and Karmic entries still active in your sources.list, and some cruft from Karmic backports.

Also "df -H" shows you have only 28GB available whereas you have 56GB used in your only Ubuntu partition. I'd hoped that you'd have at least 50% free so we could easily do a fresh install to a new partition but that's not a good option.

IMHO the only reasonable thing to do is use your live USB to back up your data in /home to some external device and perform a fresh install, **[COLOR="Red"]but[/COLOR]** looking at your boot info script results through time you have three swap partitions, two of which are not needed, and I wonder if sdb2 truly is your only Windows backup as shown here:

> "/dev/sdb2 1CC055D9C055B9AA ntfs Win Backup"

Maybe a screenshot of sdb using Gparted would be helpful but IMHO you really have yourself painted into a corner ](*,)

You asked a question here:

[http://ubuntuforums.org/showthread.php?t=1969785](http://ubuntuforums.org/showthread.php?t=1969785)

And rather than waiting for a reasonable answer you jumped into a bloody mess :cry:

---

### Post by blackhill on 2012-06-22
Thank you for your analysis of my situation

If possible, I would like to retain sda unaltered and regain access to it as it contains Windows and some data that I would prefer not to loose.

I have a full backup of all my ubuntu based data on an exterior  hard disk  and on USB sticks.

Ideally I would reformat sdb and make a fresh installation of ubuntu 12.04 on it. 
I presume I could then restore my ubuntu data files from these external sources

My initial concern is that at present if I try to boot from the hard disk(s) all I get is the Grub Rescue Prompt. 

From the depth of my ignorance, I would be tempted to use the 12.04 stick to re-format sdb and install 12.04 on it. However, I am concerned that if I tried this I might finish up with Windows on sda and ubuntu on Sdb but Grub problems which would still not be resolved.
I fear having both systems present but unable, as now,  to access either.

I would be very grateful for your comments

---

### Post by kansasnoob on 2012-06-22
> **blackhill said:**
> Thank you for your analysis of my situation

If possible, I would like to retain sda unaltered and regain access to it as it contains Windows and some data that I would prefer not to loose.

I have a full backup of all my ubuntu based data on an exterior  hard disk  and on USB sticks.

Ideally I would reformat sdb and make a fresh installation of ubuntu 12.04 on it. 
I presume I could then restore my ubuntu data files from these external sources

My initial concern is that at present if I try to boot from the hard disk(s) all I get is the Grub Rescue Prompt. 

From the depth of my ignorance, I would be tempted to use the 12.04 stick to re-format sdb and install 12.04 on it. However, I am concerned that if I tried this I might finish up with Windows on sda and ubuntu on Sdb but Grub problems which would still not be resolved.
I fear having both systems present but unable, as now,  to access either.

I would be very grateful for your comments

Slow down a bit ................ lets make sure we do this right!

I'm going down the street to grab a pizza in a few minutes so give me time to think about putting some sanity checks in place.

I particularly want to be absolutely certain that none of the partitions on sdb contain any data that you need!

---

### Post by kansasnoob on 2012-06-22
OK I'm looking, first of all your general layout:

```
=================== parted -l:

Model: ATA HDS728080PLA380 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
2      41.1MB  75.0GB  75.0GB  primary  ntfs         boot
3      75.0GB  80.0GB  4985MB  primary  fat32        hidden, lba


Model: ATA SAMSUNG SP2504C (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
3      32.3kB  94.4GB  94.4GB  extended
7      96.8kB  87.7GB  87.7GB  logical   ext4
8      87.7GB  91.4GB  3767MB  logical   linux-swap(v1)
5      91.4GB  92.8GB  1415MB  logical   linux-swap(v1)
6      92.8GB  94.4GB  1522MB  logical   linux-swap(v1)
2      94.4GB  241GB   146GB   primary   ntfs            boot


```

Typically parted -l shows partitions in their actual order so I find it a bit odd to see both drives begin with partition #2. Not sure why that would be, but please focus on size!

First of all sda is 80GB whereas sdb is 250 GB. That's important because sometimes Ubuntu/Linux will identify drives in a different order!

But sdb has a 146GB NTFS partition that's labeled Win backup:

> /dev/sdb2: LABEL="Win Backup" UUID="1CC055D9C055B9AA" TYPE="ntfs"

If that truly is a data partition you absolutely don't want to erase it!

Clear as mud?

Would you be willing to post a screenshot of both drives?

---

### Post by kansasnoob on 2012-06-22
Just thought to add, you're maybe not used to the Unity DE, so if you want to investigate what's on a specific partition look here:

[ATTACH]220087[/ATTACH]

You can see that most of my partitions are labeled but I have a 78GB partition that's not. The point is that I can mount any partition and look through it to see what's there.

---

### Post by blackhill on 2012-06-22
Thank you, I had not appreciated that.

As regards the partitions, sda has a main Windows partition which also contains data files. It is this partition which I am most concerned  about. The Windows was supplied by Dell and has a recovery partition on sda. Dell supplied a recovery disk to re-install Windows but this is not a full Windows disk and can only be used  with the recovery partition.

I had ubuntu on sdb plus its data files. There is also a partition containing backup of the Windows data files. 

Fortunately I had the wit to back up both Windows and Ubuntu data files to a 1 GB external hard drive before I rashly set out to upgrade ubuntu .

Main main concerns therefore are to try to preserve the files on sda, get ubuntu 12.04 on to sdb and provide a functioning grub to allow selection of either Windows or ubuntu.

If that can be achieved, I should be able to recover the data files from the external drive and in fact, many of the ubuntu data files are also backed up on a USB stick.

I think it should be possible to format sdb and load on 12.04 from my USB stick. That may be over optimistic but what really conerns me is the possibility that having done this I will be back to trying to establish a functional grub with the option to choose either system at boot up.

Please could you provide advice .

---

### Post by blackhill on 2012-06-22
PS  It is now nearly midnight here, my brain is about fried and rest is needed.

So, if you reply and do not get an immediate response, It will not be due to lack of interest but a real need to recharge my batteries.

Thanks

---

### Post by kansasnoob on 2012-06-23
Well, first of all about grub and the installer. The only way a user has any control over where grub gets installed during installation of the OS is by using the option "Something else" which truly is the advanced partitioning option. And even then you can only select one location to which grub installs, in your case specifically either /dev/sda or /dev/sdb.

Going back to your [first encounter with a grub error]("http://ubuntuforums.org/showthread.php?t=1364928&page=2") I think it's reasonable to assume that /dev/sda (your 80GB Windows drive) is set as your boot drive either in BIOS or perhaps even in the way the drives are connected since they're both ATA/IDE drives.

Given your knowledge level I doubt that you'd want to use the advanced partitioning option though, although IMHO it's something worth learning, but the live installer is in for a complete overhaul in Quantal so it's rather likely that what you'd learn now would be useless with future versions of Ubuntu :(

Not to worry though, we'll get back to grub, but we first need to figure out the best method for you to reinstall. Please take a moment to look at this screenshot from post #26:

[http://ubuntuforums.org/attachment.php?attachmentid=219958&d=1340156149](http://ubuntuforums.org/attachment.php?attachmentid=219958&d=1340156149)

Is that fairly representative of what you saw when attempting to upgrade to 12.04?

If so the simplest thing to do would be to select Erase Ubuntu 11.10 and reinstall. That should also leave the NTFS backup partition in place **[COLOR="Red"]but[/COLOR]** that would NOT address the issue of now having three swap partitions. Does that bother you? It's not harmful, just wastes a very small amount of space.

What really confuses me is how you ended up with no partition #1 on either sda or sdb, I spent a couple of hours trying to recreate that scenario without success :confused:

The inquisitive part of me would really like to see a Gparted screenshot of both sda and sdb, but if you want to keep that NTFS data partition on the Ubuntu drive and just want to try and get running again follow these steps:

#1: Boot your live USB and choose to run the live desktop so you'll be able to record any info/errors encountered during installation - the screenshot tool can be very useful.

#2: Right click on the Install icon and choose "open". 

#3: The first screen just asks you to select the desired language. So choose your language and click on Continue.

#4: The second screen will ask if you wish to DL updates and install 3rd party software, if I have a fast wired connection I say yes, otherwise I say no.

#5: Now you should be presented with the options about where to install Ubuntu. If, **[COLOR="Red"]and only if[/COLOR]**, you see the option "Erase Ubuntu 11.10 and reinstall" then select that and click on Continue. **DO NOT** confuse that with "Erase everything and reinstall" - that could be disastrous!

[B][COLOR="Red"]If you do NOT see the option "Erase Ubuntu 11.10 and reinstall" just click on quit!
[/COLOR][/B]
#6: The rest of the installation process should be standard fare to anyone, just entering info, but when the installation completes don't just reboot! Choose to "Continue testing", then install boot repair:

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

#7: Run the recommended repair:

[https://help.ubuntu.com/community/Boot-Repair#Recommended_repair](https://help.ubuntu.com/community/Boot-Repair#Recommended_repair)

I actually spent a couple of hours intentionally breaking things and testing so I'm fairly confident that it should install grub to the mbr of both sda and sdb ;)

---

### Post by blackhill on 2012-06-23
Many thanks for your detailed response
 

 I am almost certain that sda was set as the boot drive
 

 [http://ubuntuforums.org/attachment.p...8&d=1340156149]("http://ubuntuforums.org/attachment.php?attachmentid=219958&d=1340156149")


 I think this may be the crux of my problem. I remember a very similar screen   
 ( possibly the same one)  and being torn between option two or four. I had not upgraded my computer beyond 11.04 at any point. I may have, disastrously, assumed that 11.10 was only a minor modification of 11.04 and therefore used option 2. Looking back, that seems stupid but I can not think of any other reason why there should be references to 11.10 in the computer. There had certainly never been an attempt to install it.
 

 

 Here is a Gparted screenshot. (I could not get the screenshot to paste in. I will try to Email it to you)

 

 

 Loss of the space for the swap partitions would not matter
 

 The NTFS partition on sdb is a backup for windows files. It is not essential as these are also backed up on my external drive but I would keep the partition as is unless there is a particular reason for removing it.
 

 The instructions seem straight forward ( famous last words when I get my hands on them).
 However, no 5, I understand the section (if you see option Erase Ubuntu 11.10, ) but what if it says Erase Ubuntu 11.04 which was actually the last functional version of ubuntu on the computer.

---

### Post by kansasnoob on 2012-06-23
> However, no 5, I understand the section (if you see option Erase Ubuntu 11.10, ) but what if it says Erase Ubuntu 11.04 which was actually the last functional version of ubuntu on the computer.


The Ubuntu version number wouldn't really matter. I'm just guessing it will show 11.10 because both the most recent boot info and the info requested by me show Oneiric info.

I guess a better way for me to have phrased that would have been:

If you do NOT see the option "Erase Ubuntu 11.10 and reinstall", or if the options offered confuse you, please take a screenshot of that screen and click on quit!

You could then send me the screenshot. BTW I got that other screenshot, thanks.

The big thing is that the quit button is there for a reason. If in doubt just quit and request additional advice.

Speaking of that screenshot:

[ATTACH]220132[/ATTACH] 

I notice that sdb (the Ubuntu drive) has 8.6GB of free space at the very end. That's not a problem but when they redesigned the live installer in Maverick they sort of combined the "use largest continuous free space" and "auto-resize" options into a single option called "Install Ubuntu alongside other OS" which has created a lot of confusion.

In your case you may be offered that option, if so don't use it! It would likely put 12.04 in that 8.6GB space :(

As I said, if in doubt take a screenshot of the options offered, quit the installation, and send me the screenshot ;)

---

### Post by kansasnoob on 2012-06-23
BTW here's a brief how-to about posting screenshots and other attachments on the forums:

[http://ubuntuforums.org/showpost.php?p=4527031&postcount=4](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4)

I generally use the little paper clip at the top of the reply box but both methods have the same results.

---

### Post by blackhill on 2012-06-24
Hallejula (sp?) -- Whoopee!

ALL NOW WORKING PERFECTLY!!

Profound thanks to all and especially Kansasnoob.

12.04 is supposed to be maintained for 5 years so peace should reign in this quarter for some time.

---

### Post by kansasnoob on 2012-06-24
Just to be absolutely certain what you ended up with I'd very much like to see the output of these two commands:

```
sudo parted -l
```

```
df -H
```

Better to check things now than to get caught off guard ;)

---

### Post by blackhill on 2012-06-24
This is the output requested;-

john@john-Dell-DV051:~$ sudo parted -l
[sudo] password for john: 
Model: ATA HDS728080PLA380 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 2      41.1MB  75.0GB  75.0GB  primary  ntfs         boot
 3      75.0GB  80.0GB  4985MB  primary  fat32        hidden, lba


Model: ATA SAMSUNG SP2504C (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 3      1048kB  94.4GB  94.4GB  extended
 8      1049kB  87.7GB  87.7GB  logical   ext4
 7      87.7GB  91.4GB  3767MB  logical   linux-swap(v1)
 5      91.4GB  92.8GB  1415MB  logical   linux-swap(v1)
 6      92.8GB  94.4GB  1522MB  logical   linux-swap(v1)
 2      94.4GB  241GB   146GB   primary   ntfs            boot


john@john-Dell-DV051:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb8        88G  4.0G   80G   5% /
udev            1.1G  4.1k  1.1G   1% /dev
tmpfs           421M  893k  420M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            1.1G  500k  1.1G   1% /run/shm
john@john-Dell-DV051:~$

---

### Post by kansasnoob on 2012-06-24
> **blackhill said:**
> This is the output requested;-

john@john-Dell-DV051:~$ sudo parted -l
[sudo] password for john: 
Model: ATA HDS728080PLA380 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 2      41.1MB  75.0GB  75.0GB  primary  ntfs         boot
 3      75.0GB  80.0GB  4985MB  primary  fat32        hidden, lba


Model: ATA SAMSUNG SP2504C (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 3      1048kB  94.4GB  94.4GB  extended
 8      1049kB  87.7GB  87.7GB  logical   ext4
 7      87.7GB  91.4GB  3767MB  logical   linux-swap(v1)
 5      91.4GB  92.8GB  1415MB  logical   linux-swap(v1)
 6      92.8GB  94.4GB  1522MB  logical   linux-swap(v1)
 2      94.4GB  241GB   146GB   primary   ntfs            boot


john@john-Dell-DV051:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb8        88G  4.0G   80G   5% /
udev            1.1G  4.1k  1.1G   1% /dev
tmpfs           421M  893k  420M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            1.1G  500k  1.1G   1% /run/shm
john@john-Dell-DV051:~$

That looks just fine :)

But just for your future knowledge the installer did renumber a couple of partitions. Previous to this Ubuntu had been on sdb7:

```
Model: ATA SAMSUNG SP2504C (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
3      32.3kB  94.4GB  94.4GB  extended
**7      96.8kB  87.7GB  87.7GB  logical   ext4**
8      87.7GB  91.4GB  3767MB  logical   linux-swap(v1)
5      91.4GB  92.8GB  1415MB  logical   linux-swap(v1)
6      92.8GB  94.4GB  1522MB  logical   linux-swap(v1)
2      94.4GB  241GB   146GB   primary   ntfs            boot
```

But it's now on sdb8 because the installer changed some numbers. No big deal, but you need to know that the old command line info I provided here and in the two previous boot failure threads is no longer totally valid.

But it looks like you're good to go :guitar:

Could I also get you to mark this thread solved by clicking on Thread tools at the top of the thread?

---


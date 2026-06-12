---
title: "Lost MBR in Vista, trying to recover with Ubuntu"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by malt loaf on 2012-02-05
[SIZE=2]I've spent the last 4 days trying to resolve a problem that I probably caused myself in Win Vista.  It would take several pages to describe everything that I've tried so I'll just start[/SIZE] [SIZE=2]with the basics[/SIZE].

[SIZE=2]I have (had!) a dual boot laptop that started out as Vista 32 bit.  I wanted to try Ubuntu so I installed Lynx via Wubi, I think, (it's at least a year ago).  Everything fine.  Recently I was thinking about some changes and was using easyBCD in Windows.  Somehow I cleared the menu list, but got pulled up by a warning that pc would not boot if I saved changes.  Went back, and then somehow ended up with Vista, Ubuntu, and Vista again in the menu list.  Then I got an ambiguous warning message on closing.  Don't remember now, my brain is a bit addled with all this.  On re-booting, you guessed it, nothing.

Lots more I could say, but to cut short, I'm now using Lynx LiveCD to access machine.  I can see all my files so all is not lost.  So now I'm  trying to re-install Grub to get my boot options menu back but whatever I do I get error messages.  Probably mainly cos I don't have a clue what I'm doing.  I've tried various suggestions in forums elsewhere.  Best result so far was getting a grub menu come up on re-boot but nothing in it.  System does not seem to want to let me update grub or use chroot.

I'm guessing this may be a lost cause.  Any ideas anyone?
[/SIZE]

---

### Post by wyliecoyoteuk on 2012-02-05
Try Rescatux, has saved me from a trashed install recently.
[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

---

### Post by oldfred on 2012-02-05
Supergrub/ Rescatux is often a good choice, I like to have it and Boot-Repair in my toolbox to fix things.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Wubi uses the Windows boot loader to boot, so you do not install grub2's boot loader to the MBR like with a normal partitioned install. You do see the grub menu after you boot with Windows. The Windows BCD has both the entries for Windows and Ubuntu and the Ubuntu selection loads a grub menu.

You can install a Windows work alike boot loader from Ubuntu or use a Vista repairCD and use Windows commands to fixMBR.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by malt loaf on 2012-02-06
[SIZE=2]Thanks guys for the suggestions.  I will try the Rescatux disk, but will I be able to burn the ISO image to a CD whilst running Ubuntu from the same drive?  Seems like an ask.

I tried the Lilo idea, which seemed to go as planned, ignored various error messages and ended up with "MBR has been updated" Sounded good, but when I rebooted the grub menu had disappeared, (which I guess you would expect), but I just got "Disk read error has occurred".  "Ctrl-Alt Del to restart".

Not sure whether I am better off or worse off.  Interested to hear that a wubi installation uses the windows boot loader, which probably explains why I'm getting nowhere with grub.  But given that I can actually get an empty grub menu isn't there scope to try to force that to show the OS choices?  I don't seem to have a grub.cfg though and grub setup and grub update don't work.

Or is that all a waste of time anyway since I won't be able to boot windows once I've got to the grub menu because its a wubi install?  Don't really get all that.

As you can tell I'm confused.
[/SIZE]

---

### Post by wyliecoyoteuk on 2012-02-06
rescatux can be run from USB.
[http://www.supergrubdisk.org/2011/12/18/doc-how-to-put-rescatux-into-a-usb/](http://www.supergrubdisk.org/2011/12/18/doc-how-to-put-rescatux-into-a-usb/)

---

### Post by malt loaf on 2012-02-06
And will it write the ISO to USB correctly if I'm doing all this under Ubuntu?

---

### Post by wyliecoyoteuk on 2012-02-06
It should do, yes, (note the ubuntu users instruction).

Wubi uses the windows boot loader, which you should be able to restore, but you may lose access to Linux.

At worst, you could install grub and use it to boot windows.

---

### Post by malt loaf on 2012-02-06
[SIZE=2]Yeah, I'm about to give up on this. I don't have a memory stick with any real capacity easily available, but in any case I've tried a thousand different ways to get the windows boot loader working.  Nothing works.

At the moment I don't have access to any OS from the HDD.

I cannot get grub to install either, whatever I do.  It will install to the point of showing me a blank menu with no options.  When I try grub-update to force it to populate the list I get an error message along the lines of "is /dev mounted?"  Well yeah, as far as I know it is!!

I can't help feeling that grub is confused by the fact that I'm running Ubuntu off the live cd, but there is also a wubi install on the HDD.

Really, I've no idea what is going on. 
[/SIZE]

---

### Post by oldfred on 2012-02-06
Post this so we can see your details, If lilo does not boot that says you have some Windows issue.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Boot-Repair also runs the newer git/testing version of the script.
Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)

---

### Post by Sigma1 on 2012-02-06
> I can't help feeling that grub is confused by the fact that I'm running Ubuntu off the live cd

I don't know much about how wubi installs work, but this remark makes me wonder whether you have been using chroot, to change the root directory, before launching the update-grub command.

---

### Post by malt loaf on 2012-02-06
[SIZE=3]Well[/SIZE], [SIZE=3]you may well ask.  I tried to chroot to try a solution I saw posted somwhere but could not get it to work.  I then read somewhere else that sudo does the same thing.  If not, could you please advise how I can get it to work,I have no idea where I should be changing to!!  Should I be changing to the boot/grub folder of the wubi install?


I tried oldfred's suggestion re boot info script.  Everything seemed fine and it tells me it has created results.txt, but then I could not navigate to the directory where it should have been.  And a mysterious 18 Gb file system appeared from nowhere under Computer!!  Had to reboot twice with the live cd to get back to normality.  Bit nervous of trying again.[/SIZE]

---

### Post by Gremlinzzz on 2012-02-06
Did you try installing a dual boot.then you should have access to Vista so you can remove wubi install.

dual boot 
installing Ubuntu side by side with Vista

---

### Post by malt loaf on 2012-02-06
[SIZE=3]Hi Gremlinzzz, do you mean install Ubuntu off the live cd?  That did occur to me, but there seems to be a problem with that too.  The option to install "side by side" seems to have disappeared.  I'm not confident about what I need to do with manually setting up partitions so I've given up on that.[/SIZE]  [SIZE=3]If you can give me a steer on manipulating the existing partition setup, I might try it, but I don't want to lose my existing installation of Vista if I can help it.[/SIZE]

---

### Post by Sigma1 on 2012-02-06
Having looked around a bit, it appears that wubi installs are very different from what I'm familiar with. You might find your answer here: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Apologies if this link has already been given.

Re: your question: > **malt loaf said:**
>  Well[/SIZE], [SIZE=3]you may well ask.  I tried to chroot to try a solution I saw posted somwhere but could not get it to work.  I then read somewhere else that sudo does the same thing.  If not, could you please advise how I can get it to work,I have no idea where I should be changing to!!  Should I be changing to the boot/grub folder of the wubi install? 

sudo: this is a program, but is fundamentally used as a sort of prefix before any commands that require root (i.e. administrator) privileges. Basically, any commands that mess with anything that's not in /home

chroot: this is a command used to change the root file system from which other commands are issued... Updating grub on a live-cd won't do much, since the live-cd is read-only. If you chroot into a harddisk installation, you can run a grub update (or install it afresh), and have this operate on the disk itself.

That said, you're best off going with the link above, on a wubi install! Good luck.

---

### Post by Gremlinzzz on 2012-02-06
> **malt loaf said:**
> [SIZE=3]Hi Gremlinzzz, do you mean install Ubuntu off the live cd?  That did occur to me, but there seems to be a problem with that too.  The option to install "side by side" seems to have disappeared.  I'm not confident about what I need to do with manually setting up partitions so I've given up on that.[/SIZE]  [SIZE=3]If you can give me a steer on manipulating the existing partition setup, I might try it, but I don't want to lose my existing installation of Vista if I can help it.[/SIZE]

if it lost side by side don't try a dual boot,must have something to do with the wubi ,

---

### Post by Kixtosh on 2012-02-06
malt loaf, did you notice this particular statement from oldfred earlier?
> **oldfred said:**
> ... Wubi uses the Windows boot loader to boot, so you do not install grub2's boot loader to the MBR like with a normal partitioned install. You do see the grub menu after you boot with Windows. The Windows BCD has both the entries for Windows and Ubuntu and the Ubuntu selection loads a grub menu.

You can install a Windows work alike boot loader from Ubuntu or use a Vista repairCD and use Windows commands to fixMBR. ...Have you tried to access your Windows recovery options installed by the original vendor from BIOS? This may be a special key combination, or a "Recovery" boot option. If your computer is a little bit older, it may have shipped with a Windows O.S. disk instead. Either of these methods (recovery partition, or O.S. disk) should allow you to get to the repair Windows options, and then, once you see a command prompt, type FixMBR (you may have to type "r" for "repair" first). Maybe if you list your computer brand and model somebody will be familiar with how this works for your particular computer.

Also, just a thought that might make your life a whole lot easier while you try to find a final solution: running Lucid Lynx from the LiveCD for more than ten minutes a day is a painful experience, including attempting to browse this forum, because of the constant need to access the LiveCD. To eliminate this scourge, you could download the ISO of Puppy Linux (or Wary Puppy, if your hardware is more than five years old), and burn that to a CD. It's not as large a download as most, and the advantage is that:

[LIST]
[*]It will give you a fully functional "emergency" operating system that will boot from a CD and load itself into RAM without using your hard drive at all.
[*]Does not require any boot menu to work: If the CD is in the drive, you can boot Puppy. If the CD is not in the drive, you can attempt to boot Windows/wubi. It's as simple as that. CD in or out, basically.
[*]Puppy does not require the O.S. CD after boot, so you can remove the Puppy O.S. CD from the CD drive after the desktop has loaded, and use the CD drive normally to burn or read other stuff if necessary.
[*]It will work as fast as a normal operating system on the hard drive, so you won't be crippled while using your computer while you're waiting to find a fix to your problem.
[*]You can still access your hard drive partitions if necessary, and save your sessions and/or settings as well.
[/LIST]
The ISO download size is about 130 MB, so you'll need to be able to at least store that somewhere until you can transfer it and burn it on another machine if necessary.

---

### Post by malt loaf on 2012-02-06
kixtosh, thanks for that.  I tried the suggestion from oldfred but ran into problems.  I'm still trying to fathom it out but I think I need to work out how to use chroot before I do some of that stuff.  I've also tried all the obvious windows recovery stuff and nothing so far.  I think the bcd is not set up right but I think I'm close to sorting it.

You're not wrong about the pain of running off the live cd, and I will look more closely at your suggestion of Puppy Linux tomorrow as I'm too shattered tonight.  Been at this all day long without a break.  Thanks again, will post back progress.  Keep your eye on the thread if it's no trouble.

---

### Post by oldfred on 2012-02-06
I do not think I have seen instructions to chroot into a wubi install. That is not a partition but a file inside the NTFS partition. Only if you also have a full partition install can you follow the standard chroot instructions.

Boot script or Boot-Repair should run from liveCD.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. M

---

### Post by malt loaf on 2012-02-07
[SIZE=2]oldfred, thanks for those ideas[/SIZE][SIZE=2].  I'll back off the chroot thing.

Did you see my post #11 (I think) where I described some problems I got trying to run bootscript[/SIZE]? [SIZE=2] If I try again[/SIZE], [SIZE=2]is it possible that I'll cause any damage?[/SIZE] [SIZE=2] I'd like to post the info but I'm a bit nervous of what happened last time.

kixtosh, looking at Puppy, will I be able to burn the ISO to CD when I'm running off the live cd in the first place?  Or does that depend on the burner software?
[/SIZE]

---

### Post by oldfred on 2012-02-07
Often Linux will not mount a NTFS partition that needs chkdsk to prevent damage that chkdsk then may not be able to fix. Have you run chkdsk. The risk then is if chkdsk does something to the wubi.root file.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can mount the wubi file (if you can mount the NTFS partition). So you can copy your data.

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

### Post by malt loaf on 2012-02-07
[SIZE=2]Thanks for all the suggestions.  I'm going to mark this as solved now since I have backed up the few files that were not already backed up and deleted the ubuntu folders from c:

It's now a purely Windows problem and I'll look to other forums.  I've learned a lot about Ubuntu anyway!!!
[/SIZE]

---

### Post by Kixtosh on 2012-02-07
> **malt loaf said:**
> [SIZE=2]... [/SIZE][SIZE=2]kixtosh, looking at Puppy, will I be able to burn the ISO to CD when I'm running off the live cd in the first place? ...[/SIZE]If  you already HAD Puppy, then yes, since Puppy allows you to remove the  CD from the drive once the O.S. has booted. Running Ubuntu from a  LiveCD, I don't think so, unless you have two CD drives (but there may  be ways to do so). Maybe you can borrow an external (USB) CD drive with  write capability, and use that with your LiveCD. Otherwise, if you can  save the 130 MB file onto any external drive, then you could burn the CD  from the image file on any other computer. You'll need appropriate  software for burning image files (not just copying them), but that's  freely available for both Linux and Windows.

Out of interest, when you boot your LiveCD and open GParted, can you  see the boot partition on your hard drive, and does it have a "boot"  flag set correctly? Below you will find a GParted screenshot of my  Compaq laptop hard drive. You can clearly see:

[LIST]
[*]/dev/sda1: a  small partition at the "start" of the drive, or the far left of the  graphic representation. This has SYSTEM label, and is the ONLY partition  with a "boot" flag.
[*]/dev/sda2: the main Windows 7 partition (since this is a dual boot laptop).
[*]/dev/sda3:  at the bottom of the list, and the far right of the graphic  representation. This has a RECOVERY label, and is the partition  installed by HP to return the laptop to it's out of box state with the  need to use recovery disks (which I did burn when I first turned on the  laptop).
[*]/dev/sda4: a "locked" partition, and an extended partition, containing the main Ubuntu partition and the Swap partition.
[/LIST]
Which of your partitions shows as "boot"? Can you take a screenshot from the LiveCD and post it up here?

 ny external drive, then you could burn the CD from the image file on any  other computer. You'll need appropriate software for burning image  files (not just copying them), but that's freely available for both  Linux and Windows.

Out of interest, when you boot your LiveCD and open GParted, can you  see the boot partition on your hard drive, and does it have a "boot"  flag set correctly? Below you will find a GParted screenshot of my  Compaq laptop hard drive. You can clearly see:

[LIST]
[*]/dev/sda1: a  small partition at the "start" of the drive, or the far left of the  graphic representation. This has SYSTEM label, and is the ONLY partition  with a "boot" flag.
[*]/dev/sda2: the main Windows 7 partition (since this is a dual boot laptop).
[*]/dev/sda3:  at the bottom of the list, and the far right of the graphic  representation. This has a RECOVERY label, and is the partition  installed by HP to return the laptop to it's out of box state with the  need to use recovery disks (which I did burn when I first turned on the  laptop).
[*]/dev/sda4: a "locked" partition, and an extended partition, containing the main Ubuntu partition and the Swap partition.
[/LIST]
Which of your partitions shows as "boot"? Can you take a screenshot from the LiveCD and post it up here?

---

### Post by malt loaf on 2012-02-07
Yeah, /dev/sda1 is set as boot.  That is the C: partition with the OS on it.

---

### Post by malt loaf on 2012-02-08
Well, I narrowed it down a bit further to the BIOS not recognising the HD. Why this should have suddenly happened is a mystery since there is clearly nothing wrong with the drive. This was not the initial problem actually since the problem started out with a Windows Boot Manager screen saying Windows failed to start.
 
At some stage, this became a "Disk Read Error" message on boot up.
 
Anyway today I ran TestDisk again. Had previously run it and got back something or other but still would not boot. Anyway this time on rebooting I got back the Boot Manager screen saying Windows failed to start. This time I went through to the Windows recovery disk and after about 6 reboots the Vista installation is working perfectly again. How flaky is that? Along the way I've deleted Ubuntu (wubi). Any views on what would be the most secure and safe way to do a clean install of Ubuntu now?
 
Thanks to whoever recommended TestDisk, or maybe I just found it on another forum or thread? Thanks for all the ideas anyway. I'd never have got there without all the nudging along.

---

### Post by oldfred on 2012-02-08
I would shrink Windows usinig the MMC in Window and then I would do a full backup of  Windows. Reboot several times for Windows to run its chkdsk or other fixes it needs on a resize. NTFS needs lots of free space or about 30% so do not shrink too much. 

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)


Then you can do a full install to partitions. You need to create an extended partition to hold the extra logical partitions needed by Linux.

Lots of details on dual boot installs:
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by malt loaf on 2012-02-08
Great, thanks for that.  Plenty to study and think about.  Will try to do it right this time.  I think wubi may have been a mistake...

---

### Post by Kixtosh on 2012-02-08
Thanks for the updates on your epic adventure, malt loaf! What a mess, though ... and who would have expected the hard drive to suddenly stop being recognized by BIOS?

Just to add to what oldfred mentioned, be certain to shrink your Windows partition using Windows, not Linux tools. It's really easy to do, and I've done it myself on a couple of laptops. But before you do that, and in case it's not mentioned in those guides oldfred suggested, I would run the disk defragmentation tool in Windows about three times (it goes much faster each time after the first).

Dual boot with Ubuntu is a simple way to run Windows alongside Linux, which is what oldfred is suggesting, I think. It does work well, and I soon found myself using Ubuntu about 95% of the time. Ubuntu shuts down so fast (three to five seconds, depending on which laptop I'm using), that it's not a big deal when I eventually want to boot Windows up. If you do it this way, every time you boot Windows, you'll find it all shiny and tidy (less a few updates or virus definitions, perhaps), with fewer bugs than before. Ubuntu won't interfere with your Windows installation in any way, and if you do all the scary stuff, casual browsing, e-mails and any identity theft sensitive stuff with Ubuntu instead, you'll find Windows shouldn't give you any trouble in the future. It won't slow down so much as before, and it won't start behaving oddly for some unknown reason, so you'll get to use it properly for what you really need it for. At least, that's my experience.

In terms of space, Ubuntu can take up so little space when necessary that 10 GiB is plenty of room, if  you don't save many large files to the main hard drive, so you can leave  all the space you need for Windows. In my case, 50 GiB was a bare  minimum for Vista Business or W7. If your hard drive has plenty of  space, I would give Windows 100 GiB to breath. I run one laptop, with a small Solid State Drive, with just 5 GiB for Ubuntu and 2 GiB for Swap. It runs perfectly and the O.S. has never taken up more than 3 GiB after months of usage. In either case, you always have the option of using external storage such as USB flash drives or SD cards for documents and large downloads.

---

### Post by malt loaf on 2012-02-09
Kixtosh, thanks for that information. I will do what you suggest, but I will order a new pc in the next month. Will try to set up the present laptop as described by yourself and oldfred, then if all goes well and I'm happy with it, will do the same on the new machine, although that will have Win7. I'm doing nothing whilst I only have the one pc..............
 
One of my issues is a good email package for Ubuntu, any recommendations? I use Windows Mail at the moment because I don't like webmail, but of course that particular app is a big malware target.
 
Sorry for apparent big delays in response, but my location is Greece so there is quite a big time difference with West Coast.
 
Oh, one other question.  I have a grub folder in c:\boot  I think it can be deleted now that I manually deleted the Ubuntu folders and no longer dual boot?  Is that right?  I would rather have a totally clean environment to install into when the time comes.

---

### Post by oldfred on 2012-02-09
If you have Vista or Window 7 you may have a /Boot with the BCD in it. You have to be careful not to delete that. But any /boot with grub should be deleted. Windows will not work with both /Boot & /boot as it is not case sensitive so they are the same.

I like Thunderbird for email. I installed it years ago in XP. After installing Ubuntu and my wife wanting to check email & use web, I found I could move the Thunderbird & Firefox profiles to a shared NTFS partition and have all the same mail & bookmarks in both systems. Then we stopped booting into XP a lot less.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by malt loaf on 2012-02-09
I've renamed the grub folder that lives in C:\boot, and if nothing nasty happens will delete it in a few days.  I don't think it's anything crucial, just seems to be mainly video clips with a .mod extension.  No idea what they are; Win Media Player does not run them.
 
So I can use Thunderbird under Windows or Ubuntu?  How does a shared partition work?

---

### Post by oldfred on 2012-02-09
You have to create a separate NTFS partition. Windows will see it as d:.
In Ubuntu you create a mount point and permanently mount it with fstab. 

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by malt loaf on 2012-02-09
OK, understood.  Now I just have to find time to read all your links properly....
 
Your time is much appreciated.

---


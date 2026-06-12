---
title: "When installing ubuntu &quot;alongside Windows&quot;, and possible disk recovery."
date: 2016-03-12
forum: New to Ubuntu
---

### Post by Daxter_Xen on 2016-03-12
[INDENT=6][COLOR=#a9a9a9]Hello, I am an Ubuntu noob, and recently I tried installing it on my PC as an alternative to my (still installed) Windows 7. My current hard disk setup is: one **64 GB SSD** with Windows installed, one **250GB HDD **with Ubuntu and loader installed (on top of formatted old files in Windows format), and a **1 TB HDD**.[/COLOR][/INDENT]
[INDENT=6][COLOR=#a9a9a9][FONT=arial]When installing, my intention was to install Ubuntu as an option when booting. When I prepared the installer (burning the .iso of Ubuntu 14.04.4 into a DVD and booting it), I chose "Install alongside Windows 7" and went with it. The result was, without me being asked (or without me noticing I was asked) my **250GB **drive was used for the installation, and right now that drive is inaccessible from Windows, considered the main drive in Ubuntu, and apparently has been wiped... (other than that, the installation was a success btw)

  Point 1. : Have my files been fully deleted? Is there a way to recover them? Or should I learn to cope with loss in life and move on?
  Point 2. : I am aware that there was the option "Other" during installation for the sake of manually making partitions, but am I mistaken in believing that maybe, more details about the exact way each option worked, were in order? I don't remember being asked which drive to install Ubuntu on, and since there were multiple ones, and the system chose one without it being the main Boot one, how did it decide on which? Where exactly did I go wrong/what did I miss?

Bonus point : Can you please explain or redirect me to, what exactly did that "alongside windows" option do? As in, "it takes one partition at random/first in order/smallest, wipes it, installs Ubuntu, and sets it so that on startup the Ubuntu tool runs for you to choose whether to run Ubuntu or load Windows".

   Thank you in advance for any help.
[/FONT][/COLOR][HR][/HR]^ Old post

[FONT=arial]tl;dr : Installed Ubuntu on a drive, over files in Windows format (still have Windows on another drive), realized I was a dunce, want to recover my old files in an efficient manner.[/FONT][/INDENT]
[COLOR=#a9a9a9][FONT=arial]
[/FONT][/COLOR][FONT=arial]Alright, things happened, couldn't look into the matter (holy **** it has been almost 2 months... wow), but I returned, and I have done some (though minor) looking around concerning my problem. The result is this: 
[/FONT][INDENT][FONT=arial]I have learnt my lesson, and intend to install Ubuntu properly after this all is over. For now, I am looking for a way to recover my data. 
[/FONT][/INDENT]

[LIST]
[*=1][FONT=arial]It is a fact that those files exist (are not entirely wiped), since I found a file recovery program, intended for use on recovering deleted files, which I used to scan my entire drive (while using Windows), copying all its recovered contents in a place in my third drive. What the program returned was, many of my files (jpgs, bmps, txts, mp3s, etc.), in random order (probably in order saved on the disk), along with Ubuntu files (.gzs mostly noted). In short, as I expected, the files are there, waiting (probably a few will be corrupt but that's fine).[/FONT]
[/LIST]
[INDENT][FONT=arial]So, right now, I am asking this: 
[/FONT][/INDENT]

[LIST]
[*=4][FONT=arial]Is there a way to explore that drive (one which is formatted in Ubuntu) from Windows, with Windows expecting to find file pointers? (my headcanon ideal expected result is setting the disk's format to the previous one, Windows finds that the disk has data, is able to read it, with a portion of it being unfortunately corrupt.)[/FONT]
[*=4][FONT=arial]Are there other "if"s in the way? (e.g. file pointers being stored in a specific part of the drive, possibly being overwritten by Ubuntu therefore all is lost)[/FONT]
[*=4][FONT=arial]If the answer to the previous two is "no", then what alternatives exist?
[/FONT]
[/LIST]
[INDENT=6][FONT=arial]
[/FONT]
[/INDENT]
[FONT=arial]Once again thank you in advance for any help.[/FONT]

---

### Post by oldfred on 2016-03-12
I thought the along side option used unallocated space or shrank largest NTFS partition to make unallocated space and installed. But with multiple drives have no idea what logic it is using. Because of that, many of us partition in advance with gparted.
Do you still have the NTFS partition? It often needs chkdsk from Windows to be working.

For an install always best to use Windows to shrink the NTFS partition. While partitioner usually works some have reported issues. And Windows always needs chkdsk after a resize.

And with multiple drives, best to use Something Else. That is the only option that also lets you choose where to install grub2's boot loader. You normally want boot loader on same drive as install. So keep Windows boot loader on Windows drive and grub boot loader on Ubuntu drive. And since grub will also let you boot into Windows, set BIOS to boot Ubuntu drive.

We link to many install instructions for one drive, or multiple drives. Many new users only have one drive and do not even know what a partition is, so auto install is often easier choice for them.

Is system newer UEFI boot or older BIOS boot?
       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

      [/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/) 

[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]
[/URL] 

    [URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by yancek on 2016-03-12
The Install Alongside is basically an auto-install option and generally works on a very simple situation, one other OS on one other drive.  If you have another operating system and multiple hard drives you need to select the Manual option.  On recent Ubuntu releases, this is called "Something Else".   I assume you actually used a DVD as the Ubuntu iso is much too large to put on a CD.  Given the fact that you have three physical hard drives, I'm not sure how you expected the installer to know you wanted to use the 250GB SSD.  I think the only circumstance in which that might work is if the other two drives were full or there was no unallocated space.  If you want the system installed to a specific location on a specific drive, then you need to make that selection.  Computers aren't that smart.  They are fast and very obedient.
 
The drive on which you have installed Ubuntu is inaccessible from windows because a default windows system is totally incapable of reading or writing to a Linux filesystem.  The only place it will be seen is in places like your windows Disk Management where it will probably show as Healthy Drive and nothing more.  That's standard behavior for windows.  I'm not sure what the problem is other than Ubuntu wasn't installed to the specific drive you wanted it to be installed to.  Did you have data on an ntfs partition?  I expect it is still there and posting the output of fdisk should tell us that.  

Boot the Ubuntu medium and open a terminal and run the following command and post the output here.  This will show if there are any windows partitions to start:  sudo fdisk -l(Lower Case Letter L in the command)

Read the extremely detailed link below on installing Ubuntu 14.04, on Linux in general and if you scroll down, dual booting with windows.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Daxter_Xen on 2016-03-12
> [COLOR=#000000]I thought the along side option used unallocated space or shrank largest NTFS partition to make unallocated space and installed. But with multiple drives have no idea what logic it is using. Because of that, many of us partition in advance with gparted.[/COLOR]
[COLOR=#000000]Do you still have the NTFS partition? It often needs chkdsk from Windows to be working.[/COLOR]

[COLOR=#000000]For an install always best to use Windows to shrink the NTFS partition. While partitioner usually works some have reported issues. And Windows always needs chkdsk after a resize.[/COLOR]

[COLOR=#000000]And with multiple drives, best to use Something Else. That is the only option that also lets you choose where to install grub2's boot loader. You normally want boot loader on same drive as install. So keep Windows boot loader on Windows drive and grub boot loader on Ubuntu drive. And since grub will also let you boot into Windows, set BIOS to boot Ubuntu drive.[/COLOR]

[COLOR=#000000]We link to many install instructions for one drive, or multiple drives. Many new users only have one drive and do not even know what a partition is, so auto install is often easier choice for them.[/COLOR]

[COLOR=#000000]Is system newer UEFI boot or older BIOS boot?[/COLOR]
[COLOR=#000000]But may be best to see details:[/COLOR]
[COLOR=#000000]Post the link to the Create BootInfo summary report. Is part of Boot-Repair:[/COLOR]
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

[/URL]
[COLOR=#000000]Lots of detail, screenshots and essential info.14.04 Something Else example[/COLOR]
[http://www.dedoimedo.com/computers/u...all-guide.html]("http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html")
[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation
[/URL]
[COLOR=#000000]Any install with Something Else which is required with external drives or any second drive or any install with separate /home[/COLOR]
[COLOR=#000000]Also shows combo box with location of grub2 boot loader[/COLOR]
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[COLOR=#000000]Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:[/COLOR]
[http://askubuntu.com/questions/31278...in-a-dual-boot]("http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot")
[http://askubuntu.com/questions/27437...p-boot-optiond]("http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond")
[COLOR=#000000]Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)[/COLOR]
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
[COLOR=#000000]And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install[/COLOR]
[https://help.ubuntu.com/community/Gr...ing_Else.22.29]("https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29")[COLOR=#000000]:[/COLOR]
[COLOR=#000000]Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI[/COLOR]
[http://www.linuxbsdos.com/2012/07/23...2-hard-drives/]("http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/")[COLOR=#000000] [/COLOR]

Thank you very much for all the info. If I am to pinpoint my problem, it would be that I simply didn't understand that the option I chose was the "Default/Recommended/Automatic" one, instead clicking away when my eyes saw the phrase "manually down the road", without looking into things enough. Having half knowledge and pseudo-experience on the matter made me be rash and I guess that I missed something. 
I do not have time to look into the issue right now, but I will make sure to look through what you've given me and update this post if I need any help. I am not marking it as [SOLVED] yet, so that I may return, just in case. Thanks again and I will be back.

---

### Post by Daxter_Xen on 2016-03-12
> [COLOR=#000000]The Install Alongside is basically an auto-install option and generally works on a very simple situation, one other OS on one other drive. If you have another operating system and multiple hard drives you need to select the Manual option. On recent Ubuntu releases, this is called "Something Else". I assume you actually used a DVD as the Ubuntu iso is much too large to put on a CD. Given the fact that you have three physical hard drives, I'm not sure how you expected the installer to know you wanted to use the 250GB SSD. I think the only circumstance in which that might work is if the other two drives were full or there was no unallocated space. If you want the system installed to a specific location on a specific drive, then you need to make that selection. Computers aren't that smart. They are fast and very obedient.[/COLOR]

[COLOR=#000000]The drive on which you have installed Ubuntu is inaccessible from windows because a default windows system is totally incapable of reading or writing to a Linux filesystem. The only place it will be seen is in places like your windows Disk Management where it will probably show as Healthy Drive and nothing more. That's standard behavior for windows. I'm not sure what the problem is other than Ubuntu wasn't installed to the specific drive you wanted it to be installed to. Did you have data on an ntfs partition? I expect it is still there and posting the output of fdisk should tell us that. [/COLOR]

[COLOR=#000000]Boot the Ubuntu medium and open a terminal and run the following command and post the output here. This will show if there are any windows partitions to start: sudo fdisk -l(Lower Case Letter L in the command)[/COLOR]

[COLOR=#000000]Read the extremely detailed link below on installing Ubuntu 14.04, on Linux in general and if you scroll down, dual booting with windows.[/COLOR]

[http://www.dedoimedo.com/computers/u...all-guide.html]("http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html")

To clarify where I stood: 
I misunderstood the fact that Alongside is an auto-install due to my own mistakes, believing that I would get more options despite the fact that it was a one-click "Install now"... Don't ask, no logic there. 
Thanks for pointing out the CD-DVD matter, had slipped my mind, fixed it.

Thank you for your answer and info, I will look further into the matter soon. Sorry for your time, have a good day.

---

### Post by oldfred on 2016-03-12
Some of the auto install options can be real dangerous.
The LVM full drive install option with encryption means an entire hard drive. Many Windows users have mistaken drive as Windows calls c: "drive" and users wanted to keep d: "drive" which was on same disk.

Some have filed bug reports, but programmers say it works exactly as designed so not a bug. But not clear to non-Linux users. They have improved descriptions somewhat.

---

### Post by Daxter_Xen on 2016-05-02
Bumping my thread since I have edited new data into my first post.

---

### Post by oldfred on 2016-05-02
Install issues & file recovery should really be a separate thread. There are many posts on that topic also. And we are primarily an Ubuntu forum but do have sub-forums on other versions of operating systems.

But some of us dual boot, and I have saved a few links on recovery. It seems you used photorec. I have used it and it took me weeks to sort thru files and rename correctly. Photos can easily be renamed as file had internal date info.

An alternative Windows data recovery program is Recuva -- and it is free
 [http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---


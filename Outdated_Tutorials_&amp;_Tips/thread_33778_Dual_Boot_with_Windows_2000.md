---
title: "Dual Boot with Windows 2000"
date: 2005-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by iainm2 on 2005-05-12
Hi
Thought that I should share this with you. I followed [http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo) with partial succes but lost the ability to boot into Windows. Ubuntu worked fine.
So, did some more research and found an item relating to dual booting and Symantic (now Norton) Partition Magic. Included with Partition Magic is a product called BootMagic. Partition Magic can be purchased for as little as £9.99 on Ebay currently so the outlay is not high. 
First, install Windows 2000 as normal or drop a saved image onto the hard disk.

Now install Partition Magic in Windows 2000 - make the recovery disks just in case!
.
Install BootMagic making sure that windows can be selected- make the recovery disks, you will need them later.

Create the partitions as suggested in [http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo) using partition manager. The only addition here is to make an extra 50Mb FAT partition for BootMagic.

Follow the instruction in the how to to set up Ubuntu - Step 4 is IMPORTANT - make sure that you do not let Grub install in the MBR, it must go in your linux partition..

When the computer reboots, after completing the first stage of Ubuntu install, boot from the floppy disks created by BootMagic and follow the on screen instructions to add a linux operating system to the menu. It only needs to know which partition linux lives in.

Reboot the computer normally and you will have a choice of Windows 2000 or Linux. Select Linux, Grub will start and after the default number of seconds will boot into Ubuntu where the installation is completed.

You are now in possession of a computer which will boot windows or Ubuntu. The above is nothing like as complicated as it sounds and it does work. I am not an expert but just reasonably competent with Windows. I like Ubuntu and wanted to be able to have my cake and eat it as Ubuntu has been the most user friendly linux distro which I have tried. Many thanks.

---

### Post by lightyear on 2005-05-16
I installed Xp, and than Ubuntu on a different partition and it automatically created a bootmanager where you can choose between ubuntu and windows xp...no partitionmagic or whatsoever.  Only downside is that you have to be quick in choosing your operating system... Trying to work out if i can change the duration before it loads the default os and if you can change the default os to xp...

---

### Post by GuitarGuru on 2005-05-25
[QUOTE=lightyear]I installed Xp, and than Ubuntu on a different partition and it automatically created a bootmanager where you can choose between ubuntu and windows xp...no partitionmagic or whatsoever.  Only downside is that you have to be quick in choosing your operating system... Trying to work out if i can change the duration before it loads the default os and if you can change the default os to xp...[/QUOTE]
 I did the same thing as lightyear and it worked purfectly, but make sure to install windows first otherwise you will have to reformat your harddrive and do it again.

---

### Post by stax on 2005-06-10
Hi,
I thought it'll likely be painless for a newbie installing first Win2k and after that Ubuntu letting the Win2k installer create the Win2k partition and letting the Ubuntu installer create the Ubuntu partition. I expected this is a common operation and therefore likely won't get me into trouble. Apparently I was right as everything was straightforward and worked perfectly. My problem now is I want to change the default OS to windows. When I understood right then grub was installed in the MBR. I would like to know in which directions I have to research, which tools and skills will I need and where do I start?

---

### Post by CoriolisSTORM on 2005-06-10
Okay guys, I'm quite new here, so I figured some of you could help me.  I have Windows XP on my C partition, and a recovery partition on my D partition.  Now, my file system is NTFS, so how would I go about setting up another partition in order to install Ubuntu on it without losing data?  From what I've used on the liveCD, I love it, but its lacking just using that.  I have no backup CDs  (its a prebuilt, and HP's little program to make them doesen't work) or partition managers of any kind.

---

### Post by pizzigati on 2005-06-13
This isn't to answer your main question, C.Storm, but about the failure of your HP to make the windows recovery CDs reminded me of a similar situation I had with a new Dell just recently (the day before yesterday, in fact). I would get through most of the Dell program to make the recovery disk, it would start burning the disk and then about 1/2 way through, it would say, sorry, burning failed. So, I removed all the bloatware on the machine (particularly Norton Armageddon Protection), tried again, and voila. 

About installing Ubuntu dual-boot, it seems to me you have two choices (assuming the whole disk is being used by NTFS partitions essential to Windows. 1) Mess around with a partitioning program to shrink your main Windows NTFS partition to leave some space to put a Ubuntu Linux partition. Or, 2) Uninstall Windows, and when reinstalling (with your successfully created recovery disks :-), leave a good chunk of blank space on the disk, to later format and occupy using the Ubuntu installer.

Option 2 would be my choice, but that's just because I fried a good chunk of a harddisk with a Linux partition shrinking program just because I forgot to Windows chkdsk after I Windows defragmented.

---

### Post by yeswings on 2006-04-20
I have an old compaq. I tried to install windows 2000 but no way . When I installed ubuntu it loaded just fine but now I still want to dual boot Win 2000.
Any ideas that will help me out?
thanks 
yeswings@excite,com

---

### Post by jhpace1 on 2007-07-04
A clarification to iainm2's post:

Computer: Asus P4PE with 3 SCSI hard drives (9gb, 18gb, 18gb), IDE LS-120, and IDE DVD-DL-R/W.
OS: Windows 2000 SP4
Ubuntu 7.04 Fiesty Fawn install CD
Partition Magic 7.01 with BootMagic
You will need four 1.44MB 3 1/2-inch floppy diskettes for this.

Sources: (this web page, thanks iainm2!)
[http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo)
[http://linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=4038&start=0&postdays=0&postorder=asc&highlight=](http://linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=4038&start=0&postdays=0&postorder=asc&highlight=)
[https://help.ubuntu.com/community/WindowsDualBoot#head-6852d2e9b3e03d350a4271b58e3bdea4bbe81ad8](https://help.ubuntu.com/community/WindowsDualBoot#head-6852d2e9b3e03d350a4271b58e3bdea4bbe81ad8)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

1. Install Windows 2000 onto your hard drive.  You can either pre-partition using DOS's fdsk command, or just let Win2k take the entire hard drive.  I formatted to NTFS because of the new Ext IFS.  Let Win2k take the entire hard drive (aka primary partition) for itself, it's not a problem.

2. After you get Win2k up to SP4 with all the Microsoft updates, install Partition Magic.  Create a 50MB partition that is FAT16 on the same hard drive as Win2k (usually the 1st hard drive).  Partition Magic will automatically put the new partition at the front of the "C:/".  Be sure to create the two recovery diskettes, you WILL need these later! The computer must reboot and use what I call the "black Win2k inbetween window" during bootup to make the partition.   After another reboot, you will go back to Win2k.  Make any other non-Linux partitions you want and rearrange the drive letters as needed.

3. Install BootMagic.  If you try to install BootMagic before this, the program will complain that it cannot find a FAT16 or FAT32 partition, that's why you had to make a separate partition first.  BootMagic will read your Win2K as well as give you a "95/98 DOS prompt" (haven't tried this yet).  Make the BootMagic recovery disk.  Reboot a few times to see the BootMagic startup screen as you go into Win2k.  Make the Windows 2000 Emergency Repair disk with registry backup now from within Windows 2000.

4. Put the Ubuntu CD-R in the DVD/CD drive and reboot.  Ubuntu _should_ come up, I had to use the "Startup/install with safe video" option.  Fiesty Fawn 7.04 has a 7-step installation process.  (I had to click on the "install" drive to get it started.) What you need to do is use the Manual partitioning, not the Guided option.  Go to your empty hard drive or partition where it says there is nothing there (free space or empty).  Click and start making your partitions according to [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) or your own preferences.  You have to go back and tell Ubuntu which ext3 partition is root, which is /home, make the swap partition, etc.  Check the checkbox to make sure a format is done on the new partition.

5. Grab a pencil and a sheet of paper and write down those partitions on the screen when you are done.  These are the ones I have:

/dev/sdb  hd0
/dev/sdb2
/dev/sdb1
free space

/dev/sdc hd1
/dev/sdc1
/dev/sdc2
/dev/sdc3

/dev/sdd hd2
/dev/sdd1

Notice that each physical hard drive gets a "hd_".  This is important.  My Win2k NFTS is on sdb2, while BootMagic is on sdb1.  Hd0 is 8.6gb, hd1 is 16.95gb, and hd2 is 16.95gb.  Sdc1 is root, sdc2 is /home, and sdc is my swap partition.  Sdd1 is my huge NTFS drive for writing 8.1gb DVD-DLs from.

6.  Continue with the 7-part install.  ON THE LAST STEP, there will be an "Advanced" button on the bottom right-hand side of the window on the screen.  Click it.  It will show the install directory as (hd0).  This is GRUB being installed over your MBR as the default. Change it to (hd_), which is (hd1) in my case.  That means, "No, install /boot and GRUB into the first partition on my 2nd hard drive, which is where my Ubuntu root is located.".  Now you can finish the installation and reboot, taking the Ubuntu install CD out of the CD/DVD drive.

7. BootMagic _may_ come up during this install.  You may get a crash instead.  Don't panic.   It's not your fault, it's GRUB's fault for not installing correctly.  But you don't need to make a GRUB floppy diskette or use SuperGrubDisk to "repair" the GRUB install.  You just have to tell GRUB where to go inside the Ubuntu install because you used a /root on a dual-boot instead of /boot on a single-OS system.

You will not be able to use the BootMagic recovery diskette because Win2k "hides" the FAT16 partition, leaving only the NTFS partition "active".  This is normal. Go into Win2k and run Partition Magic (you can't run BootMagic because of an error - cannot find partition).  Use Partition Magic to make the BootMagic drive non-hidden. Reboot, and BootMagic should let you into Win2k.  Inside Windows run Partition Magic and make sure the FAT16 partition is visible.  (This is a right mouse click ->Advanced option).  You should not be forced to reboot, close Partition Magic and go into Boot Magic.  Now you can Add the new Linux (ext2) partition on the hard drive as a new OS to BootMagic. 

You won't be able to use BootMagic yet to get into Ubuntu (your computer will hang, just reboot).  Your installation is stopped "halfway" with Ubuntu, and most of the web pages out there tell newbies like myself how to use LILO or GRUB to reinstall them on the MBR.  Don't do it.  The good news is that your Win2k is untouched by GRUB so your MBR is safe.  So you can keep going into Windows while you fix the problem.

8. While in Win2k install Ext2 IFS for Windows from [http://www.fs-driver.org/](http://www.fs-driver.org/).  Run the program, and add your new Linux partitions to Win2k's naming system (but don't try to add the swap partition, it will return an error and you don't need it anyway).  For my system I named them R:/ and S:/ for root and /home, respectively.  Now you can, using Win2k, check to make sure that there is a /boot/ on your root partition.  If you don't see anything, you may need to run Ubuntu from the beginning install again.

9. Shut down Windows and reboot with the Ubuntu CD in the CD/DVD drive.  Choose the first option, "Install/Start".  This will bring you into the same setup desktop as before.  But instead of clicking on the "install" icon, follow the directions in [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).  That is, open a terminal window and become root (type "sudo -i" in Ubuntu).  Some web pages have you check your drive listing at this point, but I found mounting the drives and mkdir them unnecessary.  Just do this terminal window as root. 
Type "grub" which makes a GRUB prompt appear. 
Type "find /boot/grub/stage1". You'll get a response like "(hd0)". Now type "root (hd_,_)", where the blanks match the drive and partition from what you wrote down while Ubuntu was formatting during the install (in my case,  (hd1,0) for 2nd drive, 1st partition).  Do NOT type "root (hd0)", or you will write GRUB to your MBR!
Type "setup (hd_,_)".  Make sure the (hd_,_) matches your Linux root partition (in my case, (hd1,0)).  You will then see:

grub> setup (hd1,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,0) /boot/grub/stage2 p /boot/grub/menu.lst"... succeeded
 Done.
grub>

Type "quit"
Close the terminal window and quit the Ubuntu desktop (you should get a black Ubuntu shutdown that has you remove the install CD and then shuts down the computer).  You have now finished the Ubuntu install.

10. Boot normally into BootMagic.  The "Ubuntu" option you made earlier should now work, and you get GRUB's boot window!  (And there was much rejoicing.)  Now to learn Ubuntu...  And my three Win2k hard drives appear as icons on the desktop, interesting...

Hope this helps people out there who were as frustrated as I was at midnight last night.  The solution this morning took about two more hours of research before I found [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) that was close enough to work.  Having my Windows install safe during the process did keep me from tearing my hair out while I looked for a solution.

Jeremy Pace
Graham, NC

---


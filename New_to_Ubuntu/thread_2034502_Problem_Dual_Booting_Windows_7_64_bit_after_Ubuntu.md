---
title: "Problem Dual Booting Windows 7 64 bit after Ubuntu 12.04 installation"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by Rjbcc58 on 2012-07-28
I am running a Dell XPS 15 Laptop with the following specs:

-------------------------------------------------------------------
XPS 15
3rd Generation Intel Core i7-3612QM processor (6M Cache, up to 3.1 GHz - TPM)
8GB, DDR3, 1600MHz
English Keyboard, 80 Key, L521X
Silver Anodized Aluminum and 15.6" FHD 1080p Truelife WLED Display and Skype-Certified HD Webcam
NVIDIA GeForce GT 640M with 2GB GDDR5 VRAM
Dell SRV Software for Intel Centrino Adv-N 6235
750GB 7200 HDD with 32GB mSATA
-------------------------------------------------------------------

I spent last night attempting to install ubuntu 12.04 to dual boot with windows 7. The machine all ready had windows 7 64 bit installed, and this was my first linux installation attempt (not including wubi).

I loaded ubuntu live from usb, and using gparted saw my harddrives setup as follows:

/dev/sda1/ fat16 size:39.29 mb Label:'DellUtility' Flags:'diag'
/dev/sda2/ ntfs  size:18.25 gb Label:'RECOVERY'    Flags:'boot'
/dev/sda3/ ntfs  size:696   gb Label:'OS'    

I partioned the 'OS' drive and freed up ~170 gb for my linux install. I made an extended partition that covered the 170gbs, and made logical partitions inside it as follows:

/dev/sda4/ extended   168.73 gb
/dev/sda5/ ext4        79.10 gb Label:'root'
/dev/sda6/ linux-swap   9.77 gb
/dev/sda7/ ext4        79.86 gb Label:'home'

This went through without any errors from GParted. Next I went to install Ubuntu on the new partitions. I set my 'root' mountpoint:'/' and my 'home' mountpoint:'/home'.

After a reboot windows 7 started up. I logged in first to see if I had any problems, which I did not. However after a second reboot I realized that Ubuntu was not showing up in the (My understanding of this may be incorrect but...) 'Windows bootloader.'

My solution was to boot again to ubuntu live cd and install the 'grub' bootloader from the terminal window. I am new to Linux and may have been ignorant in running commands I found on forums to install this bootloader, but after rebooting I was presented with my new ubuntu 12.04 installion. This loads up fine, but the issue I am now facing is that Grub does not list Windows 7 as a bootable option.

I have searched extensivey on how to fix this and many have pointed to windows system recovery options. I have booted from a windows 7 installation disc and attempted to do fix via bootrec.exe and commands like /FixBoot /FixMbr etc. I cannot seem to get any of these commands to even run, as they return 'The system could not find the path specified'.

It is definitely noteworthy that bootrec /scanos finds 0 installations. As well as the windows prompts that come before the option to launch command prompt in the windows recovery options also shows no operating system.

I read that I may not be on the correct partition or drive at the windows recovery screen so I also attempted to change this via DISKPART in command, but trying the commands 'list disk' 'list drive' or 'list vdisk' all say 'no fixed *disc* found' or something like that.

I have tried simply going through the windows screens but they seem to fail without a doubt.

I am really stuck at this point and would appreciate any help. If anything I have said needs to be clarified (I'm a newb I apologize) please ask or I can provide screenshots to show my processes as well.

Thanks!

---

### Post by oldfred on 2012-07-28
You may have installed grub2's boot loader to the Windows partition, not the MBR of the drive. Windows has to have a NTFS boot signature in the boot sector as it has more boot code there.

To confirm what is where post link from running BootInfo from this:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by Rjbcc58 on 2012-07-28
I believe you are correct and I have installed grub in the wrong partition.

Bootinfo gives me this: [http://paste.ubuntu.com/1116403/](http://paste.ubuntu.com/1116403/)

Running the repair returns an error and this: [http://paste.ubuntu.com/1116403/](http://paste.ubuntu.com/1116403/)


Edit: Can anyone suggest a fix? I am a bit unclear on the steps I need to take.

---

### Post by oldfred on 2012-07-28
Script has issues mounting sda3 & sdb1. Did you do something to both? Normally the error show grub installed similar to as script shows MBR. 

It may be recoverable if only installed once. This is for grub installed to NTFS partition, but is the procedure to use testdisk to find the backup partition boot sector and recover that. If backup is damaged testdisk can create a "basic" NTFS partition boot sector. The one it creates seems to work with XP but Windows 7 seems to often need more repairs, but will then work. When NTFS partition boot sector is corrupted often Windows 7 will not run its repairs.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)


[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Do you have a Windows repairCD?

---

### Post by Rjbcc58 on 2012-07-28
I have not made any changes to sdb1, to be honest I was confused at what my sdb drive actually was, would this be the 32 gb mSata?

I am trying the steps listed in your links now and will post my results.

I do not have a 'Windows Repair CD,' I am using a Windows 7 installation disc and selecting 'repair computer.' This is how I was getting to the command prompt and attempting the bootrec commands.

Thank you for you help, I really appreciate it!

Update: I do not have the 'BackupBS' option in step 6, I.E. " If the sixth screen did not have a "BackupBS" tab, it usually means that the original and backup boot sector are identical, and you are probably suffering from a different problem."  

It suggests I use the /FixBoot commands that I have been struggling with. Will a windows repair cd fair better than the windows 7 installation cd I have now? Are these separate things?

---

### Post by oldfred on 2012-07-28
Often the fixBoot command from Windows does not work as it does not see it as NTFS. 

Use testdisk and the ReBuild BS or make a new boot sector for NTFS. 

But I found that there are at least two versions of NTFS boot sectors. I used my Windows 7 repair CD to run chkdsk on my XP install which did work better than the XP version. But it wrote a new BS - Boot sector. In testdisk (Dump) I could then see the difference. Structure was different and the XP version had ntldr and the Windows 7 version bootmgr to boot with (about the only part that was text).

So create a NTFS BS from testdisk, then run the fixBoot command from windows to convert to Windows 7.

---

### Post by Rjbcc58 on 2012-07-28
Okay so I have run 'Rebuild BS' which brought me to the image that you provided in your previous post. I was able to reboot into repair mode and run the fixboot command, however now I am shown the 'Windows failed to start. a recent hardware.....' on the file: \Boot\BCD , Status:0xc000000f

I can no longer run the fixboot commands from the command prompt window now, and the grub bootloader which brought me to my Ubuntu install previously is now gone. I am not sure if I 'created' another NTFS BS correctly, the testdisk program told me it overwrote the MBR on the disk which is when I saw these changes on boot.

Any idea what's next? :/


UPDATE: I have booted Ubuntu live from usb again it appears things have gotten worse... Looking at Gparted shows my harddrive is back to how it was when I originally started. Its as if I never installed Ubuntu. I have tried running a boot-repair, and it returns the rather scary message 'No OS found on this computer.' Boot info gives this: [http://paste.ubuntu.com/1116655/](http://paste.ubuntu.com/1116655/)

---

### Post by oldfred on 2012-07-28
The old report said one of the possibilities was RAID. You now are showing one RAID drive. Did you install with RAID? Was drive ever part of a RAID drive set? Or did you at some time turn RAID on in BIOS? 

Is this what you have?

 Intel Smart Response Technology.
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

### Post by Rjbcc58 on 2012-07-29
I do have the Intel Smart Response Technology as described in your link,  I am not sure exactly what my drive was or whether I had altered that previously. I was able to switch IRST off from BIOS to ACHI. After  this I noticed an 'ssid' option on the BIOS menu, but the bootrec  commands still will not run, and Windows System repair does not recognize my OS

---

### Post by oldfred on 2012-07-29
Have you gone thru the commands the user in the link above did to fix his system?

If so, then post a link to a new run of BootInfo.

---

### Post by Rjbcc58 on 2012-07-30
From the thread you provided:

> **godgough said:**
> I have found a solution.

To get the Ubuntu live installer (normal version) to detect the drive, in the 'Try Ubuntu before Installing' option, open a terminal and try the commands on this page:  [https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID#Load_dmraid]("https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID#Load_dmraid").  I think all that is needed is 
# modprobe dm_mod
# dmraid -ay
# ls -la /dev/mapper/
Then you can open the installer in the Live session and install.

You must also go back to Windows and open the 'Intel Rapid Storage Technology' application and go to the 'Accelerate' Tab.  Disable acceleration (this will not lose any data but will automatically back up some data if you are using maximised option).  Then you should be able to restart into GRUB.  You may need to try reinstalling GRUB (Google it).  If the GRUB screen is present then you can go back to Windows and re-enable acceleration in 'Intel Rapid Storage Technology'.

Hope this works for everyone else.

Is this the solution you are talking about? I am at work right now but will be trying this when I get home, but I am trying to make an effort to understand what I'm actually doing here. Again, I apologize for any ignorance but can you explain some things for me:

What exactly will the above commands do? The OP states this will allow the Ubuntu Live installer to recognize my drive, and then install the full version. Is this what you would instruct me to do at this point?

I am concerned about the partitions I made (based on what I'm seeing in gparted on live usb) that simply 'disappeared', or more aptly, 'reverted' to the state the harddrive originally was before I began this trip down linux lane. Is my actual Ubuntu 12.04 install still there? Should I repartition and go through the same installation steps I originally did after running the above commands?

My next question is how exactly should I install grub afterwards? I think we have concluded that my original mistake was writing to the same drive windows was in... does that mean I wrote grub to the the OS partition on the sda? Or did i write it to the 'RECOVERY' partition? Where exactly does the 'MBR' sit? 

Thanks in advance for any responses, I am trying to learn as much as I can. I will be back at it this afternoon.

Edit: Typos, clarification.

---

### Post by oldfred on 2012-07-30
I guess the bottom line is, do you want to keep the Intel Smart Response or not. It seems that is some sort of RAID which I do not understand.

The previous user decided he did not want the Intel Smart response so he deleted the RAID. That then made two drives, one the SSD and the hard drive.

I am not a fan of RAID on most desktops. Before SSDs power users might use RAID to speed up system processes that were hard drive intensive like a compile of a kernel or major application. SSDs are now even faster. But you cannot type faster, nor is download faster, so most desktop use does not get faster. Also some think RAID is a backup, but it is not as if you delete a file it is still gone. We backed up our RAID servers at work every night on a daily, weekly, monthly tape rotation.

So I have a SSD to speed up booting & loading larger applications, but it still is a luxury for most things as they still run from RAM and that has not changed. I also like having multiple drives, but like having a different or another copy of a operating system on every drive, and each drive fully configured to boot without the other drive. Data then can be on either drive and system may complain if it cannot boot a data partition but will still boot.

---

### Post by Rjbcc58 on 2012-07-30
I think I understand a little better now. It sounds to me like the 32gb msata is not entirely necessary for me, however I was able to turn the 'RAID' off and switch it to 'ACHI' and it did not make any significant changes. I was able to see an 'ssid' along with boot to usb, boot to cd drive, etc. at loadup, but that was about the only change I noticed.

As for my other questions though do you have any idea? 

I already partioned my drive, and then I already installed Ubuntu and confirmed this via gparted and boot-info, so is it normal for these to totally revert like they'd never happen, after simply rewriting the MBR (I believe rewriting the mbr from testdisk was what caused this). Likewise, is it concerning that boot-repair tells me 'no OS found'...?

I must stress again I am a beginner so I basically looking for baby steps to get my machine working again.

---

### Post by oldfred on 2012-07-30
I would not think testdisk would rewrite the partition table without the Linux partitions unless you specifically selected only  the old partitions and then told it to write a new partition table.

We have seen Windows (Vendor's) recovery partition in just starting rewrite partition table and then had to use testdisk to recover old table, but sometimes the vendor recover totally erases drive and recreates it to as purchased. Or no recovery is possible. 

Why anytime major system changes require good backups first.

MBR is very first sector on the hard drive before any partitions. Partition also have a boot sector often called PBR which is first sector in partition and not used to store data.

Very new systems now use UEFI/gpt not BIOS/MBR where  MBR is the partitioning type with a MBR as the first sector.

The first part of a MBR is IPL  or initial program loader or just boot code, last part ot MBR is the partition table.
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Rjbcc58 on 2012-07-30
Thank you oldfred, I appreciate the help and am learning a lot. With a combination of windows system recovery repair attempts, bootrec's, boot-repairs, and playing around with the Intel smart storage, I can now boot back into Windows 7 (no data loss either). 

I am now about to start round two of my installation, using the tips from the thread you showed me. I may be contacting you again in the near future ;)

---

### Post by oldfred on 2012-07-30
Glad you got Windows back ok. I might do a full backup as it is, just to be on the safe side.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---


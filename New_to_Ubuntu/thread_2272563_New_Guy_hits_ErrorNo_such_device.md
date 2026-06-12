---
title: "New Guy hits Error:No such device"
date: 2015-04-07
forum: New to Ubuntu
---

### Post by bohicaman on 2015-04-07
I'm new to Ubuntu. I set up my system as a dual boot with Ubuntu 12 and Windows7 on a ASUS 64bit built machine. I attempted to use Acronis software to "clone my C: drive. Apparently that can't be done on a dual boot system!
Anyway, now I get error saying:

error: no such device: 7127e5d-f14e-4944-b1cf-eedca9d7be3
Entering rescue mode...
grub rescue>

I only know enough to enter <ls> at the prompt. I got the following result:

(hd0) (hd0, msdos2) (hd0, msdos1) (hd1) (hd1, msdos1)

Can anyone help me recover from this error?

---

### Post by Vladlenin5000 on 2015-04-07
It can be done with Acronis and many other similar tools, including the free Clonezilla, provided you use a bootable CD/USB to run the tool.
Indeed you can't run it from inside Windows because the way it works -> rebooting from a virtual OS session it creates in order to be able to clone the Windows partitions (no tool can do that with mounted partition, irrespective of the OS). This shortcoming is obviated by booting a live session and all decent tools should provide an ISO to make a bootable CD or USB flash drive. Clonezilla does and it's free.
There are also many multi-tools like Hirens BootCD that include some _20 (twenty)_ or so tools similar to Acronis True Image.
Acronis TI is just an overpriced piece of code that adds nothing nor does it better than most free tools available.

---

### Post by bohicaman on 2015-04-07
Appreciate the quick response!
I am still at a loss as to how to recover my C: drive. Can I simply re-install Ubuntu, or will it overwrite another part of the C: drive, instead of replacing the original Ubuntu partition?

If re-install will not work, can someone give me directions on what to do? Please remember Iam new to Ubuntu. Thanks!

---

### Post by Vladlenin5000 on 2015-04-07
Please start by describing what happened...

---

### Post by bohicaman on 2015-04-07
I used Acronis to "clone" my C: drive. The C: drive is set up as a dual boot drive with Windows 7 Home Premium and Ubuntu 14.04. It (Acronis) was checked to shut  down when cloning was complete and I left system alone. When I returned and booted up system I got the message:

error: no such device:
Entering rescue mode...
grub rescue>

I am assuming the Ubuntu boot record file is corrupted or something. I just am trying to figure out how to recover it as I'm just beginning to use Ubuntu. As best I can tell, the drive letter (C:drive) has some how changed to another letter for the physical drive, but the files and programs appear in tact. I was able to at least look at the Windows partition via the "repair disc", however, in checking, the repair disc says there is no problem with the drive. I again assume that this is an Ubuntu problem.

---

### Post by oldfred on 2015-04-07
Boot-Repair cannot fix Windows issues, but has a good summary report so we can see all the details of your installs. Also with two drives do not run any autofix. Only use advanced mode.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by bohicaman on 2015-04-07
I don't believe windows7 was damaged. Trouble appears to be a boot problem with the Ubuntu partition.

---

### Post by mastablasta on 2015-04-08
boot from live DVD/USB and use boot repair tool. it has a repair boot option. but before you run that post the results of bootinfo script so we can see what the issue is and if it's safe to run boot repair.

though likely you only need to reinstall or just update grub.

next time use Clonezilla or Redobackup. much safer. I use it on windows backups and cloning as well.

---

### Post by bohicaman on 2015-04-08
I have already tried the Repair Tool. No luck. Not sure how to get to the bootinfo script as only way into Windows Disc is Command Prompt. I also tried the Ubuntu trial disc and it loads, but I can't get the results of sudo fdisk -l to print off the Terminal screen and I don't yet know how to save it as a file. When I run the grep menuentry/boot/grub/grub.cfg command, the system seems to hang and nothing happens.
Are there any Ubuntu files I can just copy to the C: drive to correct the boot problem. Or, is there a way to delete the Ubuntu partition from the C: drive without effecting Windows and start over? I'm rreally at a loss here with no computer. Thanks everyone offering assistance!!

---

### Post by oldfred on 2015-04-08
The Ubuntu partition is not the issue, it is grub in MBR and not finding the rest of grub in the Ubuntu partition. And if you do not have grub.cfg as your grep command indicates, that would be a reason why grub fails to boot.
You have to run Boot-Repair from the Ubuntu live installer or from a full download of its own liveCD. The summary report uploads the report and you can just post the link it gives. It can reinstall grub, but usually better to use advanced mode not just the autofix.

Another link:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by bohicaman on 2015-04-08
OLDFRED,
Thanks for advice! Although I'm BRAND NEW to Ubuntu, I think I follow you. I also did what you recommended on the "Another Link" site. I launched a Terminal, put in the commands listed and it printed out a bunch of info to the screen. However, I'm not sure where to find the - click on the **Online report** button:and the - write on a paper the URL (e.g., **paste.ubuntu.com/XXXXXX/**) that appears, then indicate this URL to people who help you by email or forum. Any further coaching would be GREATLY APPRECIATED!!

---

### Post by oldfred on 2015-04-08
It should pop up with another panel just like shown in the link in post #10 so you can copy the pastebin it creates. If you just run the local report it does not post that.
You do have to have working Internet for it to be able to upload the file it creates.

---

### Post by Geoffrey_Arndt on 2015-04-09
Bohicaman,

In other words, oldfred is advising that when you run the Live DVD (or usb stick), that the first priority is to establish your working internet (click on the network widget in the upper right portion of top panel).   Then run the boot repair script, and you'll get the link URL as a popup.

PS (copying ubuntu or any linux files into a windows partition will not work . . . )

---

### Post by bohicaman on 2015-04-09
Geoffrey & OldFred, I really appreciate your assistance! Here's what I did since your last posts. Please see if I got it right as for me, I'm wading in uncharted waters with Ubuntu.
I inserted the Ubuntu disk and selected "Try Ubuntu". I then went to top right and looked at "Enable Newtorking" which is checked. I assume internet works as Firefox works. From here on I am at a loss...
First, I should ask this question before continuing. I originally loaded Ubuntu 12.04.5 onto my system. It then updated itself to 14.04 LTS. It was after that t he boot error ocurred. It also just dawned on me I am using the 12.04.5 .iso disk to attempt repairs. So, do I need to download the 14.04 version before proceeding? Which, now brings up another problem. I was able to download the "Boot-Repair-Disk-64bit.iso" using this "Try Ubuntu" version (as I can't use my Windows7 side of the system). However, I tried to burn it to disk and the burner software hangs up at the "creating image checksum" and an error box saying, "System Program Problem Detected". So, I would have to figure out a way to get the 14.04 disk burned.
Now to the second part of my problem...I am not sure I know how to do what was suggested in your prior posts regarding "run boot repair script". It sounds like it is on the system already. If so, how do I locate it? And, will the 12.04.5 version work off the live disk? Again, I truly appreciate all assistance to this "Newbie" to Ubuntu!

---

### Post by oldfred on 2015-04-09
If you have working Ubuntu then, you just rerun the command to start Boot-Repair.
But if using live installer, nothing is saved everytime you reboot, so you have to reinstall it every time you boot.

Boot-Repair's script should work from any version live installer you have. But always best to have working repairCD/DVD/flash drive for the current version of every system you have installed, both Windows & Ubuntu.

Sometimes different tools to burn ISO to flash drive or DVD work or work better. Make sure download is valid by checking md5sum.
       [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM
[/URL]
 [URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick
[/URL]
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


   Usb installer from Windows - pendrive
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

    [URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
[/URL]

[URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]

---

### Post by bohicaman on 2015-04-09
I can try the boot repair from the DVD, but I don't know where it is, or what the "run" command is. I am once again assuming it is dine from the Terminal screen. Thanks!

---

### Post by oldfred on 2015-04-09
If you are using Ubuntu DVD, you have to reinstall it every time you reboot. Instructions were in first link post #6. Your DVD does have to be one of the current versions of Ubuntu.

---

### Post by bohicaman on 2015-04-09
Ok. Making progress!! I did as advised. This time the Boot-repair seemed to work - almost. System still not functioning, but I got the web site for the report. See below.
[http://paste.ubuntu.com/10786526](http://paste.ubuntu.com/10786526)
There were also 2 "No such file or directory" messages at the end.

---

### Post by oldfred on 2015-04-09
I am not sure I have seen so many errors.
And you only have Windows on entire drive.
You show the typical Windows full drive install with sda1 as a boot partition and sda2 as the main install and it takes the entire rest of drive.

But sda2 cannot be mounted nor seen other than from partition table.

In live installer is Disks and in upper right corner an star type icon. Click on it and open Smart Data.
It will tell status of drive. While it can run lots of tests, all I really know is passed or ok is good and anything else is a new drive.

---

### Post by bohicaman on 2015-04-09
Do yo think it would do any good to re-load Ubuntu, or am I gunna be stuck re-loading EVERYTHING. Also, do you think trying any of the other forums might help find someone that has been in this situation before? 
I checked the upper right corner for anything that said DISK, or a Star Icon. Probably in the wrong spot, but I don't see either.
Again, I appreciate all the assistance here!!
Bob

---

### Post by oldfred on 2015-04-09
Did you load Disks first? The icon is in its application. 
If running an older version then it is Disk Utility.

You have no Ubuntu.
And you have a broken Windows. Not sure what would have corrupted partition so much.
With Windows NTFS partitions you normally run Windows repairs which you can try.
You should try chkdsk from the Windows repair console or from a Windows repairCD. You cannot run chkdsk from Linux only Windows.

---

### Post by sandyd on 2015-04-10
Boot From ubuntu dvd and run the following:
```

dmesg
sudo apt-get install smartmontools
smartctl --test=long /dev/sda
# Go for a walk, come back in 30m, it will probably be done by then
sudo smartctl --all /dev/sda
```

It is possible that you have a bad HDD.
As oldfred has mentioned, your HDD no longer has Ubuntu on it, but still has the Ubuntu boot loader installed.

Ubuntu detects that you now have two partitions, which are:
```

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,953,523,711 1,953,316,864   7 NTFS / exFAT / HPFS
```
This being Windows 7, there are two partitions, the first being the required recovery partition and the second being the OS partition. Grub looks for the original Ubuntu partition to get its boot configuration. Unfortunately, as you can see, this is missing.

---

### Post by bohicaman on 2015-04-10
Good Morning! Well, another day and no good news!

OldFred, I am using disk for 12.04.5. It has "Disk Utility", which I clicked on. Unfortunately I do not see the star you mentioned. Regarding the cause of the corupion , I tried cloning the disk with Acronis and this is the results. I emailed their support, but have not heard anything back yet. I also tried the CHKDSK /f on Windows. Didn't repair anything, but showed no problems with the HHD.

Sandyd. I put in the command you suggested, results below.

ubuntu@ubuntu:~$ sudo apt-get install smartmontools smart--test=long /dev/hda
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package smart--test
E: Unable to locate package /dev
ubuntu@ubuntu:~$ 

Does anyone think re-loading Ubuntu from scratch will help. Otherwise it's starting to look like I will have to clean the disk and start from scratch reloading everything (over a hundred programs).

---

### Post by oldfred on 2015-04-10
With Disk Utility it is not the icon in upper right but I think it just shows Smart tools. I forget, you may have to look around.
But Sandyd's command line version should have worked. Did you copy & paste commands, so you have no typos?

Since you have no Ubuntu, did you reinstall a Windows boot loader and see if Windows boots?
You can do that from your Windows repairCD or flash drive or install a Windows like boot loader with Linux.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    

Are your hundred programs Windows or Ubuntu? With Ubuntu you can easily export a list of installed apps and reinstall from that list with one command. I export new list as part of my rsync backup so I have that in my backup.

---

### Post by bohicaman on 2015-04-10
OLDFRED, you Sir are a lifesaver!!!
The info in your last link was the answer to the Windows problem. It is all back up and running. All my programs were Windows as I just started Ubuntu. As soon as I get WORKING backup drives done, I'll try re-installing Ubuntu as it looks really interesting and I think I'll enjoy learning it! 
My thanks to all who assisted!!

The answer was 2 simple commands at the "Repair Disk" command prompt:

bootrec.exe /fixboot
bootrec.exe /fixmbr

This problem SOLVED!
Bob

---

### Post by oldfred on 2015-04-10
Glad you got Windows back. :)
Is Boot-Repair now able to mount NTFS partition, or just mount from Ubuntu live installer without errors? 
It seemed to have a lot of issues, but perhaps all the Windows repairs together chkdsk, fixboot, & fixMBR worked?

Best to only use Windows to shrink the NTFS to make unallocated space for Ubuntu. And immediately reboot so it can run chkdsk and repair itself for its new size.

---

### Post by bohicaman on 2015-04-10
Windows boots normally. I looked at disk management on the C: drive and it shows everything as normal, except no Ubuntu Partition any longer! I attached a screen shot...
Again, Thanks!!
I'll keep you posted on progress!

---

### Post by bohicaman on 2015-04-10
Opps! Spoke to soon. After reboot, I now go directly to a grub> prompt.  Any suggestions???

---

### Post by sandyd on 2015-04-10
> **bohicaman said:**
> Good Morning! Well, another day and no good news!

OldFred, I am using disk for 12.04.5. It has "Disk Utility", which I clicked on. Unfortunately I do not see the star you mentioned. Regarding the cause of the corupion , I tried cloning the disk with Acronis and this is the results. I emailed their support, but have not heard anything back yet. I also tried the CHKDSK /f on Windows. Didn't repair anything, but showed no problems with the HHD.

Sandyd. I put in the command you suggested, results below.

ubuntu@ubuntu:~$ sudo apt-get install smartmontools smart--test=long /dev/hda
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package smart--test
E: Unable to locate package /dev
ubuntu@ubuntu:~$ 

Does anyone think re-loading Ubuntu from scratch will help. Otherwise it's starting to look like I will have to clean the disk and start from scratch reloading everything (over a hundred programs).

Please type the commands on seperate lines

---

### Post by bohicaman on 2015-04-10
Sandyd
I did put the command lines in one line at a time. The results were what I posted. I have tried it again and got a whole lot more typed results. However, it is still not booting correctly. Any thoughts?
Thanks!
Bob

---

### Post by oldfred on 2015-04-10
Those lines have to be a terminal in Ubuntu or in Ubuntu live installer, not a grub prompt.

If you ran Windows fixMBR command how are you getting grub. Or did you install Ubuntu again?

Best from live installer to run Boot-Repair's summary report again and post new link.

---

### Post by bohicaman on 2015-04-10
OldFred,
I ran those lines in Terminal Mode. When I boot and just leave the system run, It gives me the Grub Repair> option. If I press F2/Delete and go into the BIOS, and I pick a certain boot disk, I can get to windows via a selection list of Operating Systems (All Windows 7, and I don't know why that is!) and all works fine.
I am currently downloading Ubuntu 14.04. As soon as it's done I'll try re-doing the "Boot-Repair" and post the results.

---

### Post by bohicaman on 2015-04-11
Question...Is "grub.cfg" supposed to be in a hidden C: directory in the Windows partition? Mine is. Just wondering if I delete it if problem goes away? And then I re-load Ubuntu.

---

### Post by oldfred on 2015-04-11
Grub is not normally in the Windows partition. Did you install grub to the Windows partition's boot sector when you installed? That is always an issue as Windows has its own boot code in that NTFS partition. Grub should never be installed to a NTFS partition boot sector.

Advanced way to create multiple repair flash drive:
I have made a Windows repair flash drive and installed grub to MBR. Grub.cfg was then the Windows NTFS partition in Windows boot folder along with BCD. Windows does not see Boot and boot as different and you have to make sure you do not have both as grub may make it with different case. Then from grub I could directly loopmount boot Ubuntu ISO, and several other ISO like gparted, parted magic & Knoppix. One repair flash drive for all systems. I only did 64 bit, but it could be 32 bit.

---

### Post by bohicaman on 2015-04-11
I didn't install grub to Windows partition. I am assuming Acronis must have moved things around during the "cloning". It also changed drive letters, etc.  (I heard back from Acronis...basically they said, to bad!!)
I downloaded Ubuntu 14.04 iso last night. Here are my thoughts...(*again please remember I am totally new to Ubuntu*). Delete grub folder from the Windows partition and then re-load Ubuntu (14.04). Your thoughts?

Regarding your second paragraph, I have to plead ignorance! I'm not sure what any of the listed files or terms mean, or do. Sorry! I got the book, "UBUNTU 14.04 LTS, Desktop Applications and Administration" by Richard Petersen. Hopefully I can read up and see what you mean. Thanks!
Bob

---

### Post by oldfred on 2015-04-11
The advanced mode was off topic and just to show you can have a grub folder in Windows and still have a working Windows. But not the normal case.

So we are starting over. :)
Not like already 4 pages of posts. And thread is shown as Solved so others will not look at it.

Best to use Windows 7's own tools to shrink the NTFS partition. Then immediately reboot so it can run chkdsk and update to new size.
Then make full backups of Windows. These have been suggested. I do not have Windows any more and with XP always had it on one hard drive & Ubuntu on my other hard drives.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

Also best to have a Windows repairCD or flash drive as most Windows repairs cannot be done from Linux. Windows tools for Windows, Linux tools for Linux, normally. 
      
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

If a new user the default install of / (root) and swap is all that is really required. But we often suggest a separate /home partition. But having a separate /home requires you to use Something Else and create your own partitions.

      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by bohicaman on 2015-04-11
Ok, removed [SOLVED] designation. Also tried to do the shrink thing. Computer Management (Disk Management) hangs when I click on Shrink. It says it's querying C: drive for available shrink space and just stays there. Still don't know if I should delete the grub folder from the C: Main Partition. I am assuming that there are some files in that partition that are causing the problems, but I don't know which ones. I don't see the need to back up the drive till I clear the problems, otherwise I'm just saving them (the problems).

---

### Post by oldfred on 2015-04-11
While some of these discuss Vista, Windows 7 has same issues:

 Windows Disk Cleanup tool to houseclean
defrag at least twice
#Partitioning generally better
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
30GB at an absolute minimum and you want at least 30% free inside the NTFS partition for Windows to work well
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
Hiberfile in Windows 7 & 8 often prevents shrink
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

### Post by bohicaman on 2015-04-11
Here's the latest. I re-ran System Recovery from Repair Disk. Then I ran the Defrag program several times. After that I re-ran the Disk Manager and got Shrink working. So, now my question is, How much to shrink??? Attached is screen shot of shrink sizes. I am assuming that after shrinking, I will be installing Ubuntu to the new partition. Is that correct? Dare I consider a light at the end of the tunnel!

---

### Post by oldfred on 2015-04-11
Make sure you leave at least 30% free in the NTFS partition. Windows starts to slow at 20% free and gets real slow at 10% free.

It all depends on what you want for Ubuntu. Standard install is just / (root) and swap and for a new user that is all that is required. I often suggest both /home and a shared NTFS data partition. Writing into the Windows system partition can lead to issues. Better to either hide or set system partition as read only and only have read/write on a data partition. Ubuntu cannot use any Windows formats as its system partitions like / or /home, but can easily read share data on NTFS.

---

### Post by bohicaman on 2015-04-11
Ok, here's a stupid question, but I just don't know...Which partition am I shrinking??? The System Reserved, or the Main Program Drive?

---

### Post by bohicaman on 2015-04-11
Ok, here's a stupid question, but I just don't know...Which partition am I shrinking??? The System Reserved, or the Main Program Drive?

---

### Post by oldfred on 2015-04-11
The system reserved is only 100MB typically and the main or c: drive is usually the rest of the drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

for  MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

---

### Post by bohicaman on 2015-04-12
OldFred, 
Thanks for ALL the help!!
After reading all your info and doing a lot of research reading, I did the following: Re-partitioned the C: drive. I also updated from Windows 7 Home to Windows 7 Ultimate. Then I re-installed Ubuntu 14.04. All is back to normal!! No programs were damaged or lost. I can now move on to learning Ubuntu. Again, my sincere THANKS!!!):P
Bob

---

### Post by oldfred on 2015-04-12
Glad you got it working. :)

---


---
title: "Can't boot my windows 7 after installing ubuntu"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by elohimguy on 2013-06-10
Hi Guys, 

I was wondering if someone could help me with my dilemma. Recently, I just installed Ubuntu OS to one of my created partitions. Keep in mind I only have (1) HDD and decided use a seperate partition to install ubunta on. Well after installing ubuntu during reboot, I do not see the option of dual booting from my windows 7 OS anymore. I been trying to recover my windows 7 partition ever since. I ran a 'boot-repair' and it recorded the following:

[http://paste.ubuntu.com/5752476/](http://paste.ubuntu.com/5752476/)

I felt like I tried everything with no prevail. I have many important things installed on my windows 7 partition and I'm hoping it didn't get erased and that I can recover it. Could someone please help me with this issue? The first time I installed and uninstalled unbutu I used "wubi" and it dual booted with success. But this time I installed ubuntu from a usb stick as instructed from this tutorial: [http://www.youtube.com/watch?v=3HANcetKsqc](http://www.youtube.com/watch?v=3HANcetKsqc). I would really appreciate if someone could help me out on this issue. This is very frustrating... Thanks!

---

### Post by manoriax on 2013-06-10
Does your computer boot Ubuntu or no OS at all?

---

### Post by VMC on 2013-06-10
Somethings strange going on. In the Boot Summary, it shows unknown filesystem type ' ', yet on line#71, it shows NTFS.
Did you install Windows 7, or did it come already installed?

---

### Post by d4m1r on 2013-06-10
How big is the drive and can you explain how it is partitioned?

---

### Post by oldfred on 2013-06-10
Boot-Repair said you have flexnet. That is a proprietary DRM software that sometimes interferes with grub as part of grub is core.img which is in the few sectors after the MBR. That is the same location flexnet hides its security data. Since you erased it (Boot-Repair did back it up), your DRM software may not work or it may restore & overwrite part of grub.

It could be just that you need to run chkdsk on your sda1 & sda2, but you can only do that from a Windows repairCD.

If you do not have a Windows repairCD and have access to another Windows 7, you can make one. It just should be either 32bit or 64bit to match yours.
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx")

---

### Post by elohimguy on 2013-06-10
> Does your computer boot Ubuntu or no OS at all?
It only boots Ubuntu. Just now I ran my Ubuntu from my usb to go through the reinstallation process so I could see what partitions were being recognized. To my surprise I can still see my original partition drive where my windows OS is installed. It's under "/dev/sda1"

---

### Post by elohimguy on 2013-06-10
> **VMC said:**
> Somethings strange going on. In the Boot Summary, it shows unknown filesystem type ' ', yet on line#71, it shows NTFS.
Did you install Windows 7, or did it come already installed?

Windows 7 was already installed.

---

### Post by elohimguy on 2013-06-10
> **d4m1r said:**
> How big is the drive and can you explain how it is partitioned?

You mean the partition windows 7 OS is installed on or Ubuntu? The partition for windows 7 is huge and I just checked not too long ago through the reinstallation wizard from Ubuntu and it recognizes the partition size at 800GB. The size of the partition for Ubuntu is around 10GB. I have a 1TB HDD and I basically shrank my main C:/drive and split it in two (I also have another 88GB partition on the windows OS in case you were trying to account for the missing figures giving me a total of 3 partitions). Thus Ubuntu was installed on the unallocated drive created from it. During the main installation menu when I begin to choose the partition for Ubuntu, I remember reserving 10% of the 10GB free space for the "swap." I used the remaining memory to install Ubuntu. I wanted to note somewhere during this phase I don't know if I screwed up. I watched the tutorial on youtube and I was instructed to choose "logical" for the swap and primary for the actual install. I'm not sure if I accidently chose primary for the swap because I remember asking myself if I chose the right option afterwards. It's only a theory and a small chance that such may be the problem. I'm still new at this so there's no telling why things went wrong for me. I partitioned it just like the guy in the tutorial instructed @ 1:45 in the video. He sets the swap @ 3:15. The link is here [http://www.youtube.com/watch?v=3HANcetKsqc](http://www.youtube.com/watch?v=3HANcetKsqc) if that helps you get a better understanding on how I set Ubuntu up.

---

### Post by oldfred on 2013-06-10
How did you shrink Windows? We normally suggest doing it with Windows Disk tools and reboot Windows.
Windows had to run chkdsk after a resize and Linux will not mount it if it needs chkdsk. So run chkdsk before doing anything else that then may not be repairable.

---

### Post by elohimguy on 2013-06-10
> **oldfred said:**
> How did you shrink Windows? We normally suggest doing it with Windows Disk tools and reboot Windows.
Windows had to run chkdsk after a resize and Linux will not mount it if it needs chkdsk. So run chkdsk before doing anything else that then may not be repairable.

Yes I did a shrink from Windows Disk tools. I will try chkdsk through windows repair.

---

### Post by elohimguy on 2013-06-10
> **VMC said:**
> Somethings strange going on. In the Boot Summary, it shows unknown filesystem type ' ', yet on line#71, it shows NTFS.
Did you install Windows 7, or did it come already installed?

Yes, exactly.

---

### Post by elohimguy on 2013-06-12
Okay guys, this is the situation. I tried the chkdsk option and it doesn't work. I tried to use the "repair windows method" and that didn't work. It couldn't find anything to repair. I did the bootrec.exe and that didn't work. Each time I booted windows I would get "there's no operating system" thus I would have to reinstall ubuntu again after the mbr was changed. Finally, I tried the last resort by using the windows 7 installation cd to do a clean install. During the install, I was able to see my partition drive windows 7 OS is on that I'm trying to access and next to it "system" is displayed. I chose the partition but I did not format the partition in hopes that I could do an install without erasing my prorams and settings. Turns out an error message popped up not allowing me to install windows 7 OS stating I did not have all of the files. Is there any software available that can jump and open another partition? I also wanted to note that my partition in windows 7 OS is installed on is encrypted. When I installed ubuntu, I remembered not being prompted to enter my encryption password for my drive. If my partition is showing there has to be a fix. The bios is just somehow not recognizing it. Hopefully someone could help me with this issue. Thanks!

---

### Post by Mark Phelps on 2013-06-12
First of all, Win7 does not come on a CD.  That's too small to hold the installation files.  Instead, it comes on a DVD.  So, if it really is a CD, then it's likely just a Recovery CD, which means it can be used to REPAIR Win7, and together with a Recovery partition, to RESTORE Win7.  But, if your Recovery partition is missing or damaged, then you won't be able to restore Win7.

Second, for Win7 problems, you should really go to the Win7 forum (sevenforums.com).  They have a tutorial that will walk you through doing what you wanted to do -- reinstall Win7 without removing the files or apps.  But, once again, you must have Installation media to do that.

And finally, you are probably NOT going to be able to do what you want to an encrypted partition.  You should ask about this on the Win7 forums to be sure.

---

### Post by oldfred on 2013-06-12
If running encrypted Windows you will not be able to install grub to MBR and dual boot. The encryption software installs a custom MBR that works with the encryption.

You can see if ewstoring the MBR & first sectors that Boot-Repair backed up works to let you boot Windows again.

Some have just installed grub2's boot loader to the MBR of a flash drive and then booted that to load & run an Ubuntu install on a hard drive. There may be other ways if Windows encryption software allows it, but I do not think so as the entire idea of encryption is to prevent other systems from seeing data.

---

### Post by elohimguy on 2013-06-12
> You can see if ewstoring the MBR & first sectors that Boot-Repair backed up works to let you boot Windows again. 

Okay, so how do I use the boot repair that backed up my MBR and first sectors to boot windows again?

---

### Post by oldfred on 2013-06-12
I have not done it, but there is a restore MBR chkbox.

[https://help.ubuntu.com/community/Boot-Repair#Advanced_options](https://help.ubuntu.com/community/Boot-Repair#Advanced_options)

---

### Post by elohimguy on 2013-06-13
> **oldfred said:**
> I have not done it, but there is a restore MBR chkbox.

[https://help.ubuntu.com/community/Boot-Repair#Advanced_options](https://help.ubuntu.com/community/Boot-Repair#Advanced_options)

Thanks! I will give it a try. For the record for all too see I did another "boot-repair" and there's been a change in information. I can now see Windows 7 listed. Hope the repair worked, will keep fingers crossed.

**comparison:**
original: [http://paste.ubuntu.com/5752476/](http://paste.ubuntu.com/5752476/)
update: [http://paste.ubuntu.com/5760307/](http://paste.ubuntu.com/5760307/)

---

### Post by oldfred on 2013-06-13
It is showing the partition as NTFS, but is not showing any of the normal Windows boot files which should show?

 Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---


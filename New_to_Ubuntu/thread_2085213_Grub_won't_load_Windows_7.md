---
title: "Grub won't load Windows 7"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by Chill713 on 2012-11-17
I sent this to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL], still no response thought I could get a faster solution here.
  I am running Windows 7 64-bit and Ubuntu 12.04 LTS on separate partitions.
  The message is sent is:
  Boot-Repair URL:  [http://paste.ubuntu.com/1365163/](http://paste.ubuntu.com/1365163/)
  Originally I was unable to access Ubuntu after a windows update  (Ubuntu was installed using wubi). Rather than logging into Ubuntu from  the Windows 7 Bootloader, it lead to the grub> command prompt.  No  matter what I did here, it would not log me into linux.  As a result I  uninstalled Ubuntu from the Add/Remove Programs application in Windows  7.  I then re-installed Ubuntu 12.04 LTS using a liveCD-USB.  This time  however, I created a partition.  I then restarted and got the GRUB  bootloader which loads Ubuntu 12.04 LTS with no problems, however when I  select windows (listed as "Windows 7 (loader)"), it just refreshes the  grub bootloader instead of loading Windows 7.  I then used the Windows 7  repair disk to run bootrec/fixmbr and bootrec/fixboot.  This led to no  bootloader coming up when I started my computer.  Instead I got a blank  black screen with a flashing white cursor.  I went on to do a  bootrec/buildbcd and bootrec/scanos.  These did nothing to change the  situation.  When I ran bootrec/scanos it said that no Windows 7  installations were present.  After this I decided to reinstall WIndows 7  only for this to do nothing to change the situation.  Afterwards I did a  boot-repair in which I began to get the GRUB bootloader, which would  load ubuntu 12.04 LTS, but still would not load Windows 7.  I also did a  sudo update-grub which recognized Windows 7 as being installed, but  still didn't fix the issue of loading Windows 7.  While running Ubuntu I  have no problem accessing my WIndows 7 partition which is formatted as  NTFS.  It shows all the files and folders reflecting that the re-install  did take place, and it also shows all of my old applications and  folders in the Windows.old folder.  I am completely stuck at this point  and have no clue what I should do next.  Any help you can offer me will  be greatly appreciate.  Thank You  --gap

---

### Post by YannBuntu on 2012-11-18
Thread on AskUbuntu: [http://askubuntu.com/questions/218539/bootloader-problems-grub-wont-load-windows-7](http://askubuntu.com/questions/218539/bootloader-problems-grub-wont-load-windows-7)

---

### Post by Chill713 on 2012-11-18
> **RAJESHKSV said:**
> Hi All, 

I just wanted to add a small point here. Sometimes before restoring Windows 7 Bootloader, i.e., before running those two commands, One has to check if main partition (C drive for most people) is active or not. If not first we need to set it active and then run the two commands given in the page. Then only it will work. Can we please add this line as well that one has to check the partition if its active or not and provide a link for the same ?  This sceanario(marking C partition active) is important when user have windows recovery partition(Say D drive) and he deleted it to install Ubuntu on it

Thanks
Rajesh KSV

I have tried these commands AT LEAST 20 times(literally) and they have not worked.  Instead of leaving me with a Windows Bootloader I get a black screen with a flashing cursor.  I'm hoping that this is because my C drive is not active as you said.  How am I supposed to check to make sure it is active, and make it active?  Also I can access all my files on windows through ubuntu by clicking and mounting the Windows partition.

---

### Post by Chill713 on 2012-11-18
> **Elfy said:**
> Please use this thread for discussion regarding

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Support threads should be posted in normal forums.

Thank you.

I have tried this many many many times and it leaves me with a black screen and a flashing cursor.  No bootloader at all.  What should I do next?

---

### Post by coffeecat on 2012-11-18
@Chill713, I have moved your two posts from this thread:

[http://ubuntuforums.org/showthread.php?t=2012409](http://ubuntuforums.org/showthread.php?t=2012409)

... into your own thread. The Community Wiki Discussions forum is not for technical support. Please note what was said in the OP of that thread:

> Please use this thread for discussion regarding

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Support threads should be posted in normal forums.

---

### Post by Chill713 on 2012-11-18
Ok so where do I post my questions now?

---

### Post by coffeecat on 2012-11-18
Here - you've already done so and someone may be able to help.

---

### Post by Mark Phelps on 2012-11-18
> **Chill713 said:**
> I have tried this many many many times and it leaves me with a black screen and a flashing cursor.  No bootloader at all.  What should I do next?

The link clearly says you have to boot from your Windows 7 Installation DVD -- so ...

When you boot from that DVD, what do you see on the screen?

Is there an option to repair the installation?

Have you tried that -- and if so, what has been the result?

---

### Post by Chill713 on 2012-11-18
> **Mark Phelps said:**
> The link clearly says you have to boot from your Windows 7 Installation DVD -- so ...

When you boot from that DVD, what do you see on the screen?

Is there an option to repair the installation?

Have you tried that -- and if so, what has been the result?

Yes I have booted from the Windows 7 Installation DVD, like I said earlier 20+ times.  I have done start up repairs which result in no obvious change to my system.  I have also gone in and ran the command prompt and have used the bootrec /fixmbr, bootrec /fixboot, bootrec /rebuildbcd which results in my system giving me a black screen with a blinking cursor that does not go away no matter what I press or how long I wait.  I have also gone into Ubuntu using a liveUSB and used boot-repair which only restores the Grub Bootloader, but once  I select Windows 7 (loader) from the bootloader I get the same black screen and blinking cursor.  So now that it is clear, what suggestion(s) do you have?  FYI I already attempted to do a reinstall on Windows 7 and even this did not fix the problem.

---

### Post by Chill713 on 2012-11-18
Sorry if it seems as though I have an attitude but if you read the very first post everything I have done and everything that has resulted is carefully explained.

---

### Post by oldfred on 2012-11-18
It looks like you did several of the Windows repairs, but did you run chkdsk? That is almost always the first thing required and often has to be run more than once or until there are no errors.

       How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

   Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

    
Script says boot sector is ok, but it only checks that it is there and over all looks ok. Sometimes it needs complete replacing, then a chkdsk.
       How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

    
Many of the Windows repairs will reinstall the Windows boot loader to the MBR. That is ok, as until you can directly boot Windows, grub will not boot Windows. 

Then once Windows is working then you can add the grub menu back into the MBR with Boot-Repair.

---

### Post by Chill713 on 2012-11-23
> **oldfred said:**
> It looks like you did several of the Windows repairs, but did you run chkdsk? That is almost always the first thing required and often has to be run more than once or until there are no errors.

       How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

   Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

    
Script says boot sector is ok, but it only checks that it is there and over all looks ok. Sometimes it needs complete replacing, then a chkdsk.
       How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

    
Many of the Windows repairs will reinstall the Windows boot loader to the MBR. That is ok, as until you can directly boot Windows, grub will not boot Windows. 

Then once Windows is working then you can add the grub menu back into the MBR with Boot-Repair.

Hey I ran a chkdsk and no problems were found.  I also ran the bootsect.exe commands and still Windows 7 won't boot.  I don't know what else I can do.  I already tried reinstalling Windows 7 and that didn't even help it boot.

---

### Post by Chill713 on 2012-11-28
Backed up harddrive, reformatted and reinstalled Windows Vista, then upgraded to Windows 7, now about to install Ubuntu on partition

---


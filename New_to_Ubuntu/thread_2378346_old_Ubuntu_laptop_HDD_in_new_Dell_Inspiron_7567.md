---
title: "old Ubuntu laptop HDD in new Dell Inspiron 7567"
date: 2017-11-22
forum: New to Ubuntu
---

### Post by fattyz on 2017-11-22
Hi everyone.  I finally gave up trying to copy my old Ubuntu install to the new laptop and I just pulled the drive out and stuck it in the new computer.  It works!  I was so pleasantly surprised!  I have a few setup problems to work out as you can probably imagine and I will try to go one thing at a time.  Although I've been using Ubuntu for years I'm still a total noob so please go easy!

The old laptop was an Acer with Ubuntu 14.04 only I think, It had not really been working for some time.  The new laptop is a Dell Inspiron 7567, Win10 256 SSD.  I just stuck the old drive in and I can go into the bios, select legacy boot and then select Ubuntu and it starts.  That's all I have been able to do so far.

How do I enable grub or some other boot menu?  I have been googling it somewhat but there seems to be so much conflicting info.  I appreciate your help and Happy Thanksgiving.

---

### Post by Bucky Ball on 2017-11-22
Run boot repair and that will fix the grub. See the Boot Repair link in my signature at the bottom of this post (last link, first line of signature).

(Boot your machine however you need to and install Boot Repair to Ubuntu (see how on that link) then run it and use 'Recommended Repair' or go for advanced options and install grub to sda.)

---

### Post by rivasdom on 2017-11-22
You probably have to install Ubuntu in UEFI mode to dual-boot. Let's see what oldfred has to say,  he's the expert.

---

### Post by oldfred on 2017-11-22
You have a new UEFI based system with Windows in UEFI boot mode.
Old install will be BIOS with MBR partitioning.

Can your system directly boot your second drive?
Is it internal or in a USB case?
If it boots then it is working? Or do you have driver issues that it only starts to boot?
UEFI & BIOS are not compatible, so you can only dual boot from UEFI boot menu, not grub.

You may just need grub installed to MBR of old drive (if it boots it already is there), best not to install to gpt's protective MBR on internal drive, although that might work if you cannot boot directly. Some also have had to move/create a /boot on internal drive to boot second drive as some systems just do not work.

You will have to have CSM/Legacy/BIOS boot on to boot old drive. Dell is (I think) the only one that lets you turn on CSM, but still able to boot and install in UEFI mode. So you may may not have to turn on/off UEFI/CSM settings.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

      
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
Long term, once you start using UEFI hardware, best to only use gpt partitioning for Ubuntu only drives whether BIOS or UEFI and use UEFI boot for all systems. 
But you can still use the old BIOS/MBR as current systems are backwards compatible.
Just saw where Intel plans that new hardware released in 2020 time frame will be UEFI class 3 or UEFI only, with no CSM or BIOS mode.

---

### Post by fattyz on 2017-11-22
Yes I boot into Ubuntu from the BIOS Internal drive, yes it boots and its working with networking (no wifi)  I am in it right now.  Yes it boots in legacy mode which I change in the BIOS and change back and it boots into windows.

Thanks

---

### Post by oldfred on 2017-11-22
I had to delete your first post with the detailed output from the Boot-Repair summary report. 
It was too large for forum, and should have had code tags, which are easy to added with # in forum's advanced editor.
It would not even let me edit it, but since you then posted link that is all that is required. But link is not working. It looks like it may have an extra character.

With a BIOS/MBR drive in an UEFI system that is the only way you will be able to boot.

If you want help on wi-fi issues, best to post new thread in Networking & Wireless. And see sticky on top of threads on before you post. You can post a wireless script link, so those who know those issues can help.

---

### Post by fattyz on 2017-11-23
Thanks for your help happy Thanksgiving!  Yes I couldn't figure out how to delete a duplicate post.  Yes I will try reading to fix the wifi, sound, and all the other stuff not working unless I run out of patience which is likely.  If I just reinstall 14.04 onto that drive what will happen?  Will I lose my compiz and emerald and stuff?  That is the only reason I have been trying to make this work I don't feel like setting it all up again.  : )

---

### Post by yancek on 2017-11-23
If you are able to select and boot Ubuntu from the BIOS on boot, why would you want to change?  The few seconds that takes is likely to be much less than the hours of re-configuring everything on a new install.  A new install is likely going to overwrite everything on the system although I beleive there is an option to save data particularly if you have a separate /home partition.  I'm not familiar with the software you mention so maybe someone else will have an opinion.

---

### Post by oldfred on 2017-11-23
I install each new Ubuntu and sometimes another flavor just to try it.
But my main working install is the current LTS. I still have 14.04 installed, am using 16.04 and have 18.04 working & mostly configured. But I will totally reinstall 18.04 when finally released.

I have all my data in a separate /mnt/data partition and each / is about 25GB. I back up list of installed apps and have a couple of files in /etc that I edit like 40_custom, fstab, and exports for NFS. After doing the same reconfigure multiple times I realized I could script most of it.

You should have good backups anyway as hard drives will fail.
       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

I use rsync to do a copy to another drive (Which is not a real backup) but also copy to flash drives & copy most critical files to DVD.
      
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by fattyz on 2017-11-25
Thank you yes I was thinking that.  We will see how much luck I have getting everything working but what you mention is probably what I will end up doing and thanks everyone again!

EDIT:  Just after posting this I decided to boot into Ubuntu and get things working and I got this! Error: no such device:
grub rescue >


After googling this awhile I think I'm toast but it was fun!

---

### Post by fattyz on 2017-11-25
Thanks for all the links!  I'll mark this as solved and move along.  Not to lose sight of the most amazing thing about the whole experience is that it worked at all.  Do you think an old install of windows would have started?  So Ubuntu performed beautifully!

---

### Post by fattyz on 2017-11-25
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

Hi sorry to revisit this but what will happen if I run this as admin on my dell?  People are saying it fixed the issue or it just did nothing or now windows won't start?  Any advice I'm nervous to try it!

Thanks!

---

### Post by oldfred on 2017-11-25
As long as you have Windows repair/recovery disk, editing BCD should not be an issue.
But do not delete default Windows entries in BCD.

I believe with UEFI, the BCD entry uses UEFI's one time boot. So then BCD reboots system and boots Ubuntu one time. Ok if you are primarily a Windows user. But you boot Windows & then reboot, so boot into Ubuntu is slower.
Often used on those systems that violate UEFI standard and only boot by description. And only valid description is "Windows Boot Manager".  Reboot must not then do description check.

And Dell normally boots ok into Ubuntu if everything else is ok. It does not have the description issue.

---

### Post by fattyz on 2017-11-25
Ok thank you so much I guess I'll make a backup and try it!

---

### Post by fattyz on 2018-01-14
Hi, I got this working and I thought it might be helpful if I tell you how I did it.  The amount of googling it took was mind numbing but eventually, it paid off.

I stumbled upon this [https://superuser.com/questions/1152001/shutdown-windows-10-truly-for-a-dual-booting-system](https://superuser.com/questions/1152001/shutdown-windows-10-truly-for-a-dual-booting-system) and thought it was a long shot but since it was simple (I mean some of the stuff I was reading was just tons of terminal commands to try and get this working) so why not?

When I went in and shut off fast startup within windows 10 as shown in that article it got fixed.  Now I can dual boot but using the bios. I start up and press F2 and choose legacy boot.  I get grub with Ubuntu options only no option to boot win 10.  Ubuntu starts on the old hard drive and works fine like it did on the old computer.  (getting wifi working is the next project)

If I restart and go back into bios and select UEFI boot win 10 starts, no option to run Ubuntu, no grub menu.

I thought I had disabled fast startup in the BIOS following  some other instructions I found googling and  I probably did but I guess it was not enough and has to be done from within windows as well?  IDK.  It's working though.  So this is probably a good work around if you want to stick your old HDD Ubuntu install in your new UEFI laptop.

Hopefully, it'll keep working, I had it working before then it stopped so I'm a bit leery of that still but it's working for now.  Thanks for your help!

---


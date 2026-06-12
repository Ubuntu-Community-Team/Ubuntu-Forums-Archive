---
title: "Boot Repair has error I don't know how to fix"
date: 2014-10-11
forum: New to Ubuntu
---

### Post by BudTuba on 2014-10-11
I am fairly new to Ubuntu, having used 13.04 and upgraded to 13.10  on my HP Pavilion dv6000.  I decided to upgrade to 14.10 and created new partitions in order to move over personal files.  Then I resized partitions to add the space of the 13.1 os to the 14.10 os.  When I started my computer, it immediately opened the Win Vista os and I never got the grub screen to choose Ubuntu.   Using a 12.04 LIve CD I was able to run gparted where I noticed the boot partition flag was set for sda1 where my Win Vista resides.  So I tried changing the boot flag to sda8 where my 14.10 resides.  It didn't work, for when I start up, a Intel repair bootscreen shows up trying to establish a boot procedure.  I don't even know what commands are available there, but found the Ctrl-Apt-Dep buttons will initiate a new boot.  So I aggain rebooted using the 12.04 32bit live CD where I could try boot repair to fix Grub.  I kept getting messages that all program managers have to be turned off and have not been able to get boot repair to work.  I am not sure how to turn them off.  The link to my error profile is 
[http://paste.ubuntu.com/8542726/](http://paste.ubuntu.com/8542726/)

Any help would be greatly appreciated.

---

### Post by oldfred on 2014-10-12
Corrected link.

Windows uses boot flag, leave it on sda1. Grub does not use boot flag.

Both 13.04 & 13.10 are obsolete. Please use only 12.04 or 14.04.
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life) 

Also unless you want to test, I do not suggest 14.10. You should have a working install of the current version(s) and then create another partition if you want to join in on testing the un-released 14.10 version.

Boot-Repair trys to download & run updates. You must have any other update progrom like Software Center or synaptic closed or you will have issues.

---

### Post by BudTuba on 2014-10-12
Thanks OldFred, The version of U I installed new is 14.04.  (I just forgot.)  The only reason I used the 12.04 CD was to be able to run Boot Repair and gparted both of which were on the CD.  Perhaps there is a 14.04 live CD with an improved Boot Repair on it?  However, after posting the help messeage, I was able to get Boot Repair on the 12.04 Live CD to fix things, however, again the only OS restored was the W Vista which is what I am using to answer your post.  The U 14.04 still resides on sda8.  How do I fix Grub to make that work as well?  Run Boot Repair again?  I also have a CD with boot repair only on it, but it leads to a terminal like screen and is not automatic, so I do not know how to use that.

---

### Post by oldfred on 2014-10-12
Boot-Repair has not be updated, lately. And if you use your trusty live installer you have to run an additional command to change to the saucy version of Boot-Repair. And it looks like the instructions I always link to are now not correct as the locations in the ppa does not a an ubuntu in it, so entry needs fixing.

Did you have anther package manager open when running Boot-Repair before? Otherwise you may have other issues with install.

You can just manually install grub using live installer.
       [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

      [/URL]
 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda8 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda8
[COLOR=#ff0000]sudo mount /dev/sda8 /mnt[/COLOR]
[COLOR=#ff0000]sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Should only need to run the two red commands above, then reboot.
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by BudTuba on 2014-10-12
To all of you following my travail,  I booted with the my Boot Repair Disk my son made for me and found it would open the same Boot Repair program I had on the 12.04 Active CD.  However, just as I found and reported before, I had to close all package manager programs that might be open.  The only one I could find open was Synaptic.  I"quit" that but still got the message.  So how does one close all package managers?  Curiously, I would have thought the Boot Repair Disk would have included a script to do that automatically.  Maybe a later version does?  In any case, all I can do right now is boot into W Vista.  Boot Repair did recognize I had U 14.04 installed on sda8.  My latest [http://paster.ubuntu.com/](http://paster.ubuntu.com/) numbers are /854308; /8546180; /8546301; /8546446.

---

### Post by oldfred on 2014-10-12
Every package manager creates the lock file to prevent others from running. Difficult to close from another app and maybe you would not that done automatically. Just do not open other apps. 

Boot-Repair still says you have lock set. You may have to manually remove that, but if new install it may just be easier to reinstall.
It looks like you have corruption in sda6 which is not currently used and in your install, so Boot-Repair is running fsck.  
So it seems like a variety of issues.

---

### Post by BudTuba on 2014-10-12
When I ran boot repair from BR disc, I did not start any other program prior.  So why it says I should have to close package managers is a mystery.  BTW what us UEFI boot mean?

---

### Post by oldfred on 2014-10-12
New computers use UEFI but have CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

BIOS is how computers have booted since first PC with a hard drive.

Since Apple Mac converted to Intel chips they have used UEFI, and all new Windows 8 pre-installed have UEFI hard ware. System must have hard ware configured for UEFI or older systems are just BIOS. And always best if hard ware has option, then to have all systems installed in same boot mode.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

Once an app creates a lock that is to prevent other apps from interfering. But if app not closed correctly then lock may  not be deleted.

 Locked dpkg - only if sure you are not running another update.
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

---


---
title: "After installing an image file I get a 'grub rescue' error...."
date: 2014-09-18
forum: New to Ubuntu
---

### Post by J Tinsby on 2014-09-18
I am using Acronis to make image backups of my system. Today I restored an image to a spare HD to see the result. The system had XP, 7, & Ubuntu on it. 

So I just restored 7 and Ubuntu, knowing that 7 wouldn't boot initially, it does now and its fine. I also installed EasyBCD 2.2 to point the MBR to the partition that has Grub on it, in my case /dev/sda5. When I boot up I get the choice to boot to 7 or Ubuntu, when I choose Ubuntu, I get a Grub rescue prompt and that's as far as I can get.

Although I have the Super Boot rescue disk I don't want to use it. It appears that it wants to put Grub on /sda and I see no way to put it anywhere else using that disc. 

I've tried the Live CD thinking that somewhere it would allow me to re-install Grub but I don't see anything like that, unless I didn't go far enough and use "install Ubuntu." I tried running 


```
sudo grub-install /dev/sda5
```

Of course from the CD that didn't fly either.

I don't want Grub on /sda, I'd like it where I had it on /dev/sda5 so that if it fails I still can boot to Windows.

Tried to use the Live CD and run the Deja Dupe backup, it did install files but I don't believe that /root is backed up by default and that's where my Grub resides, so no joy there. When I get back to my main HD I will make sure /root is included from now on.

There's probably an easy fix but my searches don't seem to be helping a lot.

Thank you in advance!

---

### Post by oldfred on 2014-09-19
Not sure how you restored. 
You could have duplicate UUIDs which are a big problem.
Or you could have new UUIDs but then grub & fstab need to be updated with new UUIDs.

Best to see details. Post link from the Boot report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by J Tinsby on 2014-09-19
Hello oldfred,

Here's the url you were asking for : [http://paste.ubuntu.com/8379910/](http://paste.ubuntu.com/8379910/)

Sure has a ton of information in it, hope it helps you.

Thanks,

J T

---

### Post by oldfred on 2014-09-19
This only shows one drive.
It has a BIOS/MBR type install, but no boot loader at all in the MBR.

Your Windows partition size has changed from what it thinks was the original size so you need to run chkdsk from your Windows repairCD or flash drive. You cannot fix that from Linux.

You have grub installed to the Partition Boot Sector (PBR) not the MBR of the hard drive. BIOS only boots by passing booting to MBR or first sector of hard drive. So without any boot loader in the MBR, your system cannot boot.

You could use Boot-Repair and install the Windows boot loader with Advanced mode and see if you can use f8 to get to internal repairs for Windows. 

And you should let Boot-Repair install grub to MBR so you can boot Ubuntu and if Windows is fixed it will also offer Windows in grub menu. Grub really only boots working Windows.

---

### Post by J Tinsby on 2014-09-19
> **oldfred said:**
> This only shows one drive.

It has a BIOS/MBR type install, but no boot loader at all in the MBR. 

Your Windows partition size has changed from what it thinks was the original size so you need to run chkdsk from your Windows repair CD or flash drive. You cannot fix that from Linux.

You have grub installed to the Partition Boot Sector (PBR) not the MBR of the hard drive. BIOS only boots by passing booting to MBR or first sector of hard drive. So without any boot loader in the MBR, your system cannot boot.

You could use Boot-Repair and install the Windows boot loader with Advanced mode and see if you can use f8 to get to internal repairs for Windows. 

And you should let Boot-Repair install grub to MBR so you can boot Ubuntu and if Windows is fixed it will also offer Windows in grub menu. Grub really only boots working Windows.

Yes there is only one drive, the main one is disconnected, that was done to prevent booting from the larger 'main drive.'

Yes the size is different this is a 240GB drive the main one is 640GB.

The MBR information was on XP which I didn't restore. I knew the MBR for 7 would be missing, but it was repaired by using the 7 install disc it boots to 7 just fine, in spite of what that log may show.

I don't want Grub on the MBR that puts it in charge of both OS's. If Grub fails you have neither, with Grub on /dev/sda5 I have 7 and Ubuntu being controlled separately. What I have now proves my point, I can boot to Win 7 but I can't get to Linux, but I STILL have an OS to use. If Grub had been put where everyone wants it I'd have neither.

The information about where to place Grub from at least 2 sources:

1/ [http://www.youtube.com/watch?v=xlTgaWs9BD0](http://www.youtube.com/watch?v=xlTgaWs9BD0)
2/ [http://khangyu.wordpress.com/2011/11/21/triple-boot-windows-7-xp-and-ubuntu-by-using-usb/](http://khangyu.wordpress.com/2011/11/21/triple-boot-windows-7-xp-and-ubuntu-by-using-usb/) 

I am puzzled that this idea isn't in use by everyone, it seems a perfectly logical and smart way to do it. You don't lose both systems since they aren't both dependent on Grub.

I thought it would be a simple process to reinstall Grub to /dev/sda5/ if there was a problem, but apparently not.

Thank you for your feedback, I defer to your experience and familiarity with Linux, but I can't agree with all of it for the reasons listed above.

The best part of this is that I am using a spare HD as a testbed, so anything that happens to the drive won't matter in the end. The main drive will be re-connected and I'll go on from there. The whole purpose of the 'test' was to see what happens when I try to restore, sector by sector, only 7 and Ubuntu. Now I have my answer, it won't work immediately as I had hoped. A re-install of Ubuntu will be needed, unless someone has another idea, I am open to suggestions of course. 

If I had made a Deja Dupe backup and backed up the /root would I be able to re-install Ubuntu from the CD, and then run that backup and have Grub and my system back as it was?

Regards,

J T

---

### Post by oldfred on 2014-09-19
Windows will not boot Ubuntu.

So if you want to do it your way you do have to depend on a third party boot manager, Neosmart's EasyBCD. That does also use grub4dos to do the chainload to the grub installed to a partition boot sector.

If you are primarily a Windows user that is fine, but I do not think it is any more reliable than booting with grub.

And if you have multiple drives, having a different boot loader in every drive directly booting the system installed on that drive is the best of both worlds. Then if either system has issues you can still boot other system from BIOS or one time boot key.

---

### Post by Michael_McKenney on 2014-09-19
Acronis restores can be tricky with multiple OS installs.   Bare metal restores to new drives that are different sizes can cause issues.  You also have to restore in the order of the original OS installation.  The first OS installed gets restored first.

---

### Post by J Tinsby on 2014-09-19
> **oldfred said:**
> Windows will not boot Ubuntu.

So if you want to do it your way you do have to depend on a third party boot manager, Neosmart's EasyBCD. That does also use grub4dos to do the chainload to the grub installed to a partition boot sector.

If you are primarily a Windows user that is fine, but I do not think it is any more reliable than booting with grub.

And if you have multiple drives, having a different boot loader in every drive directly booting the system installed on that drive is the best of both worlds. Then if either system has issues you can still boot other system from BIOS or one time boot key.

As I called out in my original post I am using EasyBCD to start Linux. What struck me was your mention *of multiple drives with a bootloader for each one*. A friend says he did it by accident once but can't recall how he accomplished it! Any advice on doing this? It'd be great to have Ubuntu on it's own drive and Win 7 on the other.

J T

---

### Post by J Tinsby on 2014-09-19
> **Michael_McKenney said:**
> Acronis restores can be tricky with multiple OS installs.   Bare metal restores to new drives that are different sizes can cause issues.  You also have to restore in the order of the original OS installation.  The first OS installed gets restored first.

Michael,

The first one installed on my main drive was XPired and I am not restoring that for many reasons. If I can get past the Grub Rescue warning I'll be fine. What is puzzling me is that my close friend using Win 7 and Ubuntu just made a backup that worked fine. BUT his machine has a 'system reserved' partition with the designation of "D" I do not have that tiny partition, but have instructions how to create one. I have no need for Bitlocker but if it will make an Ubuntu image restore reliable, I'll make one and try it.

Currently my Ubuntu install isn't anything special and can be blown out without any tears from me. I can easily re-install it all and only spend 30 minutes if that doing so. 

But I'd like to make the restored version work or at least figure out why it doesn't work. I believe it can be repaired keeping Grub on /dev/sda5, hope springs eternal! :D

Thanks

---

### Post by Michael_McKenney on 2014-09-19
system reserved D: is the F11 restore partition for Windows on most computers for the OS and all the other crap they force on you.  You need a true bare metal restore version.  Older version of Acronis did not do it well.  Bare metal means it lays everything down in order at one time including the system restore partitions.  Do you have the latest version of the backup software?  Does it do bare metal restores?

---

### Post by J Tinsby on 2014-09-19
Yes I have version 2014 it makes no mention of a bare metal restore. Have used all versions of it for many years and never had a problem, until now. It will allow a sector by sector restore, I have tried that to no avail w/Ubuntu.

J T

---

### Post by LostFarmer on 2014-09-19
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)  go down to "via the LiveCD terminal".  Note: this is a old how-to but should still be good for MBR partitioned disk.

You must use the same version of live cd as you have installed.

from the above site:
```
sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda**5**
```  be sure the live cd does not have sda5 mounted, if it is unmount it. ( can use 'disk' to do so)
grub-install will complain about installing grub to sda5 so you will need to use the force switch,.  

```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda5 --force
```

that should put the grub files in sda5 /boot/grub and the grub boot file first sector of sda5.

 I have not used the above method for about 5 years so can not say it still works, but it did work for the first version of grub 2.

the reason you need to reinstall grub from your pastebin report: 
> Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda5 and looks at sector 346908704 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. you changed the layout of the linux partition.

---

### Post by oldfred on 2014-09-19
Part of the issue of block lists with a partition install of grub. You just have to reinstall it more often.
Or one of the disadvantages of EasyBCD is that it makes you install grub in a less reliable method.

---

### Post by Impavidus on 2014-09-20
> **J Tinsby said:**
> As I called out in my original post I am using EasyBCD to start Linux. What struck me was your mention *of multiple drives with a bootloader for each one*. A friend says he did it by accident once but can't recall how he accomplished it! Any advice on doing this? It'd be great to have Ubuntu on it's own drive and Win 7 on the other.

J T
I assume the Windows boot loader in the Windows drive is still intact. You can install grub to the MBR of the Ubuntu drive. LostFarmer described how, but install it to the MBR, not the PBR. To be really sure you install it to the correct drive you can disconnect the Windows drive, but you don't have to. When you start the computer and have instructed the bios to boot from the Linux drive, you'll get a grub menu, offering you to boot either Ubuntu or Windows.

If you disconnected the Windows drive before installing grub, grub won't offer you to boot Windows. grub may not even show its menu. In this case you can reconnect the Windows drive, boot Ubuntu and update grub:```
sudo update-grub
```This will run the OS-prober and add Windows to the menu. This will also happen automatically when you get a kernel upgrade.

In all cases, even when grub has failed for whatever reason, you can change the boot order in the bios to the Windows drive, which will simply boot Windows.

---

### Post by J Tinsby on 2014-09-22
Thanks to all of you that responded, sounds like the change to another HD makes Grub not work, in spite of what Acronis would have me believe. I don't think I ever said that using the Live CD I could easliy see that all my Linux files were there where they should be, it just wouldn't boot. I tried to re-install Grub but was stopped by a message about block-lists not being recommended. i think that ***would*** have worked had I been able to do it. I don't know Linux the way you guys do so I had to stop. 

All I wanted was to know that if this HD craps out I'd have an image, that would work, to fall back on. Looks like that isn't the case <sighs> The only way to tell if your backup scheme works is to TRY it! 

I was able to use the Boot Rescue Disc and have Grub install on the MBR of Windows, that allowed it all to function but not the way I had hoped.

Thanks for all the input and help!

J T

---

### Post by oldfred on 2014-09-22
Boot-Repairs advanced mode lets you install grub to any drive. You choose operating system and choose drive.
Boot-Repair's auto fix installs grub to every MBR, so if you did that you may also have grub in the MBR of sdb also.

If you are trying to install grub to a partition boot sector you have to use --force as again that is not recommended. During Ubuntu install it does not give that message, but any reinstall does.

        >  Attempting to install GRUB to a partition PBR instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force



---

### Post by J Tinsby on 2014-09-22
> **oldfred said:**
> Boot-Repairs advanced mode lets you install grub to any drive. You choose operating system and choose drive.
Boot-Repair's auto fix installs grub to every MBR, so if you did that you may also have grub in the MBR of sdb also.

If you are trying to install grub to a partition boot sector you have to use --force as again that is not recommended. During Ubuntu install it does not give that message, but any reinstall does.

So you're saying that if I had used the Live CD, and installed Ubuntu over itself, I'd have had the choice in the built in Gparted in Ubuntu to put Grub where I wanted?

I cannot agree that the Advanced Mode allows you to put Grub where YOU want it, it'd be wonderful if it did, but my attachments showing the Advanced Mode in use don't bear that out. Note than in Img_0051 the cursor is placed on the box "Place Grub into" and there are no choices.
The Boot Rescue Disc in this instance was run on my main HD, that has XPired, Win 7 and Ubuntu.

Thank you

J T

---

### Post by oldfred on 2014-09-22
You are correct, I just reinstalled Boot-Repair as I had not yet installed it in 14.04 and it only showed sda, sdb, sdc, & sdd but no partitions.

I think this does show partitions but once more  we generally do not suggest installing to a partition. And many users think they are supposed to install to the Windows boot partition and totally corrupt Windows.

This is more like the install from a new install. And will present partition. Back with 10.10 we filed a bug report as it somehow was installing to NTFS partitions regularly. They claim they fixed it, but users still install to NTFS partitions and create major Windows repair issues. 
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by J Tinsby on 2014-09-23
Very interesting information to say the least. I can understand that people would mistakenly choose a windows partition to install Grub if they didn't know where they originally had it using the method I am using. That makes sense to me and I can see why it's not recommended. My restore of Ubuntu will work, if I can simply have Grub back again, I know from running the LiveCD I can see all the files and folders from my restored version on my test HD, they all appear to be there, in fact I even see a Grub folder but it won't allow booting.

The burning question, for me anyway, is where to type the command to re-install Grub if you have NO access to a terminal window? Do I run the LiveCD and choose 'try Ubuntu' and run it from a terminal window there? Or use the LiveCD and choose "Install" and let the installer get me to where I can put Grub where I want it? Of course you can't just quit the install after you do that it would install all the files from the LiveCD. the majority of which will be older than the ones you already are using. As mentioned before, if that Boot Rescue CD allowed you to choose your preferred Grub location I'd be running it every time! Sadly it does not...

So to re-install Grub, if I have no terminal window in my restored version of Ubuntu where do I type
```
sudo update-grub
```

 or I am left at a "Grub Rescue" prompt?


I know its a basic question but that's would solve my problem. I am referring to post #3 in the provided link: [http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Thanks again,

J T

---

### Post by oldfred on 2014-09-23
You can boot into your live install and use Boot-Repair. Or you can manually mount your install including /boot if separte and install grub with just a couple of terminal commands. Note instructions below are mostly comments.
If at grub rescue that is usually a version difference between grub in MBR and grub in install or missing grub.cfg.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)


 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub


And if at grub rescue you should be able to mount partition and boot. You, in effect, manually create a grub boot stanza like you have in grub.cfg.
      
        [https://help.ubuntu.com/community/Grub2#Command](https://help.ubuntu.com/community/Grub2#Command)  & Rescue Mode
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /vmlinuz root=/dev/sdXY ro
      initrd /initrd.img
      boot

More details:
      
 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by J Tinsby on 2014-09-23
Today I made another image backup of my main HD using Acronis 2014. My HD has XPired, Win 7 and Ubuntu on it, normally I have not been making backups of XPired because I rarely use it and never add anything to it. But I decided to backup all 3 partitions and then try and restore just Ubuntu to my spare drive, since it's small in comparison to the others, if it failed I'd start over and restore all 3 of them.

I blew out all the Linux partitions on the spare drive and left them unallocated, and proceeded to install only the 3 Linux partitions to that drive. Wonder of wonders when it was complete I was able to boot to Ubuntu with no trouble.

I don't know what made the difference, someone in the Acronis forum suggested that a when restoring partitions you have to have made a backup all of them, even if you are only restoring one. Why that makes a difference or if it did I can't answer. I intend to delete this restored copy and tomorrow try to restore Win 7 and Ubuntu. I know 7 won't boot initially and will need to have a new MBR made for it, then EasyBCd will have to be installed on 7 to allow it to boot Linux. If I can do all that with success I'll be happy... and worn out!

Thanks to all who helped!

J T

---


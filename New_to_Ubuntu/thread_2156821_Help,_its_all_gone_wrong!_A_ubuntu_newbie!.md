---
title: "Help, its all gone wrong! A ubuntu newbie!"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by snomys on 2013-06-23
This weekend, I took delivery of a new Asus Ultrabook, and I installed ubuntu 13.04 side by side with windows 8, from a pendrive. All seemed to be going well, a restart of the system allowed me to boot into windows or ubuntu from a GRUB menu.

I tried to install the jdk6 from sun, and even though the PATH, JAVA_HOME looked all set, I kept getting the following message when trying to compile code:

The program 'javac' can be found in the following packages: ... a list of pacakges.

Now when I even try to edit .profile I get:
The program 'vi' can be found in the following packages:

Everything seems to have gone wrong!

Also, when restarting my PC, and selecting the windows option, a EFI path is not found, so the only way I can book into windows is through the bios.

Please help.

The laptop has two hard drives, 1x500gb where windows 8 resides, and I put ubuntu on a separate 1x25gb SSD, I need to obviously get these problems nailed one by one, but first off is there an easy way just to wipe ubuntu and reinstall a fresh copy?

Thanks

---

### Post by sudodus on 2013-06-23
Welcome to the Ubuntu Forums :-)

Please try Boot-Repair according to these links

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

---

### Post by newb85 on 2013-06-23
I would get your issues booting Windows nailed down first.  Then, you should be able to use the USB stick you installed with to reinstall Ubuntu.  (If it's not one of the default options, you can choose to do something else, and then reformat the Ext4 as ext4 and set it as "/".)

---

### Post by steeldriver on 2013-06-23
I don't understand why you think you need to reinstall the entire system just because you can't edit your .profile with vi - just use a different editor (nano, gedit)

Of course you can install vi (or vim) if you really want to but it's by no means necessary

---

### Post by snomys on 2013-06-23
Hi

things have gone from bad to worst, after running the boot repair, i tried to resinstall ubuntu and changed the bios to load from the f: (pendrive) which it did, but at the end of the reinstall a message popped up saying fatal error unable to find boot loader on this partition, so i went through the entire list of the available partitions, all came back with the same error. It posted a logging message to ubuntu dev, but now when I restarted,
 
I cant even get into the bios, to change its boot priority, and I get this message:

error: no such device: 16545e06-... . ... .
grub rescue>


I saw a post on this and types ls, which returns:
(hd0) (hd1) (hd1,gpt5)  (hd1,gpt4)  (hd1,gpt3)  (hd1,gpt2)  (hd1,gpt1)  (hd20 (hd2,gpt4)  (hd2,gpt3)  (hd2,gpt2)  (hd2,gpt1) 

An ls on all of these returns:
error: unknown filesystem.

What can I do? I cant even get into the bios, it wont boot from the pendrive...????

Anybody know how I can get this grub rescue to rescue something?

---

### Post by oldfred on 2013-06-23
Did you turn off secure boot?
Did you turn off fast boot or hibernation in Windows.
Some systems only get to UEFI/BIOS from Windows, so if Windows does not boot....

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

If you can get back into Ubuntu live installer, add Boot-Repair again and post link to BootInfo report. Then we can make better suggestions.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sudodus on 2013-06-23
Yes you have big problems.

- But before doing too much, I suggest that you try to ***back up*** at least your personal data (if you have stored any such data yet. If you don't have a backup of the Windows system, you should back up that too (or the whole drive) for example with Clonezilla.

I am surprised that you can't even get into the bios, because that should happen before any operating system is started, and it should be independent of Ubuntu.

- Try again, and see if you can get Windows started

- Maybe it is best to reinstall Ubuntu, but wait and let oldfred help you.

---

### Post by snomys on 2013-06-23
some good news, I managed to get into the bios, and then set a boot from the windows boot.
this allowed me to enter windows, but i couldnt refresh, or reset the pc, hard disk was locked.
i used the ms dos prompt to activate the locked hard disk, and then on a reboot i could get windows to reset.


pheeeeeeeeeeeeeeeeeeeeeeeeew!

dont worry about backing up personal data, its a brand new pc, and all my valuables are on my pendrive!

so, once my windows has reset, im going to have another try to get ubuntu back on there.

can anyone explain the easiest way to do this.

as i say, last time, i loaded for usb, selected install alongside windows 8, but on doing so, i could only boot into ubuntu from grub.

also, i want to put ubuntu on my second hard disk, my main hard disk is windows 500gb, and have a smaller 25gb sdd hard disk, but i found the disk partioning setup in the ubunti installation very confusing. sda1,2,3,4,5 etc, the one that pointed to the 25gb sdd, when selected would not let me add to that node.

i am a noob, obviously this is new territory, but, some sites go on and on about uefi, and windows 8, some guys contradict others that ubuntu can be deployed out of the box to run alongside windows 8, and some say you have to disable uefi, which as a noob, i opted for the former, not the latter.

so can anyone offer the best way, starting completely fresh, whats the best way to get ubuntu onto my pc, on the 2nd hard disk, alongside windows 8....

thanks in advance

---

### Post by snomys on 2013-06-23
see my latest post, any of your sagely help would be greatly appreciated. this uefi stuff, doesit need to be swithed off, i installed last time without tampering with it, but as i say, then in starting up, grub didnt show an option for botting windows.

---

### Post by oldfred on 2013-06-23
If Windows is in UEFI mode then you need to have Ubuntu in UEFI mode. If you were just booting Ubuntu then it probably was just in BIOS mode not UEFI.
How you boot installer is how it installs. Or if you boot in BIOS mode then it installs in BIOS mode.

See link in my signature for a lot of the standard UEFI info and a couple of links to details with screen shots. If an UltraBook you have the added complications of dual video & Intel SRT which are separate from UEFI but create install issues.

What model Asus? One model so far has not been able to dual boot with UEFI. Or only installs and works in BIOS mode. The issue is only the video and how UEFI reports it so Asus should have a UEFI/BIOS update for that mode. 
 Asus K55N just does not boot Ubuntu in UEFI mode. Some things to try, but no solution
[http://ubuntuforums.org/showthread.php?t=2137233](http://ubuntuforums.org/showthread.php?t=2137233)

Other Asus have worked.
      
   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

---

### Post by sudodus on 2013-06-23
If I understand correctly, you have already installed Ubuntu in standard BIOS mode, and you could boot it, as well as Windows, but that way you must switch the BIOS mode to do it.

It might be harder to make an installation in UEFI and make it dual bootable with Windows. I did it last April, and I needed help from the Boot-Repair script and *oldfred*.

I think it is important to switch off

- secure boot
- fast boot
- maybe also Windows hibernation 

See this link about hybrid hibernation[URL="http://ubuntuforums.org/showthread.php?t=1769482&page=52&p=12608496#post12608496"]

http://ubuntuforums.org/showthread.php?t=1769482&page=52&p=12608496#post12608496[/URL]

Good luck :-)

---

### Post by snomys on 2013-06-23
Hi

Thanks OLDFRED!

Maybe OLD should be changed to WISE :P

Well this model is the asus ux32a i7 500gb 25ssd model

Any issues with this?

So, do I just boot and install ubuntu like the installation notes for 13.04 suggest from a pendrive?

Please point me to the noob-iest way of doing this please!

Thanks

---

### Post by snomys on 2013-06-23
Hi

Right now, Ive got my pc back to being windows 8 only. Both the 500gb and 25gb ssd are in original condition, I have ubuntu 13.04 on pendrive and have unetbootin ready.

---

### Post by oldfred on 2013-06-23
I have not seen that specific model, but there are many. I would think it would  be similar to the link on US31A. Some users have posted more info than others.

Are you installing Ubuntu to 25GB SSD? Then you will not be using Intel SRT to speed up Windows. Also you need to know which video Intel or nVidia you are using. Some have UEFI/BIOS that lets you set it to be one or the other and that often helps during install. But I do not know all the details on that.

If you have made a Windows repair disk or know how to recover Windows, or have a good backup of Windows, just shrink Windows using Windows disk tools and reboot so it can run chkdsk or make other repairs. You may have to run the commands to remove RAID (from Intel SRT) on both drives so it correctly installs. You may need boot parameter like nomodeset with grub menu for both install and first boot if using nVidia chip.
Then with secure boot off Ubuntu should just install if booted in UEFI mode.
You then have to run Boot-Repair to make some fixes.

See link below for more info and details. 

 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2013-06-23
I would like to add something. You have two disks. Right? You have Windows on one disk and you want Ubuntu on the other (25GB SSD). Right? Once Windows is working disconnect the Windows disk (after shutting down Windows) and only have the 25Gb SSD working in the machine. Then there will less confusion with the installer. It will only see one drive.

Once Ubuntu is installed and up and running, plug the other drive in and use the BIOS to boot into the Ubuntu SSD and once you are at a desktop open a a utility called Disks (find in the Dash - windows key). And see what lables you get for both the disks. Note down which is called sda and which is called sdb. This is important. If the Ubuntu drive is called sda then open a terminal (in the Dash) and run

```
sudo update-grub
```

That should detect the Windows drive and put Windows in the Grub boot menu. If the menu does not change run this

```
sudo grub-install /dev/sda
```

but only if sda is the Ubuntu drive. If Ubuntu is listed as sdb then run

```
sudo grub-install /dev/sdb
```

Regards.

---

### Post by oldfred on 2013-06-23
If an UltraBook, it is a portable and may not be easy to disconnect hard drive.

Often SSD is either soldered into motherboard or is actually part of hard drive even though seen as a separate device. 

But if possible to disconnect hard drive that avoids issues of corrupting Windows.

---

### Post by mastablasta on 2013-06-24
> **oldfred said:**
> Often SSD is either soldered into motherboard or is actually part of hard drive even though seen as a separate device. 
.

yup, some have hybrid drives. SSD rests on top of the drive.

btw to the OP

sda1 - means disk "a", partition 1
sda2 - means disk "a", partition 2
...

sdb1 - means disk "b", partition 1

windows marks partitions and drives with letters, so it's not clear there immediatelly what is a partition and what is actually a separate disk.

---

### Post by snomys on 2013-06-25
Hi again

I am kind of convinced going for dual boot with windows 8 and ubuntu is not the best way to go, so Im thinking about removing window8 altogether and going fully ubuntu. In doing so, are there any pitfalls, issues ahead of doing this I should consider? Again, regarding the two hard disks, would they both be accessible under ubuntu?

Look forward to your responses.

I believe I can just put windows on a VM should I need it for any reason in the years ahead!

---

### Post by oldfred on 2013-06-25
A few have totally removed Windows 8 and it worked.
But you need to be sure your system works acceptably well with Ubuntu. Some hardware is better supported than others.

Also you must turn off secure boot and fast boot in Windows. 

Some systems only can get into the UEFI/BIOS from Windows when fast boot is on. It skips the checking on whether you want to go into UEFI/BIOS to make Windows a second or two faster. But then when Windows does not boot, system is bricked. Some have had to send system back to vendor. Originally thought to be a Linux issue but then found that Windows could also cause the same issues.

---

### Post by snomys on 2013-06-25
I just really wish, there were more clearly defined postings on how to install ubuntu alongside windows 8. after my last attempt, it kind of scared me that i need to sit beside a ubuntu guru to get the job done.

---

### Post by oldfred on 2013-06-25
There are two threads that show details with screen shots in the link in my signature. And some links by computer brand where a few users posted exactly what they did.

---


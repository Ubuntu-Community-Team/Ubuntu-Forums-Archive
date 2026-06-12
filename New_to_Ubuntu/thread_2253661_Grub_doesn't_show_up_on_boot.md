---
title: "Grub doesn't show up on boot"
date: 2014-11-21
forum: New to Ubuntu
---

### Post by zair2 on 2014-11-21
Hi,

When I boot up my laptop with Windows 8.1 preinstalled (and Ubuntu since yesterday), it boots straight into Windows. I've pressed and held down SHIFT at boot and Grub still doesn't show up. I've disabled UEFI mode. I know that Ubuntu is installed because the partition shows up on Windows Disk Management and when I boot from LiveCD, it acknowledges that Ubuntu is installed (asking me if I want to uninstall, repair or reinstall Ubuntu) and it lets me access the files on the relevant partition. However, there is no other indicator of Ubuntu being installed on my laptop. 

I have attempted to repair Grub following this website: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

Unfortunately, it gave me an error at the 2nd step after mounting the drive. 

Any help is appreciated, thanks.

---

### Post by zair2 on 2014-11-21
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]When I boot up my laptop with Windows 8.1 preinstalled (and Ubuntu since yesterday), it boots straight into Windows. I've pressed and held down SHIFT at boot and Grub still doesn't show up. I've disabled UEFI mode. I know that Ubuntu is installed because the partition shows up on Windows Disk Management and when I boot from LiveCD, it acknowledges that Ubuntu is installed (asking me if I want to uninstall, repair or reinstall Ubuntu) and it lets me access the files on the relevant partition. However, there is no other indicator of Ubuntu being installed on my laptop. [/COLOR]

[COLOR=#000000]I have attempted to repair Grub following this website: [/COLOR][http://howtoubuntu.org/how-to-repair...ubuntu-live-cd]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")

[COLOR=#000000]Unfortunately, it gave me an error at the 2nd step after mounting the partition. [/COLOR]

[COLOR=#000000]Any help is appreciated, thanks.[/COLOR]

---

### Post by grahammechanical on 2014-11-21
Please confirm that you installed Ubuntu after reading this advice

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]


You say that you have disabled UEFI mode. Does Windows 8 still boot? As far as I know, it should not boot. It is my understanding that a pre-installed version of Windows will always be installed in UEFI mode.

It also helps to know which version of Ubuntu you have installed and, more importantly, the hardware specification of your machine. It is being reported that some machines have boot systems (UEFI) set up in such a way that only Windows 8 will load. And this is nothing to do with secure boot. That may be the case with your machine.

What was the error from Boot Repair?

Regards.

---

### Post by grahammechanical on 2014-11-21
Please do not do what you have done. It is bad manners. Here is the post from you with the same problem and it is in the New to Ubuntu section.

[http://ubuntuforums.org/showthread.php?t=2253661](http://ubuntuforums.org/showthread.php?t=2253661)

In that post I have given all the help that I am going to give you.

---

### Post by oldfred on 2014-11-21
Those instructions look like a chroot for a BIOS/MBR install. With UEFI you need one or two more commands.

What brand/model computer. And what video card/chip?
Some vendors modify UEFI to only boot Windows and we have to create work arounds.

Can you go into UEFI and choose the ubuntu entry? Or from one time boot key often f10 or f12 choose to boot the ubuntu entry?

Is Ubuntu installed in UEFI boot mode? If not you have to go into UEFI/BIOS and turn off UEFI and/or turn on CSM/BIOS boot mode. Then to boot Windows go back to UEFI and turn on UEFI.
Best of both systems are installed in UEFI mode. Boot-Repair can convert a BIOS install to UEFI.

---

### Post by oldfred on 2014-11-21
Threads merged. Please do not create duplicate threads, we all are volunteers and need to know what else has been posted to avoid duplicate suggestions.

---

### Post by zair2 on 2014-11-21
> **grahammechanical said:**
> Please confirm that you installed Ubuntu after reading this advice

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)



You say that you have disabled UEFI mode. Does Windows 8 still boot? As far as I know, it should not boot. It is my understanding that a pre-installed version of Windows will always be installed in UEFI mode.

It also helps to know which version of Ubuntu you have installed and, more importantly, the hardware specification of your machine. It is being reported that some machines have boot systems (UEFI) set up in such a way that only Windows 8 will load. And this is nothing to do with secure boot. That may be the case with your machine.

What was the error from Boot Repair?

Regards.
Yes, Windows 8 boots fine in Legacy Mode. I have installed the latest version of Ubuntu Desktop (14.10) 64-Bit. The specifications of my laptop are [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03879983&tmp_task=prodinfoCategory&cc=uk&dlc=en&lc=en&product=5378632](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03879983&tmp_task=prodinfoCategory&cc=uk&dlc=en&lc=en&product=5378632) 

The Boot Repair error told me to reboot in EFI mode and run Boot-Repair; I have turned on UEFI mode and it won't let me select the DVD drive to boot from, so I cannot access the liveCD.

> **oldfred said:**
> Those instructions look like a chroot for a BIOS/MBR install. With UEFI you need one or two more commands.

What brand/model computer. And what video card/chip?
Some vendors modify UEFI to only boot Windows and we have to create work arounds.

Can you go into UEFI and choose the ubuntu entry? Or from one time boot key often f10 or f12 choose to boot the ubuntu entry?

Is Ubuntu installed in UEFI boot mode? If not you have to go into UEFI/BIOS and turn off UEFI and/or turn on CSM/BIOS boot mode. Then to boot Windows go back to UEFI and turn on UEFI.
Best of both systems are installed in UEFI mode. Boot-Repair can convert a BIOS install to UEFI.

The specifications can be found [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03879983&tmp_task=prodinfoCategory&cc=uk&dlc=en&lc=en&product=5378632](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03879983&tmp_task=prodinfoCategory&cc=uk&dlc=en&lc=en&product=5378632) 

I can enter the "GNU GRUB" screen through the EFI file in the boot (sorry if I am saying something wrong, I am a complete novice at this!), in this screen it offers me the option of trying ubuntu, installing ubuntu and checking my disc for errors (which I did, and it said there were no errors).

I think I must be doing something wrong with the UEFI mode since both you and the user above have both commented that I shouldn't be able to boot into Windows with UEFI mode off. However, when I turn legacy mode on, it makes no difference.

I'm fairly sure Ubuntu isn't installed in UEFI mode; when I installed using the LiveCD I turned off UEFI mode. However, I am not sure if that makes a difference.

---

### Post by oldfred on 2014-11-21
HP only boots Windows. They modify UEFI to only let you boot an entry with Windows in the description. 
But they still will boot a hard drive so we have several work arounds so you can boot.

Most seem to rename bootx64.efi. 
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
      
 script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

    But not really difficult to manually copy a couple of files and rename.

  Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

      
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP manually renamed bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[URL="http://ubuntuforums.org/showthread.php?t=2218154"]http://ubuntuforums.org/showthread.php?t=2218154
[/URL]
 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

[URL="http://ubuntuforums.org/showthread.php?t=2218154"]
[/URL]

---

### Post by zair2 on 2014-11-21
> **oldfred said:**
> HP only boots Windows. They modify UEFI to only let you boot an entry with Windows in the description. 
But they still will boot a hard drive so we have several work arounds so you can boot.

Most seem to rename bootx64.efi. 
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
      
 script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

    But not really difficult to manually copy a couple of files and rename.

  Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

      
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP manually renamed bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[URL="http://ubuntuforums.org/showthread.php?t=2218154"]http://ubuntuforums.org/showthread.php?t=2218154
[/URL]
 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

[URL="http://ubuntuforums.org/showthread.php?t=2218154"]
[/URL]

Sorry I'm confused, could you be a bit more clear on how I should go about fixing this issue? I'm very new to this sorry.

---

### Post by oldfred on 2014-11-21
You keep saying you are in BIOS/Legacy/CSM mode, but all Windows 8 systems that are pre-installed are in UEFI boot mode. Some just auto switch to correct mode regardless of settings.

Just to confirm first, post the link to the summary report from Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

All those links show various work arounds. Most popular for HP seems to be the copy of grub files into /efi/Boot folder, rename bootx64.efi and then rename grubx64.efi to bootx64.efi. Then you can set & boot hard drive entry from UEFI menu.
If later you do get a major update to grub, you may have to copy it again so you have correct version.

---

### Post by zair2 on 2014-11-21
> **oldfred said:**
> You keep saying you are in BIOS/Legacy/CSM mode, but all Windows 8 systems that are pre-installed are in UEFI boot mode. Some just auto switch to correct mode regardless of settings.

Just to confirm first, post the link to the summary report from Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

All those links show various work arounds. Most popular for HP seems to be the copy of grub files into /efi/Boot folder, rename bootx64.efi and then rename grubx64.efi to bootx64.efi. Then you can set & boot hard drive entry from UEFI menu.
If later you do get a major update to grub, you may have to copy it again so you have correct version.
[http://paste.ubuntu.com/9155509](http://paste.ubuntu.com/9155509)

---

### Post by yancek on 2014-11-21
You've mixed MBR and UEFI.  Look at the bootrepair output you posted.  At the very top it shows Grub is installed to the mbr (master boot record) of sda.  Then scroll down to the section under sda2.  At the very top of that section you will see two entries for Ubuntu efi boot files.  Further down are some entries for HP and below that the windows entries.  You can't successfully mix an MBR install with EFI.  You should have not installed Grub to the mbr.  I don't use uefi myself so don't know how to repair that but I'm sure oldfred or some other member familiar with it will have some good advice.

---

### Post by zair2 on 2014-11-21
> **yancek said:**
> You've mixed MBR and UEFI.  Look at the bootrepair output you posted.  At the very top it shows Grub is installed to the mbr (master boot record) of sda.  Then scroll down to the section under sda2.  At the very top of that section you will see two entries for Ubuntu efi boot files.  Further down are some entries for HP and below that the windows entries.  You can't successfully mix an MBR install with EFI.  You should have not installed Grub to the mbr.  I don't use uefi myself so don't know how to repair that but I'm sure oldfred or some other member familiar with it will have some good advice.

What would I do different if I was to remove Ubuntu and try again to install it? Since all I did was follow the instructions on the screen.

---

### Post by oldfred on 2014-11-21
Boot-Repair will convert install to UEFI boot.
You always need to boot in UEFI mode not CSM/BIOS mode.

If you decide to reinstall only use Something else.
Best to to have Windows fully backed up.

       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---


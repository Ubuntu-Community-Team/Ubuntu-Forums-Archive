---
title: "ubuntu installation on hp laptop got stuck"
date: 2019-02-27
forum: New to Ubuntu
---

### Post by Murat SEVG&#304;L on 2019-02-27
Hi… &#305;ve been using ubuntu on my desktop computer for years now..now i want to install it on my hp laptop ...i changed  bios settings disabled secure boot enabled legacy mode..made a bootable usb with the help of rufus...now grub menu appears and says try ubuntu,install ubuntu etc..im choosing install it anyway and managed to choose keyboard layout network password etc and came to install the ubuntu alongside windows …...chose install it alongside windows a warning pops up warning me this process may take time but after two hours the cursor still blinks and no sign of progress…

P.S.prior to installing or trying to install i edited a line in grub and changed quiet splash to nomodeset because i saw in a post it worked……..

Is there anyone having the same issue?..Any help is appreciated

---

### Post by Impavidus on 2019-02-27
Install should take about 15 minutes. nomodeset may be necessary (initially) depending on your graphics hardware. Did you get a black screen without it?

You write you enabled legacy mode and tried to install alongside Windows. There's at least one problem. You imply that Windows is installed in UEFI mode. For a dual boot, both must be installed in the same mode. HPs don't like to boot Ubuntu in UEFI mode, but there are some workarounds. Search the forums or wait for someone to give more details.

Which Windows version? Which Ubuntu version? How is the hard drive partitioned? It's recommended that you use Windows tools to create unallocated disk space, then let Ubuntu install there.

---

### Post by Murat SEVG&#304;L on 2019-02-28
Hi impavidus…Thank you for your interest.First things first excuse my huge ignorance and lack of knowledge ...Let me tell the specifics about my computer first...its an hp laptop windows 10 home single language edition installed..there are 2 hard disk drives one is 128 gb ssd and the other is normal hd about 1 tb..when i look at the device manager i see two entries :one is intel hd graphics 620 and the other is nvidia gforce 940 mx....Actually when i was trying to install ubuntu 18.10 installation started i was able to adjust my country and the keyboard layout but after i chose install it alongside windows 10 the cursor started to blink and although i waited one hour installation got stuck and the only thing i could see was blinking cursor.....

And at this point i force shut the laptop and inserted another flash drive...now it was disaster running windows os collapsed too….and it didnt end with that..i tried to reinstall windows 10 and now surprise time when i chose my country and the keyboard layout this time windows installation got stuck because of a ''missing device driver'' problem.....i googled this and spent hours but all the solution options unplugging and replugging  or inserting it to another port didnt help...at long last i found a friend who had several windows isos and reinstalled windows again…..

Now the thing which i dont understand is......i used the same flash drives and the windows and ubuntu isos in my desktop computer and i easily and without any of these problems installed both of them and now using them with dual boot ….the partitioning you mention i did not do any partitioning prior to install ubuntu on my desktop computer ..the installation itself does the partitioning i just choose install it alongside windows 10....

as i mentioned prior to installing on laptop i made the necessary adjustments about bios (disabling secure boot,enabling legacy mode) etc...but i dunno for what reason installation freezes at the install now screen……

now the websites and my friend are saying the isos or the flash drives may be corrupted……….

So now i am afraid of trying to reinstall ubuntu for fear that i could break down windows 10 too.What do you suggest now?Thanks a lot......

---

### Post by Frogs Hair on 2019-03-01
If Windows is up and running post a snip/screen-shot of your partition table from the disk utility. Factory partitioned HP computers can be difficult to dual boot and you may not be able to easily shrink a partition to create free space for Ubuntu manually or automatically.

---

### Post by yancek on 2019-03-01
If you have a laptop with windows 10, was it pre-installed?  If so, it is undoubtedly using UEFI.  If you re-installed, did you re-install UEFI?  Dual booting windows 10 and Ubuntu UEFI is explained at the Ubuntu site below and I would suggest you read it before trying anything else.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The Install Alongside windows is a poor option with an EFI install.  Use the manual (Something Else) option.  You need to have unallocated space on the drive on which to install Ubuntu in either case so you should use the windows Disk Management tool to shrink the largest windows partition to make unallocated space.  It can't install "Alongside" if all the space is taken up by windows partitions which is the standard with any windows install.  After shrinking the windows partition, reboot windows and run chkdsk to verify there are no problems before trying to install Ubuntu.  Posting the info requested above would be useful.

---


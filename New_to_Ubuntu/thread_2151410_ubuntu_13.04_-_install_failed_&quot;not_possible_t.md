---
title: "ubuntu 13.04 - install failed &quot;not possible to install bootloader at the specific&quot;"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by bobrafa on 2013-06-04
I've got ubuntu 13.04 on a usb stick.  I have a 60 Gig hard drive in my computer that is completely blank.
I want to install ubuntu on this drive.
When I boot from the usb thumb drive I can start ubuntu 13.04.
When I go to install the operating system it gets all the way to installing the "bootloader"
Then I get the following message
"Not possible to install bootloader at the specified location"
      then there are 2 radio buttons
      "continue without bootloader"
      "cancel the installation"

I tried installing the bootloader to another drive but no luck.
I really want the bootloader on my 60 Gig drive and want to use the F8 key at boot to select this drive and boot directly from it.
I don't want a "dual boot" system installed on my C: drive where windows 7 pro is installed.

I checked the drive in the program mini tool partition wizard:
Here's what it says about the drive:
    49.5 Gig, primary active partition, format Ext4
     7.7 Gig, logical, format Linux Swap
        2 Meg unallocated.

What do I need to do to get the bootloader on this drive so that I can boot to ubuntu using the F8 key on my system at boot time??

Please reply

---

### Post by grahammechanical on 2013-06-04
The installer will default to installing the Grub bootloader into the MBR of the first hard disk (sda - sata disk a). If the Windows disk drive is sda then the Ubuntu installer is trying to install Grub into sda unless you have directed it to the 60GB drive that may be called sdb.

Are you using the Do Something Else option and are you instructing then installer to put Grub into the MBR of the correct disk? You could try installing with the Windows drive disconnected. Then the 60GB drive will be the only drive and it will be sda and the installer might automatically get it right.

Regards.

---

### Post by bobrafa on 2013-06-04
grahammechanical,

Thanks so much for the reply.  
Here's the deal on my system.
I have 5 Hard Drives installed.
The C: drive is an small SSD with only windows on it.
The other drives have my applications and data.
If I allow the installer to install grub to my C Drive will that create a "duel boot system"?
I don't want a duel boot system.  I want to use the F8 key to load the 60GB HD and boot from it.

I did try the Do Something Else option the first time I installed and tried to direct it to the 60GB drive but it didn't work.
I guess I could disconnect all 5 drives and then try install but that sounds like a hassle.
So what I need to do is get Disk #6 (the one I'm trying to install to) set up with a Grub MBR, right?
There must be a "work around" to do with without having to disconnect all 5 other internal HD's
By the way what does sda mean?

Thanks for the reply I really appreciate it.

Bobrafa

Thanks for the reply

---

### Post by gordintoronto on 2013-06-05
In Linux, drives and partitions get names which are vastly different from in Windows. The first drive is usually /dev/sda, and the first partition is typically /dev/sda1

If you are installing Ubuntu onto the sixth hard drive in your system, it might be called sdf, and that is a good place to put GRUB. It will probably still be a dual-boot system, because the installation will detect that Windows is present, but it will only show up if you select that drive as the boot device. If I'm correct, you could make it the default boot device, and still select Windows at boot time -- and your SSD will not be affected.

---

### Post by bobrafa on 2013-06-05
Thanks gordintoronto,

When I boot to windows all I get is windows.  The screen flashes a couple to times and a get a bump,bump,bump sound.  But there's not duel boot.
You are correct that the 6th drive is called sdf.  It has a primary partition and a linux Swap partiton.  But it's does not show up as a systems drive.
I'm assuming that it does not have a MBR on it.
How can I tell if Grub is installed to the dev/sda which my my ssd that has windows on it?
I formated the drive with ext4 and tried several times to install ubuntu 13.04 to it.
How do I create a MBR on sdf make it a systems drive and install Grub.
I'm lost.  
Too many years with windows and I hate windows. 
Ho

---

### Post by Mark Phelps on 2013-06-05
The BEST way to do this is what you already called a "hassle" -- disconnect ALL but the drive for Ubuntu, and installation will be a breeze.  If you accidentally install GRUB to a Windows drive, you will inherit a much bigger "hassle" to remove that, reinstall the Windows MBR to that drive -- and you will then have to reinstall GRUB properly.  A few minutes disconnecting and reconnecting drives is a lot less work than hours removing and replacing GRUB.

---

### Post by bobrafa on 2013-06-05
Mark,

Ok, this sounds like the best option.
I will disconnect all 5 of the other drives and boot from my thumb drive and install on to the 60 Gig.
Last couple of questions question.  I think that GRUB is already installed on my windows boot drive at C:.
Is there anyway to tell if GRUB is installed on my boot drive?
An if so is there a way to remove it?

Bob Rafalovich

---

### Post by Mark Phelps on 2013-06-05
> **bobrafa said:**
> Is there anyway to tell if GRUB is installed on my boot drive?
Actually, one way is to disconnect all the drives containing Linux partitions (presuming you're looking for GRUB on a Windows drive) and then reboot.  Since the working GRUB code is actually resident in a Linux filesystem partition, if GRUB still points to that, the booting will not succeed.  You will get some kind of error message, or quite possibly, something like "GRUB>"
> An if so is there a way to remove it?
Actually, there is.  Using Win7, utilize the Backup feature to create and burn a Win7 repair CD.  Then, with only the suspect drive connected, boot using that CD and proceed to the Command Line.  Then enter the command "bootrec.exe /FixMbr".

For more details on Win7 boot repairs, see the following link (from the Win7 forums): [http://www.sevenforums.com/tutorials/104341-bootmgr-missing-fix.html]("http://www.sevenforums.com/tutorials/104341-bootmgr-missing-fix.html")

---

### Post by bobrafa on 2013-06-05
Thanks Mark you've been a great help

---

### Post by gordintoronto on 2013-06-05
> **bobrafa said:**
> ...You are correct that the 6th drive is called sdf.  It has a primary partition and a linux Swap partiton.  But it's does not show up as a systems drive.
I'm assuming that it does not have a MBR on it.
How can I tell if Grub is installed to the dev/sda which my my ssd that has windows on it?
I formated the drive with ext4 and tried several times to install ubuntu 13.04 to it.
How do I create a MBR on sdf make it a systems drive and install Grub.
I'm lost.  
Too many years with windows and I hate windows. 
Ho

When you turn on the computer, lean on the Shift key. If the boot drive contains Grub, you will see a Grub menu.

Your sixth drive contains an MBR unless it is a GPT drive. If you Google GPT you will discover more than I want to know about it.

During installation, you can say "something else" about partitioning. Then you explictly set up at least the / (root) partition, and can specify where to put Grub. Put Grub on sdf, since you are really controlling things from the BIOS. Actually, you can just leave the BIOS pointing to that drive, and select Windows from the Grub menu.

---

### Post by bobrafa on 2013-06-06
I never in my life had more trouble installing an operating system.  I've installed every version of windows. Done several installs and up dates on Mac. computers.
And even did an install on a Unix once a long time ago.
Here's what's happening:
Just bought a new sata cd rom because the computer would not boot from the IDE dvd/cd rom I had installed.  Something about the pci ide controller that I had installed.
So I'm able now to boot to the ubuntu install disk via my CD (before I was using a 15 gig usb thumb drive), which probably didn't matter

So I opened the case and disconnected all 5 internal HD's.
The drive I want to install ubuntu is a 60 gig 3.5 IDE that running via an "Easy 2.0 IDE" external device via a USB port.
So I installed ubuntu and this time the install seemed to go fine.
At the end of the install it asked me to reboot.
I removed the CD from the new sata dvd/cd drive.
I booted the computer.
Only the 60 gig drive connected via USB 2.0 external adapter no other drives.
It started to load then stopped with the following messages:
error:invalid arch-independent ELF magic.
error: hd1 cannot get C/H/S values.
error:you need to load the kernal first.

So I'm assuming that Grub got loaded but now what.

I'm not done trying,  but the linux install, in my opinion "sucks".
I'm hoping that once I get it installed I will like the GUI.

Thanks for all your help.

Bob

---

### Post by bobrafa on 2013-06-06
> **gordintoronto said:**
> When you turn on the computer, lean on the Shift key. If the boot drive contains Grub, you will see a Grub menu.

Your sixth drive contains an MBR unless it is a GPT drive. If you Google GPT you will discover more than I want to know about it.

During installation, you can say "something else" about partitioning. Then you explictly set up at least the / (root) partition, and can specify where to put Grub. Put Grub on sdf, since you are really controlling things from the BIOS. Actually, you can just leave the BIOS pointing to that drive, and select Windows from the Grub menu.

Gordintoranto,

I held down the shift key on the boot up of my windows 7 pro. nothing happened, so I'm assuming that GRUB did not get installed on my ssd c drive which only has windows os on it. 

I will look into the MBR thing.  The 60 gig drive is probably over 10 years old so that may be the issue.  

I'm also thinking that since I could not boot from my old CD ROM which was IDE interface that the Asus MB Bios won't allow booting from an IDE device.
The board is a brand new ASUS with Intel processor, no connections for IDE.
I do have one of the 5 internal sata HD's that has nothing on it.
I was going to use it exclusively to store all my video files, but I may try to install again using that drive.

Thanks for your comments, I appreciate them.

Bob Rafalovich

---

### Post by bobrafa on 2013-06-06
Just a quick post to let anyone who is interested know.
Got it to work.
Here is what the issue was.
I was trying to install to a IDE HD that was running on a device that interfaced via a USB2 connection.
The mother board won't recognize the IDE HD running on a USB2 port as being bootable.
So I used one of my internal drives and it installed fine.
STUPID COMPUTER TRICKS!!!

Bobrafa

---


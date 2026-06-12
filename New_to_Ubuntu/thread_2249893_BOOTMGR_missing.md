---
title: "BOOTMGR missing"
date: 2014-10-25
forum: New to Ubuntu
---

### Post by archeryrob on 2014-10-25
OK, I have a old work computer laptop that I wanted to play and learn Ubuntu with. The condition was that I format the hard drive first. So I have a totally blank hard drive. I burnt Ubuntu 14.04.1 to a disk.

Went into BIOS and set CD/DVD as 1, HDD as 2 and USB as 3 and it will still not load the Ubuntu disk to start installing it on the blank system. What do I need to do to start the DVD to load Ubuntu?

All I get on the screen is this
> BOOTMGR is missing
Press Crtl+Alt+Del to restart


---

### Post by Iowan on 2014-10-25
Sounds like the .iso got copied to the disk instead of installed on  it. What shows on the disk if you view it from another computer?

---

### Post by yancek on 2014-10-25
You don't need to format the entire hard drive to install Linux, you just need enough unallocated space on which to install it.
The error you see is from the hard drive and is a windows error so you've overwritten your previous windows install.  Make sure the change to boot the DVD as first priority is saved in the BIOS, that you verified the download was good by doing an md5 checksum after download.  You seem to have another computer available to be writing this so you could try putting the Ubuntu DVD in it to see if it boots to eliminate that as a problem.

---

### Post by rahul25 on 2014-10-25
I prefer you use USB instead of cd, install the universal USB by searching on Google and going to first link  something as easy as  123 download it .  Run the program,  in first option choose the type of ubuntu in second browse to your iso file and in third choose your driver and you are good to go, it is highly recommended with a success rate over 95%  .  Choose USB in boot option and you are done

---

### Post by Iowan on 2014-10-25
> **rahul25 said:**
> ... Choose USB in boot option and you are doneNot always an option - especially on older computers.

---

### Post by archeryrob on 2014-10-25
[ATTACH=CONFIG]257482[/ATTACH]

I burnt the ISO to the DVD-RW from my Win7 machine.

I HAD to wipe the old computer as it was a corporate rule to get the "free" computer. It wants to install on the Win7 machine but not on the Blank Laptop.

---

### Post by archeryrob on 2014-10-25
There is not file "Bootmgr" on the disk, does it need one?

The boot folder is empty execpt for a folder called "grub" and a file called "loopback"

---

### Post by oldfred on 2014-10-25
The "blank" drive still has a Windows boot loader in the MBR. Not quite totally erased.
So for whatever reason it is not booting DVD, it then defaults to hard drive. MBR then tries to load Windows but cannot find a Windows partition to boot from and gives the bootmgr missing error.

A few computers require that you both set DVD as default, but also using one time boot key often f12 but varies by brand to also choose DVD. More to confirm you want to boot something other than hard drive.

Also if corporate locked down system, you may have settings in BIOS that you have to change to allow booting from anything other than hard drive. Or do a full reset of system/BIOS.

What are specs of computer? Brand, model, RAM, video card/chip?

It was about 2006 that computer BIOS started allowing boot from USB flash drive, so if system is newer than that it should also boot from a flash drive. Systems originally with Vista or newer systems should all boot with flash drive. A few later XP systems may also.

---

### Post by archeryrob on 2014-10-25
The computer is about 2008 and a Dell Latitude D620 dual core 4gb memory, i think. 

I got a 32 bit boot repair disk and ran it. It is open in Boot repair and it looks like Ubuntu and it says Lubuntu. The Ubuntu install disk does not autorun when inserted and when I click on "File manager PCManFM" it opens a file manager, but is only showing the C drive and not the CD drive. When I try going up past Home or click on the folder/ button at the bottom File manager closes. I finial hit "go" and "My Computer" and can open the Disk, but I can't see the Wubi.exe file or the AutoRun file

---

### Post by oldfred on 2014-10-25
Are you trying to install wubi? That is not supported past 12.04.

You have to reboot and boot from BIOS the installer, it is not something you run from inside another system.

---

### Post by archeryrob on 2014-10-25
Wubi is the exe file on 14.04.1 LTS that I downloaded. I have tried to run Ubuntu from CD and USB and change BOIS setting to make them the only viable option to load. All I get is BOOTMGR is missing. Is there another option for clearing the HDD better? I only have another Win7 machine and I formatted the disk through a USB interface to SATA to erase it all. Should I install Ubuntu from the Win7 on the 2.5" disk while on the Win7 machine, then relocate it to the Laptop? Will that confuse the installation when its in a new machine?

I don't have many other options right now.

---

### Post by yancek on 2014-10-25
> Wubi is the exe file on 14.04.1 LTS that I downloaded

That executable file will only run on an installed windows operating system.  If you don't have a windows operating system on the computer, it is worthless.  The wubi will install Ubuntu inside a running windows system as a program.  As indicated above, it is not supported any longer.  If you can't boot from a usb/flash drive, then you need to set the DVD dirve to first boot priority in your BIOS.

> There is not file "Bootmgr" on the disk, does it need one?

As indicated above, you still have windows code in the master boot record looking for that file which isn't there because you formatted the partition.
For some reason, your computer does not seem to be able to boot the DVD although you seem to have all the correct files.  Does the DVD drive work with other DVDs?  You should not be getting the Bootmgr error if you are booting from the DVD as that means you are going to the hard drive.

---

### Post by oldfred on 2014-10-25
If DVD boots on other system you can install Ubuntu from it. Just do not install any proprietary drivers that would be for that computer system, not the one you will put hard drive into. If propretary drivers then are needed you can install them after booting. But you may need boot parameters.

And make sure you use Something Else. Otherwise the default installs all put the grub2 boot loader into the MBR of sda. Or the system you install from will not boot Windows anymore, but have similar issue of grub looking for the rest of its install and not finding it. It can easily be repaired, but best not to mess up your working system.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

    

If only Ubuntu installed you will not get grub menu. If it does not boot due to video issues, reboot and hold shift key from BIOS until menu appears. Try recovery mode or add boot parameter depending on system hardware.

---

### Post by archeryrob on 2014-10-25
> **archeryrob said:**
>  I only have another Win7 machine and I formatted the disk through a **USB interface to SATA** to erase it all. Should I install Ubuntu from the Win7 on the 2.5" disk while on the Win7 machine, then relocate it to the Laptop? Will that confuse the installation when its in a new machine?

I did this and removed the 2.5" drive and hooked it to the SATA to USB converter. They ran Wubi on my Win7 machine. Then chose complete installation and choose the hard drive from the computer, knowing its size. It erased everything and when it said reboot to finish installation I un plugged the USB cable when it powered down and it just booted Windows.

Then reinstalled the 2.5" drive in the laptop and set BOIS back to CD and HDD to boot and it loaded fine. The laptop is now up and running with Ubuntu.
Nothing else would work, but this did. :p It's all resolved now

---


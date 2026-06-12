---
title: "Not new to ubuntu yet."
date: 2021-02-14
forum: New to Ubuntu
---

### Post by adrian53 on 2021-02-14
I have two SSD's for this machine. One has 32 bit Windows 8.1, the other, 64 bit Windows 8.1. Not relevent, but the reason for that is my old laser printer wanted a 32 bit system. Printer has been replaced now. I formatted the SSD with 32 bit Windows. It ran, but said on completion, that the SSD was formatted, but showed a capacity about 9GB smaller than it should be.  

I have downloaded, and burnt to a CD ubuntu 20.10, booting with the formatted SSD connected, and the CD I'd burnt, I was a little suprised to see it boot into Windows. Clearly, formatting the SSD has not removed Windows 8.1.

What should I do to get the ubuntu system from the CD, onto the SSD?

---

### Post by oldfred on 2021-02-14
Use Windows tools to shrink the NTFS partition to make space for your Linux partition(s).
Default install is / (root) as ext4 and if UEFI which Windows 8 usually is with gpt partitioning you need to be sure to boot installer in UEFI mode.
Installer will use the same ESP - efi system partition that Windows is using. But with two drives, it may depend on which drive you are installing into. Ubuntu installer wants ESP on first drive it sees, even if installing to second drive.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Shows Windows screens
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 

Lots more info on UEFI installing in link below. You can skip or skim major sections that do not apply.
Do not skip backing up system before making major changes.

---

### Post by mikewhatever on 2021-02-14
First thing you should do is edit the title, second, write a clear description of the problem.

---

### Post by adrian53 on 2021-02-14
This part of the forum is called "New to ubuntu". I have not used ubuntu  before, so would be "new to ubuntu", but, I have not been able to  install ubuntu at this point of time, therefore, I am not yet new to  ubuntu. The title accurately describes the situation.

I have not been able to rectify the first point. The problem is clearly described.

---

### Post by grahammechanical on 2021-02-14
Excuse me, but you do not say that you installed Ubuntu to the SSD. To you it is obvious that you would do so. We can only go by what you actually say. Did you use the Erase disk and install Ubuntu option? That should have wiped Windows 8 from the SSD. The install alongside option is a different matter. It makes a difference whether we install Ubuntu in the same boot mode as Windows. Legacy or UEFI? If the two operating systems are in different boot modes then Windows will still load first and with no option to boot into Ubuntu.

Regards

---

### Post by adrian53 on 2021-02-15
>>> We can only go by what you actually say.

I said I have two SSD's. I said I wanted to install ubuntu. I said I had formatted one of the SSD's. I am saying I see no ambiguity.

Forget I asked. The project I wanted to help, (Gaia), can continue with its Linux only software without my systems support.

---

### Post by yancek on 2021-02-15
Apparently, the OP has left but for those who come acroos this thread in the furture, the size of the drive shown with software used on the system is generally less than what is shown by the manufacturer for several reasons so that isn't really a problem.

Accuracy is important, the OP could not have used a CD as current Ubuntu iso files will not fit on a CD.  Was    it a DVD?  How did the iso get burned to the DVD?  Copying will not work.  Was is a USB?  What software was used to put it on a usb?  With the boot device with Ubuntu on it attached to the computer, the OP doesn't indicate that the device was set to first boot priority in the BIOS that may be the logical reason it booted windows 8.  2 instances of windows 8 were installed so it may be booting the 2nd instance and it doesn't mean the other drive was not formatted.

---

### Post by mastablasta on 2021-02-16
> **adrian53 said:**
> It ran, but said on completion, that the SSD was formatted, but showed a capacity about 9GB smaller than it should be.  

ok so the SSD was formatted with NTFS file system.

> 
I have downloaded, and burnt to a CD ubuntu 20.10, booting with the formatted SSD connected, and the CD I'd burnt, I was a little suprised to see it boot into Windows. Clearly, formatting the SSD has not removed Windows 8.1.


1. you need to select the PC to boot from CD (or rather DVD or USB because only server image fits to CD and that one has no desktop)
2. you need to install the OS and during the install format the empty drive to ext4.
3. after install is complete you need to set he boot order in UEFI/BIOS to always boot from linux drive. that way linux boot loader will recognise both OS and ask if you wan to boot to windows or linux. you cna then set defaults and there are some other cool tricks. 

descriptive title is: "installed Ubuntu but the PC still boots to windows" or " my driver can not be ETX4 formatted" or "how do i prepare the empty SSD drive for linux installation"

don't know which project Gaia you are talking about,. there are so many of them. but i am sure there is a windows version of their software. but anyway there is also a virtualbox option if the application doesn't need some massive computing power: [https://itsfoss.com/install-linux-in-virtualbox/](https://itsfoss.com/install-linux-in-virtualbox/)

---


---
title: "ubuntu does not load from OS page."
date: 2013-07-10
forum: New to Ubuntu
---

### Post by malihini2 on 2013-07-10
I have a new HP laptop with Windows 8-32bit. I did not understand why the download for any win8 machine should be the 64bit choice. So before getting started, I have both 32 and 64 burned to disks and I have tried both. I have been right through the install, but after rebbot, when I get the OS selection page, Ubuntu will not load. The windows boot manager gives me 0xc000007b error, but I have checked the disks for errors and none are found. Has anyone else had this problem? Any solution available?

---

### Post by oldfred on 2013-07-10
Are you sure your Windows is 32 bit? Most UEFI systems are 64 bit. Ubuntu only offers UEFI secure boot with 64 bit as they all are newer systems that will work with 64 bit.
Or is this a Windows RT with locked UEFI that nothing else can be installed into?
What model HP system?

---

### Post by malihini2 on 2013-07-11
Thanks for the reply. Yes! The system is 64 bit! Silly me. :? Its a Pavilion g6 with an AMD A6 CPU. The 64bit version of Ubuntu installed without any fuss, but Widows Boot manger sites 0xc000007b error when I try to use Ubuntu.

---

### Post by ITfromScratch on 2013-07-11
> **malihini2 said:**
> Has anyone else had this problem?

I had this problem with a Dell XPS. I couldn't figure out how to fix it, so I wound up installing [VirtualBox]("http://www.itfromscratch.com/virtual-box-best-virtual-machine/") in Windows 8 to host a virtual Ubuntu machine.

I hope you have better luck than I did getting dual-booting to work.

---

### Post by oldfred on 2013-07-11
Have you used Boot-Repair to fix your install? There are several bugs. One is that the os-prober only creates BIOS chain load entries which do not work with UEFI. Boot-Repair add corrrect entries. I also have info on removing incorrect entries in the thread link in my signature.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by malihini2 on 2013-07-11
Thanks for the suggestion. I'll try it.

---

### Post by malihini2 on 2013-07-12
I burned the boot repair and verified the disk. The start up procedure does not recognize the CD. I can see all the files if I open the disk, but the computer will not boot from it.

---

### Post by oldfred on 2013-07-12
Did you download a 64 bit version and the larger but one for UEFI or new systems?
 Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by leunam12 on 2013-07-12
> **malihini2 said:**
> I burned the boot repair and verified the disk. The start up procedure does not recognize the CD. I can see all the files if I open the disk, but the computer will not boot from it.Just boot from your regular ubuntu CD that you used to install, then add the boot-repair repository, install and run.

[Detailed instructions]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu")

---

### Post by malihini2 on 2013-07-12
Oldfred, I will unistall 12.04 and try 13.04. but will it load to the partition already created for 12.04? 

Leunam12, the boot manger will not boot from the 12.04 CD or the boot-repair disk, all I get is error 0xc000007b.

---

### Post by oldfred on 2013-07-12
Where is error coming from? Is that a BIOS error, or a Windows boot error? (Google seems to only have Windows repair suggestions, but I only looked at titles).
Have you set UEFI/BIOS to boot flash drive or using one time boot key to boot flash drive?

If you have installed and want to use same partitions you have to use Something else or manual install and choose the same partition for / (root) likewise for /home but if you saved anything you will not want to reformat the /home partition. It should find and existing swap partition.
Do not change Windows NTFS partition size except from inside Windows. And do not create any new partitions with Windows as it may convert to dynamic which does not work with Linux.

---

### Post by MartyBuntu on 2013-07-12
> **malihini2 said:**
> Its a Pavilion g6 with an AMD A6 CPU.

Good luck. Couldn't get ATI drivers/Wireless/Bluetooth working all at the same time on mine. For now, I'm stuck with using Linux distros through VirtualBox.

---

### Post by leunam12 on 2013-07-13
At what point do you get this error? How will you try 13.04 if you cannot boot from CD, is this a wubi install? Go to your BIOS and make sure that boot from CD is available and first on the list. If boot from CD is not available at the BIOS settings maybe you have to set BIOS in compatibility mode and also disable secure boot and see if that works.

---

### Post by malihini2 on 2013-07-14
I am sorry, I do not have the time to play techie. I need an OS. I may come back to ububtu if time allows. Thanks for the consideration.

---


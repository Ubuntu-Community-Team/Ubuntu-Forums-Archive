---
title: "Can I install Ubuntu in my PC"
date: 2019-12-22
forum: New to Ubuntu
---

### Post by utpalsarkar on 2019-12-22
I am a web-developer. I am using **Windows** from begging ](*,) . But I am not a huge fan of **Windows** :neutral: . Here is my **PC** configuration, can I install the latest version of Ubuntu (*Or suggests one please*) on my machine? And also I don't want to lose my previous data [-X there in different partition, do I have to delete all partition or can I install it in **C** drive ?

> 
OS Name    Microsoft Windows 10 Pro    
Version    10.0.17134 Build 17134    
Other OS Description     Not Available    
OS Manufacturer    Microsoft Corporation    
System Name    DESKTOP-2MRDDKO    
System Manufacturer    ASUS    
System Model    All Series    
System Type    x64-based PC    
System SKU    All    
Processor    Intel(R) Core(TM) i3-4150 CPU @ 3.50GHz, 3500 Mhz, 2 Core(s), 4 Logical Processor(s)    
BIOS Version/Date    American Megatrends Inc. 1003, 10/24/2014    
SMBIOS Version    2.7    
Embedded Controller Version    255.255    
BIOS Mode    Legacy    
BaseBoard Manufacturer    ASUSTeK COMPUTER INC.    
BaseBoard Model    Not Available    
BaseBoard Name    Base Board    
Platform Role    Desktop    
Secure Boot State    Unsupported    
PCR7 Configuration    Binding Not Possible    
Windows Directory    C:\Windows    
System Directory    C:\Windows\system32    
Boot Device    \Device\HarddiskVolume1    
Hardware Abstraction Layer    Version = "10.0.17134.1"    
User Name    DESKTOP-2MRDDKO\Utpal Sarkar    
Installed Physical Memory (RAM)    6.00 GB    
Total Physical Memory    5.87 GB    
Available Physical Memory    2.08 GB    
Total Virtual Memory    9.50 GB    
Available Virtual Memory    2.79 GB    
Page File Space    3.63 GB    
Page File    C:\pagefile.sys    
Kernel DMA Protection    Off    
Virtualization-based security    Not enabled    
Device Encryption Support    Reasons for failed automatic device encryption: TPM is not usable, PCR7 binding is not supported, Hardware Security Test Interface failed and device is not InstantGo, Un-allowed DMA capable bus/device(s) detected, TPM is not usable    
Hyper-V - VM Monitor Mode Extensions    Yes    
Hyper-V - Second Level Address Translation Extensions    Yes    
Hyper-V - Virtualization Enabled in Firmware    Yes    
Hyper-V - Data Execution Protection    Yes    

---

### Post by SeijiSensei on 2019-12-22
I recommend you download the Windows version of VirtualBox, then [create a virtual machine]("https://www.virtualbox.org/manual/UserManual.html#Introduction") and install Ubuntu to that. See if you like it. I prefer Kubuntu, the version of Ubuntu with the KDE desktop, but that's a matter of taste.

[https://download.virtualbox.org/virtualbox/6.1.0/VirtualBox-6.1.0-135406-Win.exe](https://download.virtualbox.org/virtualbox/6.1.0/VirtualBox-6.1.0-135406-Win.exe)

[http://cdimage.ubuntu.com/bionic/daily-live/current/](http://cdimage.ubuntu.com/bionic/daily-live/current/)
[http://cdimage.ubuntu.com/kubuntu/bionic/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/bionic/daily-live/current/)

The "bionic" distribution (18.04) has "long-term support."  Interim versions like 19.10 have support for nine months.

---

### Post by oldfred on 2019-12-22
I do not have Windows and have multiple Linux installs on my Haswell based system.
       Asus  Z97-AR, i5 processor, 8GB RAM, small SSD & HDD.

It does not look like you have updated UEFI to latest available. You should do that whether installing Ubuntu or not.

I have not tried VirturalBox, yet, but plan to. 

    
I use the LTS - long term support version as main working install or currently 18.04. Next LTS will be 20.04 and daily live updates to it are available, but it is changing a lot, so log files & updates are large. I have 20.04 to see what changes it has. 
Unless hardware is very new & you need the very new kernel & drivers in the 6 month releases, best to stay with LTS versions.

Did you install Windows in UEFI or BIOS boot mode? It really should be UEFI.
But you want Ubuntu in same boot mode as Windows.

More info on UEFI install in dual boot mode in link below in my signature.

---

### Post by Dennis N on 2019-12-22
I have Asus H97 motherboard with the same processor as yours, Intel Core i3-4150. You will need a newer BIOS than 10/2014 if you plan to use NVMe SSD. The NVMe support arrived in 2015 BIOS versions. And it will boot from the NVMe drive. But, I recollect that not all Asus boards using Haswell can be upgraded to support NVMe boot - only the Z97 and H97 will. Check on that. Of course, you could always using SATA SSDs if necessary.

---

### Post by TheFu on 2019-12-22
+1 for using virtualbox in the beginning.  It doesn't risk anything in your Windows install, just storage space.  Inside a VM, I'd stay away from the default Gnome3 Ubuntu desktop.  Almost any other flavor would be fine, provided you go with 18.04.  With a VM, the hostOS (Windows for you) would hide any funky hardware from the GuestOS, Ubuntu-whatever.  You won't need to deal with network drivers, wifi drivers, new/old GPU drivers. All of that is hidden because the virtual machine hypervisor provides extremely well-supported virtual hardware.  For the best VM performance, choose virtio for both networking and disk hardware to be presented to the guest machine.

Understanding the Ubuntu release cycles is important for a software developer.  If you aren't specifically working on Ubuntu software, use only LTS versions.   Explanation: [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

Any desktop variant can run all the Linux server software, so don't worry about that.  

One last, but very important thing.  "C: drive" is an incorrect term.  C: is actually a partition.  So is "D: Drive" - partitions, both of them.  In Windows that doesn't appear to matter too much, but in every other OS, confusing a "drive" with a "partition" will have catastrophic outcomes.  If you don't go with the virtual machine method, then you'll need to understand those differences BEFORE installing.  If not, it is very common to wipe Windows accidentally.  If you don't use a virtual machine setup, be certain you have backups for anything, everything, you don't want to lose.  That would be boot partition, OS partitions, data partition, and all the data inside each.

---

### Post by utpalsarkar on 2019-12-22
Thanks to all! [URL="https://ubuntuforums.org/member.php?u=1037685"][B][COLOR=#000000]
@TheFu [/COLOR][/B][/URL]Your explanation was awesome!

---

### Post by yancek on 2019-12-22
If  you eventually decide to install Ubuntu with windows, I would suggest that you read through the Ubuntu documentation below which is very thorough on dual booting with the most recent version of windows.  Skip the parts about installing UEFI as your machine is Legacy.  A bit unusual for 10 unless it wasn't preinstalled?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> can I install it in **C** drive ?

NO, not if you want to use Ubuntu.  You need a Linux filesystem

---

### Post by TheFu on 2019-12-22
> **yancek said:**
> 
NO, not if you want to use Ubuntu.  You need a Linux filesystem

Just for clarity - No is the answer if you don't use virtualization and directly install any other OS next to your Windows installation. Lots of caveats exist when doing that. Most important is to make backups of anything you cannot lose.

OTOH, if you do use virtual machines, then a block of storage, say 15-30G in size "somewhere" inside Windows will be needed for the block storage that the Ubuntu Guest uses.

---

### Post by RobGoss on 2019-12-22
Hello and welcome, My question to you would be are you planing on using Windows at all on this machine?

I would say what ever machine your using you can just add another **drive ** maybe a **SSD** if possible and install Linux / Ubuntu on that, this way you won't mess anything up on the **Windows **drive, simply unplug the Windows drive and plug the Linux drive in and install Ubuntu on it. if for some reason you do not like Linux just remove the Linux drive plug your Windows drive back in and no harm done

---

### Post by sdsurfer on 2019-12-23
^^ That is what I did. I maintain two drives, the Windows drive is more or less storage, almost never go back to it.

Alternatively you can run Ubuntu directly from the disk (CD/DVD) to test it out, no install necessary.

---

### Post by bunny9000 on 2019-12-25
> **sdsurfer said:**
> ^^ That is what I did. I maintain two drives, the Windows drive is more or less storage, almost never go back to it.

Alternatively you can run Ubuntu directly from the disk (CD/DVD) to test it out, no install necessary.

Just make sure you put your boot loader in the right place so you don't pull or wipe the wrong drive and be unable to boot anything.:P Not that I've ever done that of course.

---


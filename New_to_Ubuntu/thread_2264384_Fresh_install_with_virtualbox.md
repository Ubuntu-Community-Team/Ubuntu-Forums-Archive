---
title: "Fresh install with virtualbox"
date: 2015-02-07
forum: New to Ubuntu
---

### Post by danne33 on 2015-02-07
Hello,
I would like to install Ubuntu on my Samsung Series 5 Ultrabook NP530U3C, but still want to possibility to use Windows 8.
As the SSD is only 95 GB, then I was thinking that the disk is to small for dual boot. So I heard something about virtual box could be a possibility.
Could it be a solution to my problem? What do I need to do before I erase my hard drive to install Ubuntu?

I know there is a program called "Wine", but it never worked for my Windows programs. That is why I looking for new solutions.

---

### Post by ajgreeny on 2015-02-07
Do you want to install Ubuntu or Windows 8 as the virtual install?  I think from your post you want Windows 8, and if so, I am sure it can be done but my uncertainties are all about Win 8 and how you would install it.

Do you have a full DVD installation disk for it?
Do you know how to re-activate it after removing it? How you do that is now very different, as far as I can make out, from previous Windows versions as the authorization code is in the machine BIOS/UEFI.

So search fully and look carefully at the VBox site and forums for info on Win 8 as a guest.
[https://forums.virtualbox.org/](https://forums.virtualbox.org/)

I have WinXP running well on my VBox which is on my Xubuntu 14.04 main machine so I will be very surprised if it can not also be done for Win 8, though I have no idea exactly how you do it if you haven't got a full DVD for installation.

---

### Post by SeijiSensei on 2015-02-07
So you have a Win8 installation and want to install Ubuntu in a virtual machine?

The installation will create a file on your hard drive that represents the virtual machine's disk image.  Probably you'll want to allocate at least 10 GB to the VM, so if you don't have that much free space on the drive, you'll need to free up some space. 

If you have a spare USB device, like a 16 GB USB key, you could install the VM on that, but it will run slower than it would on the actual drive.

---

### Post by yancek on 2015-02-07
Another possibility is to install Ubuntu on a flash drive, minimum size probably 8GB but 16GB would be better.  If you want to just test Ubuntu to see if you like it or how it works on your computer you could just put the Live CD on a smaller flash drive, 4GB.

---

### Post by danne33 on 2015-02-07
Thanks for all the answers!
I have now Windows 8 installed on my computer and I really hate it. So I want to install Ubuntu on my computer and have Ubuntu as my main OS. The thing is that I still need to use Windows Programs in my work and there are no Linux alternatives. I use dual boot on my other computers and that works out great but with this computer the hard drive is to small to have dual boot. However I am willing to make a dual boot if that is the only way to solve this problem!
The program Wine is not an option as my Windows programs doesn't work with it. I want to have Ubuntu permanently installed in my Samsung computer and preferably Windows as well. It doesn't matter if it is Windows 8 or some other Windows version! I was thinking the easiest way to solve my problem: is to make a full fresh installment with Ubuntu and then install Virtual box and lastly reactivate my Windows 8, but I am maybe wrong...

My Samsung computer have no CD/DVD-drive. I can only see "C:" on "This PC". However I have 6 partitions on my Samsung computer. One of them is "C:" and the rest are empty (100% free). See attached file. I heard that the empty partitions is used to speed up the system. 
I don't have any spare Windows keys or DVDs. I don't know how to reactivate Windows 8 after removing it. 

I am happy with any solution just as long as my main OS system is Ubuntu and a way to use Windows OS. My Windows programs works well in Windows 8, 7 and XP but not with Wine. There are no Linux alternatives to my programs.

---

### Post by JeQhdMD on 2015-02-07
OK Danne33:   here's a solution which may be the safest and easiest to do (given your knowledge & experience level).   And, that is:

>  Keep Windows 8 installed exactly as it is now, 
>  Download and install Oracle's "VirtualBox" program (see Youtube for how to get it, and how to set it up),
>  Install Ubuntu inside Windows using VirtualBox . . you will have a full functional version of Ubuntu inside Windows,
>  Tweak the Ubuntu install using the method(s) described in the YouTube tutorials (especially the info on how to maximize the display), and the tweaks recommended in this:   [http://www.techdrivein.com/2014/11/2...buntu1404.html]("http://www.techdrivein.com/2014/11/20-things-todo-after-installing-ubuntu1410-ubuntu1404.html")

This way, you'd only have to boot into windows at start-up, and then start the virtual machine with Ubuntu to do your general stuff, switching back to windows only as needed.

The other methods to dual boot may be more complex, especially as your PC is likely equipped with UEFI firmware, making dual-boot setups a bit more "challenging" . . . to say the least.;)

Note:  the main disadvantages of running any VM (virtual machine) on a consumer or private PC is the requirement for ample RAM (at least 2gb,  preferably 4 or more . . . AND . . . advanced GPU operation is not supported well (gaming, CAD, etc.)

---

### Post by whitesmith on 2015-02-07
Another pitfall is that USB support for the guest OS (the one inside the VM) is not possible if you elect to go with the fully open-source VB obtainable through the repos. You'll either need to install that edition and then download the Supported Extras package from Sun or download Sun's PUEL version (recommended). Now (you thought we were through?) you'll probably find that every time the kernel changes, the VM won't work. To fix that:[```
# Download dkms from Software Center,
sudo apt-get purge virtualbox-4.3 dkms linux-headers-$(uname -r)
sudo apt-get install linux-headers-$(uname -r)
# Reinstall the PUEL version and finis!
```VMs are not exactly simple to play with. Hope I've helped.

[EDIT] Your post didn't make clear which OS you want as host. Since you've had bad experiences with Wine, as I have, I presume you want Windows for playing games and running apps that make low-level system calls that can't be whistled up in Linux. If such is the case I would recommend installing Ubuntu over the entire machine, and then making Windows the guest OS in VB. I've had fewer problems that way.

---

### Post by SeijiSensei on 2015-02-07
Do you have a DVD with a licensed copy of Windows 8?  You would need that, and an external DVD drive, to put Win8 in the virtual machine.  You could try downloading a copy of the Win8 ISO from some dark corner of the Internet, but the license key that came with your machine may not work with a different version of Windows than the one already installed.

You'll be far better off [installing VirtualBox]("https://www.virtualbox.org/wiki/Downloads") in Windows, then creating an Ubuntu VM.  After you install VB, make sure you also install the extension pack in the virtual machine.  Otherwise the VM won't have access to the USB ports.

---

### Post by danne33 on 2015-02-07
Based on the answers so far: I still think I will go for the dual boot. It is a good way to increase my computer skills.
I found out that my system is 64 bit and use UEFI.
I am looking at this page right now: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
If I make an EFI-only image, then it wouldn't be any problems right?
They recommend to use EFI-supported version. Is Ubuntu 14.10 a supported version?
Can I delete all my extra partitions except "C:"? That would free 25 GB extra.
In worst case, then I just delete my whole Windows partition and only use Ubuntu.

---

### Post by newb85 on 2015-02-07
If your limited drive space is you motivation for not installing dual-boot, then using VB won't be much better.  VirtualBox creates virtual hard drives, and that requires space on your drive.  Of course, you could dynamically size the virtual hard drive, so you wouldn't have to allocate all the space up front.  Normally, I would be afraid that a dynamically allocated virtual HDD residing on an NTFS partition would become fragmented and affect performance, but as your drive is an SSD, that shouldn't be an issue.

All the same, if you're willing take the time to set up a dual-boot system, (with the extra measures for UEFI, disabling SecureBoot and FastBoot) I think you'll have a much more fulfilling result.  Browsing the files on your Windows system from your Ubuntu environment will be much easier that way.  Ubuntu's performance will be better, because your hardware won't already be simultaneously supporting Windows.  And it eliminates any issues you could have with VirtualBox's capture of your keyboard and mouse (which I haven't found to be 100% reliable).

That said, I would not be a good reference for setting up dual-boot with Windows 8, as I've never owned or even touched a device equipped with Windows 8.  (That's not a matter of pride or disdain; it simply has yet to happen.)

---

### Post by newb85 on 2015-02-07
> **danne33 said:**
> 
They recommend to use EFI-supported version. Is Ubuntu 14.10 a supported version?
Can I delete all my extra partitions except "C:"?

14.10 would support EFI, but so would 14.04.  14.10 will only be supported until this July (9-month life cycle), while 14.04 (which is an LTS release with a 5-year life cycle) will be supported until April 2019.  Unless you plan to upgrade often, stick with LTS releases.

I would check what the partitions do before deleting them.  It's common for one to be a system restore partition, which you probably don't need, especially if you create a removable restore disc.  If your system has a D: partition for your personal files, you probably don't want to delete that.  If the C: partition for Windows is large enough, shrinking it is a good idea.  As your system is UEFI, you don't need to worry about having too many partitions.

---

### Post by danne33 on 2015-02-07
> **newb85 said:**
> I would check what the partitions do before deleting them.  It's common for one to be a system restore partition, which you probably don't need, especially if you create a removable restore disc.  If your system has a D: partition for your personal files, you probably don't want to delete that.  If the C: partition for Windows is large enough, shrinking it is a good idea.  As your system is UEFI, you don't need to worry about having too many partitions.

As you can see in my earlier reply (#5), all the partition are completely empty (0 byte used). Then there should be no problem deleting them right?

---

### Post by JeQhdMD on 2015-02-08
Well, your laptop has Intel graphics and wireless . . . which is usually a good fit for Linux.   Read up big time on uefi boot, possible issues, use of disk repair tools, etc   You'll definitely learn a lot.   Also recommend to create a live usb flash-stick bootable drive, using Knoppix.   If you have a second internal drive, that would be ideal for /home and cut down the size of Ubuntu install on the SSD.

---

### Post by newb85 on 2015-02-09
> **danne33 said:**
> As you can see in my earlier reply (#5), all the partition are completely empty (0 byte used). Then there should be no problem deleting them right?

Honestly, I find that screenshot a bit baffling.  Why did your hardware manufacturer decide you needed four different recovery partitions?  Why are they empty (perhaps you emptied them)?  Also, why is the UEFI system partition empty?  If I were you, I would not mess with the latter, but I would feel free to eliminate the recovery partitions.

As I said earlier, though, I'm inexperienced when it comes to UEFI.

---

### Post by danne33 on 2015-02-14
> **newb85 said:**
> Honestly, I find that screenshot a bit baffling.  Why did your hardware manufacturer decide you needed four different recovery partitions?  Why are they empty (perhaps you emptied them)?  Also, why is the UEFI system partition empty?  If I were you, I would not mess with the latter, but I would feel free to eliminate the recovery partitions.

As I said earlier, though, I'm inexperienced when it comes to UEFI.

I thought the same! However when I booted Ubuntu on USB stick then I could see that the partitions actually was used. It most be some kind of encryption that makes Windows to believe that the partition are empty and hidden when they are in fact filled with stuff. 

Now I got two problems:
1) Now I have dual partition with Windows 8 and Ubuntu 14.10. Right now I can only start Ubuntu and not Windows. I saw a thread that I should try use boot repair with my USB stick but my computer can't find USB as a boot possibility anymore in BIOS. Any ideas how to fix this?

2) I tried to install 6 GB SWAP but I think it didn't work (see image). Can someone confirm this and how to fix this. Is it so easy as to click Gparted -> Partition -> Format as -> Linux swap

---


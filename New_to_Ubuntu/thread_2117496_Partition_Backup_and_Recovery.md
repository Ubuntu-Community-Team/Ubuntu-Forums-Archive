---
title: "Partition Backup and Recovery"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by andperry on 2013-02-18
I'm installing Ubuntu 12.04 Desktop to dual boot with Windows 7 and have decided to install from within Windows using wubi.exe (it's more straightforward, and for the anticipated usage, I'm not bothered about the slight degradation in performance that results from using this technique). I have always partitioned hard drives for Windows systems with C: for the system/applications and D: for user data. I have also always used partition imaging software to back up the C: drive and to be able to recover it if something serious goes wrong. This technique has worked well for me for many years.

I decided therefore to create an E: partition and to install Unbuntu into here using all available space - the theory being that this partition can be imaged for recovery if the Ubuntu installation goes seriously wrong, and also to survive a C: drive recovery in the event of a problem with the Windows installation. All sounds very neat until I actually tried to recover an image of the E: drive. When the dual boot menu came up afterwards and I selected Ubuntu, got an error message to the effect of "Windows cannot boot . . .". Had to re-install Ubuntu from scratch. I have felt let down by a technique that has worked reliably for years - my understanding is that a drive should be restored exactly as it was.

I'm going to try another method, namely just to make a straight backup copy of the root.disk file. I've yet to find out whether recovery works OK, but even if it does, it does not seem as good a solution as using a partition imaging program, as the latter tends to use file compression and therefore save on hard drive space when making a number of images.

Am I missing something, or failing to understand something properly?

Thanks,

Andrew.

---

### Post by ajgreeny on 2013-02-18
I think you are misunderstanding the fact that your wubi ubuntu OS is not on a real and separate partition, but is, as you suggest you already realise, simply an encrypted image-like file within the windows OS, even if windows put that file on a separate partition when you installed it.

If you are completely serious about dual booting the two OSs, I suggest you think again about wubi, which is strictly only for checking that your hardware can run the OS, not for a long term installation.

---

### Post by andperry on 2013-02-19
Thanks for the reply. Yes I'm aware that wubi is only really for short/medium term use and as such I would rather do a 'proper job' so to speak. I have been having trouble with this anyway, which is partly why I reverted to using wubi.

Starting with an area of unallocated space on the hard drive, I've tried to install Ubuntu from the CD and have tried both the 'install alongside' and the 'something else' (manual) option. With the latter I've tried setting the bootloader to both the default option and the Windows 7 bootloader. Whatever I try, I seem to end up with a single-boot Ubuntu system - it just refuses to give me a dual boot. The only way to get back into Windows that I have found is to repair the boot sector from the Windows installation disc.

I'm totally frustrated and yet I'm sure I've done it successfully in the past with Ubuntu 11.10. What am I doing wrong?

Thanks,

Andrew.

---

### Post by Mark Phelps on 2013-02-19
> **andperry said:**
> What am I doing wrong?

You're not adding an entry for Win7 to the GRUB config file.

To do that, once booted into Ubuntu, open a terminal and enter "sudo update-grub".  That will scan your system for operating systems and kernels and you can watch it as it works.  It should show something like "Windows 7 (Loader) on ..."

When it's done, when you reboot, you should THEN be seeing a menu.

---

### Post by oldfred on 2013-02-19
You never install grub2's boot loader to a Windows NTFS partition as that has to have Windows boot code in it. That is why you have to repair Windows.

And unless you have another boot loader that multiboots, you do not install grub2's boot loader to a PBR - partition boot sector. You just install to the MBR of the hard drive or sda not partitions like sda1 or sda2 etc.

Then the sudo update-grub will find Windows and the grub menu will offer both Ubuntu and Windows.

many like a gui to repair installs.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---


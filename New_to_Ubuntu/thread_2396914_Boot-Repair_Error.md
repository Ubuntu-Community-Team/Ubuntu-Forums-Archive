---
title: "Boot-Repair Error"
date: 2018-07-22
forum: New to Ubuntu
---

### Post by mkesleem on 2018-07-22
Hi,

I re-partitioned my drive and can no longer boot using grub. I tried to use the boot-repair tool to fix this, but it didn't work.

Here is the URL from the repair.

[http://paste.ubuntu.com/p/RbJXyVg4fC/](http://paste.ubuntu.com/p/RbJXyVg4fC/)

How do I repair my grub?

Thanks

Edit:
I decreased the size of my Windows partition and increased the size of  my Ubuntu partition using gparted in Ubuntu, because I was running out  of space on my Ubuntu partition.

---

### Post by mIk3_08 on 2018-07-23
Try this command;
```
sudo apt-get install dosfstools
```

---

### Post by yancek on 2018-07-23
You need to post more details on what you had before, what changes you made.  First of all, the boot repair does not show any grub.cfg file which is the Grub menu you see on boot.  It also shows that your windows system is hibernated so the windows partitions will not be mounted or accessed.  What partitions did you change and how did you do it?

---

### Post by mkesleem on 2018-07-23
I decreased the size of my Windows partition and increased the size of my Ubuntu partition using gparted in Ubuntu, because I was running out of space on my Ubuntu partition.

Immediately after I partitioned my drive I restarted my computer. The first time I restarted I was able to boot Windows without any issues. The next time I tried to boot, I was unable to.

The grub-rescue indicates that the error is "file not found." I don't have my computer with me, so I can't tell you which file was not found, but I'm assuming with was the grub.cfg file that was not found.

---

### Post by oldfred on 2018-07-23
Your grub says this on re-install:
> Syntax error: ")" unexpected

Did you manually edit grub.cfg, or 40_custom grub entries?
Report did not show any grub.cfg which is not created if you have issues with format of files.

You could try a full uninstall/reinstall of grub from Boot-Repair's advanced options.

You also have Windows 10 in BIOS boot mode. Grub only boots working Windows so make sure you have a separate Windows repair flash drive.

---

### Post by mkesleem on 2018-07-23
I did not manually edit anything related to grub.

I did however create a backup of my Windows install using Acronis True Image immediately before trying to partition my drive.

I do not have a separate Windows repair flash drive. How do I create one if I don't currently have a working copy of Windows 10? Will I have to get a copy from a friend?

What do you mean by "You also have Windows 10 in BIOS boot mode"?

---

### Post by oldfred on 2018-07-23
Systems in the last 5 years are UEFI as Microsoft required UEFI with gpt partitioning for all new systems with Windows 8. Upgrades from Windows 7 were usually the now 35 year old BIOS/MBR configuration. UEFI systems can boot in BIOS mode with emulation. 
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
So older systems are BIOS only, newer systems are UEFI or may be BIOS if installed that way by user.

You should be able to get Windows to boot. 
First repair grub using full uninstall/reinstall with Boot-Repair. And if Windows does not boot from grub, temporarily reinstall a Windows boot loader to MBR to fix Windows. Then use Boot-Repair to restore grub to MBR (not full install, normally).

With BIOS based systems there is only one MBR (per drive), so only one system can boot. But newer UEFI has multiple boot loaders in ESP - efi system partition, so every system can be directly booted from UEFI. 

       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by mkesleem on 2018-07-23
I tried to uninstall and reinstall grub using Boot-Repair, but I got an error.

[URL="http://paste.ubuntu.com/p/3Ty7Mq9XHv/"]http://paste.ubuntu.com/p/3Ty7Mq9XHv/
[/URL]
I was however able to get to boot by reinstall MBR

[http://paste.ubuntu.com/p/MFmyxPPs38/](http://paste.ubuntu.com/p/MFmyxPPs38/)

---

### Post by oldfred on 2018-07-23
You installed the syslinux boot loader which is a Windows type boot loader.

But you still do not have a grub.cfg shown. And error seems to be that you are missing /boot/grub.
If you totally reinstalled grub, it should have recreated that.

You also show Windows fast start up on, which may prevent grub2's os-prober from completely running and causing all the issues.

       [http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by mkesleem on 2018-07-25
I was able to reinstall grub.

Everything seems to be working.

Thank you for your help!

---


---
title: "Cannot boot windows 10 afer ubuntu install"
date: 2020-06-21
forum: New to Ubuntu
---

### Post by sirtuesday on 2020-06-21
Hello, 

I recently installed ubuntu onto a second hard drive of a newly  built computer that had Windows 10 on the other drive. During the  installation phase I selected erase disk and then selected my SanDisk  SSD. After installation and reboot I was automatically brought into  Ubuntu, no grub menu. After this, I went into my bios and WD SSD with  Windows installed to boot and it booted directly to ubuntu for some  reason. I have also tried booting from the SD SSD where linux is installed, but again there is no grub menu. When I hold shift during Ubuntu start up I do see a grub menu,  but there is no Windows selection. 

I have  tried sudo update-grub and I do not see Windows using that command. If I  go into Files -> Other Locations I can see the WD with windows on it  and I can see the files I originally had on it. It is a brand new  install, so I am not worried about losing data on Windows, but would anyone  happen to know a fix for this? Would this be a situation where I should use a Windows flash drive and try to recover from there? 

I have tried boot repair and got the following: [http://paste.ubuntu.com/p/GzKPbPJh4V/](http://paste.ubuntu.com/p/GzKPbPJh4V/)

I apologize if this question has been asked a lot. I am new to this mostly, so I am trying to figure it out. A part of the reason I am trying to install both OSs now when there is no data on either.

---

### Post by oldfred on 2020-06-21
It looks like you have a newer UEFI system.
But have installed both Ubuntu & Windows in the now 35 year old BIOS/MBR configuration.
Microsoft has required vendor to install Windows in UEFI boot mode to gpt partitioned drives since release of Windows 8 in 2012. They did not even want to offer BIOS mode on new systems, but large mfgs. with many systems wanted to have BIOS for compatibility with many older systems.

With Boot-Repair and multiple drives, do not run auto fix. You typically want Windows boot loader on Windows drive and Ubuntu's grub boot loader on Ubuntu drive, particularly if BIOS/MBR. Only use Boot-Repair's advanced mode for repairs.
Grub only boots working Windows. And that means Windows cannot be hibernated nor need chkdsk. Then you have to either directly boot Windows or use your Windows repair/recovery flash drive to fix Windows. And Windows turns fast start up back on with updates which again sets hibernation flag preventing grub from booting Windows.

It also looks like you had Ubuntu sda drive set as default in BIOS when you installed Windows. Windows then put its boot partition on the sda drive & you erased it when you installed Ubuntu. Windows does not have to have separate boot partition, but you have to repair main install partition. Make sure your NVMe partition p1 has boot flag & run Windows repairs.

You are missing the first two files which probably were in a separate boot partition on sda drive.
Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

While you can fix your BIOS Windows install on the NVMe drive, you may want to consider total reinstall in UEFI boot mode, particularly since little configuration or data added yet. That also requires change from MBR to gpt partitioning which normally erases everything on a drive. If you have any data to save, make sure you have good backups.

How you boot install media for both Ubuntu & Windows, UEFI or BIOS is then how it installs to your system.
Often with multiple drives best to disconnect one drive or other. New systems have UEFI setting to disable a drive as difficult to disconnect NVMe drive, but easy to logically do in UEFI settings.

If you do not understand UEFI and gpt partitioning see the link in my signature and the many links to more info. Some is basic and some if more advanced.

---

### Post by sirtuesday on 2020-06-21
Hello, 

I just wanted to say thank you for this. I took your advice and changed all of my formats to UEFI. After some fresh installs I am able to boot into both systems and the grub menu does appear allowing me to pick between ubuntu and windows. The only difficult part was because I have an ASUS motherboard. The ASUS BIOS didn't have a way for me to disable the nvme drive, but I was able to disable the SATA drives. Either way, all fixed now!

Thanks again.

---

### Post by oldfred on 2020-06-21
Glad you got it working.

What model Asus motherboard?

---

### Post by sirtuesday on 2020-06-22
It is the Asus tuf gaming x570-plus. Great board from what I have used thus far, but I was surprised that it didn't give me the option to turn off the nvme when it let me turn off the Sata drive.

---


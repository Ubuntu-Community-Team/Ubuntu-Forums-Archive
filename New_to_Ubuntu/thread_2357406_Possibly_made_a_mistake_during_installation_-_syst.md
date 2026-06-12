---
title: "Possibly made a mistake during installation - system boots to GRUB"
date: 2017-04-01
forum: New to Ubuntu
---

### Post by conormullins3 on 2017-04-01
Hi all,

I'm very new to Ubuntu and I'm inexperienced with Linux in general; the only version of Linux I have any familiarity with was a version of Linpus Linux that came pre-installed with Acer netbooks around ten years ago. I use a Hewlett-Packard Pavilion laptop with a Toshiba 1TB internal HDD. I've got a spare 2TB Samsung D3 external HDD laying around, so I formatted it (after sensibly backing up what was on there on a newer HDD), then I used an Ubuntu boot-USB to install Ubuntu on to the HDD. The installation seemed to go well. I had formatted the HDD as NTFS, which the Ubuntu boot-loader seemed to fix after some fiddling about, and then I just let the installer run.

I rebooted my machine when prompted and was met first with a blue screen that asked me to go into GRUB. I was then met with a rather formidable-looking black screen. After a brief panic at the thought that I'd somehow managed to wipe my hard drive, I found that typing "exit" in to GRUB allowed me to boot to Windows and my files are all safe and sound (thank God!) but I seem to have made a mistake somewhere in the installation process and accidentally mucked up my laptop's internal BIOS? According to [this thread]("http://askubuntu.com/questions/446682/how-to-install-ubuntu-on-portable-external-hard-drive") this is something of a rookie error and "easily fixed". I am not sure what I've done. As it stands I can get into Windows just fine from the GRUB prompt; but I'm not sure how to revert the changes to the BIOS and just run Ubuntu off the HDD.

I apologise if you're nodding your heads along and thinking "This guy has made a ton of rookie mistakes", I'll be the first to admit that I'm ill-experienced and probably should have done more research before attempting installation. What steps can I take now so that I can run Ubuntu off of the external HDD safely?

Thanks in advance for any advice.

---

### Post by yancek on 2017-04-01
>  I had formatted the HDD as NTFS,

First big mistake.  ntfs is a microsoft proprietary filesystem type.  No Linux system will run on it so hopefully the installer corrected that and made a Linux filesystem.
Usually best to just shrink your windows partition and leave unallocated space on which to install Ubuntu.

Ubuntu has been around for over a decade so indicating which version release you are using would be helpful.  The most current is 16.10.
Windows has been around for over thirty years so indicating which version release you are using would be helpful.
If you have windowss 8 or 10 and it was pre-installed, it is likely using UEFI/GPT so that adds another layer of complexity.  Without this info, it's all guesswork.
 
The Ubuntu gives several Installation type options, which did you choose?  Also, there is an option in the installer for "Device for bootloader installation".  What did you select.

I think you will need to at least indicate how old the computer is and what version of windows and Ubuntu your are using before any specific advice can be given.

---

### Post by conormullins3 on 2017-04-02
I am using the latest version of Ubuntu, 16.10. I got it to start up fine today from the UEFI boot menu.
I am using the most up to date version of Windows 10 right now, I've had no problems with it this morning. I ran winver and it told me that it is"Version 1607 (OS Build 14393.953)"
The HP Pavilion is practically brand new, I got it last November.

I chose the "something else" installation option, got it to reformat the external HDD to "ext4" and then install Ubuntu into a partition on that. I think what has happened is GRUB has been installed on the internal Toshiba hard drive (with Windows and the recovery partition on it) while Ubuntu has been installed on the Samsung external hard drive.

---

### Post by RobGoss on 2017-04-02
> I apologise if you're nodding your heads along and thinking "This guy has made a ton of rookie mistakes", I'll be the first to admit that I'm ill-experienced and probably should have done more research before attempting installation. What steps can I take now so that I can run Ubuntu off of the external HDD safely? 

You're not the first and won't be the last person to makes these common mistakes, we've all been there that's how we learn by trial and error. The most important thing here is that you realized your mistakes and just move on **great job**, there is no need to I apologize

---

### Post by RobGoss on 2017-04-02
Can you choose between each OS to boot or do you need to access the **BIOS **in order to choose the different systems?

---

### Post by again? on 2017-04-02
If you have any problems or just want clarification of whats happened you can install **boot-info-script**.
Using terminal.
```
sudo apt install boot-info-script
```

Then run
```
sudo bootinfoscript -g
```

May take a minute or so to run and when complete you'll find a RESULTS.txt file and an archived RESULTS.txt.gz in your home directory.
You can attach RESULTS.txt.gz to a post.

---

### Post by Geoffrey_Arndt on 2017-04-02
Further info . . . . with dual-booting UEFI Windows & Linux, some things need adjustment before the install starts.   Turning off secure boot, fast-boot (windows always on) and on many HP systems, the uefi shim bootloader that Ubuntu uses in the small EFI partition may need to be renamed.    Whether Grub2 needs installing to the sda (internal hdd) - - I'm not sure, but on external multi-boot systems, grub2 should be installed to sdb or sdc (whichever the system ID's the external drive as).   

The installer media  also needs to be used in "uefi mode" - - and not "mbr mode" (the legacy "**M**aster **B**oot **R**ecord" disk system).

Boot repair may offer to do a boot-repair - - but don't run that until you've posted the boot report as guber2 lists above in post#6.

---

### Post by oldfred on 2017-04-02
The first third of this report is the updated fork of bootinfoscript.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---


---
title: "UEFI issues"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by raviolifaceman on 2013-05-08
I need a Win8  installation but love using Ubuntu. I have fiddled with them both for days. I tried installing them both ways; 8 first then Ubuntu, and vice versa. The problem is that Ubuntu formats my hard drive in UEFI and Windows 8 refuses to install to it. The disc I have has no option that I can see. I didn't even bother looking into my BIOS because I'm on a laptop mobo with no options. I then tried wubi, which didn't work on my x86 installation (I know, I was warned). I can't get rid of it now though; what was going to be Ubuntu has been removed now but Windows boot manager thingy still asks me if I want to boot into it.

Is there a way to install Linux onto my non-UEFI hard-drive? I don't really have the patience to format Windows again; I work from home and need a working PC 24/7.

---

### Post by oldfred on 2013-05-08
Windows only installs from flash drives in UEFI mode.

Ubuntu should work with either UEFI or BIOS.

One issue may be once drive is converted to gpt for UEFI boot, Windows will only install in UEFI mode, or if installing in BIOS mode converts drive to MBR, but leaves backup gpt partition table. Then Linux gets confused  with MBR(msdos) primary table and backup gpt table.
       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

You should have settings in UEFI for UEFI or BIOS/Legacy/CSM. Some also have a setting for both which may be the issue.

Both Windows and Ubuntu install in the mode UEFI or BIOS based on how you boot flash drive. You should get two choices from UEFI menu. With Ubuntu if you boot grub menu then that is UEFI, if the syslinux and standard accessibility screen then that is the BIOS mode.

    
Some early UEFI implementations would boot from efi partition (only with gpt partitioning) and if efi partition not found will look in MBR for boot file.

---

### Post by raviolifaceman on 2013-05-08
Remember I'm posting in the absolute beginners forum so I'm trying to understand what you're saying with difficulty - if I were to burn Ubuntu to a disk it should just install fine in my MBR drive? I have tried this, and it won't work.

And about the possible issue you mentioned - I am on Windows 8 now, and do not have Ubuntu installed (although it shows up in my boot list, so your suggestion of stray GPT data makes sense). Because I'm on 8, I can't use any of the solutions you're giving me - I need a Windows application to remove the GPT data. I got something called Test Disk but I'm not sure how best to use it.

---

### Post by raviolifaceman on 2013-05-08
Further information - my Ubuntu disk doesn't detect the MDR partitions whatsoever. It detects a completely blank disk.

---

### Post by oldfred on 2013-05-08
That is probably the confusion of gpt vs. MBR.

You can boot installer in live mode and download fixparts into it and run it from there. Should work whether UEFI or BIOS, but you really want to boot in BIOS mode.

After you download the amd 64 bit version with the .deb for Debian based or Ubuntu install. From file browser Naulitus you should be able to extract .deb by clicking on it and Software Center will update to install it.

Since it use Unity, click on the top icon on left size and type in terminal. Then you can click on terminal and use that to run fixparts.

---


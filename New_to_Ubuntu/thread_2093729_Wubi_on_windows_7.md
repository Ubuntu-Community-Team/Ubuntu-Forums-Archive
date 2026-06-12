---
title: "Wubi on windows 7"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by penmaker on 2012-12-11
I have windows 7 64bit installed on my lenovo z580 laptop. Last night I went to the ubuntu website and used the windows installer to install ubuntu so I can have a dual boot system, everything went fine until it asked me to reboot and windows 7 will boot when selected but ubuntu will not, I get the following error:

/ubuntu/winboot/wubildr.mbr is missing and i get a status error of: 0xC0000098

I am not wanting to remove windows and I would like to have ubuntu also but I have no clue how to fix this.

thanks in advance for anyones help!!!

---

### Post by tgalati4 on 2012-12-11
Did you install 32-bit or 64-bit Ubuntu?  What version of Ubuntu did you attempt to install?

---

### Post by penmaker on 2012-12-11
i did 64bit 12.04lts, said lts was good for laptops

---

### Post by bcbc on 2012-12-11
It doesn't affect Windows. Just Wubi is not booting. Go to the Control Panel, Add or remove programs, and uninstall Ubuntu.

There could be a few reasons why you get this problem. If you're booting using UEFI for instance.

---

### Post by deadflowr on 2012-12-11
Your Windows system should be alright. Wubi installs Ubuntu like any other program within Windows. The difference being that it loads when the computer starts or restarts to boot and not when Windows is running.
If it's just not working go to the add remove program section of Windows to remove. It'll uninstall like any other program.

---

### Post by penmaker on 2012-12-11
I did uninstall it and it still does not boot correctly now. I keep getting that error

---

### Post by vanquishedangel on 2012-12-11
You can also burn a ubuntu disk and boot from that disk, then reinstall from the disk leaving your windows install. it should give a few options for installation, install along side windows should be one of them.

I had issues with wubi before as well, I hope it gets fixed asap. To me it seems like there was an error during install, this process will replace the bootloader with grub2, which can also boot windows.

---

### Post by Mark Phelps on 2012-12-11
> **penmaker said:**
> I did uninstall it and it still does not boot correctly now. I keep getting that error

What does that mean? WHAT does not boot correctly -- Ubuntu or Win7?

---

### Post by bcbc on 2012-12-11
To remove the leftover Ubuntu in the windows boot manager:
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu]("http://askubuntu.com/a/145605/14916")

---

### Post by DuckHook on 2012-12-12
This is not really as big a problem as you fear. Nothing to worry about. Here's what happened:

> **penmaker said:**
> ...used the windows installer to install ubuntu so I can have a dual boot system

You didn't really install Ubuntu as a dual boot system. The phrase "dual boot" has a very precise meaning with operating systems. It means an installation that exists separately and independently of Windows. What you did was use an installation method called WUBI. Using this installation method, Ubuntu is installed *inside* Windows and is *dependant* on it. Whenever you turn on your computer, Windows is still booting first. But halfway through its boot process, it switches to Ubuntu. Therefore, when you uninstalled Ubuntu, Ubuntu was properly deleted, but a remnant of this "switch to Ubuntu" setting was left in the Windows bootloader. If you clean this up, your Windows bootloader will go back to behaving like it used to.

@bcbc has provided a link to good instructions for removal of this remnant.

If you are still interested in running Ubuntu as a true dual boot, the instructions are [here]("https://help.ubuntu.com/community/WindowsDualBoot").

Here's my advice:

Before doing so, lurk on this forum first. Look over old threads dealing with partitioning and preparing your HD properly for dual boot. It is a rather involved process, and also can be dangerous because you are dealing with critical areas of your HD. You MUST back up your important data first. This is an absolute necessity. A good thread to look at is [here]("http://ubuntuforums.org/showthread.php?t=2088414"), especially post #7 and #14.

It is better to patiently plan out all of your steps, ask questions on this forum and be sure of your procedures than to just forge ahead with an install. Life is happier and less stressful that way.

---

### Post by bcbc on 2012-12-12
Don't confuse the Windows boot manager with Windows. In the same way Ubuntu's boot manager (Grub) also has to load first before you select Windows in a 'normal' dual boot, the Windows boot manager has to load before you can boot into a Wubi install. If you used easyBCD instead of Grub's bootloader, you would still use that same Window's boot manager to boot a normal, partitioned install of Ubuntu.

What is different with Wubi is not that Windows has to boot partway, but that Wubi uses a virtual partition (a loop device) from a file on the NTFS (or FAT32) partition. Other than that and the combination of the Windows boot manager, grub4dos and grub2, it's the same as a normal Ubuntu install (although arguably less reliable due to the virtual partition).

You can debate the definition of what is a dual boot, multi-boot, etc. but at the end of the day, if you boot two different OSes natively then you have a dual boot. If you boot one within the other, it's a virtual machine.

Whatever you call it doesn't change the nature of the problem that needs to be solved.

---

### Post by DuckHook on 2012-12-12
Going off topic here and my ignorance is clearly showing, but aren't there subtle differences in a WUBI install that make it less stable? For example, does it use NTFS or ext4? Is the WUBI file contiguous or is it prey to Window's notorious fragmentation? I've no idea because I've no experience with WUBI, but I would imagine that a corrupted WUBI file within Windows would toast your Ubuntu installation.

Perhaps I described it improperly; but the idea I was trying to convey was what you have corrected me on. Fragility. Anyhow, thanks for correction.

---

### Post by bcbc on 2012-12-12
Yes I agree. Fragility is a good description. Although it doesn't seem to affect everyone, there are many cases where the virtual partition gets corrupted. 
The file sits on an NTFS (or FAT32) partition (and may indeed be affected by fragmentation), but contains within it either an ext4 or ext3 file system (depending on the installation method).

---

### Post by asifnaz on 2012-12-12
> **DuckHook said:**
> Going off topic here and my ignorance is clearly showing, but aren't there subtle differences in a WUBI install that make it less stable? For example, does it use NTFS or ext4? Is the WUBI file contiguous or is it prey to Window's notorious fragmentation? I've no idea because I've no experience with WUBI, but I would imagine that a corrupted WUBI file within Windows would toast your Ubuntu installation.

Perhaps I described it improperly; but the idea I was trying to convey was what you have corrected me on. Fragility. Anyhow, thanks for correction.

Well it uses logical partition and yes windows viruses could kill Ubuntu wubi installation . Wubi is here just to try Ubuntu without making any differences

---


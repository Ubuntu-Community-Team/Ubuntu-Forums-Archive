---
title: "gparted does not recognize windows partition, only shows entire disk as unallocated"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by FoxtrotUniforms on 2014-08-22
I have a newer laptop that came with win8 and I recently switched to win7 after accidentally deleting my win8 partition. I tried to replace my Mint install with Ubuntu and ended up totally erasing windows... Anyway I have win7 installed onto the entire disk because I read that would be easier than trying to install windows after linux. Now that I am trying to install Xubuntu with win7 as a dual boot I have run into a few issues that I can't seem to figure out.

1. I cannot use a USB to install Xubuntu for some reason, the bios just doesn't recognize it. I've tried using different USB sticks and different iso's but it just won't work. Luckily a cd works just fine, albeit a lot slower. 

2. Once I try to run gparted during install it does not recognize my windows partition. It just says it is all unallocated space. 

I read that this may be because windows uses GPT partitions and linux does not recognize this. But I am new to this and am pretty confused because everything worked just fine when I had win8 installed with mint.


EDIT:
Thanks all, I solved both my issues. 

With the flash drive issue I realized there is a hard disk sub-menu in the boot tab of my bios. I was just confused because it listed the flash drive outside of that sub-menu with a UUID (or something like that) prefix. 

With the gparted issue I ran the fixparts program in windows and all I typed was " 0: " (documentation and download here [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/) ) and it fixed it silently. Now gparted recognizes the windows partition and I am good to install.

---

### Post by yancek on 2014-08-22
> I read that this may be because windows uses GPT partitions and linux does not recognize this.

I would suggest you avoid whatever source you got that information from as it is totally inaccurate.

Different manufacturers have different options and sometimes multiple options for booting from usb.  Depends upon how old the hardware is.  On my desktop I can select usb under CD/DVD boot and it does nothing.  I can select it under the hard drive option and it boots.  On a notebook I have with multiple usb ports, only one will boot anything.  Check all the options for usb.

Try booting the Xubuntu install medium and when you get to the Desktop, open a terminal and just type:  sudo gparted and see if anything is recognized.
Are you sure you have GPT with windows 7?

---

### Post by ajgreeny on 2014-08-22
Linux and gparted recognises  GPT partitions with no problem, and in newer machines including mine, will run on GPT very well.

I wonder if during your messing around with windows re-installs etc etc you have made dynamic partitions which linux will not recognise, as far as I'm aware.

Unfortunately I have no real knowledge of how to deal with that, or even if it is possible, though I think I have heard of an applications which might help.  See post 2 from [http://ubuntuforums.org/showthread.php?t=2146403](http://ubuntuforums.org/showthread.php?t=2146403)

---

### Post by oldfred on 2014-08-24
The issue was that when you installed Windows 7 in BIOS mode, it converted drive from gpt to MBR, but does not do it correctly.

Linux tools see the new MBR partition but see the old backup gpt partition table that Windows did not correctly erase. Or Windows does not work well with gpt.

You have to run fixparts to remove backup gpt partition table if you let Windows do a gpt to MBR converion of a drive.

Windows 7 can also be installed in UEFI mode, but you have to convert DVD to flash drive and run some updates. Then boot it in UEFI mode from UEFI/BIOS not in BIOS mode.

---


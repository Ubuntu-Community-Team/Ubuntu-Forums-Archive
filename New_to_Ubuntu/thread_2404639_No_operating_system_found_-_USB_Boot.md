---
title: "No operating system found - USB Boot"
date: 2018-10-26
forum: New to Ubuntu
---

### Post by bianchin2 on 2018-10-26
Hi, I have a similar problem. I put Ubuntu (I tried with different flavours) and tried to install on a Fujitsu t5010 and t4210 (very old machines, they were running Xubuntu 14.04). The USB works, tested on a surface 4 and a desktop i3. But on both Fujitsu I get the message no operating system found when I select the USB Key option. In the BIOS the presence of the USB is recognized as generic USB key.

---

### Post by slickymaster on 2018-10-26
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by oldfred on 2018-10-26
Your new machines are probably UEFI that you used for testing.
But is USB flash drive set up correctly for BIOS boot, as old systems will be BIOS only?

Many have found different USB port, different flash drive, different installer to flash drive, or ISO not correct. So sometimes you just have to experiment when you have issues.

Some other issues which may apply:
       **Common BIOS  grub install issues:**
BIOS settings to disable "Boot Sector Virus Protection" or called Security or locked down Boot sector, Bitlocker
Though my drive was appearing in the bios and working for install it was actually "disabled"! 
 bios had a setting for "Fixed disk boot sector" and it was set at "Write Protect"
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on) or Intel SRT on Ultrabook
Old gpt data on drive where Windows installed in BIOS/MBR mode
**Other issues users have reported:**
BIOS in not updated to latest revision
BIOS shows floppy or firewire and you do not have those
BIOS - enable the IMMOU so USB2 ports work - Many Gigabyte boards, others ?
BIOS settings need USB mouse & keyboard, USB detection turned to "UEFI Only"
BIOS setting, Keyboard response in grub really slow
BIOS not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
BIOS not set to boot CD or USB first
BIOS has hard drive turned off - Operating system not found error Also unplugged, bad connections etc
Disable Quickboot in BIOS
BIOS/Windows Fast Boot setting prevents keyboard from working & other issues
 Dell security software on Windows 7 ties in with the BIOS cannot write to drive
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
Old BIOS, new drive 137GB max boot size or very large / partition over 100GB
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)
turning off UDMA in the BIOS my problem has gone away.(old system & may make system slower)
[https://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](https://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found) 
   After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.

---

### Post by coffeecat on 2018-10-26
@oldfred, I've moved your post from [https://ubuntuforums.org/showthread.php?t=2397116](https://ubuntuforums.org/showthread.php?t=2397116) to this new thread, which is where I think it belongs. I think you had the old thread up in your browser and were answering bianchin2 at about the time slickymaster was creating a new thread with bianchin2's post - hence the post to the old thread. If by chance I've moved it wrongly, the link for the old thread is above.

---

### Post by oldrocker99 on 2018-10-26
My continued experience has been that if you boot a USB in UEFI mode, all will be well, **UNTIL** grub is being installed. It will fail, leaving you with an unbootable system. Boot in legacy mode, and all will be well.

---

### Post by C.S.Cameron on 2018-10-28
Use **mkusb** and the flash drive will boot either BIOS or UEFI.

---

### Post by bianchin2 on 2018-10-28
Hi all an thanks!
After you said that the problem was the BIOS-UEFI boot, I used the tutorial

[https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-ubuntu-18-04-lts-bionic-beaver-on-uefi-and-legacy-bios-system.html](https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-ubuntu-18-04-lts-bionic-beaver-on-uefi-and-legacy-bios-system.html)

and removed all the securities in the BIOS (which actually never bothered previously) and ubuntu is now installing on the Fujitsu t5010

---

### Post by oldrocker99 on 2018-10-29
> **C.S.Cameron said:**
> Use **mkusb** and the flash drive will boot either BIOS or UEFI.

And, since I, after all these years, hadn't known about mkusb, this is why I keep up with these wonderful forums.

To install it:
```
sudo add-apt-repository ppa:mkusb/ppa
sudo apt updates
udo apt install mkusb mkusb-nox usb-pack-efi
```

---


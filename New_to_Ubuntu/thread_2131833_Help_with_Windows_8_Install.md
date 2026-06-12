---
title: "Help with Windows 8 Install"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by Eersfanpilot on 2013-04-02
I hate Windows 8.  I want to install and try Ubuntu. I have followed all the directions I could find on this forum. I have created a separate partition (100G) and have followed all the directions to disable SecureBoot in BIOS.  My computer is a Lenovo A10 with Windows 8 pre installed. 

I created a LiveUSB flash drive and when I reboot into BIOS with the USB, the options I get are to try Ubuntu, which I would like, or install it.  


The problem: That's as far as it goes. None of the options work. I keep getting an invalid kernel image message no matter what I try. 


I have a rooted SGS3 with CleanROM and a rooted Acer A500 with LightSpeed so I have a very introductory understanding of flashing some things. 


 I would like to get this to work but so far it seems to be proving more difficult than it's worth. 


 All help greatly appreciated!

---

### Post by nerdtron on 2013-04-02
Try thi tutorial to make a bootable USB Disk or SD Card. [http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb)
Also, be sure your Ubuntu ISO is not corrupted.

---

### Post by Eersfanpilot on 2013-04-03
Some follow up. 

I am using a RockFish USB formatted in Fat32 and already used Unetbootin to make the USB.

---

### Post by nerdtron on 2013-04-03
I see that your laptop is fairly new. I'm not sure if it is supported fully in ubuntu what version is your ISO? I hope some experts will shed light in this matter.

---

### Post by d0006 on 2013-04-03
Can you boot from the USB on another computer?
Maybe try a different distro just to test?

---

### Post by Eersfanpilot on 2013-04-03
I am using the version from the Ubuntu website they say to use for Windows 8.

I can try on an older laptop and see if that works. 

 Thanks

---

### Post by oldfred on 2013-04-03
Did you download the 64 bit version? That is the only version with UEFI support. And how you boot installer UEFI or BIOS is how it will install. To dual boot with Windows you have to install in UEFI mode, not BIOS. But some systems only let you install in BIOS mode. For those systems you then can use Boot-Repair to convert to UEFI mode.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Some others with Lenovo:
 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

[URL="https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop"]
[/URL]

---

### Post by Eersfanpilot on 2013-04-03
Ok I'll give it another try.  right now the computer has secure boot off and is set in Legacy mode. 

 So,  since I'm using the 64 bit 12.10  you are saying I should turn EFI  back on instead of Legacy?

---

### Post by oldfred on 2013-04-03
A few systems only will boot in BIOS/CSM/Legacy mode, but most should boot in UEFI mode. Often you do have to have secure boot off, but with Ubuntu that should not be a requirement.

---

### Post by Eersfanpilot on 2013-04-04
> **oldfred said:**
> Did you download the 64 bit version? That is the only version with UEFI support. And how you boot installer UEFI or BIOS is how it will install. To dual boot with Windows you have to install in UEFI mode, not BIOS. But some systems only let you install in BIOS mode. For those systems you then can use Boot-Repair to convert to UEFI mode.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Some others with Lenovo:
 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

[URL="https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop"]
[/URL]



Update:

I tried the above with EFI re-instated. I received the following error messages:

error: premature end of file /casper/vmlinuz.efi.signed.
error: you need to load the kernel first


Any additional ideas? 

Thanks

---

### Post by oldfred on 2013-04-04
I would download ISO again and install it to your flash drive. It seems like it may be corrupted. 
Did you verify md5sum?

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Eersfanpilot on 2013-04-04
I'll do that. I didn't verify, figured if I got it from the Ubuntu website it'd be ok.

---

### Post by Eersfanpilot on 2013-04-05
Ok. I re-downloaded 64 bit 12.04 and verified the MD5. It checked. 

I have EFI re-enabled. 

I got to a new screen that I have not seen so far. 

[B]"GNU GRUB version 1.99-21ubuntu3.9"

"Minimal BASH-like line editing is supported..........completions"
grub>
[/B]

That's all it gives me. No options for install.

---

### Post by oldfred on 2013-04-05
Did you download 12.04 or 12.04.2?
Only the 12.04.2 has the newest UEFI that supports secure boot, which is the same as the grub-efi & signed kernels used in 12.10.

Easier just to download this if you want 12.10? As it includes Boot-Repair.
       [https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Eersfanpilot on 2013-04-05
12.04.2 64 bit.

I originally tried the 12.10 remix  but that was giving me the errors I originally posted about so I thought I would start over with 12.04.2

---

### Post by Eersfanpilot on 2013-04-05
Thanks for all the help! Success!  I am finally enjoying a test drive of Ubuntu as I write this. 

I reformatted my flash drive, re-downloaded 12.10 64bit and left EFI  turned on. Checked the MD5 and on this try, booted right up. Looks GREAT! 

One finally question.  Advice on next steps for a permanent install? I already have a new partition made and 100G  standing by for Ubuntu to call home.

---

### Post by oldfred on 2013-04-05
So live installer on Flash drive boots and most things seem to work ok. Thats great.

If space is unallocated you should get an install side-by-side install option. System picks sizes of / (root) and swap automatically. If a new user that is all you need.
But it is better to have a shared NTFS data partition for any data you may want to share with Windows and/or a /home partition. I normally suggest / (root) be 25GB with the rest /home or shared data. You should have some swap, and it only needs to be the same size as RAM if hibernating and hibernating is not always a good idea. So a swap of 2GB is often enough.
If you want more than default install then you have to use Something Else and manually specify size, mount (/, /home etc) and format (ext4) of each partition you want. With UEFI you install grub to efi partition, which I think is default (it really should be) as all UEFI systems can only boot from efi partition.

Grub2's os-prober has a bug and still only creates BIOS boot entries that will not work with UEFI. You have to use Boot-Repair or manually add correct efi boot entries for Windows efi.

Some systems only boot with secure boot off, some only with secure boot on. Some only boot with secure boot on, and from Windows efi file. Boot-Repair will fix most of these if needed, a few need manual copying of files.

---

### Post by Eersfanpilot on 2013-04-05
Right now I am about 50% installed.  The one issue I ran into was I could not see my 100G partition that I wanted to put Ubuntu into. I am installing side by side and just split my 1T hard drive in two. 

We'll see how it goes.

---

### Post by Eersfanpilot on 2013-04-05
Fully installed. The only issue that I am seeing so far is that my touchpad is not functioning all the way. Even though it is selected to do so, I can not two finger scroll, or touch to select. I have to use the physical button at the bottom of the touchpad. 

Some other bugs started out but they seem to be correcting themselves the longer Ubuntu is running.

---

### Post by oldfred on 2013-04-05
You can search forum for touchpad issues or start a new thread with that in the title if you cannot resolve it. I have seen a variety of posts, but do not pay attention. I always use a mouse even with my laptop. I just do not like touchpads.

       But using google is often better than the forums search function.
Just append site:ubuntuforums.org to your search term
OR:
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by Eersfanpilot on 2013-04-05
Thanks, I will do that. Thanks again for all your help oldfred. You can marked this one as SOLVED!

---

### Post by Eersfanpilot on 2013-04-05
One last issue,  what should my boot priority be?  with Ubuntu in#1  it won't let me boot to Windows?

---

### Post by Eersfanpilot on 2013-04-05
After a re-boot the touchpad fixed itself. The only real issue is the booting one. 

With the computer in EFI mode it is trying to boot windows 8 using sda/5 or something, instead of my HDD selection. In order to get into Windows 8 I have to switch to Legacy Mode and boot through the BIOS by changing the boot priority to HDD in slot 1 and Ubuntu into slot 2. Also, I have to have Secureboot disabled to get back to Windows.

---

### Post by oldfred on 2013-04-05
Post a new BootInfo report. 

Not sure  if I can tell what is going on, but will try.

---

### Post by Eersfanpilot on 2013-04-06
Found out I can boot to the boot menu on my Lenovo using the little button beside the power button. This allows me to stay in EFI mode and go back and forth to Windows. I still can't boot to Windows inside the Ubuntu menu but it's an easy enough work around to not worry about it.

---

### Post by Eersfanpilot on 2013-04-06
Thanks for all the help. SOLVED, this thread can be closed if you like.

---

### Post by oldfred on 2013-04-06
I have seen a couple of cases where Boot-Repair did not create the Windows boot entries in 25_custom. Grub does not create correct entries so you have to use the one's by Boot-Repair or manually add them yourself. Examples in bug report.
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---


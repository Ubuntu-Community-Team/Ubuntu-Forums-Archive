---
title: "Dual boot win10/Ubuntu HD installation"
date: 2017-11-18
forum: New to Ubuntu
---

### Post by chaoticbob on 2017-11-18
Thanks to advice from people here and a bit of internet research I've had Ubuntu running (off a USB stick) for a few weeks and it's been fine for me. So now I want to install to HD.

At the mo, when I boot with the USB stick in place I get options to test Ubuntu off the stick,or install - I don't get an option to boot W10. I think this may be because at some time in the past I set the BIOS to look at USB first during an abortive attempt to get MINT running.

My question is - if I go for the install option, will the installer recognise W10 and guide me through the partitioning process and set up GRUB, or just reformat the whole drive? I suspect it will guide me, but knowing that Unix systems just do what they're told without trying to second guess I thought I should check.

 Rob

---

### Post by oldfred on 2017-11-18
I prefer manual install, but you need to understand something about partitions and what Ubuntu wants. But now all it really wants is / (root) partition ext4 as minimum. 

Is system UEFI or BIOS? If Windows 8 or later and pre-installed, then it is UEFI and you want to install Ubuntu in UEFI boot mode.

Best to review link in my signature if UEFI, it is a lot, but summary steps are all you need.

What brand/model system?
What video card/chip?
Some require some settings or work arounds.

With Windows 10 use Windows to shrink the NTFS partition and reboot immediately to let it run chkdsk.
Make sure Windows fast start up is off.
Best to have UEFI fast boot off.
UEFI secure boot off for many systems, but not required unless you need proprietary drivers for video or WiFi.

I suggest 25GB for / and then whatever you want for /home and/or a data partition. A shared NTFS data partition only works if Windows 10 fast start up is off, as it otherwise keeps all NTFS partitions in the hibernated state and Linux will not mount read/write.

---

### Post by chaoticbob on 2017-11-19
Thanks oldfred,it's pre-installed Windows 10 on a low-end (Pentium) HP laptop - not sure about video chip, but no video problems running Ubuntu 16.04 from a USB stick, so I guess that won't be an issue with a full install. The info in your link is clear and comprehensive - I think that info should be all I need to make the dual boot work. I understand the basics of partitioning having set up Unix systems (Sun Solaris) before , but I need to catch up on how it all works on modern PC architecture.
Thanks again, Rob.

---

### Post by oldfred on 2017-11-19
Some or many HP violate UEFI standard and use description as part of boot. And only valid description is "Windows Boot Manager".
There are many work arounds, depending on your configuration and use.
If mostly Windows you can add an entry to Windows BCD to reboot and use UEFI's one time boot which seems to work.
Some use the fallback or hard drive entry, which is how UEFI boots all external drives and will also work on internal drives. That is /EFI/Boot/bootx64.efi. If you already have that in your ESP, then bootx64.efi is just a copy of Windows efi boot file. We can change that file to be shimx64.efi to boot Ubuntu.
And some with HP now seem to just work like it should.

---

### Post by Geoffrey_Arndt on 2017-11-19
Just a couple bits of info to supplement OldFred's . . ,

>   A "Live" CD/DVD or USB Flash-Stick will never offer an option to boot Windows.   That only happens after install via either Grub (Legacy install) or UEFI bootloader (UEFI install).    The Mint thing has no bearing on a live media OS now.

>   Even though the video performance worked fine on the Live Media, that is not a 100% guaranty the video will work the same after install.   If running nVidia, a boot parameter option may be needed (nomodeset).

Best to run something like belarc or similar to get exact specs . . . as video issues are a frequent cause of install problems (after improper uefi boot-loader install, and installing to wrong partition).

---

### Post by chaoticbob on 2017-11-21
Thanks for further replies. At the mo I'm waiting on an external drive to back up Win10 stuff. 
Ultimately I hope to do everything I need to do in Linux (I mostly use open source software in Windows anyway), but there obviously isn't a 'one size fits all' way of migrating - there are hardware and disk management  issues which will have to be sorted out. So one step at a time, but thanks for warnings about possible probs with HP UEFI and video.
I'll be back I expect....
Rob.
PS thanks for the link to pre-installed Geoffrey - interesting.  Not an option for me financially at the mo, but shall keep in mind. And I'm (sort of) enjoying the challenge of the DIY approach!
R.

---

### Post by littlefoot505 on 2017-12-01
> **oldfred said:**
> Some or many HP violate UEFI standard and use description as part of boot. And only valid description is "Windows Boot Manager".
There are many work arounds, depending on your configuration and use.
If mostly Windows you can add an entry to Windows BCD to reboot and use UEFI's one time boot which seems to work.
Some use the fallback or hard drive entry, which is how UEFI boots all external drives and will also work on internal drives. That is /EFI/Boot/bootx64.efi. If you already have that in your ESP, then bootx64.efi is just a copy of Windows efi boot file. We can change that file to be shimx64.efi to boot Ubuntu.
And some with HP now seem to just work like it should.

I'll have to check into some of that. I recently dual-booted Ubuntu 17.10 alongside Windows 10 on my HP Pavilion x360 (which is about a year old; hence, it's UEFI-based). How I boot into my Linux partition is by hitting F9 to go into the firmware, then I go to the boot menu and say that I want to boot from the Ubuntu partition (I mostly use Windows). I did try unsuccessfully to install rEFInd. I'll probably start a thread on that.

---


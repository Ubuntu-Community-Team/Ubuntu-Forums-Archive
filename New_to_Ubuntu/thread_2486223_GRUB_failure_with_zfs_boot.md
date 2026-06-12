---
title: "GRUB failure with zfs boot"
date: 2023-04-23
forum: New to Ubuntu
---

### Post by charles-adams-3 on 2023-04-23
Hello,

I have an old Clevo W110ER that was working fine on Ubuntu Desktop installed from a USB stick. It runs a couple services in Docker like Home Assistant and MotionEye.

However, it won't boot anylonger and gives a grub error. I've run boot-repair from a LiveUSB but did not apply the auto repair. The output is below:

[https://paste.ubuntu.com/p/mn5kWXpwRs/](https://paste.ubuntu.com/p/mn5kWXpwRs/)

Is there a way to repair this?

Thank you for your assistance!

---

### Post by charles-adams-3 on 2023-04-23
I have run system-info script and it can be found at: [https://paste.ubuntu.com/p/DVNmgb45yy/](https://paste.ubuntu.com/p/DVNmgb45yy/)

---

### Post by oldfred on 2023-04-23
You show UEFI hardware & UEFI installs, but ran live installer & reports in old BIOS boot mode.

You have mount of ESP - efi system partitions in fstab, so UEFI installs.
see line 188 & 230.

Best to reboot live installer in UEFI mode.
Boot-Repair typically defaults to reinstalling grub of first install. If you want second install you have to use Advanced mode and select install & drive sda. Advanced mode screens:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You also are using old MBR partitioning. Ubuntu works with that although gpt is preferred for UEFI. Windows absolutely requires gpt for UEFI boot since 2012.

---

### Post by MAFoElffen on 2023-04-23
I see that your system was previously installed as BIOS/Legacy boot sometime in the past... (Grub installed to MBR) But the last install with ZFS was UEFI boot.

I see 
```

|_sda1   512M vfat                                            EFI/ESP          
|_sda2     1K                                                      Extended Partiton     
|_sda5     2G swap                   [SWAP]                             
|_sda6     2G zfs_member bpool                                          
|_sda7 107.3G zfs_member rpool                                          
sdb     58.4G                                                           Extreme

```
But that your system can't boot it, because your BIOS is set to boot as BIOS/Legacy instead of UEFI...

Please boot your computer and get into the BIOS to change it back to boot as EFI boot. Then try to boot it an see if it boots.

If it still does not boot, then we will go from there.

---

### Post by yancek on 2023-04-24
Your boot repair output shows Ubuntu installed on sda6 and sda7 and you have a vfat partition (sda1) that should be an EFI partition but there are no efi boot files on that partition.  Is your drive GPT or MBR(msdos)?   I expect it is MBR as you have an Extended partition with Logical partitions which are not used on a GPT drive.

Did you make any software changes immediately prior to this error occurring? If you have a GPT drive, you might be able to reinstall Grub EFI by booting the USB in EFI mode from the BIOS boot options menu.

---

### Post by charles-adams-3 on 2023-05-14
> **oldfred said:**
> You show UEFI hardware & UEFI installs, but ran live installer & reports in old BIOS boot mode.

You have mount of ESP - efi system partitions in fstab, so UEFI installs.
see line 188 & 230.

Best to reboot live installer in UEFI mode.
Boot-Repair typically defaults to reinstalling grub of first install. If you want second install you have to use Advanced mode and select install & drive sda. Advanced mode screens:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You also are using old MBR partitioning. Ubuntu works with that although gpt is preferred for UEFI. Windows absolutely requires gpt for UEFI boot since 2012.

So I disabled all mention of 'legacy bios' in the boot setup. Everything that had UEFI as an option has been set to it and rebooted the USB stick.

Ran boot repair again: [https://paste.ubuntu.com/p/MjQQxKfB7T/](https://paste.ubuntu.com/p/MjQQxKfB7T/) Did this give you better data? 

Otherwise my next idea is to recreate the Ubuntu LiveUSB?

---

### Post by charles-adams-3 on 2023-05-14
> **yancek said:**
> Your boot repair output shows Ubuntu installed on sda6 and sda7 and you have a vfat partition (sda1) that should be an EFI partition but there are no efi boot files on that partition.  Is your drive GPT or MBR(msdos)?   I expect it is MBR as you have an Extended partition with Logical partitions which are not used on a GPT drive.

Did you make any software changes immediately prior to this error occurring? If you have a GPT drive, you might be able to reinstall Grub EFI by booting the USB in EFI mode from the BIOS boot options menu.

The system is static except for automatic Ubuntu updates. So I made no changes. However, it is over a decade old and I replaced the BIOS battery since I started this thread just in case.

The system is on a SSD with zfs boot. 

Boot-repair was run from a Ubuntu LiveUSB that was created on a Windows 10 system.

I'm not trying to fix the USB but rather the zfs boot install on the SSD.

---

### Post by charles-adams-3 on 2023-05-14
> **MAFoElffen said:**
> I see that your system was previously installed as BIOS/Legacy boot sometime in the past... (Grub installed to MBR) But the last install with ZFS was UEFI boot.

I see 
```

|_sda1   512M vfat                                            EFI/ESP          
|_sda2     1K                                                      Extended Partiton     
|_sda5     2G swap                   [SWAP]                             
|_sda6     2G zfs_member bpool                                          
|_sda7 107.3G zfs_member rpool                                          
sdb     58.4G                                                           Extreme

```
But that your system can't boot it, because your BIOS is set to boot as BIOS/Legacy instead of UEFI...

Please boot your computer and get into the BIOS to change it back to boot as EFI boot. Then try to boot it an see if it boots.

If it still does not boot, then we will go from there.

I will remove the LiveUSB and see what options I can still set to UEFI.

---

### Post by charles-adams-3 on 2023-05-14
> **charles-adams-3 said:**
> I will remove the LiveUSB and see what options I can still set to UEFI.


So when I did that it just kept looping back to the UEFI/BIOS menu and did not reach GRUB.

I put back in the LiveUSB and did Boot-repair again: [https://paste.ubuntu.com/p/hPyBdqCwWj/](https://paste.ubuntu.com/p/hPyBdqCwWj/)

---

### Post by yancek on 2023-05-14
Your most recent boot repair output still shows Grub in the MBR, line 28 shows the boot files which are on the EFI partition and are not EFI files but files used on a Legacy boot and are usually on the / filesystem partition in /boot/grub.  You do not have a GPT drive but an msdos drive which would normally have a Legacy install of Grub, boot code in the MBR and Grub files on the root filesystem partition unless you had a separate /boot patition.

As pointed out in earlier posts, you have correct EFI partition labels on both Ubuntu systems showing sda1 as /boot/efi.  However, as I said above, there are no Grub EFI files there.  Installing Grub with boot repair in UEFI mode should work.

Lines 5-7 of the more recent boot repair indicate that Grub is the MBR and core.img is where it should be and Grub is looking for (hd0,msdos1)/boot/grub.  This is what leads me to think this may have formerly been a boot partition??  Reinstalling in UEFI mode should fix this.

---

### Post by charles-adams-3 on 2023-05-14
> **yancek said:**
> Your most recent boot repair output still shows Grub in the MBR, line 28 shows the boot files which are on the EFI partition and are not EFI files but files used on a Legacy boot and are usually on the / filesystem partition in /boot/grub.  You do not have a GPT drive but an msdos drive which would normally have a Legacy install of Grub, boot code in the MBR and Grub files on the root filesystem partition unless you had a separate /boot patition.

As pointed out in earlier posts, you have correct EFI partition labels on both Ubuntu systems showing sda1 as /boot/efi.  However, as I said above, there are no Grub EFI files there.  Installing Grub with boot repair in UEFI mode should work.

Lines 5-7 of the more recent boot repair indicate that Grub is the MBR and core.img is where it should be and Grub is looking for (hd0,msdos1)/boot/grub.  This is what leads me to think this may have formerly been a boot partition??  Reinstalling in UEFI mode should fix this.

How do I use boot-repair to fix this? I think I am following what you say is wrong but I can't translate it into actions and checks I need to set.

---

### Post by MAFoElffen on 2023-05-15
People are getting distracted with the MBR boot sector being populated, and if the BIOS is set to BIOS/ Legacy Boot, then it will cause problems... 

But... And a very important But... As long as your BIOS is set to boot from UEFI, then you are fine. Let's go on. 

I was the contributor who helped with this recent version of 'boot-repair' on repairing Grub on ZFS and LUKS. I gave the steps and code to yann, and he integrated it into the code. We all, including oldfred, tested this last version, for over a month.

The first question I have, is where does it fail? Does it ever show a boot menu? if not, then this is where we will start with this...

From what I see, you have a classic install of Ubuntu 22.04 LTS with ZFS-On-Root. Your bpool (/boot) is on /dev/sda6, and your rpool (/) is on /dev/sda7. The EFI directory is there. All the mounts are found, correct and present. 

The latest version of the script from the PPA should repair it fine. Do not use the version off a boot-repair disk. Use the latest version from the PPA. To do that 'right', boot from an Ubuntu Installer LiveUSB, and open a graphical terminal session. Add the PPA to the Live Image Environment. Install boot-repair. Run the script. Let is reinstall grub to your system. Test it.

If it has any problems, stop and ask me. I will then lead you through it, step by step manually.

---


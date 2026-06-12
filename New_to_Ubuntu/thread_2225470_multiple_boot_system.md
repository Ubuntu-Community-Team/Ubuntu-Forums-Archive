---
title: "multiple boot system"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by dan103 on 2014-05-21
Recently, I attempted to install the WUBI demo installation of Ubuntu with no success. After several frustrating attempts :confused:, I feel it's best I do a full install. However, the particular PC I'm using is already dual booting XP and Win7.

Obviously, this presents it's own problems, so I'm hoping someone in this forum can help. The Dell PC I'm using is an older Optiplex GX260 with 2GB Ram, recently upgraded from a 2.6GHz PIV to a multi-threading 3.05GHz PIV. With 1TB hard drive, I have plenty of room to install, so space is not a problem. It also has an Nvidia Gforce 6200 512mb AGP slot video card; the Win 7 partition had no drivers for the Intel onboard graphics card, so I had to install a separate video card.

However, posting earlier on this forum re: my attempts at the demo install (mentioned above), I was informed that creating a partition (especially on a multi-boot system) is difficult enough let alone creating it on a single boot PC.

If anyone has any info on how I can create a useable, properly setup partition on this machine would be helpful :)

Thanks.

Dan

---

### Post by monkeybrain20122 on 2014-05-21
Well why do you need so many Windows? XP is dead, time to remove it.

---

### Post by oldfred on 2014-05-21
Be careful on removing XP. It probably has the boot files for Windows 7 as Windows only boots from one active partition which we see as the boot flag. Any second install of Windows puts its boot files into the first install that has boot flag. Only if second install is in a primary partition may be you be able to move boot flag and copy Windows 7's boot files back to Windows 7 install. And you may have to run repairs. If in a logical partition you cannot boot from it directly but only thru a primary NTFS partition with the boot flag (or your XP partition whether you keep XP or not).

Post this to see partitions. The issue often with Windows 7 systems is that all 4 primary partitions are used. And do not create partitions with Windows as if it converts to dynamic that does not work with Linux and even does not work with all Windows tools.

From terminal in live installer:
sudo parted -l

 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---


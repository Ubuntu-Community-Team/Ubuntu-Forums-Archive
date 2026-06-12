---
title: "Unable to boot back into Windows 10 after Ubuntu 22.04 dual-boot installation"
date: 2022-06-10
forum: New to Ubuntu
---

### Post by abirdirl on 2022-06-10
Hey all,

 I'm completely new to Ubuntu and Linux itself, and wanted to try it out for code and productivity purposes. I have an existing Windows 10 installation on my main NVME SSD drive, and opted to use a separate sata SSD solely for my Ubuntu 22.04 installation to dual-boot from. However, after I had installed Ubuntu, I could not boot back into Win10 as it seems that my computer doesn't recognize it anymore. 
Upon attempting to boot into my NVME drive with Windows on it, instead of successfully booting into windows, I get prompted to "Reboot and select proper boot device or insert boot media in selected boot device and press a key". I do have a usb media drive for Win10 and attempted to try to repair the installation but to no avail.
So I am currently stuck on Ubuntu trying to figure out how I can boot back into Windows without having to wipe the drive it's on and reinstall it.

I went searching around for solutions and Boot-Repair was one that I was pointed to, I have it installed now on Ubuntu and made a pastebin.
[URL="https://paste.ubuntu.com/p/T6zktC9HS4/"]https://paste.ubuntu.com/p/T6zktC9HS4/
[/URL]Which it seems that it did detect my installation of Win10 which I think is a good sign, though I just can't boot back into it.

I haven't done anything else with it yet as it was recommended to post the pastebin here for anyone here to look over before proceeding, so this is where I am now.
I assume my booting problems stemmed from installing Ubuntu 22.04 in UEFI while my main Win10 installation was actually *not* in UEFI which I had assumed it was and instead was in legacy, assuming that I'm reading the pastebin somewhat correctly.
Another possible problem was that during the installation of Ubuntu, I had chosen /dev/sda1 (that being my sata SSD) where I had designated that as the EFI partition instead of /dev/sda as a whole. From the various guides I was reading from it seemed like that was the best course of action but I'm not sure if that had affected things negatively, or if it mattered really because of the point above haha.

Any help or pointers would be appreciated! If you need more information or if I missed something, I'd be more than happy to provide them and clear things up.

---

### Post by tea for one on 2022-06-10
> **abirdirl said:**
> I assume my booting problems stemmed from installing Ubuntu 22.04 in UEFI while my main Win10 installation was actually *not* in UEFI which I had assumed it was and instead was in legacy, assuming that I'm reading the pastebin somewhat correctly.
Line 298 - LegacyWindows detected.

Yes, you've read the report correctly. You have Windows in Legacy and Ubuntu in UEFI.
Windows 10 requires UEFI mode with GPT (although some upgrades from Windows 7/8 to Windows 10 remain in Legacy mode)

When dual booting, each OS should be installed in the same mode (Legacy or UEFI)
More info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
In order to be more robust in the future, you should seriously consider installing Windows 10 in UEFI mode.

You could spend some time trying to install Ubuntu again in Legacy mode (to match Windows 10) but really not ideal.

Do you have backups of your personal data?

---

### Post by yancek on 2022-06-10
Grub installed in UEFI mode will not boot a Legacy install of windows.  You should be able to select the windows drive in the BIOS firmware Boot Options to boot, same for Ubuntu.  Reinstalling Ubuntu in legacy mode would be the simplest as Grub would then be able to chainload windows.

---

### Post by abirdirl on 2022-06-10
I am a bit dumb and do not have a recent backup unfortunately, but I do seemingly have access to my NVME drive with Windows from Ubuntu, which I think I can still make a backup from. Though Ubuntu doesn't see my hard drive that also has a bit of data on it so it wouldn't be a full backup for me sadly.
 While it isn't ideal like you said, I think I will try out reinstalling Ubuntu again in Legacy mode instead which I think would be for the best.

---

### Post by oldfred on 2022-06-10
You also show all drives as gpt. That is another issue.
Windows only boots from gpt drives with UEFI and only from MBR/msdos drives with BIOS.
Conversion from gpt to MBR typically totally erases drive.

Not sure how you now have gpt drive with Legacy Windows? Was Windows really UEFI with ESP on sda?

---

### Post by abirdirl on 2022-06-11
I think I was finally able to reinstall Ubuntu in legacy mode. It took  me a while to figure out no matter how I tried to reinstall it, it would  install itself as UEFI and not legacy even if I booted the USB media in  legacy mode. During installation I would get a prompt saying that that  an EFI partition wasn't found and the system would likely not be able to  boot successfully. I ended up ignoring it after a fair amount of tries  and a re-flash of the Ubuntu USB and it seems like it worked out?

However  I unfortunately still cannot boot back into Windows, and trying to boot  from any drive puts me back into Ubuntu. I tried running the  Boot-Repair again and this is what I got from the pastebin this time  [https://paste.ubuntu.com/p/8pNdwgK9bj/](https://paste.ubuntu.com/p/8pNdwgK9bj/)

I did go through the recommended repair once just to see if it'd work out afterwards, but things seem to be the same. I'm not sure if I messed up somewhere.

---

### Post by abirdirl on 2022-06-11
> **oldfred said:**
> Not sure how you now have gpt drive with Legacy Windows? Was Windows really UEFI with ESP on sda?

I'm not sure myself really, I wouldn't have thought that my Windows install was Legacy. When I installed my copy of Windows 10 I got the installation media from [https://support.microsoft.com/en-us/windows/create-installation-media-for-windows-99a58364-8c02-206f-aa6f-40c3b507420d](https://support.microsoft.com/en-us/windows/create-installation-media-for-windows-99a58364-8c02-206f-aa6f-40c3b507420d) and I simply just installed it on my NVME drive through my USB normally with no problems. 
I didn't know anything about Legacy or UEFI at the time either.

---

### Post by yancek on 2022-06-11
So you installed windows 10 yourself but don't know if it was UEFI or Legacy, is that correct?  Looking at your boot repair output, I see the first partition on the SSD appears empty and that leads me to think it may have been an EFI partition for windows.  No way to know for certain but windows 10 is generally installed in UEFI mode on a GPT drive.  You may have inadvertently deleted the data on the partition, again no way to know.  If this is the case, you are not going to be able to repair the windows boot files from Ubuntu or any Linux OS, but need to use either windows DVD/USB but you indicated you already tried that.  If you are unable to boot windows by selecting the windows drive in the BIOS Boot Options, your windows boot files are either missing or corrupted.

You now have Ubuntu installed in Legacy mode on the GPT drive which is why you have the bios_boot partition.

Given your current situation this won't help now but the best thing to do when doing a dual boot with windows/Ubuntu is to disconnect or disable the windows drive before installing Ubuntu.  I don't use windows but everything I have read is that windows on a GPT drive must be installed UEFI.

UEFI is better in a number of ways and the best long term solution would be to reinstall both windows and Ubuntu in UEFI mode.  Doing that would probably overwrite any data on the partitions so I hope you have complete backups.

---

### Post by debian-is-powerful-gcc on 2022-06-12
Just go back to your bios and check what it happening, check the boot drivers that you can run first, i don't know how it named, but, just check your BIOS and check the part that you need to enable first your USB to run with it, and choose Windows, otherwise, desactivate Windows boot secure, and try to install Ubuntu in legacy mode, as a mbr partition, then a gpt if the otherone doesn't work, so, let's try it and post the results

---

### Post by debian-is-powerful-gcc on 2022-06-12
Try to reinstall windows without format any partition, in some time it asks you, so you don't need to format it, so be careful and try to reinstall windows without lossing data

---


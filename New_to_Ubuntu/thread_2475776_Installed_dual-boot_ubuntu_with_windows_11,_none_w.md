---
title: "Installed dual-boot ubuntu with windows 11, none work anymore"
date: 2022-06-08
forum: New to Ubuntu
---

### Post by bugoi on 2022-06-08
**[SIZE=4][[[SOLVED]]][/SIZE]**
[SIZE=3]**Update 6/9/22:**[/SIZE]
**Thanks for everyone who replied! I tried everyone's suggestions but to no avail. At some point I even opened up my laptop to make sure that my SSD was not disconnected. In the end I decided to use a Boot-Repair with a live USB to uninstall Ubuntu through the terminal. Afterwards I used another live USB to reinstall Windows 11 to the laptop-- successfully! After trying to reboot my laptop a couple times to make sure, everything is going smoothly so far. (fingers crossed) Looks like I'll put off dual-booting for now. Hope you all take care. **


Hello everyone,

I am very new to ubuntu so please go easy on me. Recently, I wanted to take up learning to code and tried following a guide to install an ubuntu dual-boot to my Dell XPS 13 (2021). For reference, this laptop already had the Windows 11 OS already installed. At first, I successfully installed it and my Ubuntu OS ran just fine. Just once, that is. When I tried to boot the computer again and reboot with Windows 11, the laptop has not been able to boot the Ubuntu OS or Windows 11 OS at all. I also know that Windows 11 is fairly knew and has reported multiple problems in all aspects.

So far, I have tried using a Live Boot Repair USB and was able to obtain the following about my current situation:

[https://pastebin.ubuntu.com/p/XmFNh74vwb/](https://pastebin.ubuntu.com/p/XmFNh74vwb/)

For reference, I also have tried going to my boot configurations and choosing a boot file from my partitions, using the GRUB to choose a file to boot from, and using the Windows recovery settings to reset my PC. All were to no avail. I incredibly apologize to any jargon I may have mixed, or if anything doesn't make any sense. I would be more than happy to answer more questions that can help or clearing things up that I may have missed. I appreciate anything that you guys may advise.

---

### Post by sudodus on 2022-06-08
I'm surprised that the boot-info summary shows details for /dev/sdc, but not for /dev/sda, /dev/sdb and/or some /dev/nvme... drive.

Could it be that the computer lost contact with the internal drive because a loose connection? Or did you modify some setting in the UEFI/BIOS system, that might cause this problem? Let us hope that the internal drive has not failed.

---

### Post by bugoi on 2022-06-08
Hi sudodus!!! Thank you for the reply!

It's possible I might've changed settings in the UEFI/BIOS system while trying solutions I found online and caused this. Do you know any way I can check on whether the internal drive is connected? (without having to physically dig into the laptop)

---

### Post by sudodus on 2022-06-08
The following command when booted from an Ubuntu USB drive should show all connected mass storage devices (including internal drives) and describe in a way that is easy to understand.

```

lsblk -o model,name,size,fstype,label,mountpoint

```

It should also be shown in some UEFI/BIOS menu (not all the details but at least one line for the device itself).

---

### Post by tea for one on 2022-06-08
> **bugoi said:**
> It's possible I might've changed settings in the UEFI/BIOS system while trying solutions I found online and caused this. Do you know any way I can check on whether the internal drive is connected? (without having to physically dig into the laptop)
Many new(ish) PCs/Laptops have UEFI settings where devices can be enabled/disabled.
These switches include internal storage, external USB devices, wireless, bluetooth etc.

Have a look in the UEFI settings to see if you can remember the setting where you may have changed something.
Do you have settings for Devices or Storage or SSD or NVME or similar phrases?

---

### Post by oldfred on 2022-06-08
Dell uses both Windows and Linux fwupdate to update UEFI.
Did you have UEFI Secure boot on when installing Ubuntu? Drives in AHCI, not Intel RST or RAID? 
And often an UEFI update resets some settings back to defaults. So you may need to redo settings.
Do you have latest UEFI firmware & if SSD, SSD firmware?

I have to keep a list on one system as many are changed. My other system only changed a few. But they are older and not in any auto update list. You may not even know that an UEFI update was part of the other updates.
Windows updates also may turn Windows fast start up back on which prevent the Linux NTFS driver from seeing NTFS partitions.
Double check UEFI settings, f2.

You should always be able to boot either system directly from UEFI boot menu, f12. But grub will only boot working Windows. Or Windows must not need chkdsk nor have fast start up/hibernation on.
Grub  only boots working Windows.

---

### Post by bugoi on 2022-06-08
> **sudodus said:**
> The following command when booted from an Ubuntu USB drive should show all connected mass storage devices (including internal drives) and describe in a way that is easy to understand.

```

lsblk -o model,name,size,fstype,label,mountpoint

```

It should also be shown in some UEFI/BIOS menu (not all the details but at least one line for the device itself).

hello again!
i entered the code you showed me into the LXTerminal when I booted a Live Boot Repair USB. I saw only the following:

```

USB Flash Drive  sdc     14.9G                      

```

It does indeed seem that there are no other drivers connected (although correct me if I am wrong)

---

### Post by bugoi on 2022-06-08
> **tea for one said:**
> Many new(ish) PCs/Laptops have UEFI settings where devices can be enabled/disabled.
These switches include internal storage, external USB devices, wireless, bluetooth etc.

Have a look in the UEFI settings to see if you can remember the setting where you may have changed something.
Do you have settings for Devices or Storage or SSD or NVME or similar phrases?

Thanks for the reply Tea for One!!!!

I took a look into my UEFI/BIOS Setup and found the Storage tab where I found the following with the phrases you spoke of:

-----------------------------------------------------------

[INDENT][SIZE=3]**Storage Interface**[/SIZE]
[COLOR=#696969]**Port Enablement**[/COLOR]
Select onboard drives to enable:
This page allows you to select the onboard drives you would like to enable.
**M.2 PCIe SSD**
[switch] ON


[SIZE=3]**Drive Information**[/SIZE]

M.2 PCIe SSD

Type     =512GB PM991a NVMe Samsung 512GB
Device  =PM991a NVMe Samsung 512GB

[/INDENT]
-----------------------------------------------------------

For reference, I don't recall touching any settings in the Storage tab at all previously, so the storage was always switched "ON".

---

### Post by bugoi on 2022-06-08
> **oldfred said:**
> Dell uses both Windows and Linux fwupdate to update UEFI.
Did you have UEFI Secure boot on when installing Ubuntu? Drives in AHCI, not Intel RST or RAID? 
And often an UEFI update resets some settings back to defaults. So you may need to redo settings.
Do you have latest UEFI firmware & if SSD, SSD firmware?

I have to keep a list on one system as many are changed. My other system only changed a few. But they are older and not in any auto update list. You may not even know that an UEFI update was part of the other updates.
Windows updates also may turn Windows fast start up back on which prevent the Linux NTFS driver from seeing NTFS partitions.
Double check UEFI settings, f2.

You should always be able to boot either system directly from UEFI boot menu, f12. But grub will only boot working Windows. Or Windows must not need chkdsk nor have fast start up/hibernation on.
Grub  only boots working Windows.

Hi oldfred thank you for the reply!!

According to my current UEFI settings:
[LIST]
[*]Secure Boot Mode is enabled.
[*]My drives are currently ticked in RAID, should I change it to AHCI/NVMe? Although I receive a warning that says "SATA/NVMe Operation Status changed! Warning! Changing this setting may prevent your operating system from booting or require a reinstall. Are you sure you would like to continue?". Should I select "Yes" anyway?
[*]As for the latest firmware, I believe I updated my UEFI firmware but I can double-check. Do you happen to know any way to check or update my UEFI/SSD firmware through the boot menu?
[*]Whenever I tried to boot each OS through the boot menu, Ubuntu fails and shows me a code (at the end describing a kernel panic, please let me know if you would like to see more of this code), while the Windows OS shuts the laptop down completely.
[/LIST]

---

### Post by oldfred on 2022-06-08
If you change drive settings you probably need the AHCI driver in Windows or it will not boot. Not sure if only NVMe if then AHCI driver required as it actually is different.
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 

But if you do a safe boot first to update Windows, then boot to UEFI/BIOS and change to AHCI and finally boot normally, it works
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500) &

---

### Post by TheFu on 2022-06-08
Issues like this are why I stopped dual booting and switched to using virtual machines around 2008.  Any Core2 Duo or faster CPU can handle virtual machines.  It removes nearly all the hardware hassles and lets people new to Linux learn the OS, not how to make their hardware work, which can be a challenge with really new stuff.

Plus, Win11 includes mandates that aren't mandates for Linux to work, so just avoid all those hardware settings by using a virtual machine instead.

But I get that you probably won't listen to me.  That's fine too.  At the Linux InstallFests we hold here, we always strongly push for virtual machines to be used to avoid all sorts of issues.  Of 75 people, usually about 5 insist on a dual boot or 100% wipe Windows solution.  IT in companies uses virtualization and it is a basic skill to have if you expect to work in programming or IT support, operations or architecture roles.  Plus, every time MSFT decides to screw with their boot files, you won't lose access to Linux like commonly happens to dual-tri-quad boot Linux systems with 1 MSFT OS installed too.

---

### Post by mIk3_08 on 2022-06-09
> **bugoi said:**
> **[SIZE=4][[[SOLVED]]][/SIZE]**

For more information on how to solve the thread post. Just click the "solve thread" in [COLOR=#ff0000]red [/COLOR]font below. Regards and cheers.

---


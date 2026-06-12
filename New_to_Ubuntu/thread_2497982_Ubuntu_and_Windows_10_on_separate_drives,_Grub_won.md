---
title: "Ubuntu and Windows 10 on separate drives, Grub won't show Windows 10 to boot into"
date: 2024-05-24
forum: New to Ubuntu
---

### Post by bzerk on 2024-05-24
On my main drive I've installed Windows 10, and on my second drive I previously had Mint installed. 
While having Mint, upon boot, Grub offered me to choose between Windows or Linux to boot.
I then tried out some Linux distros: Debian, POP_OS!, even started to mess with Arch Linux, and some others. Eventually dropped it, formatted the Linux drive, and tried to boot Windows again.
As it did not work, I did some things in the EFI boot partition (I guess) through the Windows CMD in repair mode. While I can't recall what exactly it was that I did, I remember deleting some Linux entries from it.

Also, there was this Microsoft forum [post]("https://answers.microsoft.com/en-us/windows/forum/all/cant-boot-up-windows-10-after-removing-ubuntu/7b492775-98ff-45cc-8bbc-269bd2a8603a") based on which I did execute the following commands:

```
chkdsk D: /f /r (and press Enter)
bootrec /fixmbr (and press Enter)
bootrec /fixboot (and press Enter)
bootrec /scanos (and press Enter)
bootrec /rebuildbcd (and press Enter)
sfc /scannow (and press Enter)

```

and also set the Windows drive letter to ```
C
```

Eventually, I came back to Ubuntu, precisely 24.4 LTS, since I've been using 22.04 on my work notebook for some months now.

Now the thing is, what ever I try, I seem to be unable to get Grub back to letting me chose which OS I want to boot.
As described [here]("https://askubuntu.com/a/124100,"), I've used the command ```
sudo efibootmgr -v
```
Also, the command ```
sudo update-grub
```
Then, as no other things worked for me, did run ```
ynnubuntu boot-repiar
``` in *default* mode, and also one time in *advanced*.
 
The options I checked are ```
Reinstall GRUB
Upgrade GRUB to its most recent version
```

As none of these worked, I just re-run boot-repair in order to get you the [report]("https://paste.ubuntu.com/p/NnXffM3fqy/") of my system, in the hopes of finding someone who may be able to help me.

---

### Post by tea for one on 2024-05-25
[COLOR="#0000FF"]Line 333[/COLOR]  - LegacyWindows detected
[COLOR="#0000FF"]Line 56[/COLOR]   - /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg
[COLOR="#0000FF"]Line 105[/COLOR] - The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
[COLOR="#0000FF"]Line 145[/COLOR] - sdb1: is---ESP

You have mixed mode installations.
Windows 10 in legacy mode (line 333)
Ubuntu in UEFI mode (Lines 56, 105, 145)

Best solution:-
Remove/isolate all disks except nvme0n1 (your Windows disk)
Back up Windows data
Re-install Windows 10 or 11 in UEFI mode with GPT
Restore data

Then, check and boot each OS from PC boot menu
Subsequently, edit Grub to locate Windows Boot Manager

---

### Post by bzerk on 2024-05-25
Hi tea for one, thank you for your reply and help!
Would it be helpful to just only reinstall Ubuntu in legacy mode? I want to avoid messing with my Windows if possible

---

### Post by tea for one on 2024-05-25
> **bzerk said:**
> Would it be helpful to just only reinstall Ubuntu in legacy mode? 
Not really a long term solution but why not give it a go?
I suspect that you wish to do this to see if Grub picks up the Windows Boot Manager?

> **bzerk said:**
> I want to avoid messing with my Windows if possible
Microsoft has mandated for many years that Windows 10/11 use UEFI mode with GPT.
If you remain with Legacy mode, then, possibly, future updates may be compromised.

Anyway, I would still recommend that you join the modern world and re-install Windows 10/11 in UEFI mode with GPT.
Whatever you decide, ensure that you have backups and only have target disks accessible before installing either Ubuntu or Windows.

---

### Post by yancek on 2024-05-25
Reinstalling Ubuntu in Legacy mode on sdb should work but you should read a bit about doing this as the standard on a GPT drive is to use UEFI.   You will need to create a bios_boot partition on that drive and you will not need the EFI partition on that drive.   There are countless sites with instructions on this if you do an online search.

Since your windows is installed on a dos drive rather than GPT, you would need to change the drive to GPT to install windows UEFI and I don't know if that will lose all your data. 

> nvme0n1    : notGPT

Did you read through the suggested repair of boot repair, beginning at line 333 to "enable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware"?  Also on line 338 it suggest turning on Legacy mode in the BIOS and mounting encrypted partitions.  Did you do this?  I would suggest you make this change before reinstalling.  My experience is that it is possible to boot mixed modes IF the systems are on separate drives.

Another thing I would mention is that Legacy/CSM may not be available on newer computers for much longer.  Beginning around 2020, some manufacturers have only enabled/allowed UEFI boot on new computers.

---

### Post by oldfred on 2024-05-25
I agree with tea for one on biting the bullet & changing Windows to UEFI.
But good backups are required as change from MBR(msdos) to gpt will totally erase drive.

I have seen users dual boot in different modes and just decided to always boot from UEFI boot menu. Older systems required settings for UEFI or BIOS/CSM/Legacy and only booted in that mode. But newer ones would boot in either mode as long as Secure boot is off in UEFI settings. Grub will not boot Windows, but UEFI boot menu will boot either system and changes boot mode to match.

Still need to plan to convert Windows to UEFI at some point in future.

---


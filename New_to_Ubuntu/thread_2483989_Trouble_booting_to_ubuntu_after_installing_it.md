---
title: "Trouble booting to ubuntu after installing it"
date: 2023-02-14
forum: New to Ubuntu
---

### Post by moeez1601 on 2023-02-14
Hi,
I am trying to dual boot my windows. When I was installing ubuntu I got an error message "Error installing grub-efi-amd64-signed". I have also the images of the error messages. The problem it is causing is that it boots directly to windows and doesn't give me an option to chose operating system. At first I thought my new OS is installed so restarted my windows and it started showing a screen for recovery key of bitlocker. I put in the recovery key but it booted into windows directly without giving me menu to choose the operating system. I have also tried boot repair in live ubuntu using my USB but that also didn't work. I am working on hp envy windows 11. I booted my USB using Rufus. My system is using UEFI boot and disk is GPT.

---

### Post by tea for one on 2023-02-14
> **moeez1601 said:**
>  I have also tried boot repair in live ubuntu using my USB but that also didn't work. 
Boot-repair will allow you to submit a report so that help can be provided.
Can you boot into an Ubuntu live session and download the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread before attempting any repair.

---

### Post by oldfred on 2023-02-14
What version of Ubuntu? If new system, you need newest version or at least 22.04.1 (.2 out in a couple of weeks). Or maybe even 22.10 to get very newest kernel  & drivers.

HP not the easiest to set up for dual boot. 
It needs some extra settings & you can only change boot order in HP's UEFI settings (not boot menu).

You also need Windows bitlocker off & Windows fast start up off.
Often easier with UEFI Secure Boot off, but Ubuntu should installs with it on. 
What model Envy, do it have nVidia as that also adds some issues.
Does it have Optane?

HP 15-dw4047nr Windows 11 WiFi issues
[https://ubuntuforums.org/showthread.php?t=2482797](https://ubuntuforums.org/showthread.php?t=2482797)
HP Zbook 15 NVRAM locked, install issues
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
HP Envy - use UEFI to change boot order & f9 f10
[https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun](https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun)
HP Pavilion 15t touch (15t cs-200) Post @@ totally remove optane card
[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)

---

### Post by moeez1601 on 2023-02-14
I already tried the second option. Here is the pastebin link: [https://paste.ubuntu.com/p/6h7CDgKC3H/](https://paste.ubuntu.com/p/6h7CDgKC3H/)

---

### Post by oldfred on 2023-02-14
See post #3.
Looks like you did not change those settings.
And is the RAID nvme1n1 really optane? That causes many issues.

---

### Post by moeez1601 on 2023-02-15
How can I check if my computer is RAID nvm1n1 really optane. It is hp envy x360. I had turned off windows fast start up. I tried turning off the bitlocker but my computer does not give option to turn off the bitlocker.

---

### Post by oldfred on 2023-02-15
It looks like HP used x360 on a variety of models.
So some issues may be similar or not?

Google tells me this & I think that is what I did in Windows.
> Press Windows Start button. Type bitlocker. Click Manage BitLocker to enter the BitLocker Drive Encryption menu. Select Turn off BitLocker to proceed with decryption.

 HP Spectre x360 15t  Optane issue
[https://ubuntuforums.org/showthread.php?t=2474790](https://ubuntuforums.org/showthread.php?t=2474790)
HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume) & 
[https://askubuntu.com/questions/1345338/common-failed-to-install-grub](https://askubuntu.com/questions/1345338/common-failed-to-install-grub)
HP X360 Update UEFI F20, probably newer now
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086) & 
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)
See last post for many boot parameters, still using UEFI, not Legacy

---

### Post by moeez1601 on 2023-02-15
I turned off the bitlocker as well. What I should do to prevent booting straight to windows?

---

### Post by oldfred on 2023-02-15
It looks like it never fully installed grub.
Does Boot-Repair now give choice to install grub (not just update it)?
Or in Boot-Repair's advanced mode choose the option to totally reinstall grub. 
Be sure to boot live installer in UEFI boot mode.

---

### Post by tea for one on 2023-02-15
> **moeez1601 said:**
> I turned off the bitlocker as well. What I should do to prevent booting straight to windows?
[COLOR="#0000FF"]Line 42[/COLOR] - SecureBoot enabled.
Jump into your UEFI settings and disable Secure Boot.

While you are there, double check the following settings:-
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Optane memory and storage

---

### Post by moeez1601 on 2023-02-15
I can see the ubuntu in Boot Option Menu but when I click on it gives error. What to do to get rid of the error?

---

### Post by oldfred on 2023-02-15
Does it boot?
Then errors may be just warnings.
Or are you getting grub> which is not fully booting.
Specifically what error?
Some are related to optional settings. Almost everyone gets some as UEFI/BIOS is not implemented the same by every vendor.

---


---
title: "Xubuntu won't boot after USB Install."
date: 2014-07-29
forum: New to Ubuntu
---

### Post by brianwitte22 on 2014-07-29
Booted Xubuntu from USB Drive from Windows 8 on Toshiba Satelite C55D laptop. 
Wiped Windows 8 and installed Xubuntu. 
After installation when the restart is prompted in order to use system, I remove USB and it says No Bootable Device.
 I reinsert USB and it goes to grub and says Try Xubuntu, Install Xubuntu like it was never installed. 
Installed and ran boot-repair with recommended repair from Try Xubuntu terminal. 
It still doesn't boot. 
Here is boot info summary: [http://paste.ubuntu.com/7893074/](http://paste.ubuntu.com/7893074/)


Thank you for any help. My ignorance is painful.

---

### Post by markodd on 2014-08-11
This is probably not helpfull but maybe, in the BIOS settings you've not set it to boot using the HDD?

---

### Post by JKyleOKC on 2014-08-11
> **brianwitte22 said:**
> Here is boot info summary: [http://paste.ubuntu.com/7893074/](http://paste.ubuntu.com/7893074/)


Thank you for any help. My ignorance is painful.Your boot-repair log shows the probable problem: > /boot/efi detected in the fstab of sda2: UUID=8D90-8B34	 (sda1)
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [email]boot.repair@gmail.com[/email]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.Win8 uses "secure boot" and that can create such situations. I fortunately haven't had to solve them myself so cannot help you much, but at least I can point you to a few resources that may. Search the forums for "uefi" and "secure boot." Hopefully, OldFred will discover your message and jump in here. Also an email message to the author of boot.repair will definitely get more assistance; he, too, is a regular on these forums.

---

### Post by Jonathan Precise on 2014-08-11
Go to BIOS settings, and go to an option that says "Secure boot". Set to disabled.

---


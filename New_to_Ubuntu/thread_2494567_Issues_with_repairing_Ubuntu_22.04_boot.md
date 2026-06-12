---
title: "Issues with repairing Ubuntu 22.04 boot"
date: 2024-01-20
forum: New to Ubuntu
---

### Post by the-rwandan-it-guy on 2024-01-20
Hello kind people, 

I am new here. I am having an issue with repairing an Ubuntu 22.04 LTS boot, and I am afraid I damaged it further while trying to use boot-repair. Any help would be kindly appreciated. [Here is the boot info summary]("https://*******.us/07NPgJ"): **s p r u n g e [dot] **us**/**07NPgJ 

For more contest: I have a very important database installed on this Lenovo laptop whose Ubuntu OS crashed. Unfortunately, I have no recent database backup, hence the attempt to fix the boot so that, hopefully, I can make a copy of the Postgresql database, then wipe clean the laptop.

Regards,
A.

- Note: I don't understand how links work yet, I realized that they get obfuscated by the system.

---

### Post by Rubi1200 on 2024-01-20
The link does not work. Please run the boot info summary from a liveUSB and choose the report and then post the pastebin link back here.

Thanks.

---

### Post by oldfred on 2024-01-20
Boot-Repair normally uses paste.ubuntu.com as its site. 
The site you used, uses a word not allowed in the forum.

If I combined it correctly, I got to your report.

You can go to that site and use the last 6 characters to get your report, but better to use working link as most that support users will not go to that extra effort and should not need to. 

You booted Boot-Repair in UEFI boot mode, but it looks like you have grub in old BIOS boot mode on very old MBR(msdos) partitioned drive.
You have UEFI system. Microsoft has required vendors to install in UEFI/gpt mode since 2012, so most hardware is UEFI.
But conversion from MBR to gpt will totally erase drive, so do not make that conversion without very good backups.

Also do not use Boot-Repair's default fix of installing grub in UEFI mode. How you boot install or repair media for both Windows & Ubuntu is then how it installs or repairs. You have BIOS system installed, so should boot in BIOS mode to make BIOS repairs.

System looks like standard BIOS boot. Did you turn on UEFI boot in UEFI/BIOS settings?
UEFI/BIOS setting is normally only for installed system, you manually select UEFI or not when booting live installer.

---

### Post by Impavidus on 2024-01-21
> **the-rwandan-it-guy said:**
> 
For more contest: I have a very important database installed on this Lenovo laptop whose Ubuntu OS crashed. Unfortunately, I have no recent database backup, hence the attempt to fix the boot so that, hopefully, I can make a copy of the Postgresql database, then wipe clean the laptop.


There's no need to first repair boot before backing up your database. You can access your harddrive using the same live system on which you use boot-repair (or reinstall).

---


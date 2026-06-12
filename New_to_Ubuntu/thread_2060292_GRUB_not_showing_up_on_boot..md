---
title: "GRUB not showing up on boot."
date: 2012-09-19
forum: New to Ubuntu
---

### Post by neale3456 on 2012-09-19
Hello. I have installed the latest version of Ubuntu and the GRUB menu is not showing up. I have tried pressing the shift and the escape keys but those don't work. Thanks for the help.

---

### Post by oldfred on 2012-09-19
You have to hold shift from BIOS until menu appears.

Does system boot?

From system or liveCD down load and run the BootInfo report. Post link it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Wim Sturkenboom on 2012-09-20
Is this a dual boot or just Ubuntu installed.

In case of dual boot, what happens? Boot straight to Windows? In that case, you might have an UEFI bios.

If it's only Ubuntu installed (and it boots properly), you can enable the menu. Edit /etc/default/grub (you need root permissions) and modify the hidden timeout as shown below (in bold red)

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
**[COLOR="Red"]GRUB_HIDDEN_TIMEOUT=[/COLOR]**
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Save the file and run
```

sudo update-grub

```
to activate the changes and after a reboot you will always have the menu.

---

### Post by YannBuntu on 2012-09-20
Hello

1) Try the 'Recommended repair' of [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Indicate us the URL that will appear. Reboot the PC.
2) if still not good, setup your BIOS so that it boot the Ubuntu disk first. Reboot the PC. Tell us what you observe.

---

### Post by neale3456 on 2012-09-20
I downloaded and installed Boot repair. I started it up and I clicked on recommend  repair and I got this error message. "You have installed on sda6 a Linux version which is not EFI-compatible. It is probably incompatible with your computer. Please install an EFI-compatible system. For example, Ubuntu-Secure-Remix-64bits and Ubuntu-64bits are EFI-compatible systems."

---

### Post by oldfred on 2012-09-20
It sounds like it is saying this is a new system with UEFI not BIOS booting. You then have to use the 64 bit version not the 32bit version of Ubuntu. Ubuntu only suggests the 32 bit as many users have old systems that can only run 32 bit. They assume users with new systems know to use 64 bit.

Post the link to the BootInfo report Boot-Repair creates.

---

### Post by neale3456 on 2012-09-20
I downloaded the 64bit version of Ubuntu and GRUB appears! Everything appears to be working fine. Thanks for the help.

---

### Post by YannBuntu on 2012-09-21
@neale3456: good job, and happy Ubuntu-ing :)


> **oldfred said:**
> It sounds like it is saying this is a new system with UEFI not BIOS booting. You then have to use the 64 bit version not the 32bit version of Ubuntu.

Exactly. B-R detected that the installed Ubuntu is 32bit (which is incompatible with 64bit-UEFI firmware), so it asks the user to reinstall a 64bit instead. 
See:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1020446](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1020446)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996332](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996332)

(@neale: you can login to your Launchpad account, and mark yourself "Affected" by these bugs)

---


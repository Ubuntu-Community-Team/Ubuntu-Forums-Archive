---
title: "full disk encryption problem with ubuntu 18.04"
date: 2021-01-23
forum: New to Ubuntu
---

### Post by elypzkou on 2021-01-23
Hello everyone I am following the steps detailed here [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)[URL="https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019"]
[/URL] to achieve (almost) full disk encryption.
Unfortunately I have run into a problem at the very end of the process.
The guide says this command ```
# while [ ! -d /target/etc/default/grub.d ]; do sleep 1; done; echo "GRUB_ENABLE_CRYPTODISK=y" > /target/etc/default/grub.d/local.cfg
``` should return almost immediatly, as the grub folder is created rather early in the installation process.
However in my case the installation stops at "installing the 'grub2' package" and the terminal keeps hanging.

I also get this error message:
GRUB installation failed.
The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.

Any idea what could be causing this ? i made sure to do everything the same way it's done in the guide


some additional information: i disabled legacy mode from my bios and i selected uefi mode on rufus when creating the bootable usb stick with ubuntu. i will try non-uefi mode and let you know if that fixes this.

---

### Post by elypzkou on 2021-01-23
update: for some unknown reason running live ubuntu in BIOS mode did not give me this installation error. I had to enable legacy mode on my bios, change the settings on rufus while preparing the live installation and pick the non-uefi option when booting from usb.

update2: found the reason. according to this bug report [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1771651](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1771651) you need to manually create an efi partition if you boot in UEFI mode and pick the "something else" option when the installation asks you if you want to partition your hard disk.

I feel like this is quite the crucial piece of information that the guide is missing.

---

### Post by coffeecat on 2021-01-23
> **elypzkou said:**
> 
I feel like this is quite the crucial piece of information that the guide is missing.

Then why not contact the author and sole editor of that guide? The page history for your link shows that "tj" is the sole editor, and links to tj's launchpad page where you can get their email if you log into launchpad.

---


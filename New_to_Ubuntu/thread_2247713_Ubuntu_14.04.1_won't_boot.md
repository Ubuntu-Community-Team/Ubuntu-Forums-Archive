---
title: "Ubuntu 14.04.1 won't boot"
date: 2014-10-09
forum: New to Ubuntu
---

### Post by whoami2 on 2014-10-09
Installed Ubuntu 14.04.1.  Rebooted and it sets at 'Loading Operating System'.  Put the live install disk in.  Ran boot-repair.  Boot-repair gave this message: 'EFI detected.  Please check the options.  Here is the URL from boot-repair.  [http://paste.ubuntu.com/8528754](http://paste.ubuntu.com/8528754).  I'm typing this thread from running the live cd.  I'm not sure how to access the ubuntu instalation, that I just installed.

---

### Post by grahammechanical on 2014-10-09
The boot loader was not installed into the MBR

> No boot loader is installed in the MBR of /dev/sda.

This is Boot Repair's recommended repair
> [COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would purge [COLOR=#666666]([/COLOR]in order to sign-grub upgrade version[COLOR=#666666])[/COLOR] and reinstall the grub-efi-amd64-signed of sda2, using the following options: upgrade-grub       sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s

The repair did not work because you did not accept Boot Repair's offer to repair.

> [COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.

No change has been performed on your computer.

It says it all, really. You need to accept the repair and do this

> Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!
Regards.

---

### Post by oldfred on 2014-10-09
Did you leave secure boot on?
The only reason to install the signed versions is if you have secure boot on.

Since you only have Ubuntu, you may have one of those systems that only boots Windows.
We can recreate the Windows folder in the efi partition, copy grub into that folder and rename it to the Windows efi file, so UEFI thinks it is booting Windows.

What brand, model computer is this?

---

### Post by whoami2 on 2014-10-15
Well being new to Ubuntu, I google searched to see why it wouldn't boot/load into the newly installed Ubuntu OS.  Tried a few things (that didn't work).  Come to find out.  The setting in my BIOS was set to EFI.  I changed it to 'Non-EFI' and now it boots into Ubuntu.  Guess I was just too new to Ubuntu to know what I was doing and tried too hard.  But it's working now and that's what matters.  Thanks for your answers though.

---


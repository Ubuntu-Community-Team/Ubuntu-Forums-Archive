---
title: "Live Mode - Recovery Mode - Entering a Boot Command"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-04-01
I have Lubuntu in a Flash Drive for running in Live Mode.  In trying fixes for my incompatible SIS Graphics card, I thought I would try Recovery Mode.

Recovery Mode is entered after a reset if holding down the left Shift key or hitting the Escape key multiple times.

I get a prompt for a boot command at the bottom of the screen.  What is typically entered there?  What would a normal boot look like?

Anything I typed was rejected.  I realize that another option is the boot menu where it is probably easier to modify the boot command, but I would also like to learn how to use Recovery Mode.

---

### Post by grahammechanical on 2014-04-01
Recovery mode as I understand it is available on an install of Ubuntu. It is an option at the Grub menu. In the latest versions of Ubuntu we find Recovery mode in the Advanced Options for Ubuntu sub-menu. The Recovery menu has the following options:

1) resume              - Resume normal boot. This loads Ubuntu without activating a proprietary video driver.
2) clean                 - Try to make free space.
3) dpkg                  - Repair broken packages.
4) failsafeX             - Run in failsafe graphic mode. I have found this option next to useless.
5) fsck                   - Check all file systems.
6) grub                  - Update Grub bootloader
7) network             - Enable networking.
8) root                   - Drop to root shell prompt.
9) system-summary - System Summary. Produces information about the hardware.

I do not know what you are thinking of. I guess that what you are getting is a space to alter the Grub boot parameters. That is not a Linux command line interface. That is why Linux commands do not work. Grub does have some commands specific to itself and the Grub boot screen does tells about a key to press to get to a Grub command line prompt. Perhaps that is what you are getting. Again, Linux commands do not work because Linux has not yet been loaded.

This is where you can get a Grub manual from

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

Regards.

---

### Post by KAWill70 on 2014-04-01
Thanks very much for the help.  I had read about the Recovery Mode in this forum and decided to try it.  A few minutes ago I reset my other computer with the Lubuntu Flash Drive inserted and held down the left shift key.

As soon as boot started the computer displayed SYSLINUX 4.07 EDD 2013-07-25 along with copyright information and a name.  On the next line it displayed the following:

boot:

If I type anything along with a carriage return it displays "Could Not Find Kernel Image".  Maybe the recovery mode is only meant for systems installed on disk.  I should probably move on.  At the normal Boot Menu (running Live) I can alter boot parameters and boot Lubuntu with some modifications (nomodeset xforcevesa) to get around my graphics adapter incompatibilities.

---

### Post by steeldriver on 2014-04-01
I think in the context of a live USB boot, interrupting it would drop you into the SYSLINUX bootloader (not grub)

You should get the option to set kernel parameters like nomodeset once you get to the 'Try [L]ubuntu' splash screen

---


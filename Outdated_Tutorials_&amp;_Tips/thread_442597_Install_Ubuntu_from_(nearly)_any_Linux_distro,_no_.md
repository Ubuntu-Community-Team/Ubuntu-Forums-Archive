---
title: "Install *Ubuntu from (nearly) any Linux distro, no partitioning needed, with Lubi"
date: 2007-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by tuxcantfly on 2007-05-13
**NEW THREAD LOCATION: [http://ubuntuforums.org/showthread.php?t=441918](http://ubuntuforums.org/showthread.php?t=441918) CHECK THERE FOR UPDATES ON INSTRUCTIONS (THESE WILL NO LONGER BE UPDATED), POST ALL REPLIES THERE**

Ever wanted to test the new K/X/Ubuntu 7.04 Feisty, but don't have a spare partition, and don't want to jeopardize your production environment by resizing partitions, dist-updating, or tinkering with its bootloader? Now you can leave your existing Linux distro (Ubuntu, Debian, Sabayon, Fedora, openSUSE, Gentoo, etc.) untouched, while being able to use Ubuntu 7.04 Feisty in a full-fledged install on a loopmounted partition, no partitioning required! Note: this guide is for Linux users, NOT for Windows users; Windows users should use Wubi [http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

**Credits**

I wrote Lubi and this guide. Lupin [http://launchpad.net/lupin](http://launchpad.net/lupin) is used as the codebase, see the Wubi forum at [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234) and the site at [http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html) for details.

**Tested Versions**

This has been tested on Sabayon 3.3 32-bit, PCLinuxOS 2007 32-bit, openSUSE 10.2 32-bit, Gentoo 2007.0 32-bit, Fedora Core 6 32-bit, Debian Sid 32-bit, Ubuntu 6.10 Edgy 32-bit, Ubuntu 7.04 Feisty 32-bit, and Xubuntu 7.04 Feisty 32-bit as the host systems. Kubuntu 7.04 Feisty 32-bit, Xubuntu 7.04 Feisty 32-bit, and Ubuntu 7.04 Feisty 32-bit were tested as guest systems. Other distros and versions, both 32-bit and 64-bit should work as the host system, just make sure you have the packages installed that are listed below. Distros and versions not based on Ubuntu 7.04 Feisty, and non-x86 architectures can also be used as the guest system, but these will require a custom build of lupin; see [https://launchpad.net/lupin](https://launchpad.net/lupin) for details.* **Installations using LVM as the root filesystem are currently not supported***. If this works/doesn't work for you please post the host/guest distro, version, and architecture.

**What it does**

Basically, it downloads a K/X/Ubuntu alternate i386 iso, creates loopmounted disk images so that they can be installed there, and adds an entry into /boot/grub/menu.lst which starts the d-i installer with that iso, and installs it into the loopmounted disk images. What thus results is a dual-boot system, in which K/X/Ubuntu are installed in loopmounted disk images in the folder /wubi/ on the filesystem, so that they can be installed without requiring any repartitioning, and they are booted using the system's GRUB, with the last menu entry, "Ubuntu", being added by the script to boot the loopmounted disk images.

**Requirements/Dependencies**

Before installing, please ensure that you have zenity (used for the GUI), and GRUB (used as the bootloader) installed. If not, install zenity and grub using emerge, apt-get, yum, yast2, or your distribution's equivalent. For Ubuntu and Debian, these should already have been installed.

**Installing**

1. Download the latest code from [http://cutlersoftware.com/ubuntusetup/lubi](http://cutlersoftware.com/ubuntusetup/lubi)

2. Then, become root:

For openSUSE and other su-based distros, login as root, while in Ubuntu and other sudo-based distros, enter:
```
sudo -s
```

3. Then, run the script:

```
chmod +x ./lubi.sh
./lubi.sh
```

4. Answer the questions asked by the wizard, wait while the iso is downloaded, the disk images are created, and the grub entry is added, and you will then be prompted to reboot; reboot.

5. Upon rebooting, the GRUB menu should have a new line at the end, saying "Ubuntu". Select that one, and it will start the d-i installer in non-interactive mode, and will reboot again

6. Select "Ubuntu" in GRUB to boot your newly installed ubuntu, then upon booting, login with the username and password you supplied to the installer

**Uninstalling/Removal/Undoing Changes**

These 2 commands, entered in the terminal, will remove your loopmounted Ubuntu install, and undo the changes to GRUB:
```

sudo rm -r /wubi
sudo mv /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

Use this guide at your own risk, though if you encounter issues related to loopmounted installation, you should ask them in the Wubi forums at [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234) as it is a generic Lupin/Wubi issue, not a Lubi problem. Post any issues related to Lubi here, and include the host and guest distro, architecture, and version. Also post results if installation succeeds on a host/guest distro/version/architecture combination that isn't listed above. The main lubi development page is at [https://launchpad.net/lubi](https://launchpad.net/lubi)

---

### Post by tuxcantfly on 2007-05-21
I've added support for suse-based distros, and gentoo/sabayon support is in the works (in the code but still untested)... any testers out there to report success/failures with installation?

---

### Post by tuxcantfly on 2007-05-21
with the latest version, all distros should (sabayon, gentoo, opensuse, ubuntu, debian, fedora tested, others should work too) now be compatible, except those installations using LVM as root filesystem

---

### Post by tuxcantfly on 2007-05-21
**NEW THREAD LOCATION: [http://ubuntuforums.org/showthread.php?t=441918](http://ubuntuforums.org/showthread.php?t=441918) CHECK THERE FOR UPDATES ON INSTRUCTIONS (THESE WILL NO LONGER BE UPDATED), POST ALL REPLIES THERE**

will some mod please close this thread for me, or, if possible, have this redirect to [http://ubuntuforums.org/showthread.php?t=441918](http://ubuntuforums.org/showthread.php?t=441918) please? thanks...

---


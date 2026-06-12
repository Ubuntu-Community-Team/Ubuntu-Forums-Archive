---
title: "Boot problem due to upgrade interrupt"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by EivindMB on 2011-11-19
Hi!

I tried to upgrade my Ubuntu from 11.04 to 11.10, but the upgrade was interrupted while installing. Now I can't start ubuntu at all.

Is there a way to go back to the last known working configuration, or perhaps finish the upgrade in recovery mode?

As of now I can enter recovery mode, but anything else is off limits.

---

### Post by dniMretsaM on 2011-11-19
The easiest thing to do would probably be a fresh install. You did make a backup of your important files, right?

---

### Post by oldfred on 2011-11-19
If you can get to command line, you should not have to chroot into your system to fix it.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by EivindMB on 2011-11-20
Thanks!

I ran "dpkg --configure -a", and now the starting recovery mode brings me some options. Things like: "Boot Ubuntu", "Drop to shell" etc. When I now try to start Ubuntu normally I get just past the Ubuntu logo with the five dots, and then I get quite a long error message:

> 
*Starting the Winbind daemon winbind
*Starting bluetooth
*PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
fsck from util-linux 2.19.1
udevd[508]: failed to execute '/lib/udev/mtp-probe' 'mtp-probe /sys/devices/pci0000:00/0000:16.2/usb2/2-1 2 2': No such file or directory

/dev/sda5: clean, 337343/18907136 files, 7546686/75597568 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
*Starting AppArmor profiles
speech-dispatcher disabled; edit /etc/default/speech-dispatcher


And nothing more happens.

Suggestions?

---

### Post by oldfred on 2011-11-20
I am not familar with those errors, someone else may have seen them.

---


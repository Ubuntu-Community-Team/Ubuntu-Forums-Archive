---
title: "Ext4-fs error"
date: 2020-01-27
forum: New to Ubuntu
---

### Post by guanacone on 2020-01-27
Hello,

Unfortunately my system crashes randomly and I'm unable to figure out why. It has something to do with ext4-fs error. Please let me know what information I can provide in order to get support.

Thank you very much.

---

### Post by TheFu on 2020-01-27
Crashing usually means a hardware failure.  The system log files should have errors and/or warnings showing any issues. Check those using whatever method you like.  There is probably a log viewer in the menu somewhere if on a desktop system.

Which DE and release of Ubuntu is being run?

What sort of disks are being used?

What have you tried already before posting?  Did you search these forums for similar issues and recommended actions to take? You should.

Commands to read up on - fsck, smartctl, journalctl

---

### Post by Impavidus on 2020-01-28
The ext4-fs message suggests there's a problem with your filesystem. A damaged filesystem, a failing harddrive or a loose connector.

---

### Post by guanacone on 2020-01-28
Thanks @Imavidus and @TheFu.

I'm running Ubuntu 18.04.3 LTS on a Lenovo ThinkPad L490 with a INTELSSDPEKKF256G8L disk. 

I googled about EXT4-fs errors but couldn't find the same error and generally struggled to understand what's going on.

When I try to run fsck from recovery mode I get the following error:
> /lib/recovery-mode/recovery-menu: line 80: /etc/default/rcS: No such file or directory
fsck from util-linux 2.31.1
/dev/mapper/ubuntu--vg-root is mounted.
e2fsck: Cannot continue, aborting.

The last thing I did before the problem started was to try to read data from a USB stick that wouldn't mount. I googled it and followed the instruction I found here: [https://itsfoss.com/mount-exfat](https://itsfoss.com/mount-exfat)
[COLOR=#FFFFFF][FONT=monospace]sudo add-apt-repository universe
[/FONT][/COLOR][COLOR=#FFFFFF][FONT=monospace]sudo apt update
[/FONT][/COLOR][COLOR=#FFFFFF][FONT=monospace]sudo apt install exfat-fuse exfat-utils
[/FONT][/COLOR]After that I was able to read the USB stick but the my laptop would randomly crash...
Tried to reinstall Ubuntu but the error persisted.
I checked /var/crash folder but it's empty

---

### Post by TheFu on 2020-01-28
What do the system logs show?

Seems the system was installed with LVM.  That means you should read up on LVM to understand the device names used.
fsck cannot be run on an active file system - like one that has been mounted.  
In the days before systemd, it would be trivial to get an fsck to run. **sudo touch /forcefsck**.  That doesn't work anymore. 
Since systemd, I haven't any clue except to use a live-environment, go into maintenance mode (but don't mount anything), install LVM, activate the VG, then scan for LVs, and finally run the fsck manually.

But I seriously doubt the issue is a corrupted file system. Journalled file systems like ext4 just don't get corrupted without some hardware failure.

exfat has nothing to do with vg-root.  1 problem at a time, please.

---

### Post by guanacone on 2020-01-31
Thanks for taking the tine to try to explain this to me, but this is way to technical for me... Just took my laptop to a store where they checked the SSD and reinstalled Windows 10. Seams to work so far.

---

### Post by guanacone on 2020-02-06
After having my laptop restored with Windows 10 I used it as is for a couple of days and everything was fine. They checked the hardware and couldn't finde any defects. So after a couple of days I downloaden Ubuntu 18.04 LTS and installed it but the problems persisted ant the system was crashing within a few minutes. After researching a little bit more, I read somewhere i should update BIOS. So restored again to Windows 10 and did all the available updates even the BIOS. This AM I reinstalled Ubuntu 18.04 LTA. I'm using it for a couple hours now and no more crashes! Hopefully this was it!

---


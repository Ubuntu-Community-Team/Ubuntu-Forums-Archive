---
title: "Is this normal GRUB behaviour?"
date: 2014-12-25
forum: New to Ubuntu
---

### Post by will59 on 2014-12-25
Pretty new here, so sorry if this isn't the most appropriate subforum for this.

My computer has two drives, with Ubuntu being installed onto the SSD, and the HDD not being used for anything right now. When booting into this second empty HDD through the BIOS, the GRUB menu still comes up and prompts me to start Ubuntu over on the other drive. Though harmless (Ubuntu is completely unaffected), it seems a bit strange to me. Is there a way of removing it so it simply displays a "operating system not found" error, or am I missing a big key concept of GRUB here?

---

### Post by grahammechanical on 2014-12-25
My guess is that this is nothing to do with the way Grub works but everything to do with the BIOS being smart enough to first look to the HDD for an operating system and after not finding one it then looks for an operating system on the next in line location for an operating system. Your boot priority may be HDD, then SSD, then DVD/CD/USB/Floppy. Or, SSD, then HDD, then DVD/CD/USB/Floppy.

> [COLOR=#252525][FONT=sans-serif]The user can control the boot process, to cause one medium to be booted instead of another when two or more bootable media are present, by taking advantage of the boot priority implemented by the BIOS. For example, most computers have a hard disk that is bootable, but usually there is a removable-media drive that has higher boot priority, so the user can cause a removable disk to be booted, simply by inserting it, without removing the hard disk drive or altering its contents to make it unbootable.[/FONT][/COLOR]
[COLOR=#252525][FONT=sans-serif]In most modern BIOSes, the boot priority order of all potentially bootable devices can be freely configured by the user through the BIOS configuration utility. In older BIOSes, limited boot priority options are selectable; in the earliest BIOSes, a fixed priority scheme was implemented, with floppy disk drives first, fixed disks (i.e. hard disks) second, and typically no other boot devices supported, subject to modification of these rules by installed option ROMs. The BIOS in an early PC also usually would only boot from the first floppy disk drive or the first hard disk drive, even if there were two drives of either type installed. All more advanced boot priority sequences evolved as incremental improvements on this basic system.[/FONT][/COLOR]


[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

Regards.

---


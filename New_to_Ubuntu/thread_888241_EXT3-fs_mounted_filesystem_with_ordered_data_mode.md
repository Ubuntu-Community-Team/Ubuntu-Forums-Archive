---
title: "EXT3-fs: mounted filesystem with ordered data mode"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-08-12
here's my dmesg:
```
...
[   25.792012] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.792047] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   25.792077] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   27.813517] Attempting manual resume
[   27.813522] swsusp: Resume From Partition 8:18
[   27.813525] PM: Checking swsusp image.
[   27.913104] PM: Resume from disk failed.
[   28.432615] kjournald starting.  Commit interval 5 seconds
**[   28.432635] EXT3-fs: mounted filesystem with ordered data mode.**
[   52.693207] Linux agpgart interface v0.102 (c) Dave Jones
[   52.750275] agpgart: Detected an Intel 830M Chipset.
[   52.750442] agpgart: Detected 892K stolen memory.
[   52.772236] agpgart: AGP aperture is 128M @ 0xf0000000
[   52.880292] NET: Registered protocol family 17
[   53.358808] i810_smbus 0000:00:02.0: i810/i815 i2c 
...
```
why does "[   28.432635] EXT3-fs: mounted filesystem with ordered data mode" take up so much time? thanks

---

### Post by bab1 on 2008-08-13
I googled the term >  ordered data mode +linux and found [[COLOR="Red"]this[/COLOR]]("http://gnuru.org/article/666/ordered-data-mode").

Did you crash the system?

Edit: If so then I would run ```
fsck
```

---

### Post by afeasfaerw23231233 on 2008-08-14
i didn't crash the system. but i don't know if it did :) 
i run fsck and 
```
 fsck
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb7 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

fsck.ext3: Permission denied while trying to open /dev/sdb7
You must have r/w access to the filesystem or be root
```
i check dmesg again after it booted up and find out it stucked at
```
[   27.922394] EXT3-fs: mounted filesystem with ordered data mode.
```

thanks for help!

---

### Post by InfinityCircuit on 2008-08-15
EXT3 has two main modes to handle journaling:

Ordered data mode

and

Data writeback mode

Data writeback mode is generally considered to be much faster and better than ordered data mode, although I don't know why ordered data mode would be causing a kernel pause.  To change the default:

```
sudo tune2fs -o journal_data_writeback /dev/sdX
```

---

### Post by InfinityCircuit on 2008-08-15
Also--to force a fsck on boot:

```
sudo touch /forcefsck && sudo reboot
```

never run fsck on a mounted disc--listen to the warnings.

---

### Post by afeasfaerw23231233 on 2008-08-15
i followed your steps but it's still the same
```
[   27.230771] swsusp: Resume From Partition 8:18
[   27.230773] PM: Checking swsusp image.
[   27.330235] PM: Resume from disk failed.
[   27.849762] kjournald starting.  Commit interval 5 seconds
**[   27.849781] EXT3-fs: mounted filesystem with writeback data mode.**
[   52.257104] Linux agpgart interface v0.102 (c) Dave Jones
[   52.293146] agpgart: Detected an Intel 830M Chipset.
[   52.293290] agpgart: Detected 892K stolen memory.

```

---

### Post by afeasfaerw23231233 on 2008-08-16
bump

---

### Post by afeasfaerw23231233 on 2008-08-18
bump

---

### Post by afeasfaerw23231233 on 2008-08-20
bump

---

### Post by t0p on 2008-08-20
I really don't understand what the problem is that you're asking help for.

Did you read the article bab1 linked to above?  I think you should.  It might make you feel better.

Here's a taste:

> On booting you may be getting this message:

     EXT3-fs: mounted file system with ordered data mode.

This is perfectly normal and says that the file system mounted OK.

---

### Post by Midahed on 2008-08-20
> **afeasfaerw23231233 said:**
> i followed your steps but it's still the same
```
[   27.230771] swsusp: Resume From Partition 8:18
[   27.230773] PM: Checking swsusp image.
[   27.330235] PM: Resume from disk failed.
[   27.849762] kjournald starting.  Commit interval 5 seconds
**[   27.849781] EXT3-fs: mounted filesystem with writeback data mode.**
[   52.257104] Linux agpgart interface v0.102 (c) Dave Jones
[   52.293146] agpgart: Detected an Intel 830M Chipset.
[   52.293290] agpgart: Detected 892K stolen memory.

```

Personally I wouldn't have changed the mode until I understood what was causing the original problem.  At best you may be masking something else that's causing it to run slow.

I see that a couple of lines before the filesystem mount line there's a message that says 'resume from disk failed'.  Is this because you're trying to power-up after hibernating your system?

It's possible that if it failed to resume from disk, the system will behave as if it had crashed and will do a precautionary filesystem check.  That may be why the system is slow.

If you have been suspending/hibernating, What does it do if you do a normal close and power-down followed by a power-up instead?

---

### Post by afeasfaerw23231233 on 2008-08-22
i never hibernate or suspend my system. i always do a normal close and power down. but every time i check dmesg it says "resume from disk failed". i don't know why.
```
[   26.056922] Attempting manual resume
[   26.056928] swsusp: Resume From Partition 8:18
[   26.056931] PM: Checking swsusp image.
[   26.156358] PM: Resume from disk failed.
[   26.675894] kjournald starting.  Commit interval 5 seconds
[   26.675913] EXT3-fs: mounted filesystem with writeback data mode.
[   52.572899] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   52.852557] Linux agpgart interface v0.102 (c) Dave Jones
[   52.871118] agpgart: Detected an Intel 830M Chipset.
```

---

### Post by Midahed on 2008-08-22
> **afeasfaerw23231233 said:**
> i never hibernate or suspend my system. i always do a normal close and power down. but every time i check dmesg it says "resume from disk failed".

It certainly looked as if the system thinks it's being brought out of a suspended state.  But it's not a problem.  I had a look at my dmesg log and found the same entries:-

```
[   34.926983] Attempting manual resume
[   34.926986] swsusp: Resume From Partition 9:2
[   34.926988] PM: Checking swsusp image.
[   34.927128] PM: Resume from disk failed.
[   34.970361] kjournald starting.  Commit interval 5 seconds
[   34.970371] EXT3-fs: mounted filesystem with ordered data mode.
[   35.247460] usb 5-4: new high speed USB device using ehci_hcd and address 3
```

I guess the boot process always looks for a suspend image in the swap partition and reports 'failure' even though the system had never been suspended.  Sorry - that was a wrong turn on my part.  At least I've learnt something. :)

Going back to your original problem, it doesn't seem to take any significant time to mount the filesystem...

```
[   26.675894] kjournald starting.  Commit interval 5 seconds
[   26.675913] EXT3-fs: mounted filesystem with writeback data mode.

```

... so what is it that makes you think there's a problem in the first place?

---

### Post by t0p on 2008-08-22
deleted

---

### Post by philinux on 2008-08-22
```
Aug 18 22:22:42 philcb-desktop kernel: [   24.849945] Attempting manual resume
Aug 18 22:22:42 philcb-desktop kernel: [   24.875086] kjournald starting.  Commit interval 5 seconds
Aug 18 22:22:42 philcb-desktop kernel: [   24.875096] EXT3-fs: mounted filesystem with ordered data mode.
```

He's deffo got a problem cos mine shows no time delay.

i'd suggest you install bootchart and see whats going on.

---

### Post by Midahed on 2008-08-22
> **philinux said:**
> He's deffo got a problem cos mine shows no time delay...

Neither does his, does it?  Or, at least, if there is a delay it appears to be AFTER the filesystem has been mounted.

As I see it there's a pause of roughly 26 seconds before the next entry in the log file.

```
[   26.675894] kjournald starting.  Commit interval 5 seconds
[   [COLOR="Red"]26.675913[/COLOR]] EXT3-fs: mounted filesystem with writeback data mode.
[   [COLOR="Red"]52.572899[/COLOR]] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
```

Or have I misunderstood something?

---

### Post by philinux on 2008-08-22
> As I see it there's a pause of roughly 26 seconds before the next entry in the log file.

Yep a long pause, must be annoying. Thats why I suggested bootchart. Sorry I meant to include more lines from the log, the copy and paste went awry.

```
Aug 18 22:22:42 philcb-desktop kernel: [   34.275609] EXT3 FS on sda3, internal journal
Aug 18 22:22:42 philcb-desktop kernel: [   34.275613] EXT3-fs: mounted filesystem with ordered data mode.
Aug 18 22:22:42 philcb-desktop kernel: [   34.709416] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 18 22:22:42 philcb-desktop kernel: [   35.100335] No dock devices found.
Aug 18 22:22:42 philcb-desktop kernel: [   35.343816] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (2 cpu cores) (version 2.20.00)
Aug 18 22:22:42 philcb-desktop kernel: [   35.343592] powernow-k8:    0 : fid 0x13 (2700 MHz), vid 0x8
Aug 18 22:22:42 philcb-desktop kernel: [   35.343596] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0x9
Aug 18 22:22:42 philcb-desktop kernel: [   35.343598] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xb
Aug 18 22:22:42 philcb-desktop kernel: [   35.343599] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xd
Aug 18 22:22:42 philcb-desktop kernel: [   35.343601] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0xf
```

---

### Post by oooh on 2011-07-02
Hi there, though from ages ago, but I get:

 [    4.716397] EXT3-fs (sda5): mounted filesystem with ordered data mode
 [   27.276245] EXT3-fs (sda5): using internal journal

Big delay there
I am trying shutdown -F
I do not hibernate
bootchar shows a looong time in ureadahead and blkid

---


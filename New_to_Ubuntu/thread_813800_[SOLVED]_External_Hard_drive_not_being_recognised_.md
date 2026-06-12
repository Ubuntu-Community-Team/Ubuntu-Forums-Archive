---
title: "[SOLVED] External Hard drive not being recognised at all"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by spamzilla on 2008-05-31
I just bought a Seagate Barracuda 7200.10 500GB HD, plugged it into my new external hard drive case and turned it on. It doesn't get recognised in XP or Ubuntu (8.04). No worries I thought, I just went to Disk Management and crap, it's not there either - same goes for Gparted. It's not recognised in BIOS, the cables are all plugged in correctly, and I have tried changing the jumper settings and no luck. I didn't even get the "new hardware found" box popup when I boot into XP. The external case power light is on, and the HD disk is running, so I presume both are working OK.

So how can I see if Ubuntu can see my drive?

Cheers

---

### Post by powerpleb on 2008-05-31
> **spamzilla said:**
> 
So how can I see if Ubuntu can see my drive?

Try```
 sudo blkid
```

But if Gparted can't see it and the BIOS can't see it I don't like your chances.

---

### Post by Mjölner on 2008-05-31
I also have an external drive which does not seem to show up.

For me I do:

> Sudo fdisk -l (the last character is a lower case L)

and you should see it as

sd??

not hd??

If you find it post the output and I can try and help you from there

---

### Post by Aearenda on 2008-05-31
It could be:
1. Bad cable - try changing the cable
2. Bad enclosure - try a different enclosure, or try the drive inside a desktop computer
3. Bad drive - try a different drive that you know works in the same enclosure
4. Bad jumpers (but I think you tried that).

The last lines of output from 'dmesg' immediately after plugging the drive in to the USB socket might be revealing. On XP, look in the Event Viewer for any errors.

---

### Post by spamzilla on 2008-05-31
> **powerpleb said:**
> Try```
 sudo blkid
```

But if Gparted can't see it and the BIOS can't see it I don't like your chances.

Here's the output:

```
/dev/sda1: UUID="c90fb310-02ea-4bb7-ab2a-d3f56160af2f" TYPE="ext3" 
/dev/sda2: UUID="cf287ec2-e4c4-445a-9d2e-898b381f63db" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda3: TYPE="swap" UUID="b274e590-eeda-4b30-9504-a0f0e9048338" 
/dev/sda4: UUID="AC348F50348F1C88" TYPE="ntfs"
```

[quote=Mjölner]I also have an external drive which does not seem to show up.

For me I do:

Sudo fdisk -l [/quote]

Here's the output:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00002c56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2437    19575171   83  Linux
/dev/sda2            2438       13320    87417697+  83  Linux
/dev/sda3           13321       13575     2048287+  82  Linux swap / Solaris
/dev/sda4   *       13576       19457    47247165    7  HPFS/NTFS
matt@matt:~$ 

```

It doesn't look like my 500gb HD is there, but I can confirm it does work. I just put it in my dad's PC and it was recognised instantly.

I'll check out dmesg and the event log asap.

Cheers guys

---

### Post by Mjölner on 2008-05-31
I'm thinking that you should look into what Aearenda posted earlier about the hardware.

---

### Post by spamzilla on 2008-05-31
> **Mjölner said:**
> I'm thinking that you should look into what Aearenda posted earlier about the hardware.

Yeah I think it must be a bad enclosure. There are no error messages in dmesg and SP3 just hosed my XP install so I can't get to the event log :lolflag:

---

### Post by Aearenda on 2008-05-31
> It doesn't look like my 500gb HD is there, but I can confirm it does work. I just put it in my dad's PC and it was recognised instantly.
Is your Dad's PC using a USB2 socket and yours just USB1?

---

### Post by spamzilla on 2008-05-31
> **Aearenda said:**
> Is your Dad's PC using a USB2 socket and yours just USB1?

When I got the HD working, I didn't use the HD enclosure with my dads PC - I plugged it directly into the mobo. The enclosure doesn't work on 3 different PC's (all USB2) so yeah it's probably broken. Back to the shop I go :/

---


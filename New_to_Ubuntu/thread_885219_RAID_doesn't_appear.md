---
title: "RAID doesn't appear"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by NevNiv on 2008-08-09
Hey folks,

I tried to do a search for nvidia raids but I couldn't find anything.  Sorry if I missed it.

I've installed Ubuntu 8.04 before with no problems, and loved it.  I recently switched to a RAID 5, which is supported by my Nvidia M2N-E SLI motherboard.

Now when I pop in the installer CD, the three SATA drives show up.  It doesn't seem to realize I have a RAID.  Is there a way around this?  I do NOT want to remove the RAID.  This is also a dual-boot machine, with Windows XP Pro on it.

I was hoping I could get them to both co-exist peacefully on the RAID 5.

I believe the RAID software in the BIOS is called MediaShield.

If anyone could point me in the right direction, or tell me it's impossible :sad: I'd appreciate it.

Thanks all :D

Edit: Corrected motherboard model from M5N-E SLI to M2N-E SLI

---

### Post by SZ07 on 2008-08-09
I don't think that it is impossible but I think the setup has to be done when you are partitioning disks/installing ubuntu.

I actually haven't worked with RAID but you may be able to find some useful info here: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by NevNiv on 2008-08-09
That's for setting up a software RAID, but thanks for trying :-/

---

### Post by psusi on 2008-08-15
Unfortunately fake raid support is rather limited currently ( see [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) ), and it's raid5 support is highly experimental, requiring you to build a custom kernel.  It is possible, but requires a good deal of hacking.

---

### Post by NevNiv on 2008-08-16
Oh, so this onboard RAID is considered a fake RAID?  I never realized that.  So my CPU does the processing?  That sucks, but I haven't even noticed because my machine is pretty fast.

Anyway, thanks a lot for the answer :)

I guess I'll do without Ubuntu for a while.  If I miss it enough, I'll set up a VM for it.

---


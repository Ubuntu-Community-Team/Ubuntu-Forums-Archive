---
title: "SD Card Won't Format"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-07-27
My Android tablet stopped recognizing my MicroSD Card, so I put it in my computer to see if the computer could recognize it. It didn't. It shows up in Disk Utility as "Unknown". When I try to format the drive, I get this message:

```
Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error

```

I REALLY don't want to have to get a new SD Card, and I don't want to format it if I don't have to.

Thanks!

DG

---

### Post by levlaz on 2012-07-29
> **doppel.ganger said:**
> My Android tablet stopped recognizing my MicroSD Card, so I put it in my computer to see if the computer could recognize it. It didn't. It shows up in Disk Utility as "Unknown". When I try to format the drive, I get this message:

```
Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error

```I REALLY don't want to have to get a new SD Card, and I don't want to format it if I don't have to.

Thanks!

DG

Did you try using [Gparted]("http://gparted.sourceforge.net/")? At least you should be able to format it then.

---


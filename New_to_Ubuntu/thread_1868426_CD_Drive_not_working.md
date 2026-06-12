---
title: "CD Drive not working"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by Mackay508 on 2011-10-24
After I upgraded to 11.10 my CD drive stopped working. Ive tried to re-install Ubuntu completely via CD but it doesn't boot at all and I cant install via USB. Anyway to get my CD drive to work again? Using lshw in Terminal I get  *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-850S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.61
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready

But it still does not play CD's or anything. Also when i try to mount it comes up with mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab for all the logical names.

---


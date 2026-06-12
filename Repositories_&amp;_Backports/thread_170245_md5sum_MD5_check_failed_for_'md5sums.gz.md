---
title: "md5sum: MD5 check failed for 'md5sums.gz"
date: 2006-05-04
forum: Repositories &amp; Backports
---

### Post by mrtv on 2006-05-04
Hi,
we have a local mirror (rsync) of ftp.ubuntu.com and someone who tried to use it as install archive noticed that some checksum was wrong. After he told me that I did some investigating, rsynced a couple of time manually and tried to verify the contents myself.

I found that file 'indices/md5sums.gz' and issued the following command:
admin@ftp [/var/ftp/pub/mirrors/ubuntu] zcat indices/md5sums.gz | grep -v -e hppa -e ia64 -e sparc -e powerpc -e warty -e s390 | md5sum -c
md5sum: MD5 check failed for 'indices/md5sums.gz'

I tried to delete that file and rsync it down again a few times, but it's always the same result. Is this the wrong way to verify the archive? Has anyone else encountered this? Any other hints or tips?

TIA and regards,
Timo

---


---
title: "DUMP: You can't update the dumpdates file when dumping a subdirectory"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by setevoy on 2013-03-02
Hi to all.

I try make *dump* on my system but got error:

```
# dump -0auL -f /media/Main/Backups/ubuntu_fs_root.dump /dev/sda7
  DUMP: You can't update the dumpdates file when dumping a subdirectory
  DUMP: The ENTIRE dump is aborted.
```

Google says that mean that I try save dump file on filesystem that I backuping - but it is not so:

```
# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        45G   27G   16G  63% /
udev            2.0G   12K  2.0G   1% /dev
tmpfs           791M  956K  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  480K  2.0G   1% /run/shm
/dev/sda5       320G  303G   17G  95% /media/Main
```

But - partion */media/Main* are **NTFS** FS - can it be cause of problem?

Thanks.

---


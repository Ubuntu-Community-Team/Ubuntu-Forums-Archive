---
title: "external hard drive can not be detected by my pc"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by math303 on 2012-12-26
hello , I have a external hard drive I use to have with my window but when I plug my hard drive in my computer Ubuntu won t open it and  I can not find it anywhere, can someone help , thank you

---

### Post by Yougo on 2012-12-26
do you still have a windows computer around?
if yes:
-plug the drive in there
  -does it work ok there?
-sign off the drive with "safely remove device" from the system tray (near the clock)
-when windows says it's safe to remove, unplug the drive.
-now plug into ubuntu pc
  -does it work now?

---

### Post by NikTh on 2012-12-26
Hi ,
also you can do as follows , to provide more info .. 

Plug the driver to Ubuntu system and then open a terminal (CTRL+ALT+T) and apply the command below
```
dmesg | tail -n 20
```Post the results back here. 

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by math303 on 2013-01-03
> **NikTh said:**
> Hi ,
also you can do as follows , to provide more info .. 

Plug the driver to Ubuntu system and then open a terminal (CTRL+ALT+T) and apply the command below
```
dmesg | tail -n 20
```Post the results back here. 

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks
mathieu@mathieu-Dimension-5100:~$ dmesg | tail -n 20
[ 1030.129053] scsi 4:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[ 1030.130137] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1030.133425] sd 4:0:0:0: [sdb] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[ 1030.134294] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1030.135164] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1030.135171] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1030.137291] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1030.138168] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1030.138176] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1030.143381]  sdb: sdb1
[ 1030.143390] sdb: p1 size 1953523120 extends beyond EOD, enabling native capacity
[ 1030.144901] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1030.145772] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1030.145777] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1030.146359]  sdb: sdb1
[ 1030.146369] sdb: p1 size 1953523120 extends beyond EOD, truncated
[ 1030.148411] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1030.149543] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1030.149549] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1030.149554] sd 4:0:0:0: [sdb] Attached SCSI disk

---

### Post by math303 on 2013-01-03
> **math303 said:**
> mathieu@mathieu-Dimension-5100:~$ dmesg | tail -n 20
[ 1030.129053] scsi 4:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[ 1030.130137] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1030.133425] sd 4:0:0:0: [sdb] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[ 1030.134294] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1030.135164] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1030.135171] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1030.137291] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1030.138168] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1030.138176] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1030.143381]  sdb: sdb1
[ 1030.143390] sdb: p1 size 1953523120 extends beyond EOD, enabling native capacity
[ 1030.144901] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1030.145772] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1030.145777] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1030.146359]  sdb: sdb1
[ 1030.146369] sdb: p1 size 1953523120 extends beyond EOD, truncated
[ 1030.148411] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1030.149543] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 1030.149549] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1030.149554] sd 4:0:0:0: [sdb] Attached SCSI disk
  sorry I was a way just came back , like you ask me I have posted the information you ask , I hope this can help , thank for you reply .

---


---
title: "ISO mount via fstab hangs boot process."
date: 2013-12-08
forum: New to Ubuntu
---

### Post by ylafont on 2013-12-08
I mounting some iso’s via fstab, with the following commands.

# ISO mount in fstab - used for PXE Booting.
/Apps/WinXP(SP3).iso /srv/pxeboot/images/winxp/ udf,iso9660 user,auto,loop              0              0
/Apps/Windows7.iso /srv/pxeboot/images/win7/ udf,iso9660 user,auto,loop    0              0
/ Apps /win7thin.iso /srv/pxeboot/images/win7thin/ udf,iso9660 user,auto,loop             0              0
/ Apps /Windows.8.1.iso /srv/pxeboot/images/win8.1/ udf,iso9660 user,auto,loop         0              0
/ Apps /Ubuntu13.10.iso /srv/pxeboot/images/ubuntu/ udf,iso9660 user,auto,loop       0              0
/ Apps /knoppix7.2.iso /srv/pxeboot/images/knoppix/ udf,iso9660 user,auto,loop 0       0
 
This works as expected and the each of the iso are mounted properly.
I have two problems which are related.
1) if I perform a **sudo fuser -m /dev/loop1 **on each of the mounts,  the systems tells me that each of the following process has the device open. by the way ,the same process are listed for all mounts. I also can’t un-mount the device unless I use the –L  option.
 
/dev/loop5:              1   243m   322   392   396   878   892  1028  1222  1225  1232  1236  1238  1239  1240  1243  1245  1256m  1287  1289  1330  1331  1332  1334  1360  1363  1398  1399  1418  1420  1425  1430  1435  1445  1456  1461  1462  1465  1472  1488  1491  1492  1493  1494  1499  1512  1519  1542  1603  1728  1732  1816m  2055  2161  2456  2507  2516  2679  2898  3052  3054  3373  3544  3571  3572  3896  4005  4117  4172  4173  4174  4175  4176  4478  4494  5027  5065  5245  7032  7156  7273  7274  8013  9556  9771
 
2)      The above would not be issues, however when I try to boot some (especially Ubuntu) of the iso's. the boot process hangs.
 
If I mount each of the iso manually, everything works fine.
 
Any ideas?

---


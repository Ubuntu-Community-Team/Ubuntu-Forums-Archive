---
title: "Seagate NAS raid 10 volume failed"
date: 2018-03-07
forum: New to Ubuntu
---

### Post by koola on 2018-03-07
Hello Guys
First I want to say hello for everyone.
I'm looking to help with my Seagate NAS 4-bay. Seagate manager show volume failed. I scaned via SMART whole disk, on disk 1 i had error, I changed it but cant rebuild it. I swaping disks and nothing. In the end I download linux and connect hdds to computer... 
```
~$ sudo fdisk -l
Disk /dev/loop0: 1.5 GiB, 1564921856 bytes, 3056488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 467B96C2-2E28-4AB6-B93F-860999F189C5

Device       Start     End Sectors   Size Type
/dev/sda1       41    1953    1913 956.5K Microsoft basic data
/dev/sda2     2048 1953791 1951744   953M Microsoft basic data
/dev/sda3  1953792 3905535 1951744   953M Microsoft basic data
/dev/sda4  3905536 3926015   20480    10M Microsoft basic data
/dev/sda5  3926016 5879807 1953792   954M Microsoft basic data
/dev/sda6  5879808 5900287   20480    10M Microsoft basic data
/dev/sda7  5900288 5922815   22528    11M Microsoft basic data
/dev/sda8  5922816 6504447  581632   284M Microsoft basic data
/dev/sda9  6504448 8503295 1998848   976M Microsoft basic data

Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: AE22FF77-8D11-455D-9E23-FEFB51AD05FD

Device       Start        End    Sectors   Size Type
/dev/sdb1       41       1953       1913 956.5K Microsoft basic data
/dev/sdb2     2048    1953791    1951744   953M Microsoft basic data
/dev/sdb3  1953792    3905535    1951744   953M Microsoft basic data
/dev/sdb4  3905536    3926015      20480    10M Microsoft basic data
/dev/sdb5  3926016    5879807    1953792   954M Microsoft basic data
/dev/sdb6  5879808    5900287      20480    10M Microsoft basic data
/dev/sdb7  5900288    5922815      22528    11M Microsoft basic data
/dev/sdb8  5922816    6504447     581632   284M Microsoft basic data
/dev/sdb9  6504448    8503295    1998848   976M Microsoft basic data
/dev/sdb10 8503296 3907027254 3898523959   1.8T Microsoft basic data

Partition 1 does not start on physical sector boundary.


Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A61DDACD-E35A-4B14-9CB3-196DB6EDA563

Device       Start        End    Sectors   Size Type
/dev/sdc1       41       1953       1913 956.5K Microsoft basic data
/dev/sdc2     2048    1953791    1951744   953M Microsoft basic data
/dev/sdc3  1953792    3905535    1951744   953M Microsoft basic data
/dev/sdc4  3905536    3926015      20480    10M Microsoft basic data
/dev/sdc5  3926016    5879807    1953792   954M Microsoft basic data
/dev/sdc6  5879808    5900287      20480    10M Microsoft basic data
/dev/sdc7  5900288    5922815      22528    11M Microsoft basic data
/dev/sdc8  5922816    6504447     581632   284M Microsoft basic data
/dev/sdc9  6504448    8503295    1998848   976M Microsoft basic data
/dev/sdc10 8503296 3907027254 3898523959   1.8T Microsoft basic data

Partition 1 does not start on physical sector boundary.


Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 72729E16-D958-43EB-9D0F-A38C8C4E4923

Device       Start        End    Sectors   Size Type
/dev/sdd1       41       1953       1913 956.5K Microsoft basic data
/dev/sdd2     2048    1953791    1951744   953M Microsoft basic data
/dev/sdd3  1953792    3905535    1951744   953M Microsoft basic data
/dev/sdd4  3905536    3926015      20480    10M Microsoft basic data
/dev/sdd5  3926016    5879807    1953792   954M Microsoft basic data
/dev/sdd6  5879808    5900287      20480    10M Microsoft basic data
/dev/sdd7  5900288    5922815      22528    11M Microsoft basic data
/dev/sdd8  5922816    6504447     581632   284M Microsoft basic data
/dev/sdd9  6504448    8503295    1998848   976M Microsoft basic data
/dev/sdd10 8503296 3907027254 3898523959   1.8T Microsoft basic data

Partition 1 does not start on physical sector boundary.

```

```
~$ sudo mdadm --examine /dev/sd*
/dev/sda:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sda1.
/dev/sda2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0426c396:7ee6ca4c:bc083245:f08513c4
           Name : (none):0
  Creation Time : Thu Jul 18 11:31:51 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1951720 (953.15 MiB 999.28 MB)
     Array Size : 975860 (953.15 MiB 999.28 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d9bb886e:1157f0e3:aacb0f41:99ba784c

    Update Time : Fri Mar  2 15:49:04 2018
       Checksum : c16cf366 - correct
         Events : 621


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8250e0d5:1424b423:4a9a00fb:55f28f3c
           Name : (none):1
  Creation Time : Thu Jul 18 11:31:52 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1951720 (953.15 MiB 999.28 MB)
     Array Size : 975860 (953.15 MiB 999.28 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fe402944:e9c495d9:3f53afd9:5efcc5e5

    Update Time : Sun Mar  4 17:08:31 2018
       Checksum : 3f1cfdf - correct
         Events : 1764


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sda4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c39dcc3c:06f9da43:cb0c2cf8:180adfcc
           Name : (none):2
  Creation Time : Thu Jul 18 11:31:54 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 20456 (9.99 MiB 10.47 MB)
     Array Size : 10228 (9.99 MiB 10.47 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a683836d:4160b63d:be985e7b:99fb5dd3

    Update Time : Sun Mar  4 17:08:30 2018
       Checksum : 3606ac5c - correct
         Events : 1072


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sda5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 00dc5b1a:43ccb750:72741a99:ab0f9f17
           Name : (none):3
  Creation Time : Thu Jul 18 11:31:55 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1953768 (954.15 MiB 1000.33 MB)
     Array Size : 976884 (954.15 MiB 1000.33 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d50f0d68:4b6f7082:dfd48289:46aed96c

    Update Time : Fri Mar  2 15:48:43 2018
       Checksum : f43efc53 - correct
         Events : 290


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sda6:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : fffc62aa:473ab087:75d549eb:acf7c992
           Name : (none):4
  Creation Time : Thu Jul 18 11:31:55 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 20456 (9.99 MiB 10.47 MB)
     Array Size : 10228 (9.99 MiB 10.47 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 70d34cee:5d9ecc8d:22cf2436:82f7ad3b

    Update Time : Fri Mar  2 15:48:45 2018
       Checksum : 96700a93 - correct
         Events : 299


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sda7:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4339c023:2473051a:9fdbb8d2:fe7d14cc
           Name : (none):5
  Creation Time : Thu Jul 18 11:31:56 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 22504 (10.99 MiB 11.52 MB)
     Array Size : 11252 (10.99 MiB 11.52 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fe56d68f:77fb37fd:5980b7df:19b57412

    Update Time : Fri Mar  2 15:48:39 2018
       Checksum : 552a6b80 - correct
         Events : 266


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sda8:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4eb245a5:8ecd2931:2639d38f:fd8a907b
           Name : (none):6
  Creation Time : Thu Jul 18 11:31:57 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 581608 (284.04 MiB 297.78 MB)
     Array Size : 290804 (284.04 MiB 297.78 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 46484728:cd8dcdd6:27eee389:7ae83516

    Update Time : Fri Mar  2 15:48:40 2018
       Checksum : 7b6fde37 - correct
         Events : 248


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sda9:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e5b786c5:19992851:9dc97bb0:ac9bb890
           Name : (none):7
  Creation Time : Thu Jul 18 11:31:59 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1998824 (976.15 MiB 1023.40 MB)
     Array Size : 999412 (976.15 MiB 1023.40 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b17fe3e7:a79907d5:0d4fc428:5a299654

    Update Time : Sun Mar  4 17:08:30 2018
       Checksum : 8dc52bbc - correct
         Events : 369


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdb1.
/dev/sdb10:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 23b955e9:532d7a6b:f5f627c4:63c2bd6d
           Name : BA-377B82:8
  Creation Time : Tue Feb 23 11:25:54 2016
     Raid Level : raid10
   Raid Devices : 4

 Avail Dev Size : 3898521911 (1858.96 GiB 1996.04 GB)
     Array Size : 3898521600 (3717.92 GiB 3992.09 GB)
  Used Dev Size : 3898521600 (1858.96 GiB 1996.04 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=311 sectors
          State : clean
    Device UUID : dfeb020f:688d8bf3:921479c5:b5816aa8

    Update Time : Fri Feb 23 11:17:01 2018
       Checksum : 8e196afc - correct
         Events : 49

         Layout : near=2
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .AAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0426c396:7ee6ca4c:bc083245:f08513c4
           Name : (none):0
  Creation Time : Thu Jul 18 11:31:51 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1951720 (953.15 MiB 999.28 MB)
     Array Size : 975860 (953.15 MiB 999.28 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 01d6f609:c4189555:19f33a2d:cb781bf9

    Update Time : Wed Mar  7 12:24:45 2018
       Checksum : 67501ca6 - correct
         Events : 663


   Device Role : Active device 1
   Array State : .A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8250e0d5:1424b423:4a9a00fb:55f28f3c
           Name : (none):1
  Creation Time : Thu Jul 18 11:31:52 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1951720 (953.15 MiB 999.28 MB)
     Array Size : 975860 (953.15 MiB 999.28 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 007e6280:b7bd3b74:45dc6af8:523b21d5

    Update Time : Wed Mar  7 11:54:32 2018
       Checksum : e8e978ce - correct
         Events : 1830


   Device Role : Active device 1
   Array State : .A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c39dcc3c:06f9da43:cb0c2cf8:180adfcc
           Name : (none):2
  Creation Time : Thu Jul 18 11:31:54 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 20456 (9.99 MiB 10.47 MB)
     Array Size : 10228 (9.99 MiB 10.47 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : bd8d78eb:e72d524f:771e8a3f:027862e6

    Update Time : Wed Mar  7 11:29:01 2018
       Checksum : 9cc92b35 - correct
         Events : 1088


   Device Role : Active device 1
   Array State : .A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 00dc5b1a:43ccb750:72741a99:ab0f9f17
           Name : (none):3
  Creation Time : Thu Jul 18 11:31:55 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1953768 (954.15 MiB 1000.33 MB)
     Array Size : 976884 (954.15 MiB 1000.33 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d5abdd6d:e5c4758b:68a18afb:3a3788fe

    Update Time : Fri Mar  2 15:48:43 2018
       Checksum : 6cb4368 - correct
         Events : 290


   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb6:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : fffc62aa:473ab087:75d549eb:acf7c992
           Name : (none):4
  Creation Time : Thu Jul 18 11:31:55 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 20456 (9.99 MiB 10.47 MB)
     Array Size : 10228 (9.99 MiB 10.47 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 38bfe645:3044d731:1ccd842c:14374426

    Update Time : Wed Mar  7 11:29:01 2018
       Checksum : 730d346c - correct
         Events : 321


   Device Role : Active device 1
   Array State : .A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb7:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4339c023:2473051a:9fdbb8d2:fe7d14cc
           Name : (none):5
  Creation Time : Thu Jul 18 11:31:56 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 22504 (10.99 MiB 11.52 MB)
     Array Size : 11252 (10.99 MiB 11.52 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1f82b9de:d0c9bbdf:ccfcd62b:2fb73457

    Update Time : Wed Mar  7 11:55:15 2018
       Checksum : 17734464 - correct
         Events : 290


   Device Role : Active device 1
   Array State : .A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb8:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4eb245a5:8ecd2931:2639d38f:fd8a907b
           Name : (none):6
  Creation Time : Thu Jul 18 11:31:57 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 581608 (284.04 MiB 297.78 MB)
     Array Size : 290804 (284.04 MiB 297.78 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d2bbca84:496b1f5d:1f656348:0658bd08

    Update Time : Wed Mar  7 11:29:01 2018
       Checksum : f4e706d - correct
         Events : 256


   Device Role : Active device 1
   Array State : .A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb9:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e5b786c5:19992851:9dc97bb0:ac9bb890
           Name : (none):7
  Creation Time : Thu Jul 18 11:31:59 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1998824 (976.15 MiB 1023.40 MB)
     Array Size : 999412 (976.15 MiB 1023.40 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fe4e898d:3b20611c:a6c909a1:2bea36c2

    Update Time : Wed Mar  7 11:54:21 2018
       Checksum : 60aa67f3 - correct
         Events : 385


   Device Role : Active device 1
   Array State : .A.. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdc1.
/dev/sdc10:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 23b955e9:532d7a6b:f5f627c4:63c2bd6d
           Name : BA-377B82:8
  Creation Time : Tue Feb 23 11:25:54 2016
     Raid Level : raid10
   Raid Devices : 4

 Avail Dev Size : 3898521911 (1858.96 GiB 1996.04 GB)
     Array Size : 3898521600 (3717.92 GiB 3992.09 GB)
  Used Dev Size : 3898521600 (1858.96 GiB 1996.04 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=311 sectors
          State : clean
    Device UUID : 773d740d:caecd425:244a758e:b46ed573

    Update Time : Fri Feb 23 11:17:26 2018
       Checksum : 53383ea9 - correct
         Events : 57

         Layout : near=2
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : ..AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0426c396:7ee6ca4c:bc083245:f08513c4
           Name : (none):0
  Creation Time : Thu Jul 18 11:31:51 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1951720 (953.15 MiB 999.28 MB)
     Array Size : 975860 (953.15 MiB 999.28 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f87da730:40692872:300274c4:d2996811

    Update Time : Fri Mar  2 15:49:04 2018
       Checksum : 5a17dd70 - correct
         Events : 621


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8250e0d5:1424b423:4a9a00fb:55f28f3c
           Name : (none):1
  Creation Time : Thu Jul 18 11:31:52 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1951720 (953.15 MiB 999.28 MB)
     Array Size : 975860 (953.15 MiB 999.28 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ad7c21e5:ec791630:4c7d0f99:1eb114f0

    Update Time : Sun Mar  4 17:08:31 2018
       Checksum : c5199f5b - correct
         Events : 1764


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c39dcc3c:06f9da43:cb0c2cf8:180adfcc
           Name : (none):2
  Creation Time : Thu Jul 18 11:31:54 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 20456 (9.99 MiB 10.47 MB)
     Array Size : 10228 (9.99 MiB 10.47 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 97d0d96a:94236c8f:d23ffc59:44c59a5b

    Update Time : Sun Mar  4 17:08:30 2018
       Checksum : ebed2d5c - correct
         Events : 1072


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 00dc5b1a:43ccb750:72741a99:ab0f9f17
           Name : (none):3
  Creation Time : Thu Jul 18 11:31:55 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1953768 (954.15 MiB 1000.33 MB)
     Array Size : 976884 (954.15 MiB 1000.33 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 897d61ee:c6ac9fbd:1d3d23a6:de1b3bb3

    Update Time : Fri Mar  2 15:48:43 2018
       Checksum : 18c47d57 - correct
         Events : 290


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc6:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : fffc62aa:473ab087:75d549eb:acf7c992
           Name : (none):4
  Creation Time : Thu Jul 18 11:31:55 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 20456 (9.99 MiB 10.47 MB)
     Array Size : 10228 (9.99 MiB 10.47 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 2bedc215:1582cdb5:4cbc2871:8ef2c68b

    Update Time : Fri Mar  2 15:48:45 2018
       Checksum : 7103f039 - correct
         Events : 299


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc7:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4339c023:2473051a:9fdbb8d2:fe7d14cc
           Name : (none):5
  Creation Time : Thu Jul 18 11:31:56 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 22504 (10.99 MiB 11.52 MB)
     Array Size : 11252 (10.99 MiB 11.52 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 4ebbedae:b3b32d44:1e934077:73e07c70

    Update Time : Fri Mar  2 15:48:39 2018
       Checksum : b0c8c627 - correct
         Events : 266


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc8:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4eb245a5:8ecd2931:2639d38f:fd8a907b
           Name : (none):6
  Creation Time : Thu Jul 18 11:31:57 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 581608 (284.04 MiB 297.78 MB)
     Array Size : 290804 (284.04 MiB 297.78 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0cb0f140:fd1f8f85:3a203f56:1006c7c1

    Update Time : Fri Mar  2 15:48:40 2018
       Checksum : bac827d3 - correct
         Events : 248


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc9:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e5b786c5:19992851:9dc97bb0:ac9bb890
           Name : (none):7
  Creation Time : Thu Jul 18 11:31:59 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1998824 (976.15 MiB 1023.40 MB)
     Array Size : 999412 (976.15 MiB 1023.40 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 3810934e:93eae28c:016945bf:5254a0e8

    Update Time : Sun Mar  4 17:08:30 2018
       Checksum : d6db5218 - correct
         Events : 369


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdd1.
/dev/sdd10:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 23b955e9:532d7a6b:f5f627c4:63c2bd6d
           Name : BA-377B82:8
  Creation Time : Tue Feb 23 11:25:54 2016
     Raid Level : raid10
   Raid Devices : 4

 Avail Dev Size : 3898521911 (1858.96 GiB 1996.04 GB)
     Array Size : 3898521600 (3717.92 GiB 3992.09 GB)
  Used Dev Size : 3898521600 (1858.96 GiB 1996.04 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=311 sectors
          State : clean
    Device UUID : 86cf95d6:1851fa3a:98e6fc1c:fa8a301e

    Update Time : Fri Feb 23 11:17:26 2018
       Checksum : 6a61edc1 - correct
         Events : 57

         Layout : near=2
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : ..AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0426c396:7ee6ca4c:bc083245:f08513c4
           Name : (none):0
  Creation Time : Thu Jul 18 11:31:51 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1951720 (953.15 MiB 999.28 MB)
     Array Size : 975860 (953.15 MiB 999.28 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 2ed30d96:1461b338:d42951bb:050bf9e1

    Update Time : Fri Mar  2 15:49:04 2018
       Checksum : 4d76c353 - correct
         Events : 621


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8250e0d5:1424b423:4a9a00fb:55f28f3c
           Name : (none):1
  Creation Time : Thu Jul 18 11:31:52 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1951720 (953.15 MiB 999.28 MB)
     Array Size : 975860 (953.15 MiB 999.28 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 88285e3c:63ff7687:13204e44:f485dbf7

    Update Time : Sun Mar  4 17:08:31 2018
       Checksum : 26bc484b - correct
         Events : 1764


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : c39dcc3c:06f9da43:cb0c2cf8:180adfcc
           Name : (none):2
  Creation Time : Thu Jul 18 11:31:54 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 20456 (9.99 MiB 10.47 MB)
     Array Size : 10228 (9.99 MiB 10.47 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5ea2c99f:02d71cfb:f2511192:81853a06

    Update Time : Sun Mar  4 17:08:30 2018
       Checksum : 6f4284f0 - correct
         Events : 1072


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 00dc5b1a:43ccb750:72741a99:ab0f9f17
           Name : (none):3
  Creation Time : Thu Jul 18 11:31:55 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1953768 (954.15 MiB 1000.33 MB)
     Array Size : 976884 (954.15 MiB 1000.33 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 76042399:c1655509:65d38ae7:2cfe97e6

    Update Time : Fri Mar  2 15:48:43 2018
       Checksum : 840035d5 - correct
         Events : 290


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd6:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : fffc62aa:473ab087:75d549eb:acf7c992
           Name : (none):4
  Creation Time : Thu Jul 18 11:31:55 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 20456 (9.99 MiB 10.47 MB)
     Array Size : 10228 (9.99 MiB 10.47 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b6a09b00:2998edd3:46abb8e9:ef04ffc1

    Update Time : Fri Mar  2 15:48:45 2018
       Checksum : 28c4bb35 - correct
         Events : 299


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd7:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4339c023:2473051a:9fdbb8d2:fe7d14cc
           Name : (none):5
  Creation Time : Thu Jul 18 11:31:56 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 22504 (10.99 MiB 11.52 MB)
     Array Size : 11252 (10.99 MiB 11.52 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 71a2b8a5:beebcecf:4dcdafb7:a0890a72

    Update Time : Fri Mar  2 15:48:39 2018
       Checksum : 7531c8b3 - correct
         Events : 266


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd8:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4eb245a5:8ecd2931:2639d38f:fd8a907b
           Name : (none):6
  Creation Time : Thu Jul 18 11:31:57 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 581608 (284.04 MiB 297.78 MB)
     Array Size : 290804 (284.04 MiB 297.78 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0f76711a:3d34fb45:c2c500f2:059a9231

    Update Time : Fri Mar  2 15:48:40 2018
       Checksum : 60413b94 - correct
         Events : 248


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd9:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : e5b786c5:19992851:9dc97bb0:ac9bb890
           Name : (none):7
  Creation Time : Thu Jul 18 11:31:59 2013
     Raid Level : raid1
   Raid Devices : 4

 Avail Dev Size : 1998824 (976.15 MiB 1023.40 MB)
     Array Size : 999412 (976.15 MiB 1023.40 MB)
    Data Offset : 24 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5f23608b:e12f750d:1a1a960d:e180c154

    Update Time : Sun Mar  4 17:08:30 2018
       Checksum : 4eac8835 - correct
         Events : 369


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde:
   MBR Magic : aa55
Partition[0] :   1141509631 sectors at    778135908 (type 72)
Partition[1] :   1936028240 sectors at    168689522 (type 65)
Partition[2] :   1936028192 sectors at   1869881465 (type 79)
Partition[3] :        55499 sectors at   2885681152 (type 0d)
mdadm: cannot open /dev/sdf: No medium found
mdadm: cannot open /dev/sdg: No medium found
mdadm: cannot open /dev/sdh: No medium found
mdadm: cannot open /dev/sdi: No medium found


```

```
 ~$ sudo mdadm --assemble --scan
mdadm: /dev/md/0 has been started with 1 drive (out of 4).
mdadm: /dev/md/1 has been started with 1 drive (out of 4).
mdadm: /dev/md/2 has been started with 1 drive (out of 4).
mdadm: /dev/md/3 has been started with 4 drives.
mdadm: /dev/md/4 has been started with 1 drive (out of 4).
mdadm: /dev/md/5 has been started with 1 drive (out of 4).
mdadm: /dev/md/6 has been started with 1 drive (out of 4).
mdadm: /dev/md/7 has been started with 1 drive (out of 4).
mdadm: /dev/md/8 assembled from 2 drives - not enough to start the array.
mdadm: /dev/md/8 assembled from 2 drives - not enough to start the array.

$ cat /proc/mdstat
Personalities : [raid1] 
md7 : active raid1 sdb9[1]
      999412 blocks super 1.2 [4/1] [_U__]
      
md6 : active raid1 sdb8[1]
      290804 blocks super 1.2 [4/1] [_U__]
      
md5 : active raid1 sdb7[1]
      11252 blocks super 1.2 [4/1] [_U__]
      
md4 : active raid1 sdb6[1]
      10228 blocks super 1.2 [4/1] [_U__]
      
md3 : active raid1 sda5[5] sdd5[3] sdc5[2] sdb5[1]
      976884 blocks super 1.2 [4/4] [UUUU]
      
md2 : active raid1 sdb4[1]
      10228 blocks super 1.2 [4/1] [_U__]
      
md1 : active raid1 sdb3[1]
      975860 blocks super 1.2 [4/1] [_U__]
      
md0 : active raid1 sdb2[1]
      975860 blocks super 1.2 [4/1] [_U__]
      
unused devices: <none>



```

I will be grateful for help

---


---
title: "extundelete help Synology DS2413+ raid"
date: 2014-08-23
forum: New to Ubuntu
---

### Post by 00229933 on 2014-08-23
so some files where deleted from a folder on my DS2413+. Im trying to use the extundelete command but I can not figure it out. I see that I need to have the drive as read only but Im not sure how to do this. I am able to mount the 11 disk raid ext3/4 and see the files. I can see the main raid is /dev/md2 but not sure what to do. Any help would be great. Thank you to any one that has time to help!

---

### Post by 00229933 on 2014-08-23
Here is the drive configuration

[COLOR=#000000][FONT=monospace]root@andrew-desktop:~# blkid[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdb1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdb2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdb5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="c9c0dc44-efe7-b293-6850-339da828d1b2" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sda1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sda2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sda5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="1731ca62-3770-533e-c678-db0a26727670" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sde1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sde2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sde5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="d3378c5c-a0a6-a7d3-e710-3c1951cdc76f" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdd1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdd2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdd5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="6a39d2f4-95fe-8faf-e377-67119158b722" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdc1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdc2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdc5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="d46872d2-ead6-da14-733a-d3aad792ac3a" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdg1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdg2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdg5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="56f18085-bd33-ffd1-841d-9cc4c91e68f0" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdh1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdh2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdh5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="8f6ad34e-02f7-9fdd-8d3e-1b46a21ed242" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdi1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdi2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdi5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="7ea7ac76-ea55-625b-dee8-aa5c9847bc55" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdf1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdf2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdf5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="9daf50c4-2a9e-f180-297c-d220e7ccb0ad" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdj1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdj2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdj5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="2715bff6-6412-4098-00f4-8f9faa440cf9" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdk1: UUID="df9949fc-d2cf-4e9e-9eb2-3163ed2a0f2c" TYPE="ext4" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdl1: UUID="3a8805ab-7add-1fee-3017-a5a8c86610be" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdl2: UUID="78f66299-ae79-4691-2316-46eae6b67d45" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/sdl5: UUID="51ff2c83-c37b-53a9-5666-3761ed7d9e0d" UUID_SUB="6102d1d6-e932-be5e-38c5-12c34d4b7bc3" LABEL="PostDrive:2" TYPE="linux_raid_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/md2: UUID="JImnma-gMzB-Zj8s-GTki-Tca3-tXa5-LxKo13" TYPE="LVM2_member" [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/mapper/vg1000-lv: LABEL="1.42.6-3211" UUID="b5977034-e7f4-4913-a8d5-66280dc470f0" TYPE="ext4" [/FONT][/COLOR]

---

### Post by 00229933 on 2014-08-23
here is another

[COLOR=#000000][FONT=monospace]root@andrew-desktop:~# sudo mdadm --detail /dev/md2[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]/dev/md2:[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]        Version : 1.2[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]  Creation Time : Tue May 28 11:09:43 2013[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]     Raid Level : raid5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]     Array Size : 39022836480 (37215.08 GiB 39959.38 GB)[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]  Used Dev Size : 3902283648 (3721.51 GiB 3995.94 GB)[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]   Raid Devices : 11[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]  Total Devices : 11[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    Persistence : Superblock is persistent[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]    Update Time : Sat Aug 23 13:57:38 2014[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]          State : clean [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] Active Devices : 11[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]Working Devices : 11[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] Failed Devices : 0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]  Spare Devices : 0[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]         Layout : left-symmetric[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]     Chunk Size : 64K[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]           Name : PostDrive:2[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]           UUID : 51ff2c83:c37b53a9:56663761:ed7d9e0d[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]         Events : 97124[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]    Number   Major   Minor   RaidDevice State[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]       0       8       21        0      active sync   /dev/sdb5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]       1       8       53        1      active sync   /dev/sdd5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]       2       8       37        2      active sync   /dev/sdc5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]       3       8       69        3      active sync   /dev/sde5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]       4       8      133        4      active sync   /dev/sdi5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]       5       8      181        5      active sync   /dev/sdl5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]       6       8      149        6      active sync   /dev/sdj5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]      11       8        5        7      active sync   /dev/sda5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]      10       8       85        8      active sync   /dev/sdf5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]       9       8      101        9      active sync   /dev/sdg5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]      12       8      117       10      active sync   /dev/sdh5[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]root@andrew-desktop:~# extundelete /dev/md2 --restore-directory 1.42.6-3211/PostDrive/Backups[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]extundelete: failed to read-only open device "/dev/md2": Error code 2133571347[/FONT][/COLOR]

---

### Post by gene8 on 2014-11-22
did you ever fix this?? got the same error and not sure if it has something to do with hard drives with 4096 byte size

---


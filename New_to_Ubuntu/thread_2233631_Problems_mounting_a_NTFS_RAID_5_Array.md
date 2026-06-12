---
title: "Problems mounting a NTFS RAID 5 Array"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by fossilman on 2014-07-09
Hello all,

I am a former MS windows user and very recently switched to Ubuntu 14.04  LTS, my hard drive configuration consisted of a single 1 Tb HDD and 4  1Tb drives in an Intel BIOS RAID 5 and formatted withing Windows 7 with  NTFS.

I made a fresh new installation with a new hard drive (former main drive  just went smoke) when using the first two options, and chosing the single disk it always stopped in an error saying that I could not copy GRUB in the /sda1 partition, after looking about the problem I solved it using the "Something Else" option and making a manual partition installation, now my logical drives finished like this:

```

sde1 / 25Gb 
sde5 /tmp 5Gb 
sde6 /swap  1Gb
sde7 /var 5Gb
sde8 /home 970+Gb
```

After surpassing the first problems during the installation, now I want to mount the RAID, so I can read/write and access all my data I had under Windows 7, then I started doing this:

```

fossilman@pangea:~$ sudo dmraid -s
*** Group superset isw_fhhecaiej
--> Subset
name   : isw_fhhecaiej_Oerth
size   : 5860561920
stride : 128
type   : raid5_la
status : ok
subsets: 0
devs   : 4
spares : 0
```

After that then I did: 

```

fossilman@pangea:~$ sudo dmraid -r
/dev/sdd: isw, "isw_fhhecaiej", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdc: isw, "isw_fhhecaiej", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdb: isw, "isw_fhhecaiej", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sda: isw, "isw_fhhecaiej", GROUP, ok, 1953525166 sectors, data@ 0
```

Apparently everything was alright, then I used:

```

fossilman@pangea:~$ sudo dmraid -ay
[sudo] password for fossilman: 
ERROR: isw: seeking device "/dev/dm-1" to 18446744073709517312
RAID set "isw_fhhecaiej_Oerth" already active
```

Then I tried the mounting command:

```

fossilman@pangea:~$ sudo mount -t ntfs-3g -o /dev/sda /mnt/raid
```

And It keeps displaying the mount help. Please, let me know what I  must do to finish this task, I really do not want to lose the data that is inside the RAID.

---


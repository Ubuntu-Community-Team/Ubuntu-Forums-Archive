---
title: "HDD 2nd Internal  won't mount, err is | zero exit status 32: mount: wrong fs type,..."
date: 2014-11-21
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2014-11-21
Hey Guys, thinks for reading. 

I have two 1TB drives in my Box. Course all the OS/Etc. on "Main"---my 2nd Internal HDD. I've saved GB of Data on there, thus would like to try to get back "Up". 
It's set up "Production" wise nder ext4. Ironically I first set up with Journal Jfs----but decided against it. I *think* this error was caused by an "ungraceful" restart. 
AKA_--My CPU completely locked up/keybord all (no way to do a soft CTR-ALT-DEL)--I gently powered off (trying to get it to prompt for shutdown--didn't work, thus just turned off). 


Here is a copy of the Error Message that pops up. 

--of course Drive name is "Saturn"

```

Error mounting /dev/sdb1 at /media/bender/Saturn: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/bender/Saturn"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail  or so

```


My apology, belose is further data, not sure if it's necessary, but have included in case. Apology for such length. 

Also, NO CLUE why it's such a high block size (that a contributor--is there a way to change the Primary Local site of  4096 (back to 1024 or 512--those are recc'd sizes, correct?) 

Just noticed one thing, I did have it at full root privledges (since it was a read/write HDD only storing non-sensitive information and I live and work alone, so....
--base superblock?  zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1



```

File system:ext4
Size:930.05 GiB

<i>Filesystem volume name:   Saturn
Last mounted on:          /media/xubuntu/Saturn
Filesystem UUID:          0c64240a-6a98-431f-9f0e-05e5f2396246
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              60194816
Block count:              240772095
Reserved block count:     12038604
Free blocks:              161775577
Free inodes:              58836370
First block:              0
Block size:               4096

Fragment size:            4096
Reserved GDT blocks:      966
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
RAID stride:              32750
Flex block group size:    16
Filesystem created:       Mon Nov 17 01:34:09 2014
Last mount time:          Thu Nov 20 08:21:58 2014
Last write time:          Thu Nov 20 22:18:40 2014
Mount count:              0
Maximum mount count:      -1
Last checked:             Thu Nov 20 08:44:19 2014
Check interval:           0 (<none>)
Lifetime writes:          335 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28


```

Thank you a lot for the help!!!

---

### Post by ajgreeny on 2014-11-21
What does ```
sudo fdisk -l
sudo parted -l
``` show?
It may give us some more clues about what is going on.

Did the disk work OK previously in Ubuntu, or has this problem always been evident?
Is the system using UEFI and GPT partitions?

Do you have a RAID running using this disk as I note the line 
```
RAID stride: 32750
```in your output, which I do not have in mine, as I don't run RAID.

I do not think the block size and fragment size of 4096 is a problem as my system also has that same output from tune2fs; I use UEFI and GPT partitions, hence my query above.

Have you tried running **sudo e2fsck /dev/sdb1** on the unmounted drive; that may be able to sort out the glitch for you?

---

### Post by whereismymindat2 on 2014-11-21
Hey @ajgreeny thank you for the reply!

Here is the resulf ot fdisk -l
_______________________________________________
```

root@Dooley:/home/bender# sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

```

_____________________________________

root@Dooley:/home/bender# 
Results of sudo parted -l


```

root@Dooley:/home/bender# sudo parted -l
Model: ATA WDC WD10EZEX-22B (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End     Size    File system     Name  Flags
 4      325GB  345GB   20.0GB  ext4
 5      345GB  357GB   12.0GB  ext4
 1      357GB  972GB   615GB   ext4
 3      972GB  984GB   12.0GB  ext4
 2      984GB  1000GB  15.7GB  linux-swap(v1)


Model: ATA WDC WD10EZEX-22B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      17.4kB  999GB  999GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           


```

______________________________________


I noticed the RAID line too. Nope, no RAID. I know "of" RAID, but would not have a clue how to set it up and almost 99.99999% sure I didn't run any commands to put into RAID state. 
(aka-I used GParted GUI-to set up everything). 

```


Not sure if it Matters (to the 2nd Drive--Issues) however you will notice I have my Production drive partitioned out.
 
Each one is

/root
/boot
/home
/tmp  (yeah, rather large tmp-for a reason for now). 
/swap


```


____________________________________________

Apology for too much info, but my hope is to give enough so you don't have to guess and/or ping to get a "101" answer. 

1st---Not sure if this matters. When I very first started out with 2nd HDD as storage.  I formatted it as jfs. (also had the Production /home as jfs thus thought wouldn't see a conflict). 
thinking of any broken link type issues--aka----before I formatted to ext4 what was on jfs--I moved temporaritly to my Production. 
After formatting, I moved back to exf4 (thus--future considerations-is there any type metadata--needs scrubbed when moving amonsts different format types--having read what I have read, don't think so...but....

Ran well for awhile (thus don't think an issue) 


____________________________________________

```

2nd--Another matter (pertinent??)--2-3 days ago. I tried to run "CHECK" (from GParted). It ran about 5-minutes then seized up. (100%). 
AKA_came back to CPU to look. The blue bar was no longer scanning. Neither mouse/keyboard worked. 

Tried a "Soft" power button shutdown (only verbiage I know)--but I barely tap it, and it shuts down showing the text screen of "stopping xyz abc"..so on
I get the same when I do a "soft" CTR-ALT-DEL and (normal) gives the text based shutting down screen.

When it seized up--it seized up--nothing worked (keyboard/mouse),etc. 

Had to hard rest. (ungraceful power shutoff).  

Tried (again) to run last night/"CHECK"  (good 9+hours)-this time, box was greyed out, stuck, not running. *BUT*, I did have the ability to gracefully shut down, thus did and 


That's where I've ended now  ;-) 

```
________________________________

THANK YOU VERY MUCH!!! Really appreciate the help!!!!
promise not to write so much next time  ;-)

R

---

### Post by whereismymindat2 on 2014-11-21
OH, PS---do you know the TEE command to push out terminal text to a file?  I'm trying to use it (for logs here), but not much success

____________________________________
1st "ODD"my "Production" machine shows  "Intel" partition table type


Disk-1 "Production"---Listed as "Intel" partition table type

When I use (against the *BAD* "Saturn" Drive (first level Analyze)
Disk 2-"Saturn"-- I get Listed as EFT GPT (relevant?)


____________________________________


Just a "general" Analyze"

```

______________________________________
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63

The harddisk (1000 GB / 931 GiB) seems too small! (< 1000 GB / 931 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  MS Data               1938106456 1953739831   15633376
   MS Data               1938106462 1953739837   15633376

[ Continue ]
FAT32, blocksize=4096, 8004 MB / 7633 MiB


```

Odd part, I'm 99.99999999% sure, I"ve never done *ANYTHING* "FAT" to the drive. I *HAVE* used FAT USB sticks for PenDrive purposes,etc. But not formatted to any FAT/MS DATA 


________________________________

Therefore, I want to TEE out the run from a DEEP scan (since I can't see back on old terminal scroll data) 

Here is just one screen grab of several errors. that scrolled then disappared


```


MS Data                 25820773   25823652       2880 [NO NAME]
Bad root_cluster
check_FAT: Unusual media descriptor (0xf0!=0xf8)
Warning: number of heads/cylinder mismatches 2 (FAT) != 255 (HD)
Warning: number of sectors per track mismatches 18 (FAT) != 63 (HD)
  MS Data                 25820797   25823676       2880 [NO NAME]
Bad root_cluster
check_FAT: Unusual media descriptor (0xf0!=0xf8)
Warning: number of heads/cylinder mismatches 2 (FAT) != 255 (HD)
Warning: number of sectors per track mismatches 18 (FAT) != 63 (HD)

```

and  if it matters, hers is the first LIST from the Analyze of the cursory (non-deep) scan

```

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   P MS Data                       34 1926176793 1926176760 [Saturn]
Directory /

>drwxr-xr-x  1000  1000      4096 19-Nov-2014 14:05 .
 drwxr-xr-x  1000  1000      4096 19-Nov-2014 14:05 ..
 drwx------  1000  1000     16384 17-Nov-2014 01:34 lost+found
 ?---------     0     0         0                   backintime
 ?---------     0     0         0                   FEBE
 ?---------     0     0         0                   New_Back_In_Time
 drwxrwxr-x  1000  1000      4096 18-Nov-2014 12:01 DDR_TTEST
 ?---------     0     0         0                   Desktop_Backup
 ?---------     0     0         0                   RANTHONY_usb
 ?---------     0     0         0                   Rescue
 ?---------     0     0         0                   APTIK
 -rw-r--r--     0     0       303 18-Nov-2014 20:49 ppa.list
 ?---------     0     0         0                   archives
 -rw-r--r--     0     0     35267 18-Nov-2014 21:05 packages-installed.list
 -rw-r--r--     0     0     35267 18-Nov-2014 21:05 packages.list
-rw-r--r--     0     0 1054702976 18-Nov-2014 21:20 app-settings.tar.gz
 ?---------     0     0         0                   themes
 ?---------     0     0         0                   icons
 ?---------     0     0         0                   User_Agent
>?---------     0     0         0                   HailStorm
                                                   Next
Use Right to change directory, h to hide deleted files
    q to quit, : to select the current file, a to select all files
    C to copy the selected files, c to copy the current file

```

Therefore "good news" I guess is that it's seeing *SOMETHING* 


REGARDING TEE
Therefore  What is the correct way to TEE out a log file?  I've never been able to get it to work. 
--------------------------
This is one of many TEE articles I've tried.

[http://embraceubuntu.com/2007/05/17/using-tee-to-write-to-files-and-the-terminal/](http://embraceubuntu.com/2007/05/17/using-tee-to-write-to-files-and-the-terminal/)

The EXAMPLE: $sudo apt-get upgrade 2>&1 | tee ~/apt-get.log
_________________________________________________

Put Folder on Desdktop Saturn-Full-Analyze-Log
cd / to that--the run testdisk from that cd directory. 


cd /home/bender/Desktop/Saturn-Full-Analyze-Log/ 
testdisk 2>&1 | tee Saturn_Full_Analyze.txt

It messed up any ability to imput/make choices insidd the term (aka--junk as if I were actually typing commands like CTRL, TAB,etc.) 

______________________________


Then, when I tried........
(took out the 2>&1

When I open the text file with Mousepad, looks like this. 
All types of goofy characters  (is that some ISO/CHAR/ASCII set Mousepad can't read?) 





```

cd /home/bender/Desktop/Saturn-Full-Analyze-Log/ 
testdisk | tee Saturn_Full_Analyze.txt

[?1049h[1;25r(B[m[4l[?7h[39;49m[?25l[?1h=[39;49m[37m[40m[H[2JTestDisk 6.14, Data Recovery Utility, July 2013
[2dChristophe GRENIER <grenier@cgsecurity.org>
[12dreview. If you choose to create the text file, (B[0;1m[39;49m[37m[40mtestdisk.log(B[m[39;49m[37m[40m , it
[13dwill contain TestDisk options, technical information and various
[14doutputs; including any folder/file names TestDisk was used to find and
[15dlist onscreen.
[17dUse arrow keys to select, then press Enter key:
[18d(B[0;7m[39;49m[37m[40m>[ Create ](B[m[39;49m[37m[40m Create a new log file
[19d [ Append ] Append information to log file
[20d [ No Log ] Don't record anything
[18d [ Create ]
[19d(B[0;7m[39;49m[37m[40m>[ Append ][20;34H(B[m[39;49m[37m[40m[?1h=[39;49m[37m[40m[H[2JTestDisk 6.14, Data Recovery Utility, July 2013


```

AGAIN, THANK YOU VERY MUCH FOR THE ASSISTANCE!! WOULD REALLY LIKE TO HAVE THIS DATA BACK! ;-)

R.

---

### Post by ajgreeny on 2014-11-21
No need to use tee to put output from terminal into a file; simply use ```
command > filename.txt
``` to make a new file called filename.txt or ```
command >> filename.txt
``` to append the new output to the end of that already existing file.

You can then read the txt file with your GUI text editor or if in command line, with nano.

---

### Post by oldfred on 2014-11-21
Testdisk has its own log file, cannot you use that?

I normally do not suggest separate /boot partitions for most desktops.

I do suggest gpt partitioning if drive will be Linux only. Windows only boots from gpt with UEFI. 
But fdisk does not work on gpt partitioned drives.

Do not know about other formats than ext4 which seems to be the best general purpose format. 

But if you have a hard shutdown you often have to run fsck on your partition(s). And if not ext family it would be totally different file check utility. You may have to run it on all ext4 partitions.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by whereismymindat2 on 2015-10-06
@ajgreeny, @oldfred
THANK YOU!! for the assistance.

---


---
title: "Adding Second HDD"
date: 2016-09-27
forum: New to Ubuntu
---

### Post by bobowon on 2016-09-27
Been trying to add a second HDD as the one I started with is running low on memory. 
I formatted the new HDD with gparted as ext4. 
When trying to make a folder on this drive I am unable.
When checking the properties of this drive it's owner is "root" its group is also "root" and I suspect this to be the problem although I am not entirely sure.
I have looked at other forums from people with similar issues but have thus far been unable to change the owner to myself. (most likely because I am a ubuntu novice at best)

I am hoping someone can confirm if this is even the reason I cannot make folders on this drive and how to fix it if it is the problem.

---

### Post by SeijiSensei on 2016-09-27
Yes, at the outset, only root can create folders on the drive.  There are ways to change this, but you need to tell us how many accounts you have on the machine.  If you're the only user, you can do this:

1) Create a "mount point," an empty directory to which the partition will be attached.  Let's say it's going to be /data:
```

cd /
sudo mkdir /data

```

2) Now if you're going to be the only user, you can grant full permissions to yourself
```

sudo chown bob:bob /data
sudo chmod ug+rwx,o+rx /data

```
That gives full read/write/execute permissions to bob and any members of the "bob" group.  Anyone else can list the contents of the directory (via the eXecute permission), and read the files contained therein.

One thing that might make life easier is to create a "symbolic link" in your home directory:
```

cd ~
ln -s /data

```
Note there's no "sudo" here.  Now if you open your home directory with a file browser, you'll see "data" as one of the folders.  You can now treat it just the same as any other directory in your home folder.  If you're coming from Windows, a symlink is like a Windows "shortcut".

Before going much further you would do well to learn about about permissions.  Start with this: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by bobowon on 2016-09-27
I am the only user. 
1) went well, I was able to use that command and it seems to have worked. 
2) I don't fully understand this part. do I just replace "bob" with my username and paste that into terminal, then paste the second line of code? (I tried just replaceing bob with my username and pasting the two lines in and nothing seems to happen)

---

### Post by Bashing-om on 2016-09-27
bobowon; Hello;

As I pass by:
> 
do I just replace "bob" with my username and paste that into terminal, then paste the second line of code? (I tried just replaceing bob with my username 

Yep, as in Yes . that is the correct.
> 
pasting the two lines in and nothing seems to happen

again uh huh .. a no return is just the system doing as told - no sas or back-talk, that is a good thing . System has nothing bad to report and just did as directed .

[INDENT][INDENT]it's all good
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
so after attempting to put in those lines of code the end result is having a link to a folder names "data" in home, and the second hdd still is owned by root, not sure why or maybe if it's not mounted right.

---

### Post by Bashing-om on 2016-09-27
bobowon; Ho Kay .

Let us back up a step, What is the file sytem(s) on this 2nd hard drive ?
```

sudo fdisk -lu

```
and where/how are you mounting said hard drive to the ubuntu file system ?

[INDENT][INDENT]it is a process
[/INDENT][/INDENT]

---

### Post by Geoffrey_Arndt on 2016-09-27
Did you process (enter) each command at a time, . . . . rather than pasting #2 and trying to execute both at same time?

---

### Post by bobowon on 2016-09-27
I used the program GParted to format it, according to gparted the file system is ext4, mount point is /media/logan/3TBHD, partition /dev/sda1 

info from the line of code spit this out at me, not entire sure what is useful or not so ill just paste it all.

```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: FA166F8C-0DB7-4D3C-807C-EEB2B7EBF7A4


Device     Start        End    Sectors  Size Type
/dev/sda1   2048 5860532223 5860530176  2.7T Microsoft basic data




Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x181b55b5


Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1  *          2048 1937014783 1937012736 923.7G 83 Linux
/dev/sdb2       1937016830 1953523711   16506882   7.9G  5 Extended
/dev/sdb5       1937016832 1953523711   16506880   7.9G 82 Linux swap / Solaris


Partition 2 does not start on physical sector boundary.
```

---

### Post by Bashing-om on 2016-09-27
bobowon; Great.

So does the mount point(s) exist ?
show:
```

ls -al /media/
ls -al /media/logan/
ls -al /media/logan/3TBHD

```
stepping through the directory tree  while looking at the permissions .
That 3TBHD is a Windows only drive ! Windows IS NOT posix compliant - no honor for linux access rights .

AND that 3TBHD drive is shown as the 1st hard drive sda - with but a single partition booting Windows !. Is not the target the added sdb drive of " /dev/sdb: 931.5 GiB " ?
Also noting this sdb drive is bootable .

set our sights on the correct target, and please forgive my denseness here and re-define the goal here .
 Booting ubuntu on sdb .. and you want to do what ?

[INDENT][INDENT]sometime I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
the 1TB drive is the original, I never considered if a drive could be windows only or not. the goal was to add the 3tb drive as extra storage.

Edit: I use this computer for Plex to stream media
Here is the code that those lines spit out

```
logan@Media-server:~$ ls -al /media/
total 16
drwxr-xr-x   4 logan logan 4096 Sep 13 13:10 .
drwxr-xr-x  25 root  root  4096 Sep 27 15:57 ..
drwxr-x---+  3 root  root  4096 Sep 27 16:32 logan
drwxr-xr-x   2 root  root  4096 Sep 13 13:10 SecondHDD
logan@Media-server:~$ ls -al /media/logan/
total 12
drwxr-x---+ 3 root  root  4096 Sep 27 16:32 .
drwxr-xr-x  4 logan logan 4096 Sep 13 13:10 ..
drwxr-xr-x  3 root  root  4096 Sep 27 14:41 3TBHDD
logan@Media-server:~$ ls -al /media/logan/3TBHD
ls: cannot access '/media/logan/3TBHD': No such file or directory
logan@Media-server:~$
```

also here is what those lines of code spit out

```
logan@Media-server:~$ ls -al /media/
total 16
drwxr-xr-x   4 logan logan 4096 Sep 13 13:10 .
drwxr-xr-x  25 root  root  4096 Sep 27 15:57 ..
drwxr-x---+  3 root  root  4096 Sep 27 16:32 logan
drwxr-xr-x   2 root  root  4096 Sep 13 13:10 SecondHDD
logan@Media-server:~$ ls -al /media/logan/
total 12
drwxr-x---+ 3 root  root  4096 Sep 27 16:32 .
drwxr-xr-x  4 logan logan 4096 Sep 13 13:10 ..
drwxr-xr-x  3 root  root  4096 Sep 27 14:41 3TBHDD
logan@Media-server:~$ ls -al /media/logan/3TBHD
ls: cannot access '/media/logan/3TBHD': No such file or directory
logan@Media-server:~$
```

---

### Post by Bashing-om on 2016-09-27
bobowon; K;

With you so far .
As is now there is but that one Windows partition on sda .
And you desire to access that file system from the ubuntu install ---- and -- you want to mount that sda drive  permanently from within ubuntu ? In that sda is physically installed in that box and is not removable media, correct ?

[INDENT][INDENT]letting the mud settle out of the waters
[/INDENT][/INDENT]

---

### Post by oldfred on 2016-09-27
Then you are not bob, but logan. Every bob in the work then has access to your system (just kidding).

If you create the new mount point like /data or /mnt/data, you must unmount from a default mount using Nautilus first. Or use the default.

To confirm who you are:
       echo $USER 


 sudo chmod -R a+rwX,o-w /media/logan/3TBHD        
 sudo chown -R $USER:$USER /media/logan/3TBHD
#where $USER should be your login name

---

### Post by bobowon on 2016-09-27
yes, this is inside the case of the computer, plugged in and not a removeable drive. (well not without a screw driver)

---

### Post by yancek on 2016-09-27
The reason you have a data directory/mount point created in your /home/user directory is because that is the default location when a user logs in to a terminal.  Delete it.

You need to change the owner:group for:   /media/logan/3TBHD from the current:  root:root to logan:logan with the commands suggested above.  That is, if the output you posted is correct and the user name is actually logan and you want the mount access point to be /media/logan/3TBHDD.
 
When you ran the command:  ls -al /media/logan/  it shows "drwxr-xr-x  3 root  root  4096 Sep 27 14:41 3TBHDD"
When you ran the next command:   ls -al /media/logan/3TBHD  you got the following error which is correct.    ls: cannot access '/media/logan/3TBHD': No such file or directory
You left the second letter D off the command (3TBHDD) which is the name you show for that mount poiint..

---

### Post by bobowon on 2016-09-27
correcting one of the previous commands from before where i missed a letter I got this spit out at me 
logan@Media-server:~$ ls -al /media/logan/3TBHDD
total 24
drwxr-xr-x  3 root root  4096 Sep 27 14:41 .
drwxr-x---+ 3 root root  4096 Sep 27 18:37 ..
drwx------  2 root root 16384 Sep 27 14:41 lost+found
logan@Media-server:~$ 


not sure if that changes anything

---

### Post by oldfred on 2016-09-27
The post above is wrong, use this:

sudo chmod -R a+rwX,o-w /media/logan/3TBHDD
 sudo chown -R $USER:$USER /media/logan/3TBHDD

If an internal drive, you may want to permanently mount it with fstab. Then on reboots it always is there in the same place.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="https://wiki.archlinux.org/index.php/Fstab"]https://wiki.archlinux.org/index.php/Fstab
[/URL]
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) 

[URL="https://wiki.archlinux.org/index.php/Fstab"]
[/URL]

---

### Post by Bashing-om on 2016-09-27
bobowon; k .

Making progress, 
Now we have a known mount point,
Next question for clarification - what do you want to attach to this mount point ? I have in mind the target is sda1.
> 
/dev/sda1   2048 5860532223 5860530176  2.7T Microsoft basic data

where I am also going to assume the file system here is NTFS.
Now I can give you a general mounting of this device, you will have to adjust to suite your particular needs to restrict/allow access.
we can run something like:
```

sudo mount -t ntfs /dev/sda1 /media/logan/3TBHDD

```
and access to look at what is:
```

ls -al /media/logan/3TBHDD

```

And see what adjustments need to be made .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
it is sda1 that is the new hdd I'm trying to add
currently its actually ext4 and not ntfs but I can change that if it makes things better/easier
and if it helps the purpose of the drive is mostly to hold media content such as music and video to be streamed via Plex

---

### Post by Bashing-om on 2016-09-27
bobowon; Yuk !

Now "something" is not what you expect.
terminal command :
```

sudo fdisk -l /dev/sda

```
will show that you only have the one Windows partition - of a size 2.7T - on that hard drive. No wiggle room to add partitions. 
a) do you make up partitions on the sda drive ?
b) do you re-adjust the target from sda to somewhere on sdb ? Whereas sdb also only has one active partition .

Bear in mind linux nomenclature;
sda would be the 1st hard drive on the sata controller that the system 1st recognizes - a device !
sdb is that 2nd hard drive
sdc would be a third
then the partitions on these devices are designated 1, 2, 3, 4 and so on
such that sda1 is the 1st hard drive and 1st partition
sdb5 is the 2nd hard drive and the 5th partition
sdc3 would be the 3rd hard drive and the 3rd partition.

still with that rat
[INDENT][INDENT][INDENT]in the wood pile
[/INDENT][/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
A) I made one large partition on the sda drive
b) sdb is the drive that the operating system is installed to

might add some pictures of the program i used to format sda just incase that gleams any new info

here is the code that that code spit out 
logan@Media-server:~$ sudo fdisk -l /dev/sda
[sudo] password for logan: 
Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: FA166F8C-0DB7-4D3C-807C-EEB2B7EBF7A4


Device     Start        End    Sectors  Size Type
/dev/sda1   2048 5860532223 5860530176  2.7T Microsoft basic data


screenshots
[http://pasteboard.co/8iOfzpXEt.png](http://pasteboard.co/8iOfzpXEt.png)


[http://pasteboard.co/8iOtjzGqL.png](http://pasteboard.co/8iOtjzGqL.png)

---

### Post by Bashing-om on 2016-09-27
bobowon; Hey ...

We are still not on the same page !
On sda yes there is one LARGE partition. but it is not a linux partition:
> 
Microsoft basic data


However as this is a GPT partitioned device, let's swap tools to look at it.
show:
```

sudo gdisk -l /dev/sda

```
where it is a 'g' for (G)UID -= think GPT- rather than the 'f'' on 'fdisk'.

If ya gonna shoot rats, it is rat shot that is loaded
if ya gonna shoot buffalo ya want a .50 caliber Sharps .

[INDENT][INDENT]let's identify what we are shooting at
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
here is the code that that spit out

logan@Media-server:~$ sudo gdisk -l /dev/sda
[sudo] password for logan: 
GPT fdisk (gdisk) version 1.0.1


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): FA166F8C-0DB7-4D3C-807C-EEB2B7EBF7A4
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2925 sectors (1.4 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      5860532223   2.7 TiB     0700  Second HDD
logan@Media-server:~$

---

### Post by Bashing-om on 2016-09-27
bobowon; And ... 

Again I affirm that on the sda there is but that single one partition encompassing the entirety of the available disk space.
An ext4 partition is not in the equation . and if you are shooting at a ext4 partition, you are shooting at the air . none exist on this device.
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
This single partition is a Windows partition, and most likely is of the NTFS file system .

Now I ask you . what do you want to do given this information ?

[INDENT][INDENT]resetting the sights
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
So is there a way to make this drive capable of being written to on this computer?
as it stands right now I am not the "owner" of this drive and cannot do anything with it. (root still owns it)

What I am hoping to use it for like I said was put movies and other such media on it. can that be done with how its currently set up?

---

### Post by yancek on 2016-09-27
> An ext4 partition is not in the equation

The second image in post #20 shows The GParted screen with sda1 as an ext4 partition.  You can verify this by running:  sudo parted -l(Lower Case Letter L in the command)
Then all you should need to do is run the commands suggested in post 16 and put an entry in fstab as suggested if you are going to have the drive permanently attached.

---

### Post by Bashing-om on 2016-09-27
@ yancek , Well ..

It is a confusing designation for the file system type 
The terminal commands all indicate this as NTFS
code >>  0700
Type >> Microsoft basic data

Not to say we can not try and mount the sda1 partition each way, and see for ourselves what the file system is actually .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
tried to go and follow the instructions from post #16 but I appear to have achieved nothing in my attempt. it has gone over my head

---

### Post by Bashing-om on 2016-09-27
bobowon; Ho Kay .

In small steps.
2 terminal commands.
```

sudo mount -t ntfs /dev/sda1 /media/logan/3TBHDD
ls -al /media/logan/3TBHDD

```
Do you have access to the file system as a NTFS file system ?
What results ?? , maybe we do something else.

[INDENT][INDENT]try try try again
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
first line of code spit this out 
logan@Media-server:~$ sudo mount -t ntfs /dev/sda1 /media/logan/3TBHDD
[sudo] password for logan: 
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
logan@Media-server:~$

---

### Post by bobowon on 2016-09-27
clicked the unmount in the ....file explorer(named after some fish i think)?  and got this when running the line again 

logan@Media-server:~$ sudo mount -t ntfs /dev/sda1 /media/logan/3TBHDD
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
logan@Media-server:~$

---

### Post by Bashing-om on 2016-09-27
bobowon; Welp ..

Quite probable that what the system is telling you is the truth . the partition is already mounted - from prior attempts.
so.
what results :
```

ls -al /media/logan/3TBHDD

```
where I can accept the system tells you that "you" do not have permission. try it anyway as given and tell us what happens.
Adverse result, we make adjustments.

[INDENT][INDENT][INDENT]try try try again
[/INDENT][/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
that code spits this out

logan@Media-server:~$ ls -al /media/logan/3TBHDD
ls: cannot access '/media/logan/3TBHDD': No such file or directory
logan@Media-server:~$

---

### Post by Bashing-om on 2016-09-27
bobowon; Welp ..

Let's say then that GParted sees the file system correctly as ext4.

Make sure that the partition is not presently mounted:
```

mount

```
do you see sda1 in that output  :

No ?
Then we mount it as:
```

sudo mount /dev/sda1 /media/logan/3TBHDD

```
now can we access it ?
```

ls -al /media/logan/3TBHDD

```

Keep in mind, that what we mount manually - we are responsible to the system to UNmount !!

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
put in mount, did not see sda1, put in next line of code says that it does not exist, or mount point does not exist. last code says no such file directory. I dont think i missed anything but here is the everything just in case 

```
logan@Media-server:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4001524k,nr_inodes=1000381,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=804188k,mode=755)
/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=804188k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
logan@Media-server:~$ sudo mount /dev/sda1 /media/logan/3TBHDD
[sudo] password for logan: 
mount: mount point /media/logan/3TBHDD does not exist
logan@Media-server:~$ ls -al /media/logan/3TBHDD
ls: cannot access '/media/logan/3TBHDD': No such file or directory
```

---

### Post by Bashing-om on 2016-09-27
bobowon; hummmm ...

> 
mount: mount point /media/logan/3TBHDD does not exist

It did exist at one time .. you did show it to us .

OK. what is the story now ?
show:
```

ls -al /media/
ls -al /media/logan/

```

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
maybe we were using the wrong name for the drive?

logan@Media-server:~$ ls -al /media/
total 16
drwxr-xr-x   4 logan logan 4096 Sep 13 13:10 .
drwxr-xr-x  26 root  root  4096 Sep 27 21:32 ..
drwxr-x---+  2 root  root  4096 Sep 27 21:59 logan
drwxr-xr-x   2 root  root  4096 Sep 13 13:10 SecondHDD
logan@Media-server:~$ ls -al /media/logan/
total 8
drwxr-x---+ 2 root  root  4096 Sep 27 21:59 .
drwxr-xr-x  4 logan logan 4096 Sep 13 13:10 ..
logan@Media-server:~$

---

### Post by Bashing-om on 2016-09-27
bobowon; Ho Kay ...

Now I am a believer .. terminal does not lie .
The former mount was from automounting .

As there is no mount point let us make up one of our own , then attach sda1 to it .
```

sudo mkdir /mnt/look

```
to make our mount point.

and now:
```

sudo mount /dev/sda1 /mnt/look

```
where we mount as a ext4 file system.

and finally can we look and see ?
```

ls -al /mnt/look

```

tell me Yes !

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
So stuff happened, not entire sure what this means
the drive no longer shows up in the file explorer

logan@Media-server:~$ sudo mkdir /mnt/look
[sudo] password for logan: 
logan@Media-server:~$ sudo mount /dev/sda1 /mnt/look
logan@Media-server:~$ ls -al /mnt/look
total 24
drwxr-xr-x 3 root root  4096 Sep 27 14:41 .
drwxr-xr-x 3 root root  4096 Sep 27 23:30 ..
drwx------ 2 root root 16384 Sep 27 14:41 lost+found
logan@Media-server:~$

---

### Post by Bashing-om on 2016-09-27
bobowon; Welp ..

curios and curioser ...

As we mounted in /mnt that bypasses the GUI mounting . deliberate implementation .
What now is of concern, is that there are no files in that partition. is that expected on your part ?
what returns:
```

ls -al /mnt/look/lost+found

```

And ReMeMbeR .. we must unmount what we mounted when we are done ! and all done and shutting down do:
```

sudo umount /mnt/look

```



Do we copy a few test files to sda1 and see what is what ?

[INDENT][INDENT]progress made !
[INDENT][INDENT][INDENT]even with small steps[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
when putting in first line of code it spits this back at me (and currently there are no files in the partition, this is expected, but hoping to change by the end of this) 

logan@Media-server:~$ ls -al /mnt/look/lost+found
ls: cannot open directory '/mnt/look/lost+found': Permission denied
logan@Media-server:~$

---

### Post by Bashing-om on 2016-09-27
bobowon; Hey hey !

Progress made ! .. look'n good .

OK. not knowing how you intend to use this storage, and what restrictions you might want ( at a later time. huh ) . let's make "you" the owner of that file system.
```

sudo chown logan:logan /mnt/look

```

Do we need at this time to copy in some test files and see how the storage partition functions ?

Next now is to make this access permanent ? AND is it your desire to also have access via the GUI ?
 pros and cons to have GUI access also -  If so, how is your editing skills ?, ya comfortable with which text editor ? .. as we will make a backup of /etc/fstab and add into this file mounting directives for the sda1 device .

RemEmBer, we mounted, we must direct to UNmount sda1 .

[INDENT][INDENT]I with you thus far
[INDENT][INDENT]we gonna shoot this sucker ?
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-27
Alright, I was able to successfully create a folder onto the drive, copy a movie into said folder, and successfully watch said movie. I suppose that means I now own this drive! :D 

Also i was able to find the folder the drive is in via the file explorer so that's user friendly enough for me in terms of access. I am reasonably comfortable with text editor so long as you tell me what to put in it. (although all my experience is windows based so hopefully ubuntu is not horribly different in some crazy way for some reason)

guess at this point we need to make sure everything works if the computer is restarted.


(also on a side note the media streaming program plex that i use for media streaming works too!)

my next reply might be delayed a few hours as it is getting late in this part of the good ol canada so I shall be sleeping. I will check back in the morning and continue asap (I shall leave the computer running in case of complications)

---

### Post by Bashing-om on 2016-09-27
bobowonl Yeah !

We set up to make permanent .

What would you like for the permanent storage partition name ?
And show us: - now use code tags ! -
```

sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

and we
[INDENT][INDENT]make it so
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-28
What should the name be? not sure what the name currently is, unless its the same as the label
Here is the code that that spit out

```
logan@Media-server:~$ sudo blkid[sudo] password for logan: 
/dev/sda1: LABEL="3TBHDD" UUID="0263d081-7f2b-4113-8ec9-24d0c8022e9c" TYPE="ext4" PARTLABEL="Second HDD" PARTUUID="1e1edc16-3486-40df-bcd7-0ec2dad99a91"
/dev/sdb1: UUID="fa25a441-1206-49a1-90d4-a9d4ffc68475" TYPE="ext4" PARTUUID="181b55b5-01"
/dev/sdb5: UUID="f3d99380-6007-4c77-a3b3-97dad437238e" TYPE="swap" PARTUUID="181b55b5-05"

```

---

### Post by oldfred on 2016-09-28
You can manually create any mount point you want, or system default uses UUID first or label if you have one. So I always label my partitions.
But I have labeled partitions Data and mounted at data. Since case is used in LInux those are two totally different locations, not one data/Data.

Default mounts are in /media/$USER. You can only mount a partition once, or you must unmount from /media if you clicked on it in Nautilus before manually mounting to another location.

To see what is mounted in terminal, but it has a lot of system defaults shown also:
mount

If you want to permanently mount, go back to post # 16 for links to detailed instructions on using fstab.

---

### Post by yancek on 2016-09-28
> What should the name be? not sure what the name currently is, unless its the same as the label

If you still have the partition mounted from the suggestions in posts from yesterday, the mount (access) point/directory should be /mnt/look. That would only be the case if you have not re-booted the computer as the mount method used yesterday was temporary. So navigate there to see if you still have what was shown yesterday.  If you want to mount the partition (sda1) somewhere other than /mnt/look, you first need to unmount that mount point.  If you have re-booted and /mnt/look shows nothing, then go to the step below to mount it elsewhere.

> sudo umount /mnt/look

As suggested above, you can select any mount point you want.  Earlier, you showed /media/logan/3TBHDD.  If that is what you want then use the following command to mount it.

> sudo mount /dev/sda1 /media/logan/3TBHDD

You should then be able to navigate to /media/logan/3TBHDD and see the two hidden files and the lost+found as you did yesterday.  The blkid output shows ext4 as the filesystem type so if you get an error with the above command indicating you need to enter a filesystem type, try:

> sudo mount -t ext4 /dev/sda1 /media/logan/3TBHDD

I'm curious as to what exactly "Second HD" is.  That is not standard so I assume you created that as well as the 3TBHDD, is that correct?  Might be why you got the message yesterday that sda1 was already mounted when you tried mounting it elsewhere.  

Note the difference in the output of blkid for sda1 and sdb1.  I don't generally use labels so I'm not sure what to expect.  Your sda1 blkid shows "LABEL="3TBHDD" as well as "PARTLABEL="Second HDD" with different UUIDs for each although it is the same partition.  That looks a little odd to me but it might be due to using labels.  Hopefully, someone more familiar with the use of labels on partition will post an explanation.

---

### Post by bobowon on 2016-09-28
right now the computer has not been restarted so its still mounted as it was yesterday. 
I can find it by going to mnt then to look. 
I guess right now what i want is to have it as it is right now all the time. from the sound of it if I reboot the computer I will have to remount the drive?

---

### Post by Bashing-om on 2016-09-28
bobowon; Morning !

Back, You have the most excellent of advise .

OK, the mount point "name" is for your convenience and to aid your long term thought process . That name can be anything you want . The present name " look" is my thought pattern to aid in "looking" at what is contained in sda1 .

If you are happy to keep that name we can continue on and make sda1 a permanent attachment - under that name -  to the file system.
We do this by adding the device's partition, sda1 to the (F)ile (S)ystem (TAB)le - fstab - .

SOP is to make a backup of any file that is to be edited . Bad things are always a possibility . Cheap insurance to make this backup.
```

sudo cp /etc/fstab /etc/fstab-28sep2016

```

Now we edit our operational system file, fstab, to attach the target sda1:
Comments are a good thing here !
Fire up your favorite text editor, here I will use the text editor 'gedit' as the reference .
```

sudo -H gedit /etc/fstab

```
As this is a system file we are editing, this action requires the elevated privileges of "sudo" and as it is a graphical application we isolate to the GUI with the flag "H" . There are other procedures to use a GUI editor to make the addition - I find "sudo -H" to be the more convenient . ( nano being my goto on-the-fly editor ) ( not going into a nano tutorial in this thread ) .

OK, the file is opened and we make the addition.
add these 2 lines ( copy and paste for best results ) :
As we have an uncertainty of the UUID assingment, we will try !
```

# storage device sda1 added to system 28sep2016
UUID=1e1edc16-3486-40df-bcd7-0ec2dad99a91 /mnt/look            ext4    defaults        0       2

```
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- bodhi.zazen -Understanding fstab
save the file and exit back to terminal.

As noted we can not have a file system attached by 2 means, thus we UN-mount what we manually mounted:
```

sudo umount /dev/sda1

```

Error check !
To try your new configuration immediately you have to reload /etc/fstab:
```

sudo mount -a

```
As the old mount no longer exist (umount) we can now do that test:
If they system is not happy, the system will tell so, else there is no return from "mount -a " .

AND like yancek; I am totally confused about the sda1 UUID assignment !  And above my skill level to know . Quite possibly why the CLI sees the file system type different than the GUI; NTFS as apposed to ext4 .

I would truly like to understand the why of the UUID disparagement !
What returns:
```

ls -alh /dev/disk/by-uuid

```
and we get a look at the UUID assignments from a different perspective, see what we can then work out. I do not like sloppy work ; this is indeed a loose end I would prefer was tied up .

[INDENT][INDENT]can we do that ?
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-28
for some reason i am unable to post reply

edit, ok so this reply worked, when i try and post what I want to the page gives me error or tells me the post needs to be at least one character long. but aparently this unimportant reply right now works just fine :(


EditEdit. the drive did not mount, said it could not find the uuid and listed two

mount: can't find UUID=d1d0cf46-958f-4a12-a604-0ac66040648b
mount: can't find UUID=1e1edc16-3486-40df-bcd7-0ec2dad99a91

Editeditedit

the fstab change gave this warning aswell
logan@Media-server:~$ sudo -H gedit /etc/fstab


** (gedit:15984): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

---

### Post by Bashing-om on 2016-09-28
bobowon; Welp;'

I recon we are going to have to address :
> 
/dev/sda1: LABEL="3TBHDD" UUID=[color=red]"0263d081-7f2b-4113-8ec9-24d0c8022e9c"[/color] TYPE="ext4" PARTLABEL="Second HDD" PARTUUID=[color=red]"1e1edc16-3486-40df-bcd7-0ec2dad99a91"[/color]

There should be ONLY one unique UUID to any device !
for example my system:
> 
sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdb2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb3: LABEL="ubie15.10" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
/dev/sdc1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:~$



As your system reports:
> 
mount: can't find UUID=d1d0cf46-958f-4a12-a604-0ac66040648b
mount: can't find UUID=1e1edc16-3486-40df-bcd7-0ec2dad99a91

let's see what the system does see.
At this time we look:
show now the return:
```

ls -alh /dev/disk/by-uuid

```

As a poke and a test we might try the UUID 0263d081-7f2b-4113-8ec9-24d0c8022e9c see if the system will associate this UUID to sda1 ??

[INDENT][INDENT]got my learning cap on
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-28
for some reason I keep getting error when trying to reply with the lines of code that spit out


edit: I am able to take a screenshot and link it [http://pasteboard.co/8EtCQrAjT.png](http://pasteboard.co/8EtCQrAjT.png) 
but for some reason just pasting the code tells me I need at least one character to make a post

---

### Post by Bashing-om on 2016-09-28
bobowon; Hey !

The forum is presently experiencing some glitches and other problems. Please report the issues in posting in the forum :
[https://ubuntuforums.org/showthread.php?t=2331266](https://ubuntuforums.org/showthread.php?t=2331266)


Oweee !! and from that last screen shot .. we have yet a 3rd UUID for a device that is to have only ONE unique identification.
I am going to have to do a lot of homework and learn how these UUIDs are generated and associated .
If there is a rush to get this system operational, I would suggest at this time to wipe that problematic drive and reformat once again to ext4 .

You can try editing into /etc/fstab the alternate UUIDs - one at a time - and see if there is a positive result .
terminal command:
```

sudo mount -a

```
after each edit will tell the tale .

In the meantime. I am going to get my mind cleared and focus on learning the why 3 UUIDs for a single device can possibly occur .

[INDENT][INDENT]wonderful,
[INDENT][INDENT][INDENT]an opportunity to learn
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Dennis N on 2016-09-28
The two UUIDs are expected if the partition table is GPT. First is the file system UUID, the second is the partition UUID. Each can have their own "label" as well. gparted calls the partition labels "names"; the names column in gparted only shows up when viewing gpt disks.

blkid line from this computer which has a GPT partition table:

```
/dev/sda3: LABEL="Xubuntu-1404" UUID="5c45e413-c03f-4174-a028-f8fc5ebb1563" TYPE="ext4" PARTLABEL="Xubuntu-1404" PARTUUID="9ce4e0f3-cb45-4770-96ea-b93e5e3c1bde"

```
/dev/disk/by-uuid shows UUID of the file system (or should).

---

### Post by Bashing-om on 2016-09-28
bobowon; Hey hey ...

Little by little, I am learning and beginning to formulate a new plan of attack .

GPT !!
This sda drive is formatted GPT .. and that is a difference in what I am accustomed to .
Valid to have the 2 UUIDs !
as reference:
> 
blkid
/dev/sda1: UUID="CBB6-24F2" TYPE="vfat" PARTLABEL="EFI SYSTEM PARTITION" PARTUUID="d0d0d110-0a71-4ed6-936a-304969ea36af" 
/dev/sda2: LABEL="SYSTEM" UUID="0a3407de-014b-458b-b5c1-848e92a327a3" TYPE="ext4" PARTLABEL="GNU/LINUX" PARTUUID="98a81274-10f7-40db-872a-03df048df366" 
/dev/sda3: LABEL="DATA" UUID="b411dc99-f0a0-4c87-9e05-184977be8539" TYPE="ext4" PARTLABEL="HOME" PARTUUID="7280201c-fc5d-40f2-a9b2-466611d3d49e" 
/dev/sda4: UUID="f9fe0b69-a280-415d-a03a-a32752370dee" TYPE="swap" PARTLABEL="SWAP" PARTUUID="039b6c1c-7553-4455-9537-1befbc9fbc5b"


So now I ask to see:
```

ls -l /dev/disk/by-label
ls -l /dev/disk/by-partuuid/


```
And we verify what the correct UUID is .

[INDENT][INDENT]it's amazing out here 
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-28
here is those lines[URL="http://pasteboard.co/8G1BVzXka.png"]
http://pasteboard.co/8G1BVzXka.png[/URL]

---

### Post by Bashing-om on 2016-09-28
bobowon; Still;

clear as mud to me.

 for confirmation:
```

ls -alh /dev/disk/by-uuid

```
Of my mind set .
Thus far I have not changed my logic .

[INDENT][INDENT]I can be flexible, however
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-28
here is what that has spit out 

[http://pasteboard.co/8GswrkHD7.png](http://pasteboard.co/8GswrkHD7.png)

---

### Post by Bashing-om on 2016-09-28
bobowon; OK !

I am convinced that I have been in error for the correct UUID to pass from /etc/fstab to the system for sda1 !

From square one, show me - and I do hope that you can paste these now into the thread in code tags -
( my dyslexia !! )
```

mount
ls -al /mnt/
sudo blkid -c /dev/null -o list
cat /etc/fstab

```

And we make the correct edit to /etc/fstab and make sure that the file is in compliance !

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT]do it different
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-28
here is what that vomits up! (the paste worked!)

```
 logan@Media-server:~$ mountsysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4001524k,nr_inodes=1000381,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=804188k,mode=755)
/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=804188k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
logan@Media-server:~$ ls -al /mnt/
total 12
drwxr-xr-x  3 root root 4096 Sep 27 23:30 .
drwxr-xr-x 26 root root 4096 Sep 27 21:32 ..
drwxr-xr-x  2 root root 4096 Sep 27 23:30 look
logan@Media-server:~$ sudo blkid -c /dev/null -o list
[sudo] password for logan: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4    3TBHDD   (not mounted)  0263d081-7f2b-4113-8ec9-24d0c8022e9c
/dev/sdb1  ext4             /              fa25a441-1206-49a1-90d4-a9d4ffc68475
/dev/sdb5  swap             [SWAP]         f3d99380-6007-4c77-a3b3-97dad437238e
logan@Media-server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=fa25a441-1206-49a1-90d4-a9d4ffc68475 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f3d99380-6007-4c77-a3b3-97dad437238e none            swap    sw              0       0
UUID=d1d0cf46-958f-4a12-a604-0ac66040648b /storage ext4 defaults 0 0
# storage device sda1 added to system 28sep2016
UUID=1e1edc16-3486-40df-bcd7-0ec2dad99a91 /mnt/look            ext4    defaults        0       2
logan@Media-server:~$ 


```

---

### Post by yancek on 2016-09-28
> and from that last screen shot .. we have yet a 3rd UUID for a device that is to have only ONE unique identification.

Actually, the UUID shown is the original when it was under /media/logan/3TBHDD:  0263d081-7f2b-4113-24d0c8022e9c.

I think this is the UUID you need so I would comment out the line below as shown with a hash mark at the beginning of the line as shown:

> #UUID=1e1edc16-3486-40df-bcd7-0ec2dad99a91 /mnt/look            ext4    defaults        0       2

and replace it with:

[QUOTE]UUID=0263d081-7f2b-4113-24d0c8022e9c /mnt/look extr defaults 0 2

and if you have problems with that, change the "/mnt/look" part to "/media/logan/3TBHDD"  (without quotes.  Remount after doing this.

[/QUOTE]

---

### Post by Bashing-om on 2016-09-28
bobowon; k ...

Cooking with Crisco !

We edit /etc/fstab:
remove ( or comment out ) the line:
UUID=d1d0cf46-958f-4a12-a604-0ac66040648b /storage ext4 defaults 0 0
as it does not exist on your system and is presently of no value.

And for our adventure in sda1 land .. make :
 UUID=1e1edc16-3486-40df-bcd7-0ec2dad99a91 /mnt/look            ext4    defaults        0       2
to be:
```

UUID= 0263d081-7f2b-4113-8ec9-24d0c8022e9c /mnt/look            ext4    defaults        0       2

```
where we insert the correct UUID !

save the file and exit back to terminal.
and error check :
```

sudo mount -a

```

If all is well, and no error is reported .. 
reboot the system .. and verify that sda1 is now availabale :
```

mount

```

UH Huh ! .. now you have a storage drive at your disposal .

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-09-28
bobowon; k ...

Cooking with Crisco !

We edit /etc/fstab:
remove ( or comment out ) the line:
UUID=d1d0cf46-958f-4a12-a604-0ac66040648b /storage ext4 defaults 0 0
as it does not exist on your system and is presently of no value.

And for our adventure in sda1 land .. make :
 UUID=1e1edc16-3486-40df-bcd7-0ec2dad99a91 /mnt/look            ext4    defaults        0       2
to be:
```

UUID= 0263d081-7f2b-4113-8ec9-24d0c8022e9c /mnt/look            ext4    defaults        0       2

```
where we insert the correct UUID !

save the file and exit back to terminal.
and error check :
```

sudo mount -a

```

If all is well, and no error is reported .. 
reboot the system .. and verify that sda1 is now availabale :
```

mount

```

UH Huh ! .. now you have a storage drive at your disposal .

---

### Post by Bashing-om on 2016-09-28
bobowon; k ...

Cooking with Crisco !

We edit /etc/fstab:
remove ( or comment out ) the line:
UUID=d1d0cf46-958f-4a12-a604-0ac66040648b /storage ext4 defaults 0 0
as it does not exist on your system and is presently of no value.

And for our adventure in sda1 land .. make :
 UUID=1e1edc16-3486-40df-bcd7-0ec2dad99a91 /mnt/look            ext4    defaults        0       2
to be:
```

UUID=0263d081-7f2b-4113-8ec9-24d0c8022e9c /mnt/look            ext4    defaults        0       2

```
where we insert the correct UUID !

save the file and exit back to terminal.
and error check :
```

sudo mount -a

```

If all is well, and no error is reported .. 
reboot the system .. and verify that sda1 is now availabale :
```

mount

```

UH Huh ! .. now you have a storage drive at your disposal .

---

### Post by bobowon on 2016-09-28
after changing fstab uuid stuff i got some warnings, not sure if those are important

also got an error saying ignore entry at line 13 (line 13 is the one with the uuid

```

logan@Media-server:~$ sudo -H gedit /etc/fstab
[sudo] password for logan: 


(gedit:22429): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (gedit:22429): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported


** (gedit:22429): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported


** (gedit:22429): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
logan@Media-server:~$ sudo mount -a
mount: /etc/fstab: parse error: ignore entry at line 13.

```

this is fstab, figure i will post it incase something is wrong here due to previous attempts or something (maybe nothing is wrong and those errors are nothing)

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=fa25a441-1206-49a1-90d4-a9d4ffc68475 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f3d99380-6007-4c77-a3b3-97dad437238e none            swap    sw              0       0
# storage device sda1 added to system 28sep2016
UUID= 0263d081-7f2b-4113-8ec9-24d0c8022e9c /mnt/look            ext4    defaults        0       2

```

---

### Post by Bashing-om on 2016-09-28
bobowon; K !

I see the error !

there is a space between UUID= and 0263d081 .
remove the space such that:
UUID=0263d081-7f2b-4113-8ec9-24d0c8022e9c
the file now complies with the exact expected formatting.


[INDENT][INDENT]them there little bitty things
[/INDENT][/INDENT]

---

### Post by bobowon on 2016-09-28
By gosh I think we got it! 

made the edit and restarted the computer and have access to the drive!
all is looking well!

I think that is everything, (i will watch the forum for just a little longer just incase you have anything else to add) 

would like to thank everyone who contributed, especially Bashing-om!

---

### Post by Bashing-om on 2016-09-28
bobowon; Hey ! Outstanding !

I too appreciate all the input from all the fellas ..
Shame was a 5 minute job that took 2 days !
Me mostly look'n for the worst; worrying to protect the back side .
Pleased that it has all worked out and my treppadations were groundless .

Good thing here is that I did pick up/re-enforce a thing or 3 . I do hope you enjoyed the ride.

when you are sure this is all said and done:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

remember, can open a thread anytime there is a question/concern.

[INDENT][INDENT]help is what we - try - to do
[/INDENT][/INDENT]

---

### Post by yancek on 2016-09-28
> there is a space between UUID= and 0263d081

A lesson in precision.  Spaces where there should be none, no space where there should be, an  upper case letter which should be lower case and vice versa are just a  few examples.  Computers are not smart but they are very fast and obedient and will do exactly what we tell them to do and not necessarily what we want them to do. Just  FYI, earlier you showed a directory Second HD.  It's generally bad practice to use spaces in directory and file names, most specifically when you are accessing them from a terminal.  Good job.

---


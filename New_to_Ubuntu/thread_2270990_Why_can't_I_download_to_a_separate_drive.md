---
title: "Why can't I download to a separate drive?"
date: 2015-03-26
forum: New to Ubuntu
---

### Post by Aaron_Corcos on 2015-03-26
I have Ubuntu installed on a 128GB SSD drive.  When I try to download programs and files to my 2TB HDD drive or move programs and files already downloaded on the 128GB SSD to the 2TB HDD, it says "... cannot be copied because you do not have permissions to create it in the destination."  Why is this and is there a way around it?

---

### Post by grahammechanical on 2015-03-26
Is the 2TB drive formatted? What format? Are there folders on the drive? Did you create those folders as an Administrator or as standard user?

If we create a folder as administrator (or root) then we cannot move files into it unless we are working as administrator or we have changed the permissions on that folder to read and write access to that folder.

To illustrate. Use the file manger and select a folder on the SSD. Choose a folder in your home folder, such as Documents. Right click the folder and from the drop down menu select Properties and in the dialog that opens select Permissions. You will see this

> Owner: Me
Access: create and delete files
Group: your user name
Access: Access files
Others
Access: Access files.


Now do the same with the folders on the "TB drive and tell us what you see. If the owner is not "Me" then you, when working as a standard user, which is the way we work in Ubuntu, will not be able to create or delete files in the folder. Which is what we are trying to do when we try to move files into the folder.

If that is the case then as administrator we need to change the permissions of that folder so that "Group" and "Others" can have access to create and delete files. First tell us the situation and then we can tell you what to do about it.

Regards.

---

### Post by Aaron_Corcos on 2015-03-26
I don't believe the 2TB HDD is formatted.  There are folders in it, but I don't know how they were created.  The owner of the 2TB HDD is listed as "root".

---

### Post by sammiev on 2015-03-26
Use gparted to bring the info up from the 2TB HDD and post a screen shot here.

---

### Post by mastablasta on 2015-03-27
> **Aaron_Corcos said:**
>  The owner of the 2TB HDD is listed as "root".

there you have it. it should be your user.

---

### Post by yancek on 2015-03-27
Putting data folders/files on the external should be resolved by changing ownership suggested above but, I'm wondering about what software you are downloading and trying to put on an external data drive.  Software programs usually need to be in a specific location on the system as there are often dependencies they need to access.  Not sure if that's what you were doing?

---

### Post by Aaron_Corcos on 2015-03-28
[ATTACH=CONFIG]260944[/ATTACH]

---

### Post by Vladlenin5000 on 2015-03-28
The extended partition could probably be removed and the other EXT4 partitions expanded to use all of the disk, but that has nothing to do with the permissions. The previous posts should be enough to understand and correct the situation.

---

### Post by Bashing-om on 2015-03-28
Aaron_Corcos; Hello;

Pay attention to what yancek posted.
And as the file format is 'ext4' on that 2nd drive, we can change the ownership from that of 'root'.
To preclude transcription errors, - so we can copy paste that UUID - , please post the output of terminal command:
```

ls -al /media/arlbro

```
we then provide you the explicit command to change that filesystem owner to "you" .
----------------------
Question:
As you say:
> 
I have Ubuntu installed on a 128GB SSD drive.

I would have expected the drive that the operating system is installed onto, to be the 1st device recognized (sda). Here the 2TB HDD is seen as sda . Huh ?
Maybe best to get a different look at the drives from a different perspective:
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-28
[ATTACH=CONFIG]260945[/ATTACH]

---

### Post by Bashing-om on 2015-03-28
Aaron_Corcos; Shucks;

One can not copy/paste from a screen shot. Lacking the response from that requested; I offer:
```

sudo chown -R arlbro:arlbro /media/arlbro/<That_UUID>

```

Still, not known why the 2TB HDD is seen as 'sda' .

[INDENT][INDENT]no big deal
[/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-28
[ATTACH=CONFIG]260948[/ATTACH]

---

### Post by Bashing-om on 2015-03-28
Aaron_Corcos; Hey ;

Can not copy and paste from a screen shot. please use code tag posting the result of:
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

To enable ME to give you the explicit UUID ( <That_UUID> ).

[INDENT][INDENT]not always easy
[INDENT][INDENT][INDENT]being easy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QIII on 2015-03-28
Aaron_Corcos --

You have been asked a couple of times to post back with the results of terminal commands in code tags.  If the tutorial offered is difficult to understand, this may be easier:

1. Highlight text and click the # button in the text box header.  

or

2. Click the # button first, place your cursor between the code tags and type or paste your text.

or 

3.  Type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Aaron_Corcos on 2015-03-28
My bad

```
total 8drwxr-x---+ 2 root root 4096 Mar 28 17:16 .
drwxr-xr-x  3 root root 4096 Mar 25 19:03 ..
```

That is the terminal output of
```
[COLOR=#000000][FONT=Ubuntu Mono]ls -al /media/arlbro[/FONT][/COLOR]
```

---

### Post by Bashing-om on 2015-03-28
Aaron_CorcosAaron_Corcos; Good, We are learning ,

> **Aaron_Corcos said:**
> My bad

```
total 8drwxr-x---+ 2 root root 4096 Mar 28 17:16 .
drwxr-xr-x  3 root root 4096 Mar 25 19:03 ..
```

That is the terminal output of
```
[COLOR=#000000][FONT=Ubuntu Mono]ls -al /media/arlbro[/FONT][/COLOR]
```

In an earlier screen shot the 'ls' command depicted a mounting with the UUID 99af8.......
Now it does not. all I can surmise is that the 2 TB HDD is an external device, and was not connected when that last 'ls -al' command was run.

Re-connect the drive and show us once more the outputs of :
```

sudo fdisk -lu
ls -al /media/arlbro

```
so that I have that UUID mount point in a manner that I can copy and paste back to you for the 'chown' command to effect the change in ownership of the file system.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-28
> **Bashing-om said:**
> Re-connect the drive

How do I do this?

---

### Post by Bashing-om on 2015-03-28
Aaron_Corcos; Hey

> 
How do I do this?


This begs the question, is this an external drive we are talking about ? .. I am only making a surmise as formerly the 'ls' command showed a mountpoint in the directory " /media/arlbro/ :
see your : [http://ubuntuforums.org/attachment.php?attachmentid=260945](http://ubuntuforums.org/attachment.php?attachmentid=260945)

Now it does not .. humm ... so what gives ? ONE possible explanation is that it is an external device .
I am not at your terminal, nor standing behind you; all I can go by is what you relate with the commands that are passed to you.

We are presently trying to find that mountpoint of the 2TB HDD to effect that change in ownership of the contained file system.

Another possible explanation is If this is an internal drive, and is not declared in the config file " /etc/fstab " ( File System Table). Then one can mount that drive from the file manager, such that the mount point then becomes active.
Then provide the outputs of terminal commands:
```

sudo fdisk -lu
ls -al /media/arlbro

```

as you get to know your operating system ->
[INDENT][INDENT][INDENT][INDENT]this is all in the process of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-28
You just said a lot of stuff I don't understand.

---

### Post by Bashing-om on 2015-03-28
Aaron_Corcos; Hey;

This forum also functions as an institution of instruction. Where did I loose you and we continue this little lecture.
Keep in mind, all we are doing here is establishing how and where the 2TB HDD gets mounted. No big deal to see.
Once we know the mount point ( how the file system gets attached to the main operating system) we can then effect that change in ownership.

So my current question is, is this an external hard drive attached to the computer through a USB cable ?
OR
an internal hard drive, that is activated from the file manager ( nautilus ?)
-------------
When the terminal command "ls -al /media/arlbro" is run, we want to see that 2TB HDD identifier (<That_UUID>)
It is a very simple process to change that ownership, all we need is that unique identifier - obtained when the hard drive is attached to the main operating system ( mounted ) . -> " ls -al /media/arlbro " will provide the info when the hard drive is in a mounted condition.

[INDENT][INDENT]none of us were born knowing
[INDENT][INDENT][INDENT]time and effort yields knowledge
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-28
Well, its not an external drive connected through a USB.

---

### Post by Bashing-om on 2015-03-28
Aaron_Corcos; OK;

> **Aaron_Corcos said:**
> Well, its not an external drive connected through a USB.
Then we are looking at it being an internal drive that you physically added - that is not explicitly mounted .
So, from the desktop is there icons in the launcher for additional file systems ? ( I have not used unity in some time) to mount the 2 TB HDD OR perhaps mount it from the file manager ?
In any event mount the 2TB HDD and provide the output of terminal commands:
```

sudo fdisk -lu
ls -al /media/arlbro

```

and I will provide that explict command to change the ownership of the file system on that 2TB HDD .

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-28
The drive is already mounted.

This is the terminal output of that command:
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000be0f9


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  3840038911  1920018432   83  Linux
/dev/sda2      3840040958  3907028991    33494017    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      3840040960  3907028991    33494016   82  Linux swap / Solaris


Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000230fa


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758   250068991   124783617    5  Extended
/dev/sdb5          501760   250068991   124783616   83  Linux


Disk /dev/sdc: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdf1cc55b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sdc2          718848   238642695   118961924    7  HPFS/NTFS/exFAT
/dev/sdc3       238643198   250068991     5712897    5  Extended
/dev/sdc5       238643200   242556927     1956864   83  Linux
/dev/sdc6       242558976   243025919      233472   82  Linux swap / Solaris
/dev/sdc7       243027968   250068991     3520512   83  Linux


Disk /dev/mapper/sda5_crypt: 127.8 GB, 127776325632 bytes
255 heads, 63 sectors/track, 15534 cylinders, total 249563136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table


Disk /dev/mapper/ubuntu--vg-root: 93.5 GB, 93474258944 bytes
255 heads, 63 sectors/track, 11364 cylinders, total 182566912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table


Disk /dev/mapper/ubuntu--vg-swap_1: 34.3 GB, 34301018112 bytes
255 heads, 63 sectors/track, 4170 cylinders, total 66994176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
```

---

### Post by Bashing-om on 2015-03-28
Aaron_Corcos; so far so well.

Confirmed that 'sda' is that 2TB HDD.

Now how about the unique identifier ?
```

ls -al /media/arlbro

```
while 'sda' is mounted.

off this topic:
I do not know what is going on with the encryption:
> 
Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

I would be in remiss if I did not point out a possible problem.

[INDENT][INDENT]small steps, getting there
[/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-28
This is the output:
```
total 8drwxr-x---+ 2 root root 4096 Mar 28 22:00 .
drwxr-xr-x  3 root root 4096 Mar 25 19:03 ..

```

I don't know either what's going on with the encryption.

---

### Post by Bashing-om on 2015-03-28
Aaron_Corcos; And once more .

That last output still does not have 'sda' mounted.
Prior to running the "ls" command, please insure that you have clicked on the device icon such that it is in a mounted condition.
once mounted then run:
```

mount
ls -al /media/arlbro

```
in all these hours, perhaps something has changed ???
the 'mount' command will show what is mounted and where (also)

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]more than 1 way to skin this cat
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-29
[ATTACH=CONFIG]260956[/ATTACH]
This window popped up when I tried to mount the drive.

---

### Post by Bashing-om on 2015-03-29
Aaron_Corcos; Good;

So that drive was mounted, IF at that point you had ran the terminal command:
```

ls -al /media/arlbro

```
we would have that UUID where I am able to copy and paste it into the command to 'chown' .
We are doing good, you are learning.
I do not mean to be difficult - I could from the info provided give you the command  - just much safer to copy that UUID to preclude ME making a typo, and also to KNOW that the drive is mounted when we execute the 'chown' command.

If at any time you do not understand what we are doing and why, please please ask for clarification. It is unwise to ever run a command that you do not understand - under any circumstances.

We have to have that drive mounted, we must have that identifier; and then we can execute the 'chown' of that target file system from "root" to ""you"".

At this time, mount the drive and provide the output of:
```

mount
ls -al /media/arlbro

```
where the 'mount' command lists all available file systems and their mount properties; 'ls' list the List  information  about  the FILEs at that mountpoint. You have access to the manual, it is installed by default on your system . See:
```

man ls
man mount

```Executed from terminal, type q to "quit" out of the manual.
Again, it is no big deal. I hope you have some enjoyment from this learning experience and are not becoming frustrated or confused.

[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-30
Thank you for all of your help.  I really am learning a lot.

This is the terminal output when I copy and pasted the command:
```
arlbro@aaronPC:~$ mount
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdb1 on /boot type ext2 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/home/arlbro/.Private on /home/arlbro type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=9167d4b176da3230,ecryptfs_fnek_sig=802fe8150a9f644f)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=arlbro)
arlbro@aaronPC:~$ ls -al /media/arlbro
```

---

### Post by Bashing-om on 2015-03-30
Aaron_Corcos; Sheeeshhh ...

I do not know what I can say.

Post 7, 10, and 27 have screenshots ( that I can not copy from ) of  'sda1' in a mounted condition. Why can you not provide that same same information from terminal - when 'sda1' is mounted ?

Again, that last output from the "mount" command does not show that 'sda1' is mounted. What is taking place ?
Are you ready to take another step forward in system administration ? I can and will provide the command sequence to explicitly mount 'sda1'  in order to obtain the requested output .

Once I have the UUID in a form I can copy/paste back to you then will I formulate the command to change the ownership of the file system that is on 'sda1' and provide it to you ...That is all we are trying to get done. Simple.

[INDENT][INDENT]nothing to it
[/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-30
Is this what it should look like?

```

total 12
drwxr-x---+  3 root root 4096 Mar 30 15:47 .
drwxr-xr-x   3 root root 4096 Mar 25 19:03 ..
drwxr-xr-x  22 root root 4096 Mar 25 17:39 99af8cd5-6bdb-42ed-b683-2f8de8a4fd77

```

---

### Post by Bashing-om on 2015-03-30
Aaron_Corcos; Yes !

We have lift off !

Now with that partition still mounted (verify)
```

ls -al /media/arlbro

```
that it is still mounted.
Now do terminal command:
```

sudo chown -R arlbro:arlbro /media/arlbro/99af8cd5-6bdb-42ed-b683-2f8de8a4fd77

```
copy and paste this command for best results. That is an uppercase 'r', - linux is case sensitive -.
See; that " 99af8cd5-6bdb-42ed-b683-2f8de8a4fd77 " is " < That_UUID > " .

Now "YOU" arlbro have access to that file system.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Aaron_Corcos on 2015-03-30
That's incredible!  Thank you so much!

---

### Post by Bashing-om on 2015-03-30
Aaron_Corcos; Nawww ..

That's ubuntu !
I am pleased to be of some small amount of help.
I trust you learned a bit, and are just that much more comfortable with this our operating system of choice . 

If this matter is now concluded to your satisfaction ->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

This forum can be your best friend;
[INDENT][INDENT][INDENT]ask and thou shalt be given
[/INDENT][/INDENT][/INDENT]

---

### Post by mytien on 2015-04-09
i also can't I download to a separate drive? why?

---

### Post by Bashing-om on 2015-04-09
mytien; Hello;

No telling ... yet .
Have you read over the thread, and understand what the procedure is to find out the why ?
We need to know
a) the file system on the affected drive
b) the partitioning scheme
c) the access rights to the mount point
d) how you are attempting to access the affected hard drive

[INDENT][INDENT]so a tale will be told
[/INDENT][/INDENT]

---


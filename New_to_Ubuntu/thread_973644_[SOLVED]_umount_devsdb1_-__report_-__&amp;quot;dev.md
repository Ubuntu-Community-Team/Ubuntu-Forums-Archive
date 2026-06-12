---
title: "[SOLVED] umount /dev/sdb1 -  report -  &amp;quot;device is busy&amp;quot;"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-06
Hi Guru's

Didn't know exactly what to put in the Subject line for this, as I'm working on a new learning project here.

My 2nd HD appears under places just fine.
If I click on it, it mounts just fine.
Upon mounting, device appears in /etc/mtab and in the filesystem as /media/disk - which I assume is normal.
This HD2 is formatted as ext3 and used to backup /home from hda.

But, to perform a backup it MUST be MOUNTED FIRST!  OK.....

To perform the backup manually I first mount the 2nd hard drive and am using the following from root.
```
rsync -av --delete /home /media/disk/FullHomeBackup
```
and it works just fine!  Exactly the way I want it to.

My goal is to learn to use Crontab, but FIRST I need to learn how to make sure when I do, my code will be right and that I understand WHY it's right or why it's not too!

But, before I attempt learning Crontab, I need to learn a few more basics.  And I've read until I'm blue in the face and it's going over my head.

Here is the PROBLEM I am currently having.

IF hdb IS mounted I can use ```
umount /dev/sdb1
``` and it unmounts OK UNLESS I manually mounted it using code.
But, before I could mount it using code from terminal, I had to enter it into my /etc/fstab in order for it to be found.

IN /etc/fstab I entered the UUID because trying /dev/sdb1 did not work, also trying /dev/sdb1 /media/disk did not work either.
But using the UUID and saving the /etc/fstab file, THEN I could MOUNT the 2nd hard drive from root.
BUT using umount /dev/sdb1 returns the complaint "device is busy".
Also, when it was mounted from root, it did not appear on the desktop which is no big deal.

My current thought is that I entered the wrong information AFTER the UUID or possibly not enough information in the /etc/fstab?

Currently I know NOTHING at all about Crontab, so I'll have questions about it later.

Yes I have read the man mount, man umount, man fstab, and many others, plus spent several hours on-line as well.  It seems to stick in this thick skull of mine longer if I learn the hard way, but sometimes, I just get stuck and don't know what I'm doing wrong.

I think if someone with 2 hard drives would post their /etc/fstab for me, or possibly a few folks, I could study them and see what differences their are.

Interestingly, my 2nd hard drive added it's own swap file to itself, all I did was format it as ext3 (which I understand is the journalizing type file system), created a single folder on it and have been running the backup (mirror actually) manually each night.

Most of the Ubuntu instructions and tips & techniques I've read are either outdated, because those features are NOT available in Hardy.  EG: getmntent file not found.  That was supposed to fetch the mount point of the 2nd hard drive according to the instructions.  Also something else for setting up a cron that was supposed to be under System was not their and NOT in Synaptic or Add/Remove either.  Then after a couple of hours of looking for it, I found it was a Red Hat or Unix program.  So it shouldn't have been mentioned in an Ubuntu tutorial, unless older versions had it.  Sorry, can't remember what it was, probably a GUI type of Crontab?????  Since that's what I'm trying to learn by this coming weekend.

Thanks for your help!

TTUL
Gary

---

### Post by cmittle on 2008-11-07
That sounds odd.  I used the /dev/sda1 /media/200gdisk method on my fstab and it worked.  Unfortunately I just discovered that my second hard disk went bad so I have removed that entry from my /etc/fstab and will enter it again when I get my replacement disk.  

Out of curiosity why do you want to unmount it?

---

### Post by tarps87 on 2008-11-07
Can you post the output of ```
sudo fdisk -l
```
Also which version of Ubuntu are you using, from your post I am assuming it is Ubuntu 8.04?
How did you format the drive? I should never add partitions to its self.

I have to hard drives on my desktop but am not at home so can not post it, also one has xp on it and will be different.
Here is a link to the Ubuntu wiki on fstab, there are some examples at the bottom:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Kellemora on 2008-11-07
Hi Cmittle

It's not really so much that I want to unmount it.  It HAS to be mounted in order to mirror to it.  But by trying to figure out WHY umount is failing I might learn something from it.

If I mount the 2nd hard drive using the command line, it's not visible on the desktop as it is if I mount it by clicking on the drive in Places/Computer.

If I mount it using Places/Computer the umount command works just fine.  But if I mount it from a command line, then umount fails.
So apparently I'm NOT mounting it correctly.  Which also means the drive is probably running full speed the whole time it's mounted, if mounted from a command line.

My GOAL HERE is to write a crontab that mounts the hard drive, runs the rsync, then unmounts the hard drive after it's done.
I can do rsync just fine from the command line.  But I have to MOUNT the drive manually from Places/Computer first.
And yes I can LEAVE it mounted, but, what IF the power goes out and the computer reboots while I'm gone?  The backup drive won't be mounted when the crontab runs and it will then automatically delete the backup from the crontab, if I understand those directions correctly.  One error = AUTO-DELETE code.

I have NOT asked how to write a crontab file yet!
As always, I will try to learn on my own first.
Then, like now, when I'm stuck and confused, THEN I will ask for help.

I honestly have read everything I can on mounting using Mount and unmounting using Umount, both here on these old forums and on the web.  I'm obviously not picking up something important.

Thanks for responding!

TTUL
Gary

---

### Post by Kellemora on 2008-11-07
Hi Tarps

Yes it's Ubuntu 8.04!

Here is a copy of my fstab, but I've lined out the things I've tried so far.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5ecf8cf3-6da6-4a8c-98fb-03f0795065ce /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1 /media/disk
#Edited above line out, didn't work.
#UUID=d3fbb684-3d1d-4ce3-9bc0-bff0e7400bb3  /  ext3  relatime,errors=remount-ro  0  1
#Edited above line out, didn't work as umount still failed.
#UUID=d3fbb684-3d1d-4ce3-9bc0-bff0e7400bb3  /media/disk  ext3  relatime,noexec  0  1
#Edited above line out, didn't mount, error, no such file.
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

As I mentioned to cmittle above, my eventual goal is to mount drive 2, rsync my /home folder to it, then umount drive 2, by running the commands I'm currently doing manually in crontab.
I have NOT studied crontab YET, but assume the commands used there are going to have to work manually before they will work as a program line in crontab.
My text for performing the backup (mirror) works just as I want it to.  But manually I must mount the 2nd drive before running the rsync commmand.  Using a command line for mounting is where I'm running into difficulty.

From everything I've read, I'm doing it exactly the way it said to do it, but then it won't unmount using umount, says 'device is busy', which to me means it's running doing something.

Here is the printout of blkid if I mount using Places/Computer, meaning manually.
```
root@HPpav753nUbuntu:/home/gary# blkid
/dev/sda1: UUID="5ecf8cf3-6da6-4a8c-98fb-03f0795065ce" TYPE="ext3" LABEL="Ubuntu" 
/dev/sda2: LABEL="CentOS" UUID="b2dfb5d3-7d88-449f-a85a-acd4688d0407" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="Debian" UUID="ff1280a7-eafc-4e70-8868-a1a78a543ac0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="9372c6a8-d6d1-4ce7-8b59-66bd9fdc989c" 
/dev/sdb1: UUID="d3fbb684-3d1d-4ce3-9bc0-bff0e7400bb3" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="965110ea-e71a-4010-a838-4b17ca169a54" 
root@HPpav753nUbuntu:/home/gary# 

```

Added this note through Edit:
The /dev/sdb5 swap, added itself AFTER I did rsync of the /home file from sda1 to sdb1.  The only thing I did was format the whole drive as ext3, then created the folder for the backup and copied (rsync) /home to sdb1.

If I try to mount the disk from the command line, I get that it is NOT found in fstab or mtab.
But if I click on it in Places/Computer it mounts just fine.

So my question here is WHY?????

Why cannot ROOT find it, but Gnome can?????

Does the mount command in Gnome work differently?????

SEE why I'm so confused here!

Please unscramble my headbone, hi hi.......

Thank You

TTUL
Gary

---

### Post by tarps87 on 2008-11-10
I don't yet understand why it wont un mount, as long as there is nothing looking at the drive, things like the shell pointing to the drvie will lock it.
Have you tried mounting it a read only ```
sudo mount -t ext3 -r /dev/sdb1 /mnt
```
then trying to un mount it using umount?
Ubuntu 8.04 should work with UUID's and device names (/dev/sdb1) where as Ubuntu 8.10 wants to use UUID's which is why I asked which version

---

### Post by The Cog on 2008-11-10
It will always report device busy if a running process is in there. I.e if you open a terminal and go **cd /media/200gdisk** then you will not be able to unmount it until that process leaves - **cd /** will do. I am guessing that your backup script process is the one that's in there.

Failing that, **umount -l** (l for lazy) might work - it kind of leaves it half-mounted I think - doesn't fully unmount until whatever is holding it busy releases it.

---

### Post by tarps87 on 2008-11-10
I was assuming that if all the processes using the drive where closed it would 'leave' the drive. Although paying more attention I think you maybe right as the commands are probably being run from the same terminal which may still be looking at the drive.

---

### Post by JohnFH on 2008-11-10
I noticed a couple of errors from your /etc/fstab file:

#UUID=d3fbb684-3d1d-4ce3-9bc0-bff0e7400bb3  /  ext3  relatime,errors=remount-ro  0  1
#Edited above line out, didn't work as umount still failed.

The mountpoint is set to /  - set it to something like /media/BackupDisk and make sure /media/BackupDisk directory exists.

#UUID=d3fbb684-3d1d-4ce3-9bc0-bff0e7400bb3  /media/disk  ext3  relatime,noexec  0  1
#Edited above line out, didn't mount, error, no such file.

Does /media/disk actually exist before mounting?

Write a script when combines the commands - mount, rsync, unmount, whatever.  Run the script from the command line and edit the script when problems occur.  That way you won't forget the commands for next time.

---

### Post by The Cog on 2008-11-10
What I had in mind what that maybe your backup script was doing something like:
> cd /media/disk/FullHomeBackup
rsync blah blah blah
umount /media/disk/FullHomeBackup
in which case the backup script is still alive with the backup disk as its "current" directory.

If that's not it, then running lsof > lsof.txt might help figure out what process has what files open.

---

### Post by Kellemora on 2008-11-10
Hi Guys

Thanks for responding.........

Here is what I have.  BEFORE I mount the second hard drive from the command line, it appears under Places/Computer.  If I mount it from Places/Computer it appears on the desktop and can be unmounted using umount /dev/sdb1 from the command line.

However, if I mount it from the command line using /mount /dev/sdb1 it does mount, but disappears from Places/Computer
If I try to unmount using umount /dev/sdb1 it says it's BUSY.

```
root@HPpav753nUbuntu:/home/gary# umount /dev/sdb1
umount: /: device is busy
umount: /: device is busy
root@HPpav753nUbuntu:/home/gary# 
```

I did find an error in my fstab, that last #1 needed to be a #2

I've got the drive mounted and have no way of unmounting it?
Except for rebooting.

If ALL I did was type in terminal

```
mount /dev/sdb1
```

and it Mounted, WHAT is making it BUSY?

For John:  No /media/disk does not appear UNLESS I mount through Places/Computer.  I WANT the mount point to be Root as I will be copying MANY separate files to the Hard Drive.  I really don't want to backup /home because /home has programs in it like /.wine and I only need to backup the Datafiles I have on Drive_C in wine, not all the programs there.
Seems to me that if you MOUNT the ENTIRE hard drive using ROOT at the mount point, ALL contents of that hard drive are available.  I could be wrong, I usually am.

For Cog:  I'm NOT running any scripts at all yet.
If I mount the 2nd hard drive using Places/Computer I can run my Rsync script from the root terminal and it runs perfectly and does what is expected.  But that's JUST rsync NOT mount or umount commands.  By opening from Places/Computer after Rsync is finished, I can then unmount the 2nd HD from the desktop.

I'm afraid if I MOUNT the second hard drive using something like 
mount /dev/sdb1/FullHomeBackup (after I put that in Fstab, then I could not get to /dev/sdb1/FullUSRBackup or /dev/sdb1FullVarBackup or /dev/sdb1/EudoraDataBackupfromWine.
Although I haven't tried that yet.

Unfortunately, I have to shut down and reboot to unlock the 2nd hard drive to give it a try before actually saying, it don't work, hi hi.........

But you guys did give me some more ideas to try here, and I see from the man mount something you said is getting a little clearer here.  Mounting the 2nd HD as ROOT is confusing it with ROOT of which there can only be one ROOT directory on the system.

Thanks!

TTUL
Gary

---

### Post by Kellemora on 2008-11-10
Hi Guys

Man, I thought I was DEAD MEAT here for awhile!
Had absolutely no way to safely shut down the system to reboot.
System Quit was missing both Restart and Quit after using the unmount -l /media/sdb1 commmand......

OK, I made a directory using
mkdir /media/sdb1
I can mount from the command line using
mount /media/sdb1
But if I use the command
umount /media/sdb1
I still get that the device is busy and it won't unmount.

I've just rebooted again and will try a couple of other things.

Just out of curiosity though, does Mounting a 2nd hard drive using the Command Line to do so, cause it to take precedence over the Root hard drive?????

TTUL
Gary

---

### Post by Kellemora on 2008-11-10
Duplicate Post

---

### Post by psusi on 2008-11-10
Do NOT try to mount something over the root.  You need to mount new filesystems into an empty directory.  If there is anything already in the directory, it becomes inaccessible since all references to that directory now go to the newly mounted filesystem.  By mounting the external drive over /, you made the real root filesystem no longer accessible and started using the other drive for everything, which is really, really broken.

---

### Post by JohnFH on 2008-11-10
When you mount something from /dev/ directory, you are making it available for other programs to access.  So the way to think about it is this:

```
 mount /dev/sdb1 /media/sdb1 
```

means to point the /media/sdb1 directory at the device called /dev/sdb1, so that when you read or write anything under /media/sdb1, you are reading and writing to the device called /dev/sdb1.

It doesn't matter what the mountpoint is, you still have access to the complete device.

Try the following:

1. Create the directory /media/backup
2. Edit your entry in /etc/fstab to be something like:
UUID=.... /media/backup /dev/sdb1 ....
3. Type:  mount -a
4. Now check that /media/backup/ contains your backup disk
5. Run your rsync backup utility
6. Umount the backup drive:  umount /dev/sdb1

Hope that helps.

---

### Post by JohnFH on 2008-11-10
> **Kellemora said:**
> Hi Guys

OK, I made a directory using
mkdir /media/sdb1
I can mount from the command line using
mount /media/sdb1
But if I use the command
umount /media/sdb1
I still get that the device is busy and it won't unmount.

TTUL
Gary

If you still have this problem, could you show the contents of /etc/mtab before and after mounting.

The file /etc/mtab shows the current mounts with the options used to create each one.  Very useful when you're not sure what device is mounted where.

---

### Post by Kellemora on 2008-11-10
Hi John

Here is a copy of my amended fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5ecf8cf3-6da6-4a8c-98fb-03f0795065ce /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1 /media/disk
#Edited above line out, didn't work.
   UUID=d3fbb684-3d1d-4ce3-9bc0-bff0e7400bb3  /media/sdb1  ext3  relatime,errors=remount-ro  0  2
#Above line causes disk to mount at boot up.
#Edited above line out, didn't work as umount still failed.
#UUID=d3fbb684-3d1d-4ce3-9bc0-bff0e7400bb3  /media/disk  ext3  relatime,noexec  0  2
#Edited above line out, didn't mount, error, no such file.
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

As you can see I used the UUID for the drive and set the mountpoint to /media/sdb1

What this is doing is Mounting the hard drive upon bootup.
Something I really didn't want to happen!  But I can study the fstab manual again to see how to stop that.

However, thanks to everyone's help it is NOW WORKING as expected.

I CAN (from the root terminal)
umount /media/sdb1
and it unmounts and disappears from the desktop.
I CAN
mount /media/sdb1
and it mounts and reappears on the desktop!  yay!
However, if I do unmount it and try to mount it from Places Computer where it still appears, it says I am not privileged to mount this device.  Whereas before I could.  So it looks like I have to work on setting permissions for that.  Which I should be able to figure out.

Thank you all Very Much!
You got me over the hurdle of where I was stuck!
Now I can get back to learning some more of this stuff.

TTUL
Gary

---

### Post by JohnFH on 2008-11-10
Glad we can help!  

It's refreshing to see someone willing to put the effort into learning, so well done and hope you enjoy it!

Couple of quick pointers (but don't let that stop you from reading the man pages, of course):
- To stop it mounting at startup, include the option 'noauto' in /etc/fstab when mounting.
- About permissions, there are options to handle that as well: user, users, group.

Glad you got it working.

---


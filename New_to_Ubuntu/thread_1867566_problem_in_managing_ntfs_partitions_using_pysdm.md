---
title: "problem in managing ntfs partitions using pysdm"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by vicke4 on 2011-10-23
Hi i installed pysdm to auto mount my ntfs partitions on startup.i used the following link:
[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14]("http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14")

It worked fine for several days.now my problem is all of my ntfs partitions are turned to read only mode.i tried to change it using the above guide but i can't.so please help me how to make the partitions mode to read and write.

---

### Post by TeoBigusGeekus on 2011-10-23
Change the ownership of their mount points
```
sudo chown -R yourusername: /media/mountpoint
```

---

### Post by coffeecat on 2011-10-23
Unfortunately, chowning a NTFS filesystem won't work. NTFS is a Microsoft filesystem.

@vicke4, two things. Post the output of this terminal commmand:

```
cat /etc/fstab
```

You can highlight the output and then right-click -> copy to paste it into your post. This will show us the configurations pysdm has set up and whether they are OK.

Second thing. Are you running 11.10/Oneiric? Some people are reporting that the package ntfs-3g is not installed somehow, or more likely being uninstalled, and NTFS partitions are becoming read-only because of this. The package ntfs-3g in 11.10 includes the utilities formerly provided by ntfsprogs and if you install ntfsprogs in 11.10 this removes ntfs-3g. Perhaps this is something to do with it. I've upgraded two Natty/11.04 systems to 11.10 and I've not had this problem. Whatever - check that you have ntfs-3g installed and, if not, install it.

By the way - pysdm, and other apps in the repositories for automounting ntfs partitions, is out-of-date and unmaintained. Unfortunately, there's no safe substitute for manually editing /etc/fstab, at least until someone develops a GUI app for this.

---

### Post by TeoBigusGeekus on 2011-10-23
> **coffeecat said:**
> Unfortunately, chowning a NTFS filesystem won't work. NTFS is a Microsoft filesystem.


I wasn't talking about the whole filesystem, just the mount point.
Wouldn't it work?

---

### Post by coffeecat on 2011-10-23
> **TeoBigusGeekus said:**
> I wasn't talking about the whole filesystem, just the mount point.
Wouldn't it work?

Unfortunately, no. When you mount a filesystem and chown the mountpoint, this actually chowns the filesystem and not the mountpoint. You can prove this to yourself by creating an internal partition with ext2/3/4 filesystem, creating a mountpoint and then doing "ls -l" before and after mounting and chowning, and then unmounting again. Once the filesystem has been chowned, this overrides the ownership of the mountpoint and shows up in the output of "ls -l". After you unmount the partition, "ls -l" tells you that the mountpoint is owned by root again.

It's a subtle point, but important.

The -R (recursive) option would act on the folders and files within the filesystem, but again wouldn't work with NTFS.

I think I'll have to write a howto! :)

---

### Post by TeoBigusGeekus on 2011-10-23
> **coffeecat said:**
> 
I think I'll have to write a howto! :)
Do it!
Thanks for the info, appreciated.

---

### Post by Morbius1 on 2011-10-23
I hope you don't mind the intrusion but you might also want to post the output of this command as well:
```
sudo blkid -c /dev/null
```Blkid will show you where your partitions are at the moment and you can compare that to fstab to see if they are still pointing to the same device.

Pysdm was written a long time ago and is not maintained ( repackaged but not updated ). It doesn't recognize partitions by UUID but uses the old /dev/sdxy way of identifying partitions and partitions can "flip" unless you specify them by UUID.

---

### Post by vicke4 on 2011-10-23
@cofeecat
Yes i am using 11.10.i checked ntfs-3g is installed.

output of cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid         0  0  
# / was on /dev/sda10 during installation
UUID=0770e53c-47df-49bd-b9a4-dc309c160d74  /            ext4  errors=remount-ro           0  1  
# /home was on /dev/sda11 during installation
UUID=48e299e2-fbcd-47e3-a5c7-f7aa871ea3dd  /home        ext4  defaults                    0  2  
# swap was on /dev/sda8 during installation
UUID=38470f15-f978-4ec8-aa17-cac4d2d80a75  none         swap  defaults                    0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,umask=000     0  0  
/dev/sda1                                  /media/sda1  ntfs  nls=iso8859-1,umask=000     0  0  
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sda5                                  /media/sda5  ntfs  defaults                    0  0  
/dev/sda7                                  /media/sda7  ntfs  defaults                    0  0  
/dev/sda9                                  /media/sda9  ntfs  defaults                    0  0  
/dev/sdb1                                  /media/sdb1  vfat  defaults  
```

@Morbius1 output for sudo blkid -c /dev/null

```
/dev/sda1: LABEL="System Reserved" UUID="5C325D54325D346C" TYPE="ntfs" 
/dev/sda2: LABEL="Windows 7" UUID="445C064F5C063C64" TYPE="ntfs" 
/dev/sda5: LABEL="Photos&Songs" UUID="01CC0E41E0B197E0" TYPE="ntfs" 
/dev/sda6: LABEL="Softwares&Games" UUID="01CBF5B8BA1FE0B0" TYPE="ntfs" 
/dev/sda7: LABEL="Other files" UUID="01CC0E489D1F7360" TYPE="ntfs" 
/dev/sda8: UUID="38470f15-f978-4ec8-aa17-cac4d2d80a75" TYPE="swap" 
/dev/sda9: LABEL="Videos&Movies" UUID="54B00BECB00BD400" TYPE="ntfs" 
/dev/sda10: UUID="0770e53c-47df-49bd-b9a4-dc309c160d74" TYPE="ext4" 
/dev/sda11: UUID="48e299e2-fbcd-47e3-a5c7-f7aa871ea3dd" TYPE="ext4" 
```

Thanks for your replies guys.......

---

### Post by coffeecat on 2011-10-23
@vicke4, I'll wait till Morbius1 has commented on your /etc/fstab. Morbius1's comments on mounting NTFS partitions are always worth taking note of.

---

### Post by Morbius1 on 2011-10-23
@coffeecat, my apologies. I meant to add to not take over your post.

If this is the partition in question:
>  /dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,ro,umask=000  0  0Then it has somehow been reset as read only so edit fstab as root:
```
gksu gedit /etc/fstab
```And remove the "ro," part of that line so that it looks like this:
```
 /dev/sda6 /media/sda6  ntfs  nls=iso8859-1,umask=000  0  0
```Then unmount the partition:
```
sudo umount /media/sda6
```And then run the following command which will test for errors and if there are none mount the partition with the new line so that you don't have to reboot:
```
sudo mount -a
```

---

### Post by coffeecat on 2011-10-23
> **Morbius1 said:**
> @coffeecat, my apologies. I meant to add to not take over your post.

@Morbius1, not at all. I read your posts on NTFS issues with great interest, and it's good when two or more people can work together with an issue. I must admit I totally missed that "ro" on a first read-through, so I'm glad you are involved.

A thought. Do you have any suggestions as to how the OP can get more optimal mount options in those fstab lines? I notice that you often recommend "windows_names" and I've taken this to heart with my own NTFS partitions.

---

### Post by Morbius1 on 2011-10-23
Well, I would make a lot of changes if it were my fstab but I didn't want to confuse the issue. For example I would change the sda6 line to this:
```
 UUID=01CBF5B8BA1FE0B0 /media/Software-Games ntfs defaults,nls=iso8859-1,uid=1000,umask=000,windows_names 0 0
```I'd have to create the /media/Software-Games folder first.

The other thing I would do is mount the the following with a noauto option or at least set them as read only:
> /dev/sda1: LABEL="System Reserved" UUID="5C325D54325D346C" TYPE="ntfs" 
/dev/sda2: LABEL="Windows 7" UUID="445C064F5C063C64" TYPE="ntfs"The "System Reserved" should never be touched and I'm kind of old school when it comes to write access to the partition that the Windows OS lives in.

---

### Post by vicke4 on 2011-10-23
Thank you Morbius1 my problem solved.Now i have one another problem during start up i am seeing following error message

The disk drive for /media/sdb1 is not yet or not present.

continue to wait,or press S to skip mounting or M for manual recovery.

@Morbius1 
can you please tell me how to mount ntfs partitions manually on(editing fstab and creating empty folders in home directory which i did when i was using openSUSE i had never problems with that method)start up instead of using pysdm.

---

### Post by coffeecat on 2011-10-23
> **vicke4 said:**
> 
The disk drive for /media/sdb1 is not yet or not present.

continue to wait,or press S to skip mounting or M for manual recovery.

The partition sdb1 is (or was) a FAT one, and is not present in your blkid output. My guess is that, if you don't have a second hard drive, it was a pendrive that you had plugged in when you ran pysdm, and pysdm simply created fstab entries for everything in sight (including the System Reserved partition - and I 100% agree with Morbius1 about not mounting that.).

The fix is straightforward. Open fstab for editing with:

```
gksu gedit /etc/fstab
```

and remove this line:

```
/dev/sdb1                                  /media/sdb1  vfat  defaults
```

Which doesn't have fields 5 and 6 anyway, unless they were omitted when you pasted fstab into your earlier post.

---

### Post by vicke4 on 2011-10-24
Thanks my problem is solved.is there any alternative and stable software to pysdm to manage NTFS partitions?

---

### Post by coffeecat on 2011-10-24
Not one I'd recommend. They all seem to be unmaintained and buggy, unless Morbius1 knows of one that I've not heard of. There certainly seems to be a gap waiting to be filled here. In the meantime, the only reliable way is to edit /etc/fstab yourself. You may find this useful:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you find editing fstab daunting, don't forget there are many here who can help.

---

### Post by Paddy Landau on 2011-10-24
> **vicke4 said:**
> Thanks my problem is solved.
Please mark the thread as solved.

> **vicke4 said:**
> is there any alternative and stable software to pysdm to manage NTFS partitions?
You can let Ubuntu manage them for you. You really don't need to fiddle with fstab.

Method 1, if you want the partitions automatically mounted when you log in:

[LIST]
[*]Remove the ntfs lines from your fstab.
[*]Start [gconf-editor]("apt:gconf-editor").
[*]apps > nautilus > preferences > media_automount (check the box)
[/LIST]
Method 2, if you want the partitions automatically mounted only when you use them the first time:

[LIST]
[*]Remove the ntfs lines from your fstab.
[*]When you first click on a partition (from Nautilus) after logging in, Nautilus will automatically mount the partition.
[/LIST]

---

### Post by Morbius1 on 2011-10-24
> **coffeecat said:**
> Not one I'd recommend. They all seem to be unmaintained and buggy, unless Morbius1 knows of one that I've not heard of. There certainly seems to be a gap waiting to be filled here.
None of them are reliable or up to date. What someone over at Ubuntu Central Command might want to consider is taking the part of the installer within the "Something Else" option when it asks you where you want to install the OS and make that a stand alone application. 

It gives you a list of your partitions and asks you what you want to do with them. For all these non system disks it will basically ask you 3 questions:

Where is the partition?
How is it currently formatted?
And Where do you want to mount it?

It then uses a series of 3 templates each one dependent on how the partition is formatted to add entries into fstab so that when the user reboots all these partitions are mounted. It does it by UUID. It does it so that all local users have access ( for ntfs and fat32 ). It does it with a fairly usable set of options. 

Also, The only problem with not having entries in fstab is that the default mount allows access only to that user so something like "umask=000" isn't possible. It also has no idea what "windows_names" is. In fact you won't find that in "man mount" either. :wink:

---

### Post by SPARTAN-118 on 2011-10-29
> **Paddy Landau said:**
> Please mark the thread as solved.


You can let Ubuntu manage them for you. You really don't need to fiddle with fstab.

Method 1, if you want the partitions automatically mounted when you log in:

[LIST]
[*]Remove the ntfs lines from your fstab.
[*]Start [gconf-editor]("apt:gconf-editor").
[*]apps > nautilus > preferences > media_automount (check the box)
[/LIST]
Method 2, if you want the partitions automatically mounted only when you use them the first time:

[LIST]
[*]Remove the ntfs lines from your fstab.
[*]When you first click on a partition (from Nautilus) after logging in, Nautilus will automatically mount the partition.
[/LIST]

In my Oneiric Ocelot install, there is not "media_automount" in nautilus preferences, only "media_autorun_x_content[_ignore/_open_folder/_start_app]". I'm using GNOME 3. MountManager and pySDM do nothing for me, both say that my media partition for Windows (NTFS) is set to automatically mount at boot, but it's not.

---

### Post by Morbius1 on 2011-10-29
> both say that my media partition for Windows (NTFS) is set to automatically mount at boot, but it's not.There's only one way to find out who's telling the truth:
Post the output of the following command:
```
mount
```While you're in the terminal post the output of these commands so we can also see how to fix it:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```

---

### Post by coffeecat on 2011-10-29
> **SPARTAN-118 said:**
> In my Oneiric Ocelot install, there is not "media_automount" in nautilus preferences, only "media_autorun_x_content[_ignore/_open_folder/_start_app]". I'm using GNOME 3. MountManager and pySDM do nothing for me, both say that my media partition for Windows (NTFS) is set to automatically mount at boot, but it's not.

If you are running Oneiric, all you need to is to click on the NTFS partition in the left "Places" pane of nautilus, and it will automount read-write. That is so long as you haven't used one of the 3rd-party mounting apps that you mention. If you have, you need to look at /etc/fstab to see if mountmanager and/or pysdm have set up things badly.

Also - check that you still have ntfs-3g installed. The package ntfs-3g is installed by default but some people have seen this disappear, perhaps as a result of installing a conflicting package.

---

### Post by SPARTAN-118 on 2011-10-29
[COLOR="Black"]> **coffeecat said:**
> If you are running Oneiric, all you need to is to click on the NTFS partition in the left "Places" pane of nautilus, and it will automount read-write. That is so long as you haven't used one of the 3rd-party mounting apps that you mention. If you have, you need to look at /etc/fstab to see if mountmanager and/or pysdm have set up things badly.

Also - check that you still have ntfs-3g installed. The package ntfs-3g is installed by default but some people have seen this disappear, perhaps as a result of installing a conflicting package.

Wait, hold on a second. I thought "automount" meant "automatically mount partition at startup". I already know how to get Nautilus to mount it, like you said, and I guess it makes sense to call that automount. But what I want to do is to get the partition (/dev/sda2) to automatically be mounted at startup, so I don't have to open Nautilus and click on it before opening, say, Banshee (which doesn't load properly if the partition is not mounted, as my media libraries are on it). Typing in "sudo fdisk -l" gives me this:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70a45faf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   204802047   102400000    7  HPFS/NTFS/exFAT
/dev/sda2   *   204802048   976768064   385983008+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29422942

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   148437594    74217773+  83  Linux
/dev/sdb2       148439038   156300367     3930665    5  Extended
/dev/sdb5       148439040   156300367     3930664   82  Linux swap / Solaris

```

Closer to the top, with the NTFS partitions, I see "Boot" if flagged; however, I have no idea what that means, as I still have to click on it in Nautilus in order to use it (and get Banshee to see it, more importantly). What I find weird is that, none of my Linux partitions have "Boot" flagged.[/COLOR]

---

### Post by coffeecat on 2011-10-29
Yes, the term "automount" is a bit ambiguous. I meant that when you click on a partition in Places the system **auto**matically **mount**s it, rather than you having to mount it manually from the terminal. What you are wanting is for the system to mount your NTFS sda2 partition on bootup. If you look at the discussion earlier in this thread you'll see that Morbius1 and I are of the opinion that all the GUI utilities for achieving this are unreliable in one way or the other. They all write lines in /etc/fstab which is the file the system uses for mounting filesystems on bootup. Unfortunately, it's far more reliable to write your own.

Post the output of:

```
cat /etc/fstab
sudo blkid
```

And we can take it from there. However, one caveat. sda2 looks to be your Windows C: partition. Is that so? If so, imo, bad idea to have it mounted on bootup. For a Windows C: partition, I prefer to mount as and when needed (preferably never) and read from it only, never write except in an emergency. Because Linux uses a different system of permissions from Windows, hidden Windows system files are visible read-write when mounted from Linux and it's possible to accidentally damage your Windows system.

**EDIT**: @Morbius1, oops, sorry, I've only just noticed that you posted after SPARTAN-118 posted and before me. I've had scrolling problems with this laptop today. That's my excuse anyway! :)

---

### Post by coffeecat on 2011-10-29
> **coffeecat said:**
> Yes, the term "automount" is a bit ambiguous. I meant that when you click on a partition in Places the system **auto**matically **mount**s it, rather than you having to mount it manually from the terminal. What you are wanting is for the system to mount your NTFS sda2 partition on bootup. If you look at the discussion earlier in this thread you'll see that Morbius1 and I are of the opinion that all the GUI utilities for achieving this are unreliable in one way or the other. They all write lines in /etc/fstab which is the file the system uses for mounting filesystems on bootup. Unfortunately, it's far more reliable to write your own.

Post the output of:

```
cat /etc/fstab
sudo blkid
```

And we can take it from there. However, one caveat. sda2 looks to be your Windows C: partition. Is that so? If so, imo, bad idea to have it mounted on bootup. For a Windows C: partition, I prefer to mount as and when needed (preferably never) and read from it only, never write except in an emergency. Because Linux uses a different system of permissions from Windows, hidden Windows system files are visible read-write when mounted from Linux and it's possible to accidentally damage your Windows system.

**EDIT**: @Morbius1, oops, sorry, I've only just noticed that you posted after SPARTAN-118 posted and before me. I've had scrolling problems with this laptop today. That's my excuse anyway! :)

---

### Post by SPARTAN-118 on 2011-10-29
No. The C: partition is the smaller one; I gave Windows about 100GB for programs and such, then partitioned the rest of my 500GB hard drive for use with media (ie music, videos, pictures, etc). Linux is installed on an older 80GB drive, with 4GB for swap (I have 2GB of RAM installed) and the rest for everything else.

Anyway, the output for the code you mentioned is:
```
alucai@alucai-desktop:~$ cat /etc/fstab
UUID=2cff5f85-c9a9-46a3-b5a1-19746902aee9 / ext4 defaults 0 1
UUID=d52dcc18-9c7f-4295-8066-c6e6cf962496 swap swap sw 0 0
alucai@alucai-desktop:~$ sudo blkid
[sudo] password for alucai: 
/dev/sda1: UUID="24E8E3EFE8E3BD64" TYPE="ntfs" 
/dev/sda2: LABEL="Matt's Files" UUID="01CC26BB29DD2380" TYPE="ntfs" 
/dev/sdb1: UUID="2cff5f85-c9a9-46a3-b5a1-19746902aee9" TYPE="ext4" 
/dev/sdb5: UUID="d52dcc18-9c7f-4295-8066-c6e6cf962496" TYPE="swap" 

```

@Morbius1
Sorry, didn't see your post until coffecat mentioned it, as I went straight to Page 3 when I saw that I had replies.

The output of the code you gave me is:
```
alucai@alucai-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alucai/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alucai)
alucai@alucai-desktop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="24E8E3EFE8E3BD64" TYPE="ntfs" 
/dev/sda2: LABEL="Matt's Files" UUID="01CC26BB29DD2380" TYPE="ntfs" 
/dev/sdb1: UUID="2cff5f85-c9a9-46a3-b5a1-19746902aee9" TYPE="ext4" 
/dev/sdb5: UUID="d52dcc18-9c7f-4295-8066-c6e6cf962496" TYPE="swap" 

```

I didn't post the "cat /etc/fstab" again, so you can just look up at my response to coffeecat.

By the way, I appreciate the help, both of you.

---

### Post by coffeecat on 2011-10-29
Both MountManager and pySDM are gravely mistaken if they are telling you that sda2 is set to automatically mount at boot. :) This is what I would do. Open a terminal and create a mountpoint:

```
sudo mkdir /media/sda2
```

Normally I prefer a mountpoint with the same name as the partition label, but "Matt's Files" complicates things, so let's keep it simple. Next open /etc/fstab with:

```
gksu gedit /etc/fstab
```

Take care - you have root privileges. Add this line:

```
UUID=01CC26BB29DD2380     /media/sda2     ntfs     defaults,nls=iso8859-1,uid=1000,umask=000,windows_names  0 0
```

Save and close gedit. You can see I've adapted a line Morbius1 posted earlier in this thread. You can now test it with:

```
sudo mount -a
```

If everything is working satisfactorily, that's it. It will be mounted on bootup.

---

### Post by SPARTAN-118 on 2011-10-29
Thanks, I made all the changes, and, after unmounting the partition and killing Banshee, "sudo mount -a" worked fine with no errors (it gave me one before I unmounted it, which, I suppose, was unnecessary, but oh, well).

I can't test it now, as I am busy working on something important, but I will let you know ASAP if the partition mounts at startup.

EDIT: Okay, thanks, that worked perfectly! If I need to make any changes in the future, I'll just edit fstab myself (using a guide to make sure I don't mess up, of course!).

---

### Post by ConfusedButEnthused on 2011-11-06
Thank you.  I was so hoping there was more, however.  

I have a slightly different issue: my start-up hangs on failure to mount of my ntfs partition.  I can mount manually after booting.  My fstab had this entry until I commented it out:

# Windows XP Disk Definition so it will mount on startup:
/dev/sda1   /media/sda1   ntfs  defaults   0   1

This worked in all prior versions.   :-k

---

### Post by Paddy Landau on 2011-11-07
> **ConfusedButEnthused said:**
> ... my start-up hangs on failure to mount of my ntfs partition...
Try using ntfs-3g, and change 1 to 0:
```
/dev/sda1   /media/sda1   ntfs-3g   defaults   0   0
```

---

### Post by SPARTAN-118 on 2011-11-07
Just wanted to say that I switched over to Kubuntu (fresh install, no GNOME or Unity to speak of) and that the instructions you gave me in editing my fstab worked great! The only thing I changed was the mount point (the folder in /media that I mount it to).

The command "mount -a" worked again, and, though KDE doesn't show mounted partitions on the desktop, I'm confident it worked, as Amarok gave me no errors (though I don't know if it would request the partition to be mounted or not if it couldn't find the Collection; I never tested it). 

One thing: 
nothing bad will happen if I keep the exact same options coffeecat used, right?

---

### Post by coffeecat on 2011-11-07
You'll be fine with those options (courtesy of forum member Morbius1!) It doesn't matter which desktop environment you are using - under the hood mounting a partition is the same.

Good luck!

---


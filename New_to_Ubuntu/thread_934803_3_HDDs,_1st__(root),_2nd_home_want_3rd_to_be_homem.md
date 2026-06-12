---
title: "3 HDDs, 1st / (root), 2nd /home want 3rd to be /home/me/Music"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by k3lt01 on 2008-10-01
Hi.

I have 3 hard drives in my desktop 1st 20 gb / (root), 2nd 80 gb /home, and I want the 3rd 200 gb to be /home/michael/Music but it just mounts as a 200gb media. 

While it does go to where I want it even lists in the Places drop down as 200 gb media in the spot is should list as Music.

Is there something about Ubuntu that wont let me have 3 HDDs (or possbly more) and mount them this way? Is there a way, I hate to say it "like Windows", that I can just rename the HDD and it mount as /home/michael/Music and come up that way in Places as well?

Thanks in advance.

---

### Post by Michael.Godawski on 2008-10-01
Have you tried to change the path in the fstab file?

```
 gksudo gedit /etc/fstab
```

---

### Post by k3lt01 on 2008-10-01
> **Michael.Godawski said:**
> Have you tried to change the path in the fstab file?

```
 gksudo gedit /etc/fstab
```
yep and it did nothing

---

### Post by starcannon on 2008-10-01
> **k3lt01 said:**
> Hi.

I have 3 hard drives in my desktop 1st 20 gb / (root), 2nd 80 gb /home, and I want the 3rd 200 gb to be /home/michael/Music but it just mounts as a 200gb media. 

While it does go to where I want it even lists in the Places drop down as 200 gb media in the spot is should list as Music.

Is there something about Ubuntu that wont let me have 3 HDDs (or possbly more) and mount them this way? Is there a way, I hate to say it "like Windows", that I can just rename the HDD and it mount as /home/michael/Music and come up that way in Places as well?

Thanks in advance.
I would just move the /home/michael/Music folder to the 3rd hdd, then middle click drag and drop the folder back into /home/michael and choose "Link Here" from the menu, that should accomplish the task your after with none of the fuss.

GL and have fun.

---

### Post by cariboo on 2008-10-01
You need to add a label to your hard drive, assuming it is formnatted as ext3 you can use e2label:

```
e2label /dev/sdc1 Music 
```

Change the /dev/sdc1 to what you drive actually is. if your drive is formatted as NTFS you need to install ntfs-progs and use ntfslabel to change the label of the drive.

Jim

---

### Post by kpkeerthi on 2008-10-01
> **k3lt01 said:**
> Hi.

I have 3 hard drives in my desktop 1st 20 gb / (root), 2nd 80 gb /home, and I want the 3rd 200 gb to be /home/michael/Music but it just mounts as a 200gb media. 

While it does go to where I want it even lists in the Places drop down as 200 gb media in the spot is should list as Music.

Is there something about Ubuntu that wont let me have 3 HDDs (or possbly more) and mount them this way? Is there a way, I hate to say it "like Windows", that I can just rename the HDD and it mount as /home/michael/Music and come up that way in Places as well?

Thanks in advance.

Your fstab needs a bit of tweaking. Post the output of the below commands:
```
cat /etc/fstab
```
```
sudo blkid
```
```
mount
```
```
sudo fdisk -l
```

---

### Post by vanadium on 2008-10-01
I support the advice of starcannon, which is the cleanest approach. You should work with a symbolic link.

Preferably, you would have the third disk mounted under /mnt. That way, it won't clutter your desktop with a permanent icon (you can still create a launcher if you want an icon).

Then, you would create a symbolic link under your home directory to that volume.

To have it listed in the Places drop down menu, just create a Bookmark to it in Nautilus.

If you post the output of

```

mount
sudo fdisk -l
cat /etc/fstab

```

we can post precise instructions on to how accomplish that (two or three terminal commands).

---

### Post by k3lt01 on 2008-10-01
Thanks everyone for the suggestions and advice, Starcannon and Vanadum especially.

With the advice offered I did some googling and made my own symbolic link using [this link]("http://www.fileformat.info/tip/linux/ln.htm") to help, and got the icon of my screen using the method in [this link]("http://ubuntuforums.org/showthread.php?t=919593&highlight=multiple+hard+drives").

---

### Post by k3lt01 on 2008-10-01
Take most of that last post back,not the thanks though cause I do appreciate the help and I have learned somethings in this process.

here are my outputs
```

michael@michael-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=332a385c-ac07-4dc9-9ec1-fef320977793 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=dacc4da9-1d9b-4399-9e26-539c6a22e25d /home           ext3    relatime        0       2
# /dev/sdc1
UUID=9bad53a3-388a-4fe0-842a-45925bd1636a /home/michael/Music ext3    relatime        0       2
# /dev/sda2
UUID=a31c5493-bb54-412a-8ad8-b0e5d6d2e1c6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

```
michael@michael-desktop:~$ sudo blkid
/dev/sda1: UUID="332a385c-ac07-4dc9-9ec1-fef320977793" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="a31c5493-bb54-412a-8ad8-b0e5d6d2e1c6" 
/dev/sdb1: UUID="dacc4da9-1d9b-4399-9e26-539c6a22e25d" TYPE="ext3" 
/dev/sdc1: UUID="9bad53a3-388a-4fe0-842a-45925bd1636a" TYPE="ext3" LABEL="Music" 
/dev/sdd1: UUID="92201E9D201E887D" LABEL="FreeAgent Drive" TYPE="ntfs" 

```

```
michael@michael-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sdb1 on /home type ext3 (rw,relatime)
/dev/sdc1 on /home/michael/Music type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/sdd1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
```

```
michael@michael-desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe442e442

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2237    17968671   83  Linux
/dev/sda2            2238        2480     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d353cb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0097bdb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401   83  Linux

```

I have reloaded everything, clean install and these are the outputs after the new install. The 200gb media icon is back on the desktop to after the install so I wont get rid of that until I know the Places link reverts to the Music link it should be.

---

### Post by k3lt01 on 2008-10-01
> **starcannon said:**
> I would just move the /home/michael/Music folder to the 3rd hdd, then middle click drag and drop the folder back into /home/michael and choose "Link Here" from the menu, that should accomplish the task your after with none of the fuss.

GL and have fun.It won't let me do this at all, I keep getting told I don't have permissions.



> **cariboo907 said:**
> You need to add a label to your hard drive, assuming it is formnatted as ext3 you can use e2label:

```
e2label /dev/sdc1 Music 
```

Change the /dev/sdc1 to what you drive actually is. if your drive is formatted as NTFS you need to install ntfs-progs and use ntfslabel to change the label of the drive.

JimSame thing, it won't let me do anything because I don't have permissions, even if I sudo it it still wont let me.

---

### Post by vanadium on 2008-10-01
You will now need to clearly restate what the current issue is. I see that your 200 GB volume, sdc1, apparently is successfully mounted under /home/michael/Music. So what is the remaining problem?

You say you did a clean install. However, you also must have edited the /etc/fstab file yourself?

---

### Post by starcannon on 2008-10-01
Not sure how your permissions got hosed up; but assuming that there is nothing on the Music drive yet, I would recommend unmounting it, use gparted to wipe it and reformat to ext3, mount it in mnt to say /mnt/Music, chmod /mnt/Music to your preferred permissions, then sym link it to your ~/ (use the middle click drag drop method its just easy). That should do it, and if I were setting mine up, is exactly how I would do it. 

Theres about a half a dozen ways to skin this cat, I generally tend to lean towards easy and clean.

GL and have fun.

---

### Post by k3lt01 on 2008-10-01
> **vanadium said:**
> You will now need to clearly restate what the current issue is. I see that your 200 GB volume, sdc1, apparently is successfully mounted under /home/michael/Music. So what is the remaining problem? Ok, currently the 200gb hdd shows up in "Places", where it would say "Music" it says 200 gb media. There is also an icon on the desktop for the 200 gb hdd. When I click on "Home" in "Places" it shows a locked "Music" folder. If I open it it says 200gb media in the path box at the top. In the Music/200 gb media folder there is a "lost + found" folder that I can't delete because of permissions. So basically everything is going to the correct place it just shows up wrong and wont let me do anything with it.

> **vanadium said:**
> You say you did a clean install. However, you also must have edited the /etc/fstab file yourself? Yep last night I did a clean install after I had modified things. This was to get to back to square one. The outputs posted in this thread are ***_after_*** the clean install so thats what Ubuntu has done.

Believe it or not, I'm enjoying this challenge :D.

Thanks again for all the help.

---

### Post by DGortze380 on 2008-10-01
> **k3lt01 said:**
> Ok, currently the 200gb hdd shows up in "Places", where it would say "Music" it says 200 gb media. There is also an icon on the desktop for the 200 gb hdd. When I click on "Home" in "Places" it shows a locked "Music" folder. If I open it it says 200gb media in the path box at the top. In the Music/200 gb media folder there is a "lost + found" folder that I can't delete because of permissions. So basically everything is going to the correct place it just shows up wrong and wont let me do anything with it.


You can change all this in fstab. You're going need to set your user as the owner of 200 gb media, set the name to "My Music" (or whatever you want...this is in the "Label" section of the wiki linked below), and set it to mount without a desktop icon. I'll google around because I don't remember the syntax for all those, but they can all be changed in fstab.

EDIT: This should get you started with changing the owner at least.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by k3lt01 on 2008-10-01
I started the desktop up 1/2 an hour ago to see if I could at least change the name from 200 gb media to Music and the thing booted with the name "Music" for the 200 gb hdd. The icon for a hdd is still on the desktop but as "Music", it is "Music" in Places but the icon in Places is still a hdd icon.

Permissions have still not changed.

Is this all happening because it thinks the 200 gb hdd is removable media? So that would be why changing from /media to /mnt will hide it, but will it change permissions?

I have to go out now for while and wont be back till this afternoon, I will work on it when I get back.

---

### Post by vanadium on 2008-10-02
```

The outputs posted in this thread are after the clean install so thats what Ubuntu has done.

```

I just cannot believe that Ubuntu would put this line in /etc/fstab on its own:

```

UUID=9bad53a3-388a-4fe0-842a-45925bd1636a /home/michael/Music ext3    relatime        0       2

```

Anyway, I am learning something new, and that is that your 200BG is a removable disk. Alas, different approaches apply for removable media. 

A removable disk should not be mounted through /etc/fstab. Probably your disk is now mounted twice (I believe this is possible in Linux). It is mounted under $HOME/Music by fstab and under /media/Music by the automatic gnome system HAL (I believe it is).

* Remove the line in /etc/fstab (you can place a # before it or delete it)
* Reboot the system. Your "Music" icon should be on the desktop and in the places menu. The icon is automatically called "Music"because you labeled your external disk properly.
* Delete your $HOME/Music. Replace it by a symbolic link to /media/Music (ln -s /media/Music $HOME)

The only remaining issue you have is a permissions issue. Obviously, as a linusx system administrator, you should know a little bit about permissions, so you can give yourself as a user the necessary permissions. You can change the owner of the /media/Music mount point. Such a mount point is automatically created and remove as the disk is connected/disconnected, but settings are "remembered": "sudo chown $USER:$USER /media/Music". This may only be effective after disconnecting and reconnecting the drive.

---

### Post by k3lt01 on 2008-10-02
> **vanadium said:**
> I just cannot believe that Ubuntu would put this line in /etc/fstab on its own:

```

UUID=9bad53a3-388a-4fe0-842a-45925bd1636a /home/michael/Music ext3    relatime        0       2

```Believe it, this is not an episode of Ripleys Believe it or Not, Ubuntu wrote this in not me.

> **vanadium said:**
> Anyway, I am learning something new, and that is that your 200BG is a removable disk. Alas, different approaches apply for removable media. Lets clarify something here, the 200 gb hdd is not a removable disk, it is an internal drive just like the other two, so it seems everything else you then said, apart from the permissions bit, is irrelevant to my situation.

> **vanadium said:**
> The only remaining issue you have is a permissions issue. Obviously, as a linusx system administrator, you should know a little bit about permissions, so you can give yourself as a user the necessary permissions. You can change the owner of the /media/Music mount point. Such a mount point is automatically created and remove as the disk is connected/disconnected, but settings are "remembered": "sudo chown $USER:$USER /media/Music". This may only be effective after disconnecting and reconnecting the drive.
I'm not a system administrator, this is my desktop pc which basically contains all my stuff. I am learning about Linux and more specifically Ubuntu as I go along and through this forum.

---

### Post by unutbu on 2008-10-02
To set the permission on /home/michael/Music, try
```

sudo chown -R $USER:$USER /home/michael/Music

```
This should make you the owner of all things in /home/michael/Music.

Now for the bad news: There is an open bug related to the manner in which Hardy labels hard drives: 

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/190366](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/190366) 
[http://ubuntuforums.org/showthread.php?t=766167](http://ubuntuforums.org/showthread.php?t=766167)

You many not be able to change it until the bug is fixed.

---

### Post by k3lt01 on 2008-10-02
Thanks Unutbu, and thanks for the info on the bug. I'll go and try the permissions modification now and let post back when its done.

EDIT: Unutbu, your a legend. I have got permissions, I deleted the "Lost + Found" folder and am now copying my music collection to the drive. YAY.

---

### Post by DGortze380 on 2008-10-03
> **k3lt01 said:**
> Thanks Unutbu, and thanks for the info on the bug. I'll go and try the permissions modification now and let post back when its done.

EDIT: Unutbu, your a legend. I have got permissions, I deleted the "Lost + Found" folder and am now copying my music collection to the drive. YAY.

The question now is, does this work after a reboot? My guess is that if you haven't change the owner in fstab (as per the link I posted previously) on reboot the disk will again be owned by root.

---

### Post by k3lt01 on 2008-10-03
> **DGortze380 said:**
> The question now is, does this work after a reboot? My guess is that if you haven't change the owner in fstab (as per the link I posted previously) on reboot the disk will again be owned by root. Yes it works after a reboot.

The only issue now is it has a hdd icon instead of a folder in "Places" and that is described in the link Unutbu posted, and it still thinks the 3rd internal hdd is a removable disk and it shows it as a removable disk in"Places". I hope that will change when I change it from /media to /mnt.

---


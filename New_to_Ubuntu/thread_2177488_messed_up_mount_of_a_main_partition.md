---
title: "messed up mount of a main partition"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by James_Cracknell on 2013-09-28
Hi there, I am a complete newbie with Ubuntu and I had no idea what i was doing when I first insstalled it (which took me 2 days) I think I have mounted a main partition in the wrong place entirely and now I can't seem to get it to show up in the nautilus thingy on the left of the screen (I think that's what it's called?)

Anyway when I go into the terminal and type 'mount' this is what I get:

uboo@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /host type fuseblk (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/uboo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=uboo)
/dev/sdb1 on /media/James Backup type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


Now I'm sure it's the sda3 partition I'm trying to auto-mount at startup so that it shows up in the pane on the left (is that nautilus?) but it won't budge as I've already mounted it wrongly (complete newbie mistake)

What are my options? Would a fresh install of Ubuntu Work after using wubi to uninstall? I'm using Ubuntu 12.04 LTS dualboot with win7

Please Help! - Many Thanks in advance - A Completely Determined Ubuntu Newbie.

---

### Post by deadflowr on 2013-09-28
.
Wubi installs create a virtual disk(a file inside windows) which show up as host in Ubuntu(in wubi).

To access the /host files go to file system and locate host.
You can open it and then bookmark it to the side panel.

---

### Post by James_Cracknell on 2013-09-28
I don't see it there, this is what I get when I go into terminal and type 'dir /host' :

root@ubuntu:~# dir /host
book              PerfLogs               ubuntu
BOOTSECT.BAK          ProgramData               Users
Documents\ and\ Settings  Program\ Files           wamp
END              Program\ Files\ (x86)        Windows
msdia80.dll          Programs               wubildr
MSOCache          Recovery               wubildr.mbr
OEM              $Recycle.Bin
pagefile.sys          System\ Volume\ Information
root@ubuntu:~#

This is also what shows up in the host directory you mentioned, but no 'sda3' or anything similar.

---

### Post by deadflowr on 2013-09-28
It's because sda3 is already mounted.
It's what host(Windows) is.
Mounted partitions will show up as the mountpoint.
So /dev/sda3=/host

And I meant looking in the file manager(nautilus) for  file system.
It's in the side panel.
And then you can add host to the side panel.

---

### Post by TheFu on 2013-09-28
I don't know.

Nautilus mounts are not "real mounts" - so don't trust them to be availble to non-Nautilus programs.  I'm sure I don't understand how nautilus mounts work, just that lots and lots of people have issues when using them for anything non-trivial.  Use the "mount" command or/and /etc/fstab to mount things.

Besides that, I can't tell anything about your machine from the info provided.  
* did you use lvm?
* did you select encryption?
* is this a wubi install?

Also, it would be VERY helpful if you wrapped the output in "code" tags. Use the Adv Reply for a GUI.  It will make things like this easier to read for a volunteer to help.

In the meantime, might I suggest that you seek a local "installfest" to get expert help from locals?  In the last year, many things about installing Linux has become much more complex and doing it on a dual-boot is even harder thanks to secureboot, UEFI, GPT/non-GPT partitions.

The output of **boot-info** (see my signature) would be helpful.

Sorry that I'm not any real help.

---

### Post by James_Cracknell on 2013-09-28
Ok I think I understand, but I managed to get my removable USB drive to show up in the panel and I kind of hoped I Could do that for my C:\ drive.
To make the USB drive automount at boot I used the following commands in the terminal:

[B]sudo blkid
// to get the device ID

[/B][B]sudo mkdir /mnt/James Backup
// to create the directory for the mount

[/B][B]sudo chown uboo /mnt/James Backup
// to take ownership of the directory

[/B]**sudo -i**
[B]nano /etc/fstab

//to open some fstab stuff

//finally added the line:
[/B]UUID=xxxxxxxxxxx /mnt/James Backup ntfs users,defaults 0 0[B]


Rebooted my machine and there it was in the side panel.
I tried the same procedure for the sda3 partition but it didn't work.

Also when I boot up I get the message 'An error occoured while mounting ' /media/system''
Press S to skip or M for manual recovery

Although I dont think this is related.

Also, how do I get the Host directory onto the side panel (I would prefer a nice disk image like the one for my external USB HD but I will settle for this)

[/B]

---

### Post by James_Cracknell on 2013-09-28
Hi there, I'm not sure if I used lvm, I don't think I used encryption and yes it's a wubi install.

Also I know now for future to use the adv reply feature for adding code sections - and I much appreciate the help anyone can provide whether it's practical or otherwise :)

---

### Post by TheFu on 2013-09-28
If this is wubi, I'm completely clueless ... however, parts of the fstab line must be quoted if you insist on having spaces in the path. It is better to remove the spaces.

---

### Post by deadflowr on 2013-09-28
As stated, sda3 is mounted already.
It is host.
Open nautilus go to "file system"
inside file system should be various directories.
Locate host then open it and then bookmark it.

Here
[http://askubuntu.com/questions/113172/how-to-view-windows-files-on-a-wubi-install](http://askubuntu.com/questions/113172/how-to-view-windows-files-on-a-wubi-install)

---


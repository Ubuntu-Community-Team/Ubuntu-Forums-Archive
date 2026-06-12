---
title: "Unable to share folder on disk using Samba -Rights problem?-"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by tassadar2 on 2014-06-30
Hi All,

I've a folder on my user folder that is shared using samba (shared with everyone), and works ok.

I've a secondary 2TB disk formatted with ext4, and a folder on it that I want to share. My problem is that as soon as I share it with Samba (shared with everyone) it un-shares itself automatically. I suspect that it's a problem is caused by the rights on this secondary disk.

I've use chown to take ownership on the disk:

sudo chown -R elhtpc /media/elhtpc/STORE

And I've also try chmod:

sudo chmod -R 777 /media/elhtpc/STORE

Problem persists.

How can I share a folder content on this disk?

Many thanks in advance

---

### Post by Morbius1 on 2014-06-30
You have two problems:
> My problem is that as soon as I share it with Samba (shared with everyone) it un-shares itself automatically.
That's a new one. Are you sure it's un-shared?

Run and post the output of the following commands to see if it has a share definition:
```
testparm -s
```
```
net usershare info --long
```
> I've use chown to take ownership on the disk:
sudo chown -R elhtpc /media/elhtpc/STORE
And I've also try chmod:
sudo chmod -R 777 /media/elhtpc/STORE
Problem persists.
How can I share a folder content on this disk?
The problem is where the shared folder is located. /media/elhtpc is a system created folder controlled by an Access Control List that prevents anyone from getting access to STORE except elhtpc. Doesn't matter what permissions are on STORE itself.

Your best bet is to force all of your samba clients to look like "elhtpc" for your shares. You can put it in the share definition or if all you have are guest accessible shares you can put it in the [global] section of /etc/samba/smb.conf - under the workgroup line:
```
force user = elhtpc
```
Then save smb.conf and restart samba:
```
sudo service smbd restart
```

---

### Post by tassadar2 on 2014-06-30
Many thanks for the answer, morbius1,

At this moment I have no access to this computer, but I will an a pair of hours.

When I say that it unshares the folder I mean that i select to share on the folder properties and accept, then folder icon appears with "share" mark, but one or two seconds later it dissapears.

I don't know why the disk appears as elhtpc property, I used gparted to make disk partition, I mean, I don't know how to avoid it. 

I can't format the whole disk again, it's not a problem, if you tell me how to do it that it will be accesible only for elhtpc user.

Regards

---

### Post by tassadar2 on 2014-07-01
Many thanks again for the help, Morbius1.

I've format disk again with gparted (ext4), so I can't write on disk (as usual), so I made:

```
chmod -R 777 /media/elhtpc/ALMACEN
```

(The actual name is ALMACEN, not STORE). Now I had access from the local machine to write and create folders.

I try to share a folder (right click, properties, share tab, share with samba, allow guests, everyone: full control, elhtpc:full control), and on Rights tab I set "Ohers: Can view and modify content" and check "Apply to subfolders and its contents".

In this moment the folder get the "shared" icon but I can't access to it from Windows machine. Another important thing is that the values I set on share tab seems to dissapear when I press "accept".

I've try to force all of my samba clients to look like "elhtpc" for the shares.  I edit /etc/samba/smb.conf and add "force user = elhtpc" under the workgroup line.

Now I can access to the new shared folder but I have only read rights, not write. If I enter on share tab in folder properties, I set "allow guests, everyone: full control", but when I accept and enter again is changed to "read only".

I've try:
```
sudo chown -R elhtpc /media/elhtpc/ALMACEN
```
But problem persist.


I copy the result of testparm -s

```
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    force user = elhtpc

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


```

This is the output of cat /proc/mounts:

```

rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=1833868k,nr_inodes=458467,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=369760k,mode=755 0 0
/dev/disk/by-uuid/928a3979-d26c-4d5a-96bc-7106314f545c / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
none /sys/fs/cgroup tmpfs rw,relatime,size=4k,mode=755 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /run/user tmpfs rw,nosuid,nodev,noexec,relatime,size=102400k,mode=755 0 0
none /sys/fs/pstore pstore rw,relatime 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,name=systemd 0 0
/dev/sdb1 /media/elhtpc/ALMACEN ext4 rw,nosuid,nodev,relatime,data=ordered 0 0

```

result of cat /etc/mtab | grep ALMACEN

```

/dev/sdb1 /media/elhtpc/ALMACEN ext4 rw,nosuid,nodev,uhelper=udisks2 0 0

```

¿How to get write access?

Many thanks in advance

---

### Post by tassadar2 on 2014-07-01
I've just format the disk using ext3 instead of ext4 and now I can read/write in the disk from the Windows machine.

Am I missing important differentes if I "downgrade" from ext4 to ext3? The disk is going to be used mainly to manage downloads (transmission, jdownloader...) and storing files, films and tv series mainly.

Even with this, I would like to use ext4 if is possible in any way.

Many thanks in advance.

---


---
title: "make self owner of a file"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by quadrplax on 2014-05-14
Ok, I feel really, really stupid right now, but hey, there's no stupid questions according to the rules. I've been googleing for about 15 minutes on how to take ownership of a file, but nothing is working. I would like an EXACT command of how to take ownership of a file root owns from a terminal. My username is "quadrplax" and the file is "start-tor-browser". Thanks for helping me with this extremely simple task. After that I'll save the command in a safe place and make 1,000,000 backups so I never lose it.

---

### Post by SeijiSensei on 2014-05-14
```

sudo chown quadrplax:quadrplax /full/path/to/the/file
sudo chmod u+rw /full/path/to/the/file

```
That makes the owner quadrplax and assigns the file to the quadrplax group.  By default you are the only member of that group, but you can add other users on your machine if you choose.

The second command makes the file **r**eadable and **w**ritable by the **u**ser that owns the file.

---

### Post by DuckHook on 2014-05-14
> **quadrplax said:**
> ...I've been googleing for about 15 minutes on how to take ownership of a file, but nothing is working...You may find [this]("http://www.rackspace.com/knowledge_center/article/linux-file-permission-concepts") link useful.

---

### Post by simplychrislike on 2014-05-14
The file is called "**start**-tor-browser". So maybe you also need to make the file executable.
So now after you're the owner, it's simply this line:
```
chmod u+x /full/path/to/the/file
```

---

### Post by quadrplax on 2014-05-14
```
quadrplax@quadrubuntu:~$ sudo chown quadrplax:quadrplax "/windows/TOR UBUNTU/tor-browser_en-US/start-tor-browser"
chown: changing ownership of '/windows/TOR UBUNTU/tor-browser_en-US/start-tor-browser': Operation not permitted
```

---

### Post by oldos2er on 2014-05-14
Can you give some info about your hard disk partitions and folders? /windows is not a location most people are going to have existing on their systems.

---

### Post by The Cog on 2014-05-14
Agreed. The output of the command **mount** would be very informative.

---

### Post by quadrplax on 2014-05-14
In my signiture: > MY SYSTEM SETUP: I run Ubuntu 14.04 LTS on an HP EliteBook 6930p. I have  Ubuntu installed on a 16GB Flash Drive, as I cannot use the system's  HDD.
"/windows" is a FAT32 4GB partition for files I can use in Windows, and I keep a lot of stuff there for the convenience of access in both operating systems.

Edit: "mount" info:
```

quadrplax@quadrubuntu:~$ mount
/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdb1 on /windows type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=quadrplax)
quadrplax@quadrubuntu:~$ 

```

---

### Post by SeijiSensei on 2014-05-15
Files on vfat volumes have nothing like *nix permissions.  Commands like chmod are meaningless for files on a vfat filesystem.

Is there some reason why that file must reside on the vfat volume?  Why don't you just copy the "TOR UBUNTU" directory over to the regular filesystem, like in your home directory?

---

### Post by quadrplax on 2014-05-15
It works fine in the Ext4, in fact I was made owner automatically, so I'll mark as solved, but is there really no way to own a file in Fat32?

---

### Post by SeijiSensei on 2014-05-15
DOS was a single-user, single-tasking operating system.  There was only one user, the person seated at the console.  File ownerships and permissions only make sense on multi-user systems like *nix and Windows NT derivatives.

If you mount the device as root, you can configure the mount point and mount options to assign ownership of the vfat filesystem to a specific Unix user.  You can do this from [/etc/fstab]("https://help.ubuntu.com/community/Fstab#fat16_and_fat32"); here's an example from that linked document:
```
/dev/hda2 /media/data1 vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```
This directive assigns ownership of the filesystem to the user with uid=1000 (the first user Ubuntu creates) and group 100 ("users").  The umask grants read/write/execute privileges on the filesystem.

USB sticks are usually formatted with FAT32 as a lowest-common-denominator that manufacturers can rely on.  You might consider backing up the files on the device and reformatting it as NTFS or ext4, depending on how you use it.

---


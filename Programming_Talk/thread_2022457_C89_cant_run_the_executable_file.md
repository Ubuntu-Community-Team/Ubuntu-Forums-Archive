---
title: "C89 cant run the executable file"
date: 2012-07-11
forum: Programming Talk
---

### Post by scorpious on 2012-07-11
I've created a simple program using geany. It compiles and builds without hassle. However when I try to run the program I get
```
./geany_run_script.sh: 5: ./testing: Permission denied
```I tried running it through the terminal and get a similar responce
```
bash: ./testing: Permission denied
```and when I double click on the executable file from the file browser I get 
```
There is no application installed for executable files
```I did some googling and tried a few things without any success
```
chmod +x testing.ext
```I also right clicked the file>>properties>>permissions>> and tried to select "Allow executing file as program". However any changes that I make under the permissions tab instantly change back to the original.

NOTE: This is on a separate partion. If i save the .c file onto my Ubuntu partition everything works fine.

---

### Post by the_unforgiven on 2012-07-11
> **scorpious said:**
> I've created a simple program using geany. It compiles and builds without hassle. However when I try to run the program I get
```
./geany_run_script.sh: 5: ./testing: Permission denied
```I tried running it through the terminal and get a similar responce
```
bash: ./testing: Permission denied
```and when I double click on the executable file from the file browser I get 
```
There is no application installed for executable files
```I did some googling and tried a few things without any success
```
chmod +x testing.ext
```I also right clicked the file>>properties>>permissions>> and tried to select "Allow executing file as program". However any changes that I make under the permissions tab instantly change back to the original.

NOTE: This is on a separate partion. If i save the .c file onto my Ubuntu partition everything works fine.

The fact that you cannot set the executable permissions on the file points towards you not having write access to the directory - to modify the directory entry. Does the 'chmod +x ..' command return any error?

Another possibility could be that the filesystem is mounted "noexec" - which will prevent the OS from executing any file in spite of being marked executable.

---

### Post by scorpious on 2012-07-11
yes I'm also thinking that permissions is the problem (I'm currently reading the chown manual to try and adjust the permissions). Using  chmod doesn't return any error but i doesn't appear to do anything else either.
How do i check to see if the partition is mounted "noexec"?

EDIT: the partition in question is NTFS

---

### Post by the_unforgiven on 2012-07-11
> **scorpious said:**
> How do i check to see if the partition is mounted "noexec"?

EDIT: the partition in question is NTFS

Just type "mount" command.
Typical output will look like:
```

proc on /proc type proc (rw,**noexec**,nosuid,nodev)
none on /sys type sysfs (rw,**noexec**,nosuid,nodev)

```

HTH ;)

---

### Post by scorpious on 2012-07-11
Thanks for your help. Here's the output, looks like you were right. I assume its possible to change it so I can execute files?

```
tom@tom-Linux:/media/Storage/Documents/University/ENCE260$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
**proc on /proc type proc (rw,noexec,nosuid,nodev)**
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
/dev/sda6 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

```

---

### Post by the_unforgiven on 2012-07-11
> **scorpious said:**
> Thanks for your help. Here's the output, looks like you were right. I assume its possible to change it so I can execute files?

```
tom@tom-Linux:/media/Storage/Documents/University/ENCE260$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
**proc on /proc type proc (rw,noexec,nosuid,nodev)**
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
/dev/sda6 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

```
No, the one you highlighted is a linux system filesystem - it's got nothing to do with your application being executable or not. It's actually a virtual filesystem generated by kernel.

I presume your application resides on /media/Storage - which is mounted with ntfs-3g?
This is the entry for /media/Storage from the mount output:
```
/dev/sda6 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```
I'm afraid, but permissions model using ntfs-3g is a bit complicated - you can check out the details [here]("http://linux.die.net/man/8/ntfs-3g").

---

### Post by scorpious on 2012-07-11
I'm not sure if its -3g or not. I just know I selected NTFS when creating my partition a while back.

In any case I think it'll easier for a newb like myself to simply save everything into my Ubuntu partition and copy all files over when I've finished working. If I'm feeling brave one day I'll attempt to play with the permissions.

Thanks for your help.

---


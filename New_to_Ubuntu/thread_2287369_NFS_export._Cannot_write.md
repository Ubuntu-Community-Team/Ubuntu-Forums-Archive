---
title: "NFS export. Cannot write"
date: 2015-07-18
forum: New to Ubuntu
---

### Post by quirinovix on 2015-07-18
Hello. I have an export i can't do anything else to try to write. CIFS i write with no problem. Same folder exported as nfs and cifs.

Server:
file /etc/exportfs
/midias *(rw,crossmnt)

ls -la
drwsrwsrwx   2 root root  4096 Jul 18 22:57 midias

Client:
#mount
 //192.168.0.252/midias on /midias/cifs type cifs (rw)
192.168.0.252:/midias on /midias/nfs type nfs (rw,rsize=8192,wsize=8192,soft,sloppy,vers=4,addr=192.168.0.252,clientaddr=192.168.0.1)

file auto.master
/midias        /etc/auto.midias    --ghost

file /etc/auto.midias
nfs    -rsize=8192,wsize=8192,soft,timeout=30,rw    192.168.0.252:/midias
cifs    -fstype=cifs,rw,noperm,guest,soft,async,noatime    ://192.168.0.252/midias

ls-la
drwxrwxrwx   4 root root     0 Jul 18 22:54 midias




What am i missing?

---

### Post by sandyd on 2015-07-18
Hi, what error are you getting when you attempt to create a file in the mounted folder?

---

### Post by quirinovix on 2015-07-19
xbmc@xbmc:/midias/midias_nfs$ mkdir test
mkdir: cannot create directory ‘test’: Read-only file system

root@xbmc:/midias/midias_nfs# mkdir test
mkdir: cannot create directory ‘test’: Read-only file system

Also can't write through nautilus, can't move.

I had also tried to mount by fstab, command line, same error.

---

### Post by quirinovix on 2015-07-19
I tried to mount the export on another pc and got the same error. Not sure, but looks like the problem is at server side.

---

### Post by SeijiSensei on 2015-07-20
And you're sure it's not the server's drive that is marked read-only?  Have you tried running fsck on the exported partition of the server's drive?

---

### Post by quirinovix on 2015-07-20
I will check when arrive home. But don't believe. I had nothing mounted (yet) at this share (i will mount when the export works rw). The share is a folder at / (/midias).

---

### Post by quirinovix on 2015-07-20
Checked. Not the problem.
The server is a raspberry. Running raspbian. What i have at it:

root@raspberrypi:/home/pi# mount
/dev/root on / type ext4 (rw,noatime,data=ordered)
devtmpfs on /dev type devtmpfs (rw,relatime,size=470416k,nr_inodes=117604,mode=755)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=94944k,mode=755)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run/shm type tmpfs (rw,nosuid,nodev,noexec,relatime,size=189880k)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
/dev/mmcblk0p5 on /boot type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,errors=remount-ro)
nfsd on /proc/fs/nfsd type nfsd (rw,relatime)


Had also tried no_root_squash. Didn't work.

---

### Post by quirinovix on 2015-07-20
Well.

I had mounted a flash drive (ntfs) into folder /midias. Gone to client pc, entered at /midias folder and got to write.
I believe if a mount a ext drive, it will work. Will try tomorow. Now i'm to sleepy to do it and have to work soon.

Anyway, i'd like to know what's going on. (i remember than, through ssh i can write at folder /midias with no problem, also through cifs share).

---

### Post by quirinovix on 2015-07-21
Had changer owner and group (nobody and nogroup). Also didn't work.

---


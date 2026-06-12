---
title: "Move files from ntfs partion to trash in dual boot (Ubuntu 16.04/Windows 7)"
date: 2020-04-10
forum: New to Ubuntu
---

### Post by sebbleroni on 2020-04-10
I am currently setting up my system for dual boot between Ubuntu 16.04 and Windows 7. I already mounted my Windows ntfs filesystem under Ubuntu according to my /etc/fstab file:

```


[...]
#Data
/dev/sda4    /media/data    ntfs    rwxrwxrwx,auto,user,umask=0000,uid=1000    0    0

#Documents
/media/data/[...}Documents    /home/sebb/Documents    none     bind    0    0
[...]

```

Now I have the problem that if I try to move files to the Trash using nautilus, the files do not appear in /media/data/.Trash-1000 as described in various other threads ([https://ubuntuforums.org/showthread.php?t=1499345](https://ubuntuforums.org/showthread.php?t=1499345)). Is there something obviously wrong with my /etc/fstab file? I tried rebooting my system several time, without any success.

Thank you already!

---

### Post by TheFu on 2020-04-10
Yes. This is WAY WRONG.

```
/dev/sda4    /media/data    ntfs    rwxrwxrwx,auto,user,umask=0000,uid=1000    0    0
```
You want:
```
UUID=xxxxxxxxyyyy-xxxxxxxx   /media/data    ntfs    async,big_writes,timeout=2,auto,user,umask=0000    0    0
```

Use **blkid** to get the correct UUID for the device.  device names (sda4) can change. UUIDs or LABELs are much safer.

From the manpage:
```
       user   Allow an ordinary user to mount the filesystem.  The name of the
              mounting  user  is  written  to the mtab file (or to the private
              libmount file in /run/mount on systems without a  regular  mtab)
              so  that  this same user can unmount the filesystem again.  This
              option implies the options noexec,  nosuid,  and  nodev  (unless
              overridden   by  subsequent  options,  as  in  the  option  line
              user,exec,dev,suid).

```

The big_writes option should improve performance 30% or more.

For lurkers, if the drive is a USB connected device, best to use the automounter with some protective options:
*x-systemd.automount,x-systemd.idle-timeout=600s* so the file system is mounted only when used and not mounted the rest of the time.

---

### Post by Morbius1 on 2020-04-10
> /dev/sda4    /media/data    ntfs    rwxrwxrwx,auto,user,umask=0000,uid=1000    0    0
How curious.

I'll admit that I would have bet all of wife's money that wouldn't mount.

I've never seen rwx... in an fstab declaration before.

So I added the same ( almost ) declaration on one of my test systems:
UUID=40F76A4E40B0C5CB /media/data ntfs rwxrwxrwx,auto,user,umask=0000,uid=1000    0    0

And sure enough the darn thing mounts. Who knew.

If I create a file in that folder then delete it it will show up in Trash:
tester@vub1604:~$ ls -al /media/data/.Trash-1000/files | grep sent
-rwxrwxrwx 1 tester root   0 Apr 10 17:08 sent-to-trash

We can get nit-picky about your options:

I would ( and did ) use the UUID number for the partition rather than /dev/sdxy.
I would get rid of the **rwxrwxrwx** just because it doesn't look right.
**auto** is in the  defaults
**umask=000** is the default for ntfs.
**user** will do nothing in the context of this fstab statement. 

But none of that matters. Keep them in or take them out the only one that matters is **uid=1000**.

Anyhoo, the thing mounts as is and trash ends up in trash so there's something else going on here. Maybe it's the bind ...  I'll have a look when I get a chance.

---

### Post by Morbius1 on 2020-04-11
> Maybe it's the bind ...  I'll have a look when I get a chance.         
OK ... I think I finally understand the question now.

If I delete a file I placed in /media/data ( sent-to-trash ) then go to trash:/// in Nautilus I can find it and delete it.

If I delete a file I placed in /home/tester/Documents which is a bind mount to /media/data the file is missing from trash:/// in Nautilus.

It appears to be a bug(?): [https://bugzilla.kernel.org/show_bug.cgi?id=70831](https://bugzilla.kernel.org/show_bug.cgi?id=70831)
It was submitted as a kernel bug but it may be a gnome / gvfs bug.

What I can do however is create a symlink to /media/data from my home directory:
```
ln -s /media/data /home/tester
```
I will have a /home/tester/data directory from which I can send a file ( trashed-from-symlink ) to trash and it shows up in trash:/// in Nautilus:
[ATTACH=CONFIG]285491[/ATTACH]

---

### Post by sebbleroni on 2020-04-13
Thank you for the advice regarding the device names, I changed it to the UUID name. Still, this does not solve my intial problem. Right now, if I try to move something from media/data/.../Documents to trash, nautilus only complains, that it cannot put the file to trash...

---

### Post by sebbleroni on 2020-04-13
> **Morbius1 said:**
> 

What I can do however is create a symlink to /media/data from my home directory:
```
ln -s /media/data /home/tester
```
I will have a /home/tester/data directory from which I can send a file ( trashed-from-symlink ) to trash and it shows up in trash:/// in Nautilus:
[ATTACH=CONFIG]285491[/ATTACH]


Unfortunately this does not work for me. I have edited my fstab according to the answer given above, but the gvfs-trash command fails with the error

```
 
gvfs-trash test.pdf
Error trashing file: Unable to find or create trash directory

```

---

### Post by TheFu on 2020-04-13
```
gvfs-trash sends files or directories to the "Trashcan". This can be a
       different folder depending on where the file is located, and [B]not all
       file systems support this concept[/B]. In the common case that the file
       lives inside a users home directory, the trash folder is
       $XDG_DATA_HOME/Trash.
```

Some trash implementations will not take trash across file systems.

There is a workaround for trash.  Daily, automatic, versioned, backups. Any interest in that?

---


---
title: "Transfering media files from Vista to Xubuntu"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by hallucinario on 2008-06-12
hi there,

been looking through the forums but have had no luck with this problem.

I have a pentium dual core which is running on Vista but i decided to do a dual boot. Xubuntu works fine BUT i can seem to be able to access the vista c: as this is where all my music/photos/videos are.

I just have 1 120gig hard drive that has been partitioned... i have both operating systems on my f:...

How do i access my music/my videos/my pictures on xubuntu?... ive read some instructions but if someone could tell me in plain english it would be much appreciated.
thanks

Dave

---

### Post by Gannon8 on 2008-06-12
Why can't you view it? Is the drive not showing up or is it an error message?

Go into a terminal and type "mount" (no quotes) and press enter. Post what it spits out.
Open a terminal by going to Applications > Accessories > Terminal.

---

### Post by Google Spider on 2008-06-12
Just open "Home" and click c drive (or whatever drive you have your media in)

---

### Post by _sphinx_ on 2008-06-12
ok
I think you should find some post regarding this problem but any way I am going to show you how to mount the c: drive.
first locate your c: drive mostprobably ntfs by 
```

sudo fdisk -l

```
Then make a new directory any where you want preferably in /media/<disk>. I would do this by
```

sudo mkdir /media/disk

```
then mount your drive into that directory. I would do it like
```

sudo mount /dev/sda1 /media/sda1/

```
Replace /dev/sda1 with what you find in your output of fdisk -l. This would mount your directory as read only. If you wanna mount as read write do.
```

sudo mount -w /dev/sda1 /media/sda1/

```

---

### Post by _sphinx_ on 2008-06-12
I think you have to install ntfs-3g before you can do all I have stated above

---

### Post by hallucinario on 2008-06-12
> **Gannon8 said:**
> Why can't you view it? Is the drive not showing up or is it an error message?

Go into a terminal and type "mount" (no quotes) and press enter. Post what it spits out.
Open a terminal by going to Applications > Accessories > Terminal.



thanks heaps for the help.. well this is what it spat out

davidcburrows@davidcburrows-laptop:~$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
davidcburrows@davidcburrows-laptop:~$ 


I tried the mount c: and it spat out

davidcburrows@davidcburrows-laptop:~$ mount c:
mount: can't find c: in /etc/fstab or /etc/mtab
davidcburrows@davidcburrows-laptop:~$ 

Im sooo lost

---

### Post by Gannon8 on 2008-06-12
Your windows partition isn't mounted. Do what _sphinx_ said.

And doesnt ntfs-3g come with ubuntu? I can mount my windows partition without installing it. Or does it have to do with Vista?

---

### Post by _sphinx_ on 2008-06-12
Actually I dont know that it come with ubuntu or not, so I just mentioned it for the sake of mentioning. :P

---

### Post by Gannon8 on 2008-06-12
I dunno. I heard you could only resize a vista partition with the vista partitioner, so I was thinking that it was a filesystem change, and it needed a new driver. I'm still using Windows XP (I like my rights) and I can mount it without installing anything else.

---

### Post by _sphinx_ on 2008-06-12
I don't think so it has anything to with Vista it's just the ntfs partition we care about.

---

### Post by The Cog on 2008-06-12
You should be able to find it in Places. Mine is called "15.8G Media" which is about as unhelpful as you can get, but it's there.
EDIT: That's with Ubuntu. I don't know if Xubuntu has an equivalent.

If you can't find it there, get the output from the command 
```
sudo fdisk -l
```
and post it here.

---

### Post by gn2 on 2008-06-12
Have you tried ntfs-config or pysdm from Synaptic yet?

---

### Post by theZoid on 2008-06-19
> **_sphinx_ said:**
> ok
I think you should find some post regarding this problem but any way I am going to show you how to mount the c: drive.
first locate your c: drive mostprobably ntfs by 
snip....
```

sudo mount /dev/sda1 /media/sda1/
snip.....

```

Here is what I'm getting:

```
john@c90s:~$ sudo mount /dev/sda1 /media/sda1/
fuse: failed to access mountpoint /media/sda1/: No such file or directory
john@c90s:~$
``` 

I just want the vista partition to show up in Thunar file manager.  I've added the following to fstab:

```
/dev/sda1 /media/VistaOS ntfs-3g nls=utf8,umask=0222 0 0
```

and here is my fstab afterwards:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=30bb5cce-d680-492a-9f1c-4eaf93463fca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=becb0b17-454b-4bc1-8df7-b6a9075ff43e /home           ext3    relatime        0       2
# /dev/sda4
UUID=93a506ea-d7f3-430b-8b44-41baa6cd5352 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1 /media/VistaOS ntfs-3g nls=utf8,umask=0222 0 0
```

Xubuntu....question is, how do I get my partitions to show up in Thunar file manager just like Ubuntu?

thanks much !!

---


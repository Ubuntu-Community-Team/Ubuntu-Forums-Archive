---
title: "fstab - make default file permission 755"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by zia.newversion on 2013-09-24
Hi, this is pretty basic stuff and I feel like I should know it already.

I use [FONT=courier new]/etc/fstab[/FONT] to automount ntfs partitions at boot. The pattern I use:

```
# <uuid> <mount-point> <fs-type> <options> <dump> <pass>
UUID="THEUUID0123456789" /media/Data ntfs defaults 0 0
```

It works! But when in terminal, I do [FONT=courier new]ls /media/[/FONT], the directory "Data" has a green background. I'm not sure what that indicates, but I have a hunch that it depends on permissions (or ownership?) If I do [FONT=courier new]stat -c "%a" /media/Data[/FONT], I get 777.
I want default permissions to be 755 or 775. However, that poses a problem because the owner of [FONT=courier new]/media/Data[/FONT] (and its subdirs) is root, and if permission is not 777, I'll have to login as root whenever doing any modifications to the mounted fs. Is it possible to automount with owner=me and permission 755.

In short, I want to remove the annoying green background behind directory name without losing access to [FONT=courier new]/media/Data[/FONT] (and its subdirs) from a non-root user. Is that possible? If yes, how?
(Is it through the "options" argument in fstab?)

---

### Post by spacesamurai2 on 2013-09-24
Yes, your hunch is correct as this is caused by adding 777 perms to a directory.

To answer the second part of your question, yes you can mount it by user so that not root but you are the owner. 
UUID="THEUUID0123456789" /media/Data defaults,uid=1000,rw 0 0

(In this case, you would be uid 1000. You can change this as needed, and can add a gid as well)

---

### Post by ptn107 on 2013-09-24
try this instead:

```
UUID="THEUUID0123456789" /media/Data ntfs auto,uid=1000,gid=1000,umask=0022 0 0
```

umask*[1]* is actually used as the inverse or the permissions you're looking for.  umask=0022 mounts with permissions 0755 or -rwxr-xr-x

fmask is another useful option, but for files only.  dmask is the same but for directories only.  umask controls both that's why we use it.

*[1] [https://wiki.archlinux.org/index.php/NTFS-3G]("https://wiki.archlinux.org/index.php/NTFS-3G")*

---

### Post by zia.newversion on 2013-09-24
Thank you. I'm marking this solved.
I have not yet tested this, though your explanations and references to docs are sufficient, I think. Is there a way to test[FONT=courier new] /etc/fstab[/FONT] without rebooting?

Off-topic questions:
@spacesamurai2: I understand that [FONT=courier new]uid[/FONT] is "User ID", but what is [FONT=courier new]gid[/FONT]?
@ptn107: I like umask. But would [FONT=courier new]rw[/FONT] give 777 permission or everything? Or should it change the permissions now that [FONT=courier new]uid[/FONT] is defined?

---

### Post by JKyleOKC on 2013-09-24
You can "sudo mount -a" to remount without rebooting. It's the standard way to test changes to /etc/fstab, since if it fails the system is still up so you can fix things; a reboot could leave you out in the cold and having to do things with a Live CD and chroot to bet it going again.

The "gid" is Group ID.

No, the "rw" and default permissions are separate although they do interact. If a device is mounted "ro" then giving write permissions won't override the read-only attribute, and if it's "rw" you can still have groups or "others" forbidden to write.

---

### Post by spacesamurai2 on 2013-09-25
Glad you found the answer you are looking for :)

GID stands for Groud ID. Checkout /etc/group for a list.

As for testing fstab, you can always run "sudo mountall" and it should pickup the entires.

---


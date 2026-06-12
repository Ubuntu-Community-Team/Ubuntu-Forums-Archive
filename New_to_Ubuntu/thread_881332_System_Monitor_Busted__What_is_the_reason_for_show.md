---
title: "System Monitor Busted?  What is the reason for showing the same drive twice?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Primaris on 2008-08-05
So why is System Monitor displaying what the attached image is showing?
[[IMG]http://img409.imageshack.us/img409/5051/screenshotpc8.th.jpg[/IMG]](http://img409.imageshack.us/my.php?image=screenshotpc8.jpg)
How do I get rid of the duplicate information, as I find it very, very annoying. 

Plus it will confuse the other users. 

Thank you.

---

### Post by Paqman on 2008-08-05
It's actually supposed to do that in Hardy, although I agree it's confusing. What it's showing is the actual physical device at the top, while the bottom one is a virtual file system called gvfs.

---

### Post by InfinityCircuit on 2008-08-05
This is not a bug.  gvfs, the replacement for gnomevfs, uses fuse to mount volumes as well:

> One of the most significant failings of the old GnomeVFS library is that it doesn't make mountpoints accessible to applications that don't use the library. Back in February, Larsson proposed resolving this problem in GVFS by creating a FUSE bridge. FUSE is a userspace virtual filesystem layer that is implemented at the kernel level. Exposing GVFS mount points through FUSE would make it possible for all applications, including command-line utilities, to access files through GVFS.

"A large problem with gnome-vfs is that applications not specially coded to use gnome-vfs will not be able to read non-local files," wrote Larsson in a February mailing list post. "A nice solution to this would be to use FUSE to let such apps use normal syscalls to access the files. In general its quite tricky to map any URI to a FUSE file, but with the mountpoint + filename setup gvfs uses it is very easy to create a FUSE filesystem that lets you access all the current vfs mounts." 

[http://arstechnica.com/journals/linux.ars/2007/09/28/gnome-2-22-planning-gio-and-gvfs-proposed-for-inclusion](http://arstechnica.com/journals/linux.ars/2007/09/28/gnome-2-22-planning-gio-and-gvfs-proposed-for-inclusion)

---

### Post by Primaris on 2008-08-05
Bug or not it does not make logical sense to have the same hard drive space listed twice. 

So how do I remove one of them from system monitor.

---

### Post by Primaris on 2008-08-10
> **Primaris said:**
> Bug or not it does not make logical sense to have the same hard drive space listed twice. 

So how do I remove one of them from system monitor.


Anybody?  All I would like to do is remove one of these drives from showing in "System Monitor."  Since they are the same drive there is no reason for them to be listed twice and it is causing confusion for the users I'm trying to support.

---

### Post by SunnyRabbiera on 2008-08-10
I dont have a solution, I would just tell everybody not to worry about it as it doesnt take up any room or anything.

---


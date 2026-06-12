---
title: "[SOLVED] CLI - mount command"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-09
What do I use the mount command for?  Any time I insert a disk I have no problem accessing it.  Do I have automount or something?  Where is the configuration file for this feature?

---

### Post by pvsdilhan on 2008-10-09
If you can access disk without a problem then you do not have to worry about this. Just take it easy. :)

---

### Post by Nxion on 2008-10-09
Hope this shead some light on your question:

 	 	**kernel-based automounter for Linux**

 	 Autofs controls the operation of the automount daemons. The automount daemons automatically mount filesystems when they are used and unmount them after a period of inactivity. This is done based on a set of pre-configured maps. 
 The kernel automounter implements an almost complete SunOS style automounter under Linux. Automounter version 4 (autofs4) has to be enabled when compiling the kernel. Debian packaged kernels have it enabled.

---

### Post by jemate18 on 2008-10-10
> **adamogardner said:**
> What do I use the mount command for?  Any time I insert a disk I have no problem accessing it.  Do I have automount or something?  Where is the configuration file for this feature?

mount doesnt have config files....

But you can check out
/etc/fstab

and search the meaning of entries about it.. or you can try to fstab howto on google

Ubuntu by default, when detecting a USB drive, mounts it at /media

---

### Post by adamogardner on 2008-10-10
> **pvsdilhan said:**
> If you can access disk without a problem then you do not have to worry about this. Just take it easy. :)

If I take it easy, then in five years I won't know how to use mount.  My interests compel me anyway.  Learning is how I relax.

---

### Post by Dr Small on 2008-10-10
> **jemate18 said:**
> mount doesnt have config files....

But you can check out
/etc/fstab

and search the meaning of entries about it.. or you can try to fstab howto on google

Ubuntu by default, when detecting a USB drive, mounts it at /media
Mount does have a config file, and you mentioned it.
It is /etc/fstab. If you setup options in it, it directly affects mount.

To the OP:
Generally, mount is used when there is no autmounter present. I use mount to mount my USB thumb-drive, CDROM, DVDROM, etc. If you use Ubuntu, you generally do not have to worry about mounting things manually.

Dr Small

---


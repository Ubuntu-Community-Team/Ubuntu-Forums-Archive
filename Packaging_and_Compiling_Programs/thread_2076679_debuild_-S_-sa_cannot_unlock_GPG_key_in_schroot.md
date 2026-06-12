---
title: "debuild -S -sa cannot unlock GPG key in schroot"
date: 2012-10-26
forum: Packaging and Compiling Programs
---

### Post by Korn on 2012-10-26
Hello,

when running "debuild -S -sa" to create the source files and sign them in Ubuntu 12.04 I only had to enter my passphrase once and then it is automatically used to unlock my private key on future runs of the command.
But on Ubuntu 12.10 in a Ubuntu 12.10 schroot there is this error instead:
```
Enter passphrase: can't connect to `/run/user/korn/keyring-x30g9r/gpg': No such file or directory
gpg: can't connect to `/run/user/korn/keyring-x30g9r/gpg': connect failed
```

I already tried to add /run in the /etc/schroot/buildd/fstab file but it did not work. This is the file:
```
# fstab: static file system information for chroots.
# Note that the mount point will be prefixed by the chroot path
# (CHROOT_PATH)
#
# <file system>	<mount point>	<type>	<options>	<dump>	<pass>
/proc		/proc		none    rw,bind        0       0
/sys		/sys		none    rw,bind        0       0
/dev/pts	/dev/pts	none	rw,bind		0	0
/run		/run		none	rw,bind		0	0
tmpfs		/dev/shm	tmpfs	defaults	0	0
# Mount a large scratch space for the build, so we don't use up
# space on an LVM snapshot of the chroot itself.
/var/lib/sbuild/build	/build	none	rw,bind	0	0
```

---


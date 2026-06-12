---
title: "[quantal] sbuild error: E: 10mount: E: boost::filesystem::create_directory"
date: 2012-10-07
forum: Packaging and Compiling Programs
---

### Post by Korn on 2012-10-07
Hello,

today I created a chroot for quantal i386 on my lucid server.
This is the /etc/schroot/chroot.d/quantal-i386 config:
```
[quantal-i386]
type=directory
directory=/var/chroot/quantal-i386
union-type=aufs
groups=admin
root-groups=sbuild
personality=linux32
```

Now when trying to build a package with sbuild there is this mount error:
```
$ LANG=C sbuild -v -d quantal -c quantal-i386 -A bashare_0.5.0-1~getdeb3.dsc 
W: Group 'admin' not found
W: Group 'admin' not found
E: 10mount: E: boost::filesystem::create_directory: File exists: "/var/lib/schroot/mount/quantal-i386-e46c1f3a-e0ff-46bc-a9be-c70289cf263a/dev/shm"
E: quantal-i386-e46c1f3a-e0ff-46bc-a9be-c70289cf263a: Chroot setup failed: stage=setup-start
Chroot setup failed
E: Attempt to log to nonexistent log stream
Error creating chroot session: skipping bashare
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
Finished at 20121007-2049
Build needed 00:00:00, 0k disc space
```

The warnings about the missing admin group are no problem because they also appear with my precise-i386 schroot. But the sbuild command succeeds with my precise-i386 schroot although the /etc/schroot/chroot.d/precise-i386 is not different:
```
[precise-i386]
type=directory
directory=/var/chroot/precise-i386
union-type=aufs
groups=admin
root-groups=sbuild
personality=linux32
```

The debootstrap for lucid did not include a symlink for quantal so I created it manually:
```
$ ls -la /usr/share/debootstrap/scripts/
total 136
drwxr-xr-x 2 root root 4096 2012-10-07 18:10 .
drwxr-xr-x 3 root root 4096 2012-03-03 11:42 ..
-rw-r--r-- 1 root root 5555 2011-10-25 07:07 breezy
-rw-r--r-- 1 root root 5591 2011-10-25 07:07 dapper
-rw-r--r-- 1 root root 6256 2011-10-25 07:07 edgy
lrwxrwxrwx 1 root root    3 2012-03-03 11:42 etch -> sid
lrwxrwxrwx 1 root root    3 2012-03-03 11:42 etch-m68k -> sid
-rw-r--r-- 1 root root 6376 2011-10-25 07:07 feisty
-rw-r--r-- 1 root root 6990 2011-10-25 07:07 gutsy
lrwxrwxrwx 1 root root    5 2012-03-03 11:42 hardy -> gutsy
-rw-r--r-- 1 root root 7987 2011-10-25 07:07 hoary
-rw-r--r-- 1 root root 5861 2011-10-25 07:07 hoary.buildd
lrwxrwxrwx 1 root root    5 2012-03-03 11:42 intrepid -> gutsy
lrwxrwxrwx 1 root root    5 2012-03-03 11:42 jaunty -> gutsy
lrwxrwxrwx 1 root root    5 2012-03-03 11:42 karmic -> gutsy
lrwxrwxrwx 1 root root    3 2012-03-03 11:42 lenny -> sid
lrwxrwxrwx 1 root root    5 2012-03-03 11:42 lucid -> gutsy
lrwxrwxrwx 1 root root    5 2012-03-03 11:42 maverick -> gutsy
lrwxrwxrwx 1 root root    5 2012-03-03 11:42 natty -> gutsy
lrwxrwxrwx 1 root root    5 2012-03-03 11:42 oneiric -> gutsy
-rw-r--r-- 1 root root 3445 2011-10-25 07:07 potato
lrwxrwxrwx 1 root root    5 2012-03-03 11:42 precise -> gutsy
lrwxrwxrwx 1 root root    5 2012-10-07 18:10 quantal -> gutsy
-rw-r--r-- 1 root root 8422 2011-10-25 07:07 sarge
-rw-r--r-- 1 root root 5706 2011-10-25 07:07 sarge.buildd
-rw-r--r-- 1 root root 5936 2011-10-25 07:07 sarge.fakechroot
-rw-r--r-- 1 root root 6542 2011-10-25 07:07 sid
lrwxrwxrwx 1 root root    3 2012-03-03 11:42 squeeze -> sid
-rw-r--r-- 1 root root 7458 2011-10-25 07:07 warty
-rw-r--r-- 1 root root 5743 2011-10-25 07:07 warty.buildd
-rw-r--r-- 1 root root 7757 2011-10-25 07:07 woody
-rw-r--r-- 1 root root 5743 2011-10-25 07:07 woody.buildd
```

According to people in #ubuntu-motu this should be ok.

So I don't know what is going wrong here. So I ask you for help.

---

### Post by Korn on 2012-10-09
This was the problem:
```
$ ls -la /var/chroot/quantal-i386/dev/shm 
lrwxrwxrwx 1 root root 8 2012-10-07 18:12 /var/chroot/quantal-i386/dev/shm -> /run/shm
$ sudo rm /var/chroot/quantal-i386/dev/shm
```

---


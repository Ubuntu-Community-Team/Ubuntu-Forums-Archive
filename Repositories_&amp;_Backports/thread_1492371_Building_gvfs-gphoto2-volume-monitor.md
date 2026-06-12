---
title: "Building gvfs-gphoto2-volume-monitor"
date: 2010-05-24
forum: Repositories &amp; Backports
---

### Post by Paul Crawford on 2010-05-24
I am trying to build the gvfs-gphoto2-volume-monitor daemon to try out the patch reported here for my Ubuntu 10.04 LTS system as a possible solution to the problems I am having with a Nikon D300s (and others have reported with various other cameras):
[https://bugzilla.gnome.org/show_bug.cgi?id=610261](https://bugzilla.gnome.org/show_bug.cgi?id=610261)
I tried these steps and had some success:
```

apt-get source gvfs
sudo apt-get build-dep gvfs
cd gvfs-1.6.0+git20100414/
./configure 
make

```
But once done, I found the following files called gvfs-gphoto2-volume-monitor in my system:
```

-rwxr-xr-x 1 paul 6.5K 2010-05-24 21:40 /home/paul/Documents/software/gvfs-1.6.0+git20100414/monitor/gphoto2/gvfs-gphoto2-volume-monitor
-rwxr-xr-x 1 paul 128K 2010-05-24 21:40 /home/paul/Documents/software/gvfs-1.6.0+git20100414/monitor/gphoto2/.libs/gvfs-gphoto2-volume-monitor
-rwxr-xr-x 1 root 51K  2010-04-14 10:28 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor

```

Now what worries me is the system-supplied version is 51kB, while I have one at 6.5kB, and a hidden version (in .libs) that is 128kB. How can I have succeeded here? Why did my build produce to executables?

Please note that I have not yet attempted to patch anything, this is purely an attempt to recreate the Ubuntu file. There were only a few warnings during the build, but it just looks wrong. Any help?

---

### Post by u1106 on 2010-05-30
Building software in Debian based systems is always done using the following command:

```
dpkg-buildpackage -rfakeroot -uc -us 
```Does that make a difference? (make sure to start in a clean environment)

---

### Post by u1106 on 2010-05-30
The result will be an installable Debian package. Use

```
dpkg-deb -x
```to investigate what is in the package without actually installing it.

(of course you can find all build products also somewhere in the build tree. But by using the Debian package you are sure only to look at the final result and not any irrelevant intermediate build products)

---


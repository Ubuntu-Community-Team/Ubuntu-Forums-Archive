---
title: "error running pkgsrc bootstrap"
date: 2009-10-07
forum: Packaging and Compiling Programs
---

### Post by J05HYYY on 2009-10-07
hello, I'm trying to bootstrap pkgsrc on ubuntu from source.

(using a new method, downloading the folders directly from the website using FTP rather than downloading the tar. At the end, I will give my complete method and why I deem it to be important as opposed to the "usual" installs.)

./ **_PLEASE SCROLL TO THE BOTTOM_** \.
_______________________________________________________________

It all started when I an error when running the script...

```

./boot-strap: 209: /home/J05HYYY/Desktop/PhatFTP/bootstrap/work/bmake/configure: Permission denied

```

I assume it's because configure doesn't have execute permissions ... but there is a problem.

I can't do "chmod +x configure" because /work/bmake/configure isn't created until the "./bootstrap" script is run.


_________________________________________________________

Heres an example to elaborate on the permissions problem:

If I have a script like this, called permissionsproblem ...
```

#!/bin/sh
echo 'echo "echo #!/bin/sh"' >> thescript.sh
echo 'echo "this the script I want permissions to execute"' > thescript.sh
./thescript.sh
rm thescript.sh

```

... and I run the commands:
```

chmod +x permissionsproblem
sudo ./permissionsproblem

```

... I get the error:
```

./permissionsproblem: 4: ./thescript.sh: Permission denied

```

Instead of the output:
```

This is the script I want permissions to execute

```

... I need to do this without changing the permissionsproblem script's code

---

### Post by J05HYYY on 2009-10-07
never mind ... I opened the boot-strap file and realised it was simply copying another file I downloaded anyway, so all I had to do (while in the pkgsrc directory) was:

```
chmod -R +x
```

although, if anyone can solve the problem above, it would be interesting to see.

________________________________________________________________________________

now im getting this error

```

===> Installing packages
===> running: (cd /home/J05HYYY/Desktop/PhatFTP/pkgtools/bootstrap-mk-files && /home/J05HYYY/Desktop/PhatFTP/bootstrap/work/bin/bmake  -DPKG_PRESERVE MAKECONF=/home/J05HYYY/Desktop/PhatFTP/bootstrap/work/mk.conf install)
bmake: don't know how to make install. Stop

bmake: stopped in /home/J05HYYY/Desktop/PhatFTP/pkgtools/bootstrap-mk-files
===> exited with status 2
aborted.

```

... this was because I downloaded only the bootstrap-mk-files/files directory instead of bootstrap-mk-files, missing the configure script.

_________________________________________________________________________________

I'm now getting this, after failing to install the first time:

```

===> Installing for bootstrap-mk-files-20090807
ERROR: bootstrap-mk-files-20090807 is already installed - perhaps an older version?
ERROR: If so, you may use either of:
ERROR:     - "pkg_delete bootstrap-mk-files-20090807" and "/home/J05HYYY/Desktop/PhatFTP/bootstrap/work/bin/bmake reinstall"
ERROR:       to upgrade properly
ERROR:     - "/home/J05HYYY/Desktop/PhatFTP/bootstrap/work/bin/bmake update" to rebuild the package and all
ERROR:       of its dependencies
ERROR:     - "/home/J05HYYY/Desktop/PhatFTP/bootstrap/work/bin/bmake replace" to replace only the package without
ERROR:       re-linking dependencies, risking various problems.
*** Error code 1

Stop.
bmake: stopped in /home/J05HYYY/Desktop/PhatFTP/pkgtools/bootstrap-mk-files
*** Error code 1

Stop.
bmake: stopped in /home/J05HYYY/Desktop/PhatFTP/pkgtools/bootstrap-mk-files
*** Error code 1

Stop.
bmake: stopped in /home/J05HYYY/Desktop/PhatFTP/pkgtools/bootstrap-mk-files
===> exited with status 1
aborted.

```

but when I run these recommended lines:

```

J05HYYY@J05HYYY-laptop:~/Desktop/PhatFTP$ /home/J05HYYY/Desktop/PhatFTP/bootstrap/work/bin/bmake reinstall 
bmake: don't know how to make reinstall. Stop

bmake: stopped in /home/J05HYYY/Desktop/PhatFTP
J05HYYY@J05HYYY-laptop:~/Desktop/PhatFTP$ /home/J05HYYY/Desktop/PhatFTP/bootstrap/work/bin/bmake updatebmake: don't know how to make update. Stop

bmake: stopped in /home/J05HYYY/Desktop/PhatFTP
J05HYYY@J05HYYY-laptop:~/Desktop/PhatFTP$ /home/J05HYYY/Desktop/PhatFTP/bootstrap/work/bin/bmake replacebmake: don't know how to make replace. Stop

bmake: stopped in /home/J05HYYY/Desktop/PhatFTP

```


They are not there! =(

____________________________________________________________________________

After trying to remove each package unsuccessfully (using make de-install) I decided to delete the directories /usr/pkg/ and /var/db/ which at least brought me back to the previous error after failing to install properly the first time:

```

===> Installing for bootstrap-mk-files-20090807
=> Creating installation directories
cd /home/J05HYYY/Desktop/PhatFTP/bootstrap/work/wrk/pkgtools/bootstrap-mk-files/work/bootstrap-mk-files-20090807 && for file in bsd.* sys.mk; do			 /usr/bin/install -c -o root -g root -m 444 $file /usr/pkg/share/mk/$file;	 done
=> Automatic manual page handling
=> Registering installation for bootstrap-mk-files-20090807
Segmentation fault
*** Error code 139

Stop.
bmake: stopped in /home/J05HYYY/Desktop/PhatFTP/pkgtools/bootstrap-mk-files
*** Error code 1

Stop.
bmake: stopped in /home/J05HYYY/Desktop/PhatFTP/pkgtools/bootstrap-mk-files
*** Error code 1

Stop.
bmake: stopped in /home/J05HYYY/Desktop/PhatFTP/pkgtools/bootstrap-mk-files
===> exited with status 1
aborted.

```

obviously, I will continue to try to fix it, but if anyone has a solution for the previous error ... please share

I will ask this question to the pkgsrc-users mailing list and see how it goes.

______________________________________________________________________________

I got a reply back saying the pkg_install package was updated yesterday to correct the issue. Now I'm getting this:

```

===> Installing for bmake-20090909
=> Creating installation directories
/usr/bin/install -c -s -o root -g root -m 555 /home/joshua/Desktop/PhatFTP/bootstrap/work/wrk/devel/bmake/work/Linux/bmake /usr/pkg/bin
/usr/bin/install -c -o root -g root -m 444 /home/joshua/Desktop/PhatFTP/bootstrap/work/wrk/devel/bmake/work/bmake/bmake.1 /usr/pkg/man/man1
=> Automatic manual page handling
=> Registering installation for bmake-20090909
bmake-20090909 requires installed package bootstrap-mk-files-20090807
===> running: (cd /home/joshua/Desktop/PhatFTP/pkgtools/pkg_install && /home/joshua/Desktop/PhatFTP/bootstrap/work/bin/bmake  -DPKG_PRESERVE MAKECONF=/home/joshua/Desktop/PhatFTP/bootstrap/work/mk.conf install)
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 90: Could not find ../../archivers/bzip2/builtin.mk
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 91: Could not find ../../archivers/libarchive/builtin.mk
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 92: Could not find ../../devel/zlib/builtin.mk
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 93: Could not find ../../security/openssl/builtin.mk
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 95: Malformed conditional (!empty(USE_BUILTIN.openssl:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 102: Malformed conditional (empty(USE_BUILTIN.bzip2:M[yY][eE][sS]) ||  empty(USE_BUILTIN.zlib:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 111: Malformed conditional (empty(USE_BUILTIN.bzip2:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 115: Malformed conditional (empty(USE_BUILTIN.zlib:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 119: Malformed conditional (empty(USE_BUILTIN.libarchive:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 128: Malformed conditional (empty(USE_BUILTIN.bzip2:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 131: Malformed conditional (empty(USE_BUILTIN.zlib:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 134: Malformed conditional (empty(USE_BUILTIN.libarchive:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 140: Malformed conditional (empty(USE_BUILTIN.bzip2:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 143: Malformed conditional (empty(USE_BUILTIN.zlib:M[yY][eE][sS]))
bmake: "/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/Makefile" line 146: Malformed conditional (empty(USE_BUILTIN.libarchive:M[yY][eE][sS]))
bmake: Fatal errors encountered -- cannot continue

bmake: stopped in /home/joshua/Desktop/PhatFTP/pkgtools/pkg_install
===> exited with status 1
aborted.

```

I installed the folders listed after "Could not find ../../blahblahblah"
_____________________________________________________________________________________

now getting

```

===> Extracting for pkg_install-20091008
/bin/cp: cannot stat `/home/joshua/Desktop/PhatFTP/pkgtools/pkg_install/../../net/libfetch/files': No such file or directory
*** Error code 1

Stop.
bmake: stopped in /home/joshua/Desktop/PhatFTP/pkgtools/pkg_install
*** Error code 1

Stop.
bmake: stopped in /home/joshua/Desktop/PhatFTP/pkgtools/pkg_install
===> exited with status 1
aborted.

```

__________________________________________________________________________

again, I downloaded and installed the missing package and finally got

```

===========================================================================

Please remember to add /usr/pkg/bin to your PATH environment variable
and /usr/pkg/man to your MANPATH environment variable, if necessary.

An example mk.conf file with the settings you provided to "bootstrap"
has been created for you. It can be found in:

      /usr/pkg/etc/mk.conf

You can find extensive documentation of the NetBSD Packages Collection
in /home/joshua/Desktop/PhatFTP/doc/pkgsrc.txt.

Hopefully everything is now complete.
Thank you

===========================================================================

```

Usually, you can download the binary files for each package separately, or download the whole pkgsrc tree using a tar file.

My problems with these methods were:

A binary wont work on different machines.
Extracting the whole tar file is ~120MB *note after compilation and installation, this will be more.* from [http://wiki.netbsd.se/How_to_use_pkgsrc_on_Linux](http://wiki.netbsd.se/How_to_use_pkgsrc_on_Linux) ~170MB
A tar file requires a program to extract the files.


By downloading, compiling and installing just the directories required for the bootstrap, it took a total of ~40MB. This is a significant difference in size. The script I wrote should be completely portable as it was written in sh. So it should be good for embedded devices and porting.

... script coming soon, watch this space :)

---

### Post by J05HYYY on 2009-12-04
[READ HERE TO DOWNLOAD AND INSTALL ONLY THE ESSENTIAL PKGSRC FILES REQUIRED FOR THE BOOTSTRAP FROM SOURCE!!!]("http://j05hyyy.cwahi.net/phpBB3/viewtopic.php?f=3&t=4#p6")

... it's from my lonely forum. I haven't tested it recently but it should still work! :)

---


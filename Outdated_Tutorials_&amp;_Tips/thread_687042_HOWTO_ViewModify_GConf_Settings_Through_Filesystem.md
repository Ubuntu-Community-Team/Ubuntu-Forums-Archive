---
title: "HOWTO: View/Modify GConf Settings Through Filesystem"
date: 2008-02-03
forum: Outdated Tutorials &amp; Tips
---

### Post by allquixotic on 2008-02-03
This tip demonstrates how to build and install the program gconf-fs. 

**Introduction**:
As you might have guessed, this allows you to "mount" your GConf settings into the file system. GConf is a core component of GNOME. It is a hierarchical list of program settings. Since using GConf does not constitute programming, many power users take advantage of GConf settings to tweak available options in programs. If you have ever used Windows, then you might know of the Windows Registry; GConf is extremely similar to this concept.

One possible way to view the GConf configuration space is simply as a file system, containing "folders" which are GConf Keys, and "files" which are GConf Settings. A setting has a name and a value, the value usually being a string of some sort -- very much like a plain text file.

One cool thing about GConf-FS is that you can browse the GConf tree using Nautilus, for example. You can also edit settings using any graphical text editor.

GConf-FS can be a blessing to users who want to regularly edit GConf settings. For a one-off setting provided to you in the forums, it's usually sufficient to use the command line tool "gconftool-2" to change the setting. But once you are aware of a dozen or so useful GConf settings, you might want to make it a little more accessible.

This allows neat things like:

1. Tarring your entire GConf tree and sending it to a GNOME-savvy developer, so they can troubleshoot a problem for you
2. Backing up your GConf settings
3. Migrating your GConf settings to another computer
4. Conveniently viewing and editing your GConf settings from your favorite file browser or text editor
5. An alternative to gconftool-2 for changing GConf settings from shell scripts
6. You can use networked filesystems like SAMBA to share your GConf settings with others. With a bit of clever instrumentation (copy on write), you could have two computers sharing the same GConf database simultaneously, for both read and write!
7. Most developers who interact with GConf should be able to find some scenario they'd like to use this for -- e.g. grepping through all your GConf settings using a regex with find and grep
8. Programmers whose language does not have bindings for the GConf API can use Gconf-FS to read/write GConf settings, as long as the language supports standard UNIX file I/O.

**Requirements**:
Packages: libfuse2, fuse-utils, libxml-libxml-perl, libio-string-perl, libfuse-perl, libgnome2-gconf-perl, build-essential.
The most convenient way to install these would be to run from the command line,
**sudo aptitude install libfuse2 fuse-utils libxml-libxml-perl libio-string-perl libfuse-perl libgnome2-gconf-perl build-essential**

**Obtaining the software**:
Grab [GConf-FS-0.02.tar.gz](http://ftp.funet.fi/pub/languages/perl/CPAN/authors/id/L/LS/LSIM/GConf-FS-0.02.tar.gz) .

**Installing the software**:
1. Untar the package:
**tar xvzf GConf-FS-0.02.tar.gz**
from the directory the package is in.
2. Run **perl Makefile.PL**
3. Examine the output of
**perl -V:version**
 for the raw perl version, e.g. 5.8.8 
4. Run the following, replacing 5.8.8 with your actual perl version (it's 5.8.8 in Gutsy Gibbon):
 ```
LDDFLAGS = -shared -L/usr/lib \
LDFLAGS = /usr/lib \
SITELIBEXP = /usr/share/perl/5.8.8 \
SITEARCHEXP = /usr/lib/perl/5.8.8 \
 make && make install
```
5. Create a file with the following script. You can run this script with no arguments to mount your user's GConf tree on /mnt/gconf-(user).

```
#!/bin/bash
export THEDIR=/mnt/gconf-`whoami`
sudo mkdir "$THEDIR"
sudo chown `whoami` "$THEDIR"
sudo chgrp `whoami` "$THEDIR"
sudo chmod 777 "$THEDIR"
detachtty /tmp/detach-gconf-fs-`whoami` /usr/bin/gconf-fs.pl $THEDIR

```

**Note:** You will need to install the **detachtty** package to use this script.

**Backout Instructions:**

If you want to reverse the changes made to your system that were made when you went through this tutorial, perform the following steps:

1. Remove any packages which were not previously installed when you ran the command in the **Requirements** section. **WARNING:** Some of these packages are installed by default on certain spins/versions of Ubuntu, and removing them may be detrimental to your system. For instance, without libfuse2, you will not be able to use ntfs-3g to read/write NTFS partitions!
2. If you created a script in step 5 above, remove it.
3. If you ran the script from step 5, unmount the gconf-FS like this: 
```
sudo umount /mnt/gconf-`whoami`
attachtty /tmp/detach-gconf-fs-`whoami`
^C (press Ctrl+C)

```

This is a fun, mildly useful tool for developers and power users. Enjoy! :D

-Sean

---

### Post by Rurushu on 2008-07-25
That's what I get when I try to run the script:

```
maya@maya-laptop:~/GConf-FS-0.02$ bash gconf-fs.sh
mkdir: cannot create directory `/mnt/gconf-maya': File exists maya@maya-laptop:~/GConf-FS-0.02$ ;;; detachtty: 1217024712: Successfully started

;;; detachtty: 1217024712: Child terminated, exiting

;;; detachtty: 1217024712: exiting
maya@maya-laptop:~/GConf-FS-0.02$ 

```

Nothing mounted in /mnt/gconf-maya/

Any idea how to solve this problem?

---

### Post by Wise Ferret on 2008-09-16
Doesn't work here too. I get an empty folder in /mnt/gconf-myname.

---


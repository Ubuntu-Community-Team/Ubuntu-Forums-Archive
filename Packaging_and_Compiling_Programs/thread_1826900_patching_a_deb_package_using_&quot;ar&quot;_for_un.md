---
title: "patching a deb package using &quot;ar&quot; for unpacking and packing"
date: 2011-08-17
forum: Packaging and Compiling Programs
---

### Post by forumbz on 2011-08-17
I have a deb package provided by an organization. I found that there was bugs in the code(python). Thus,

1. I unpack it with "ar xv abc.deb"
2. unpack tar.gz with "tar zxvf control.tar.gz data.tar.gz"
3. fix bugs (a.py)
4. update md5sum for (a.py)
5. packing control.tar.gz with "tar zcvf control md5sum postinst prerm"
6. packing data.tar.gz with "tar zcvf data.tar.gz usr"
7. make deb with "ar rcv abc_patch.deb debian-binary control.tar.gz data.tar.gz"
8. put abc_patch.deb in my "personal ppa" see [https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

I then apt-get install abc_patch.deb but it raised "size mismatch".

Did I make any mistake in patching the deb package ?

---

### Post by pdwerryhouse on 2011-09-08
Eww. Messy.

The control file has a "Installed-Size" line in it that you will probably have to update, too, although that's going to be painful.

If there aren't any pre- or postinst scripts, you might actually find it easier to use alien to convert it to a tarball, unpack and fix the bug, then repack and convert back to a deb.

Either way, it's still messy.

Or, since it's python, and you've got all the source, maybe try making a new deb package from scratch, perhaps with py2dsc (in python-stdeb).

---

### Post by dodle on 2011-10-02
I've been told that it is not a good idea to use ar for packaging debs. Apparently there are two versions of ar. The one that comes with Ubuntu/Debian is the GNU version. But the one that is built into dpkg is the BSD version and apparently there are small differences in the produced packages. I'm not 100% sure about this, but it is what I have been told. 

This is what I would do: Create a directory to hold the contents of the deb. Unpack the contents of data.tar.gz to the directory. Make a subdirectory called "DEBIAN" and extract the contents of control.tar.gz to the DEBIAN directory. Make your changes then repackage using dpkg. From a terminal navigate to the directory that contains your new directory. So if you placed your directory on the desktop you would navigate to the desktop. Now use the following command to package the deb (I'm doing this from memory so I hope that it is all correct):

```
fakeroot dpkg -b mydirectory
```

---


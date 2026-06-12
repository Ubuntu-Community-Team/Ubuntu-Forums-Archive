---
title: "Applying patches?"
date: 2006-07-28
forum: Packaging and Compiling Programs
---

### Post by mattisking on 2006-07-28
I'm playing around trying to get the latest version of libipoddevice from cvs (0.4.6 - not released yet) but I can't get anywhere in building it. It always fails somewhat cryptically in the ./autogen.sh. I thought maybe there are patches involved... maybe something our developers have done to get things working for Ubuntu. So, using this as an example (but I'd like to know generally as well), how do I apply patches?

$ sudo apt-get build-dep libipoddevice0
$ sudo apt-get source libipoddevice0

At this point I can usually just:
$ ./autogen.sh --prefix=/usr
$ make
$ sudo make install

I can certainly do it with this package, but not from cvs. So, in general, I see there is always (in the apt-get source) directories a "debian" directory that contains a patches directory and a bunch of files like compat, changelog, control, ... etc.

Does following the build process ./configure && make && sudo make install for a package obtained from apt-get source with a debian subdirectory as described apply the patches automatically as part of the configure or make or are the steps to apply the patches done separately before or during the build process? If they aren't done for you using the general process, how do you apply patches? Can they all be applied (there are multiple .patch files in the patches directory) at once or one at a time?

Let's say I got libipodevice0 from apt-get source and then also from CVS... How could I merge the patches from source (assuming they weren't applied upstream) with what I got from CVS? Of course I realize I could manually do it but is there a better/standard way? What utilities need to be used?

Thanks!

Update: I'm finding this thread to be very helpful: [http://www.ubuntuforums.org/showthread.php?t=200762&highlight=applying+patches]("http://www.ubuntuforums.org/showthread.php?t=200762&highlight=applying+patches")

---

### Post by mlind on 2006-07-28
to test out a patch
```

patch -p1 --dry-run < /path/to/patch.diff

```
or for .gz (bcat for ,bz2)
```

zcat patch.gz | patch -p1 --dry-run

```

Without --dry-run the patch is applied. If source has changes a bit, using fuzz (-F) may help, but it also increases risk or error.
For debian source packages, patches are placed on debian/patches. Patching is done by using dpatch, quilt or similar. cdbs does this automatically.


You can get binary and sources of libipoddevice cvs version from my repository
```

deb http://www.elisanet.fi/mlind/ubuntu dapper experimental

```

---

### Post by mlind on 2006-07-28
> **mattisking said:**
> 
I can certainly do it with this package, but not from cvs. So, in general, I see there is always (in the apt-get source) directories a "debian" directory that contains a patches directory and a bunch of files like compat, changelog, control, ... etc.


[Debian maintainer's guide]("http://www.debian.org/doc/maint-guide/") will probably answer to most of your questions regarding to packaging process

> **mattisking said:**
> 
Does following the build process ./configure && make && sudo make install for a package obtained from apt-get source with a debian subdirectory as described apply the patches automatically as part of the configure or make or are the steps to apply the patches done separately before or during the build process? If they aren't done for you using the general process, how do you apply patches? Can they all be applied (there are multiple .patch files in the patches directory) at once or one at a time?


For debian source package, first patching happens when debian packaging information is applied on original source (done by apt-get source). patches on debian/patches are applied on build time, before configuring the package. You can see the patching target executing if you build package that has patches on debian/patches directory.

You can use multiple patch files, or just one big patch. Patches are applied  in "natural order", similar how you would sort a directory listing. Numbers  first, then alphabets. *01_fix_code.patch* is applied before *02_new_feature.patch* and *ugly_hack.patch* is applied after these.


> **mattisking said:**
> 
Let's say I got libipodevice0 from apt-get source and then also from CVS... How could I merge the patches from source (assuming they weren't applied upstream) with what I got from CVS? Of course I realize I could manually do it but is there a better/standard way? What utilities need to be used?


I usually --dry-run those patches manually to see if they apply. If not, then try to fix that. Then I just make up some funny names for the patches and place them to debian/patches directory. If you're not using cdbs, just plain debhelper stuff, then patching process is bit more complex. New Maintainers -manual should cover the basics though.


**Note**
You should always leave the actual source untouched and add features/custom content using patches. Additional files, like icons or manual pages should be placed on debian/ folder only and install those when binary target is executed.


/edit
I've also used emacs for creating and testing patches, and it has very support for the task. I bet vim has it too.

---

### Post by mattisking on 2006-07-28
Hey mlind, Thanks a LOT man. That really helps!

---


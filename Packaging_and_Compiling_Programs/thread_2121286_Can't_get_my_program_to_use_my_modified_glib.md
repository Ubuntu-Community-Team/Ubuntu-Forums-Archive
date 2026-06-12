---
title: "Can't get my program to use my modified glib"
date: 2013-03-01
forum: Packaging and Compiling Programs
---

### Post by JeyPeyy on 2013-03-01
I made a small change to the glib source code (GFileInfo.c to be more precise), ran ./configure (with a new prefix), make and make install. 

Then I changed /usr/lib/x86_64-linux-gnu/pkgconfig/gio-2.0.pc file so that the prefix is my working directory and that everything goes to the right path. Writing "pkg-config --cflags --libs gio-2.0" in the terminal seems to give a good output.

Then I made a small haxx.c file that took use of this new glib. I compiled it with
```
gcc haxx.c $(pkg-config --cflags --libs gio-2.0)
```

But when I run "ldd a.out", it only shows me the old paths. What am I doing wrong?

Thanks!

---

### Post by JeyPeyy on 2013-03-02
Anyone?

---

### Post by schragge on 2013-03-05
Wouldn't rebuilding the deb source with your changes be easier than compiling *glib* from scratch? What version of glib do you need? Currently, it's [2.32.3]("http://packages.ubuntu.com/precise-updates/libglib2.0-0") in precise and [2.34.1]("http://packages.ubuntu.com/quantal-updates/libglib2.0-0") in quantal.

```

sudo apt-get install devscripts quilt
sudo apt-get build-dep glib2.0
apt-get source glib2.0
cd glib2.0*
[COLOR=#FF0000]cat <<EOF >~/.quiltrc-dpkg
d=. ; while [ ! -d $d/debian -a `readlink -e $d` != / ]; do d=$d/..; done
if [ -d $d/debian ] && [ -z $QUILT_PATCHES ]; then
QUILT_PATCHES="debian/patches"
QUILT_PATCH_OPTS="--reject-format=unified"
QUILT_DIFF_ARGS="-p ab --no-timestamps --no-index --color=auto"
QUILT_REFRESH_ARGS="-p ab --no-timestamps --no-index"
QUILT_COLORS="diff_hdr=1;32:diff_add=1;34:diff_rem=1;31:diff_hunk=1;33:diff_ctx=35:diff_cctx=33"
[ -d $d/debian/patches ] || mkdir $d/debian/patches
fi
EOF[/COLOR]
[COLOR=green]export DEBFULLNAME="Jey Peyy"
export DEBEMAIL=jey.peyy@example.com
alias dquilt="quilt --quiltrc=${HOME}/.quiltrc-dpkg"[/COLOR]
dquilt new jp-fix-to-gfileinfo.patch
dquilt add gio/gfileinfo.c
editor gio/gfileinfo.c
[COLOR=blue]# make your changes to gfileinfo.c[/COLOR]
dquilt refresh
dquilt header -e
[COLOR=blue]# describe your patch[/COLOR]
sudo dch -l~jey
[COLOR=blue]# describe your changes[/COLOR]
debuild -i -us -uc -b
[COLOR=blue]# wait for build process to end[/COLOR]
sudo debi

```Lines marked [COLOR=green]green[/COLOR] can be added to your *~/.bashrc*. Lines marked [COLOR=red]red[/COLOR] must be done only once: the [quilt]("http://manpages.ubuntu.com/manpages/precise/en/man1/quilt.1.html") setup will work for all your future deb packages.

---


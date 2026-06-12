---
title: "How To: Install D.J. Bernstein's Daemontools"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by ki1ian on 2008-06-04
Hi,

I been trying to install [[COLOR="Red"]Daemontools[/COLOR]]("http://cr.yp.to/daemontools.html") in Hardy.    I tried to follow the installation [[COLOR="Red"]instructions[/COLOR]]("http://cr.yp.to/daemontools/install.html") on the site and ended up with a load of errors.  Has anyone installed this successfully?

Here are the commands I used:

```
sudo mkdir -p /package
sudo chmod 1755 /package
cd /package
```

then unpacked the [[COLOR="Red"]daemontools-0.76.tar[/COLOR]]("http://cr.yp.to/daemontools/daemontools-0.76.tar.gz") into the package folder.

```
cd admin/daemontools-0.76
sudo package/install
```


And got this output:
```

Linking ./src/* into ./compile...
Compiling everything in ./compile...
sh find-systype.sh > systype
rm -f compile
sh print-cc.sh > compile
chmod 555 compile
./compile byte_chr.c
./compile byte_copy.c
./compile byte_cr.c
./compile byte_diff.c
./compile byte_rchr.c
./compile fmt_uint.c
./compile fmt_uint0.c
./compile fmt_ulong.c
rm -f makelib
sh print-ar.sh > makelib
chmod 555 makelib
./compile scan_ulong.c
./compile str_chr.c
./compile str_diff.c
./compile str_len.c
./compile str_start.c
./makelib byte.a byte_chr.o byte_copy.o byte_cr.o byte_diff.o \
	byte_rchr.o fmt_uint.o fmt_uint0.o fmt_ulong.o scan_ulong.o str_chr.o \
	str_diff.o str_len.o str_start.o
rm -f choose
cat warn-auto.sh choose.sh \
	| sed s}HOME}"`head -1 home`"}g \
	> choose
chmod 555 choose
./choose c trydrent direntry.h1 direntry.h2 > direntry.h
./compile envdir.c
envdir.c:1:20: error: unistd.h: No such file or directory
In file included from envdir.c:5:
direntry.h:8:23: error: sys/types.h: No such file or directory
direntry.h:9:21: error: sys/dir.h: No such file or directory
envdir.c: In function \u2018main\u2019:
envdir.c:28: error: \u2018DIR\u2019 undeclared (first use in this function)
envdir.c:28: error: (Each undeclared identifier is reported only once
envdir.c:28: error: for each function it appears in.)
envdir.c:28: error: \u2018dir\u2019 undeclared (first use in this function)
envdir.c:42: warning: implicit declaration of function \u2018chdir\u2019
envdir.c:45: warning: implicit declaration of function \u2018opendir\u2019
envdir.c:50: warning: implicit declaration of function \u2018readdir\u2019
envdir.c:50: warning: assignment makes pointer from integer without a cast
envdir.c:56: error: dereferencing pointer to incomplete type
envdir.c:57: error: dereferencing pointer to incomplete type
envdir.c:58: error: dereferencing pointer to incomplete type
envdir.c:71: error: dereferencing pointer to incomplete type
envdir.c:74: error: dereferencing pointer to incomplete type
envdir.c:78: warning: implicit declaration of function \u2018closedir\u2019
envdir.c:80: warning: implicit declaration of function \u2018fchdir\u2019
envdir.c:82: warning: implicit declaration of function \u2018close\u2019
make: *** [envdir.o] Error 1
Copying commands into ./command...
cp: cannot stat `compile/svscan': No such file or directory

```

Any help would be much appreciated, thanks.

---

### Post by ZabiGG on 2008-06-04
Hi there ;)

I'm no expert, but I see one problem that's easily solved

sudo mkdir -p /package
sudo chmod 1755 /package
cd /package
Your permission on the second line should be 755

Hope this helps :)

---

### Post by ki1ian on 2008-06-05
Ooops!

Thanks ZabiGG,

Changed the permissions on the /package folder to 755 and now the installer spits out a different output:

```
Linking ./src/* into ./compile...
Compiling everything in ./compile...
./compile envdir.c
envdir.c:1:20: error: unistd.h: No such file or directory
In file included from envdir.c:5:
direntry.h:8:23: error: sys/types.h: No such file or directory
direntry.h:9:21: error: sys/dir.h: No such file or directory
envdir.c: In function \u2018main\u2019:
envdir.c:28: error: \u2018DIR\u2019 undeclared (first use in this function)
envdir.c:28: error: (Each undeclared identifier is reported only once
envdir.c:28: error: for each function it appears in.)
envdir.c:28: error: \u2018dir\u2019 undeclared (first use in this function)
envdir.c:42: warning: implicit declaration of function \u2018chdir\u2019
envdir.c:45: warning: implicit declaration of function \u2018opendir\u2019
envdir.c:50: warning: implicit declaration of function \u2018readdir\u2019
envdir.c:50: warning: assignment makes pointer from integer without a cast
envdir.c:56: error: dereferencing pointer to incomplete type
envdir.c:57: error: dereferencing pointer to incomplete type
envdir.c:58: error: dereferencing pointer to incomplete type
envdir.c:71: error: dereferencing pointer to incomplete type
envdir.c:74: error: dereferencing pointer to incomplete type
envdir.c:78: warning: implicit declaration of function \u2018closedir\u2019
envdir.c:80: warning: implicit declaration of function \u2018fchdir\u2019
envdir.c:82: warning: implicit declaration of function \u2018close\u2019
make: *** [envdir.o] Error 1
Copying commands into ./command...
cp: cannot stat `compile/svscan': No such file or directory
```

---

### Post by ZabiGG on 2008-06-05
OK. I believe I see the problem. Compiling in Ubuntu is not done the same way as explained in the instructions you linked.

Check out this page

[http://www.monkeyblog.org/ubuntu/ins...a_repositories]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")
How to install anything in Ubuntu

And search for compile

You'll find all the necessary instructions, and these should work.

Very good luck to you ;)

---

### Post by t00lk1t on 2008-06-06
Hi Kilian,

I think the daemontools installer package can be found in the multiverse repository - this takes away some of the pain of compiling from scratch!

Chris

---

### Post by Cappy on 2008-06-06
You also need ```
sudo apt-get install libc6-dev
```
if you still want to compile it

---


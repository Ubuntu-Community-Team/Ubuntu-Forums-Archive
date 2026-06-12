---
title: "Qt make error: /usr/bin/ld: cannot find -lXrender"
date: 2012-06-20
forum: Programming Talk
---

### Post by pellyhawk on 2012-06-20
I downloaded qt-everywhere-opensource-src-4.7.3.tar from official ftp and installed Qt 4.7.3 not as a root user on VMware Ubuntu 10.04.(I installed software package as root user)

After  run the following command,

```
./configure -prefix /usr/local/Trolltech/Qt-4.7.3-pc
```

```
make
```

I got these output results.

```
-L/home/ian/qt-everywhere-opensource-src-4.7.3/lib -L../JavaScriptCore/release -L/usr/X11R6/lib -ljscore -L/home/ian/qt-

everywhere-opensource-src-4.7.3/lib -lXrender -lQtGui -L/usr/X11R6/lib -lQtNetwork -lQtCore -lpthread -lXext -lX11 -lm 
/usr/bin/ld: cannot find -[COLOR="Red"]lXrender[/COLOR]
collect2: ld returned 1 exit status
make[1]: *** [../../../../lib/libQtWebKit.so.4.7.3] Error 1
make[1]: Leaving directory `/home/ian/qt-everywhere-opensource-src-4.7.3/src/3rdparty/webkit/WebCore'
make: *** [sub-webkit-make_default-ordered] Error 2
```

But I run the following commmand:
```
cd /usr/lib
ls -l
```

I got these output results:
```
lrwxrwxrwx   1 root root       19 2012-03-20 19:55 [COLOR="Red"]libXrender.so.1 -> libXrender.so.1.3.0[/COLOR]
-rw-r--r--   1 root root    34412 2009-12-04 06:44 [COLOR="Red"]libXrender.so.1.3.0[/COLOR]

```

Thanks in advance.

---

### Post by MadCow108 on 2012-06-20
you need to install libxrender-dev for the .so symlink

---

### Post by pellyhawk on 2012-06-21
> **MadCow108 said:**
> you need to install libxrender-dev for the .so symlink

Thanks for your suggestion.

But another issue appeared. After installing libXrender-dev on my vmware ubuntu, everytime I run command"make", my laptop alway happened [COLOR="Red"]blue screen of death[/COLOR]. My RAM is 2G.

How to deal with this problem? Thanks.

---

### Post by pellyhawk on 2012-06-22
try many times(run command "make"), and succeeded.

But while I run:```
make install
```

I got these result:
```
ian@mike-desktop:~/qt-everywhere-opensource-src-4.7.3$ make install
cd src/tools/bootstrap/ && make -f Makefile install
make[1]: Entering directory `/home/ian/qt-everywhere-opensource-src-4.7.3/src/tools/bootstrap'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/ian/qt-everywhere-opensource-src-4.7.3/src/tools/bootstrap'
cd src/tools/moc/ && make -f Makefile install
make[1]: Entering directory `/home/ian/qt-everywhere-opensource-src-4.7.3/src/tools/moc'
mkdir: cannot create directory `/usr/local/Trolltech': Permission denied
make[1]: *** [install_target] Error 1
make[1]: Leaving directory `/home/ian/qt-everywhere-opensource-src-4.7.3/src/tools/moc'
make: *** [sub-moc-install_subtargets-ordered] Error 2
ian@mike-desktop:~/qt-everywhere-opensource-src-4.7.3$ 

```

What's the matter? Thanks

---

### Post by steeldriver on 2012-06-22
> **pellyhawk said:**
> 
```

mkdir: cannot create directory `/usr/local/Trolltech': Permission denied

```What's the matter? Thanks

looks like you don't have permission to write to /usr/local - you need to run 'make install' with sudo privileges

```
sudo make install
```

---

### Post by MadCow108 on 2012-06-22
or the the prefix in configure to a path you can write to

---


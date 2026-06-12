---
title: "Converting .rpm to .deb using alien"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by JoeBrooks on 2008-09-02
I'm trying to convert the file z600llpddk-2.0-1.i386.rpm to .deb. I installed alien from the terminal, but when I enter

```
sudo alien z600llpddk-2.0-1.i386.rpm
```

it returns:

```
Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/z600llpddk
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: symbol _ZTVN10__cxxabiv117__class_type_infoE used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol IPCcreate_printer used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol __gxx_personality_v0 used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol IPCstart_page used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _ZdlPv used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol IPCdestroy_printer used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _Znwj used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol IPCend_job used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol IPCcreate_job used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol IPCend_page used by debian/z600llpddk/usr/lib/liblexprintjob.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: 2 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: symbol _Znwj used by debian/z600llpddk/usr/lib/liblexprinter.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _Unwind_Resume used by debian/z600llpddk/usr/lib/liblexprinter.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _ZTVN10__cxxabiv117__class_type_infoE used by debian/z600llpddk/usr/lib/liblexprinter.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _ZTVN10__cxxabiv120__si_class_type_infoE used by debian/z600llpddk/usr/lib/liblexprinter.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol __gxx_personality_v0 used by debian/z600llpddk/usr/lib/liblexprinter.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _ZdlPv used by debian/z600llpddk/usr/lib/liblexprinter.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _Unwind_Resume used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _ZTIPKc used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _ZTVN10__cxxabiv117__class_type_infoE used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _ZTVN10__cxxabiv120__si_class_type_infoE used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol SendCommand used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol __cxa_begin_catch used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol __cxa_pure_virtual used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol __gxx_personality_v0 used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol __cxa_end_catch used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol __cxa_allocate_exception used by debian/z600llpddk/usr/lib/liblexz600core.so.0.0.0 found in none of the libraries.
dpkg-shlibdeps: warning: 3 other similar warnings have been skipped (use -v to see them all).
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: z600llpddk-2.0: No such file or directory
```

What am I doing wrong?

---

### Post by LowSky on 2008-09-02
follow these instructions i got from here
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)

```
sudo apt-get install libstdc++5 alien
```

```
sudo apt-get install ia32-libs alien
```
```
mkdir lexmark
cd lexmark
wget http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz
```

```
tar xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
```

```
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
```

```
tar xvzf install.tar.gz
```

```
alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm
```

```
/usr/lib/cups/backend/z600
```

```
direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"
```

```
sudo /etc/init.d/cupsys restart 
```

---

### Post by philinux on 2008-09-02
Use the --scripts parameter to include the scripts.

See man alien.

-c, --scripts
           Try to convert the scripts that are meant to be run when the package is installed and removed. Use
           this with caution, because these scripts might be designed to work on a system unlike your own, and
           could cause problems. It is recommended that you examine the scripts by hand and check to see what
           they do before using this option.

---

### Post by WRDN on 2008-09-02
To convert the RPM to a Debian package with alien, you need to add the "-d" directive:

```
fakeroot alien -d [name].rpm
```

---

### Post by JoeBrooks on 2008-09-02
> **philinux said:**
> Use the --scripts parameter to include the scripts.

See man alien.

-c, --scripts
           Try to convert the scripts that are meant to be run when the package is installed and removed. Use
           this with caution, because these scripts might be designed to work on a system unlike your own, and
           could cause problems. It is recommended that you examine the scripts by hand and check to see what
           they do before using this option.

so...

```
sudo alien z600cups-1.0-1.i386.rpm -c --scripts postinst postrm preinst prerm
```

?

---

### Post by JoeBrooks on 2008-09-02
> **LowSky said:**
> ```
alien -t z600cups-1.0-1.i386.rpm
```

```
/usr/lib/cups/backend/z600
```

```
alien -t z600cups-1.0-1.i386.rpm
```

returns

```
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `z600cups-1.0': File exists
unable to mkdir z600cups-1.0:  at /usr/share/perl5/Alien/Package.pm line 257.
```

and then 

```
/usr/lib/cups/backend/z600
```

returns

```
bash: /usr/lib/cups/backend/z600: No such file or directory
```

---

### Post by JoeBrooks on 2008-09-02
> **WRDN said:**
> To convert the RPM to a Debian package with alien, you need to add the "-d" directive:

```
fakeroot alien -d [name].rpm
```

returns
```

Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `z600cups-1.0': File exists
unable to mkdir z600cups-1.0:  at /usr/share/perl5/Alien/Package.pm line 257.
```

---

### Post by drubin on 2008-09-02
Here is a link that might help
[http://finebushpeople.net/LexmarkZ600](http://finebushpeople.net/LexmarkZ600)
[http://ubuntuforums.org/archive/index.php/t-616097.html](http://ubuntuforums.org/archive/index.php/t-616097.html)

---


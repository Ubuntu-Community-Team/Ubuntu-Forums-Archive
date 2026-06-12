---
title: "convert debian  *.deb file to tar.gz"
date: 2011-01-27
forum: Packaging and Compiling Programs
---

### Post by cccc on 2011-01-27
hi

Howto convert debian *.deb file to *.tar.gz?

---

### Post by SevenMachines on 2011-01-27
I don't know if theres a 'one command' or 'one line' way to do this but certainly the following works on the few occasions i need to do this

## Example using hello package

In short,
```
$ dpkg -x hello_2.6-1_i386.deb ./tmp
$ cd tmp
$ tar -czvf hello_2.6-1.tar.gz *
```In long :)
```
$ ls
hello_2.6-1_i386.deb
```## Extract the package contents to the ./tmp directory
```
 $ dpkg -x hello_2.6-1_i386.deb ./tmp
```## Change to the tmp directory
```
$ cd tmp/
$ ls -R

.:
hello_2.6-1.tar.gz  usr

./usr:
bin  share

./usr/bin:
hello

./usr/share:
doc  info  man

./usr/share/doc:
hello

./usr/share/doc/hello:
changelog.Debian.gz  changelog.gz  copyright  NEWS

./usr/share/info:
hello.info.gz

./usr/share/man:
man1

./usr/share/man/man1:
hello.1.gz

```## Create gzipped, tarred archive from all files in the current directory
```
$ tar -czvf hello_2.6-1.tar.gz *

usr/
usr/share/
usr/share/info/
usr/share/info/hello.info.gz
usr/share/doc/
usr/share/doc/hello/
usr/share/doc/hello/changelog.Debian.gz
usr/share/doc/hello/changelog.gz
usr/share/doc/hello/NEWS
usr/share/doc/hello/copyright
usr/share/man/
usr/share/man/man1/
usr/share/man/man1/hello.1.gz
usr/bin/
usr/bin/hello
```## Just to check all the files are actually in there
```
$ tar -tvf hello_2.6-1.tar.gz

drwxr-xr-x seven/seven       0 2010-10-15 12:33 usr/
drwxr-xr-x seven/seven       0 2010-10-15 12:33 usr/share/
drwxr-xr-x seven/seven       0 2010-10-15 12:33 usr/share/info/
-rw-r--r-- seven/seven   11773 2010-10-15 12:33 usr/share/info/hello.info.gz
drwxr-xr-x seven/seven       0 2010-10-15 12:33 usr/share/doc/
drwxr-xr-x seven/seven       0 2010-10-15 12:33 usr/share/doc/hello/
-rw-r--r-- seven/seven    3603 2010-08-06 21:04 usr/share/doc/hello/changelog.Debian.gz
-rw-r--r-- seven/seven    6673 2010-04-05 19:50 usr/share/doc/hello/changelog.gz
-rw-r--r-- seven/seven    3128 2010-04-08 00:06 usr/share/doc/hello/NEWS
-rw-r--r-- seven/seven    2264 2010-08-06 18:10 usr/share/doc/hello/copyright
drwxr-xr-x seven/seven       0 2010-10-15 12:33 usr/share/man/
drwxr-xr-x seven/seven       0 2010-10-15 12:33 usr/share/man/man1/
-rw-r--r-- seven/seven     738 2010-10-15 12:33 usr/share/man/man1/hello.1.gz
drwxr-xr-x seven/seven       0 2010-10-15 12:33 usr/bin/
-rwxr-xr-x seven/seven   13708 2010-10-15 12:33 usr/bin/hello
```Note, 'file-roller', the default archive manager can extract .deb packages and build tar.gz archives if you prefer a gui

---

### Post by cccc on 2011-01-27
Thx a lot, but what about to convert using **alien** 

[http://linux.die.net/man/1/alien](http://linux.die.net/man/1/alien)

or using this perl script:

[http://www.miketaylor.org.uk/tech/deb/](http://www.miketaylor.org.uk/tech/deb/)

Has someone already tried?

---

### Post by SevenMachines on 2011-01-28
Doh! haven't used alien in years so completely forgot about it
```
$ sudo alien -t hello_2.6-1_i386.deb
```
should work

---

### Post by cccc on 2011-01-28
Thx a lot:```

# sudo alien -t file.deb
Warning: Skipping conversion of scripts in package file: postinst
Warning: Use the --scripts parameter to include the scripts.
file.tgz generated
```

using -c parameter, without warning:```

# sudo alien -t -c file.deb
file.tgz generated
#

```

---


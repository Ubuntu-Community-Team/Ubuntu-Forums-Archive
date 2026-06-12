---
title: "Package: UbuntuHomeBackup"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-31
I found just what I am looking for. A way to backup /home with various configs, etc.

UbuntuHomeBackup
[https://wiki.ubuntu.com/UbuntuHomeBackup](https://wiki.ubuntu.com/UbuntuHomeBackup)

I d/l-d this and looked around the tarred file. It became obvious to me that I had to install the package with make, make install and such.

What programs/packages are needed to make this work? I have heard of build-essential. What others?

Then, in the terminal, what commands get issued to what package and in what order?

---

### Post by ezramorris on 2008-10-31
> **Mark_in_Hollywood said:**
> I found just what I am looking for. A way to backup /home with various configs, etc.

UbuntuHomeBackup
[https://wiki.ubuntu.com/UbuntuHomeBackup](https://wiki.ubuntu.com/UbuntuHomeBackup)

I d/l-d this and looked around the tarred file. It became obvious to me that I had to install the package with make, make install and such.

What programs/packages are needed to make this work? I have heard of build-essential. What others?

Then, in the terminal, what commands get issued to what package and in what order?

Hi,
Assuming you have untarred the tar file and you are inside the ubuntu-home-backup-0.1 directory:
```
sudo apt-get install build-essential
./configure
make
sudo make install
```

This is generally the sequence to run when compiling stuff like this, although you don't need to install build-essential every time as long as you installed it once.

For future reference, if the directory contains an INSTALL file, read that. If not, try README.

Hope this helps.

---

### Post by cariboo on 2008-10-31
I you want to create a .deb, use checkinstall instead of make, Fill in the info when prompted and follow the rest of the prompts. You can also skip the make install, just double click on your newly created .deb and gdebi will install it.

You may have to create a launcher for it, the executable is usually located in /usr/bin or /usr/local/bin.

Jim

---

### Post by ezramorris on 2008-10-31
> **cariboo907 said:**
> You may have to create a launcher for it, the executable is usually located in /usr/bin or /usr/local/bin.

You shouldn't need to specify the path in a launcher.

---

### Post by Mark_in_Hollywood on 2008-10-31
> **ezramorris said:**
> Hi,
Assuming you have untarred the tar file and you are inside the ubuntu-home-backup-0.1 directory:
```
sudo apt-get install build-essential
./configure
make
sudo make install
```

This is generally the sequence to run when compiling stuff like this, although you don't need to install build-essential every time as long as you installed it once.

For future reference, if the directory contains an INSTALL file, read that. If not, try README.

Hope this helps.

With build-essential installed, I tried your code as follows. (and I apologize for the lengthy post, but I'm LOST)

mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ make
make  all-recursive
make[1]: Entering directory `/tmp/ubuntu-home-backup-0.1'
Making all in src
make[2]: Entering directory `/tmp/ubuntu-home-backup-0.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/share/locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
main.c:10:21: error: gtk/gtk.h: No such file or directory
In file included from main.c:12:
interface.h:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from main.c:13:
support.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:51: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
support.h:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:63: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:66: error: expected ‘)’ before ‘*’ token
main.c:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c:16: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c:17: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c: In function ‘main’:
main.c:39: error: ‘window’ undeclared (first use in this function)
main.c:39: error: (Each undeclared identifier is reported only once
main.c:39: error: for each function it appears in.)
main.c:41: error: ‘backup_name_entry’ undeclared (first use in this function)
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/tmp/ubuntu-home-backup-0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/ubuntu-home-backup-0.1'
make: *** [all] Error 2
mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ sudo make install
Making install in src
make[1]: Entering directory `/tmp/ubuntu-home-backup-0.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/share/locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
main.c:10:21: error: gtk/gtk.h: No such file or directory
In file included from main.c:12:
interface.h:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from main.c:13:
support.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:51: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
support.h:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:63: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:66: error: expected ‘)’ before ‘*’ token
main.c:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c:16: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c:17: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c: In function ‘main’:
main.c:39: error: ‘window’ undeclared (first use in this function)
main.c:39: error: (Each undeclared identifier is reported only once
main.c:39: error: for each function it appears in.)
main.c:41: error: ‘backup_name_entry’ undeclared (first use in this function)
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/tmp/ubuntu-home-backup-0.1/src'
make: *** [install-recursive] Error 1
mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$

---

### Post by ezramorris on 2008-10-31
> **Mark_in_Hollywood said:**
> mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..

Woah, if one thing fails, then let's sort it out before the next step. :-)

Try
```
./autogen.sh --prefix=/usr
```
then the other stuff again.

---

### Post by mdpalow on 2008-11-01
Hi there,

If you're looking for a back-up program, please see my signature below for a link. A lot easier than what you're running into right now I think.

Good luck...

---

### Post by Mark_in_Hollywood on 2008-11-01
> **ezramorris said:**
> Woah, if one thing fails, then let's sort it out before the next step. :-)

Try
```
./autogen.sh --prefix=/usr
```
then the other stuff again.

Nope, but almost:

mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ ./autogen.sh --prefix=/usr

**Error**: You must have `autoconf' installed.
Download the appropriate package for your distribution,
or get the source tarball at [ftp://ftp.gnu.org/pub/gnu/](ftp://ftp.gnu.org/pub/gnu/)

**Error**: You must have `glib' installed.
You can get it from: [ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)

**Error**: You must have `automake' installed.
You can get it from: [ftp://ftp.gnu.org/pub/gnu/](ftp://ftp.gnu.org/pub/gnu/)

---

### Post by ezramorris on 2008-11-01
> **Mark_in_Hollywood said:**
> Nope, but almost:

mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ ./autogen.sh --prefix=/usr

**Error**: You must have `autoconf' installed.
Download the appropriate package for your distribution,
or get the source tarball at [ftp://ftp.gnu.org/pub/gnu/](ftp://ftp.gnu.org/pub/gnu/)

**Error**: You must have `glib' installed.
You can get it from: [ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)

**Error**: You must have `automake' installed.
You can get it from: [ftp://ftp.gnu.org/pub/gnu/](ftp://ftp.gnu.org/pub/gnu/)

```
sudo apt-get install autoconf libglib2.0-0 automake
```
then:
```
./autogen.sh --prefix=/usr
make
sudo make install
```

You can use mdpalow's suggestion of QuickStart, and it is quite a useful app. However, some people don't like to suggest it/use it because it isn't open source.

---

### Post by Mark_in_Hollywood on 2008-11-01
> **ezramorris said:**
> ```
sudo apt-get install autoconf libglib2.0-0 automake
```
then:
```
./autogen.sh --prefix=/usr
make
sudo make install
```

You can use mdpalow's suggestion of QuickStart, and it is quite a useful app. However, some people don't like to suggest it/use it because it isn't open source.

I looked at QuickStart. It seems more complex than my needs. I don't want or care about compression. I have an 80gig usb ext. drive. I want to copy /home over to it. Both as 2nd copy and during distribution upgrades.

Meanwhile:

mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ ./autogen.sh --prefix=/usr

**Error**: You must have `glib' installed.
You can get it from: [ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)
mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ sudo aptitude install glib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find package "glib", and more than 40
packages contain "glib" in their name.
...

---

### Post by ezramorris on 2008-11-01
> **Mark_in_Hollywood said:**
> I looked at QuickStart. It seems more complex than my needs. I don't want or care about compression. I have an 80gig usb ext. drive. I want to copy /home over to it. Both as 2nd copy and during distribution upgrades.

Meanwhile:

mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ ./autogen.sh --prefix=/usr

**Error**: You must have `glib' installed.
You can get it from: [ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)
mark@Lexington-19:/tmp/ubuntu-home-backup-0.1$ sudo aptitude install glib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find package "glib", and more than 40
packages contain "glib" in their name.
...

try libglib2.0-dev

---


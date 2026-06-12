---
title: "Alien not working with ymessenger rpm.  Solutions or .deb anyone?"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by amx401 on 2011-10-30
I have searched the web, and keep coming up with alien for .rpm files in Ubuntu.  I downloaded the Fedora yahoo messenger rpm file, but do not know what to do with rpm.  When I run the command rpm, I get this:

```

$ rpm -ivh rh9.ymessenger-1.0.4-1.i386.rpm 
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: cannot open Conflictname index using db5 - Permission denied (13)
error: cannot open Obsoletename index using db5 - Permission denied (13)
error: Failed dependencies:
	/bin/sh is needed by ymessenger-1.0.4-1.i386
	gdk-pixbuf >= 0.8.0 is needed by ymessenger-1.0.4-1.i386
	libX11.so.6 is needed by ymessenger-1.0.4-1.i386
	libXext.so.6 is needed by ymessenger-1.0.4-1.i386
	libXi.so.6 is needed by ymessenger-1.0.4-1.i386
	libXmu.so.6 is needed by ymessenger-1.0.4-1.i386
	libc.so.6 is needed by ymessenger-1.0.4-1.i386
	libc.so.6(GLIBC_2.0) is needed by ymessenger-1.0.4-1.i386
	libc.so.6(GLIBC_2.1) is needed by ymessenger-1.0.4-1.i386
	libc.so.6(GLIBC_2.1.3) is needed by ymessenger-1.0.4-1.i386
	libc.so.6(GLIBC_2.3) is needed by ymessenger-1.0.4-1.i386
	libdl.so.2 is needed by ymessenger-1.0.4-1.i386
	libgdk-1.2.so.0 is needed by ymessenger-1.0.4-1.i386
	libgdk_pixbuf.so.2 is needed by ymessenger-1.0.4-1.i386
	libglib-1.2.so.0 is needed by ymessenger-1.0.4-1.i386
	libgmodule-1.2.so.0 is needed by ymessenger-1.0.4-1.i386
	libgtk-1.2.so.0 is needed by ymessenger-1.0.4-1.i386
	libm.so.6 is needed by ymessenger-1.0.4-1.i386

```

I have also tried using alien to no effect:

```

$ sudo alien -dk rh9.ymessenger-1.0.4-1.i386.rpm 
[sudo] password for kendrick: 
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
Warning: Skipping conversion of scripts in package ymessenger: postinst
Warning: Use the --scripts parameter to include the scripts.
error: db5 error(-30969) from dbenv->open: DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/kendrick/.rpmdb
ymessenger_1.0.4-1_i386.deb generated

```


Am I missing something?

I am very frustrated by this, and going to walk away for a minute.  I have googled answers before posting on here.  Thank you for your help.

---

### Post by Paqman on 2011-10-30
What exactly are you trying to accomplish? Empathy can connect to the Yahoo network if you just want to chat using your Yahoo account.

---

### Post by mick222 on 2011-10-30
why not use empathy or the online yahoo i dont think yahoo supports linux anymore. It was probably an old rpm file check when it was made.version 1.04 very old.

---

### Post by amx401 on 2011-10-30
I am using empathy right now and as far as pure messaging goes, I have no problems.  But I don't have access to features like file share, photo share, buzz or anything like that. (to my knowledge at least)

I would like an IM that has features beyond basic text and emoticons.  If there is a better program, please let me know.

Thank you.

---


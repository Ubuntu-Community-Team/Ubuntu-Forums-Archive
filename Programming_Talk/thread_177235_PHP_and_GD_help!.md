---
title: "PHP and GD help!"
date: 2006-05-16
forum: Programming Talk
---

### Post by noob_Lance on 2006-05-16
Hey, im looking to compile the GD library with PHP for a script im working on... but i have no clue how to do this... can someone please help me.. thanks:)

~Lance

---

### Post by hagen00 on 2006-05-16
I believe it's as easy as 

```
apt-get install php4-gd
```
or
```
apt-get install php5-gd
```

Maybe restart apache after that.

---

### Post by noob_Lance on 2006-05-16
ahahahah thanks :p i didnt kno it was in the repo's :p

---

### Post by hagen00 on 2006-05-16
it's a pleasure...and mate, this is Ubuntu, absolutely everything is in the repos! Isn't it great?!

---

### Post by noob_Lance on 2006-05-16
do you know how to make a deb package to install and modify some little things in other programs :p because i have a program i would like to be in the repos lol :P

---

### Post by hagen00 on 2006-05-17
No, but google does
[http://ftp.sun.ac.za/ftp/pub/documentation/building_packages/AT8047723203.html]("http://ftp.sun.ac.za/ftp/pub/documentation/building_packages/AT8047723203.html")

---

### Post by Ahriman on 2006-05-24
What about calendar support? Normally, I compile PHP with --enable-calendar , but I cannot see this module in the repos. Any clues as to how to add it into the installed PHp without removing the current install and manually compiling it?

---

### Post by Kvark on 2006-05-24
According to Synaptic both php 4 and 5 have calendar support and a whole lot of other stuff compiled in. From the description of libapache2-mod-php5:
> Compiled in extensions include: bcmath, bz2, **calendar**, ctype, dba, dbx, exif, filepro, ftp, gettext, iconv, mbstring, mime_magic, openssl, overload, pcre, posix, session, shmop, sockets, standard, sysvmsg, sysvsem, sysvshm, tokenizer, wddx, xml, xmlrpc, yp, zip, and zlib.

---


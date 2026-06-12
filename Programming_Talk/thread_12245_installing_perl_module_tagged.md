---
title: "installing perl module: tagged"
date: 2005-01-23
forum: Programming Talk
---

### Post by KayMyst on 2005-01-23
hi, I'm trying to install tagged 0.40, a perl module for id3 tags,and I get the following error when I run "sudo make":

Manifying blib/man3/MP3::Tag::ID3v2-Data.3
Can't open blib/man3/MP3::Tag::ID3v2-Data.3 for writing: Invalid argument
 at /usr/share/perl/5.8/ExtUtils/Command/MM.pm line 126
make: *** [manifypods] Error 255

the same thing append when I tried to install another module: Compress Zlib:

Manifying blib/man3/Compress::Zlib.3pm
Can't open blib/man3/Compress::Zlib.3pm for writing: Invalid argument
 at /usr/share/perl/5.8/ExtUtils/Command/MM.pm line 126
make: *** [manifypods] Error 255


thanks for your help

---

### Post by defkewl on 2005-02-17
Are you using super user when installing it?

---

### Post by nosiad2 on 2005-06-27
please help...i am having the some error as the first poster above....

steps i took:

as norm user:
perl Makefile.PL
make

i get the error when doing 'make'.

i also tried doing the above commands as root(sudo) with no success....
whats going on?

---


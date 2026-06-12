---
title: "How to install GNU C/C++ Compilers"
date: 2006-03-23
forum: Programming Talk
---

### Post by Hilarryous on 2006-03-23
I tried installing GNU C/C++ compilers with the following command:

sudo apt-get install build-essential

I have internet connection, but I keep on getting the following message:

Media change: please insert the disc labeled
 'Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20060115)'
in the drive '/cdrom/' and press enter

Can anyone help?

Thanks!!

---

### Post by pranith on 2006-03-23
hi,
     the error is because u included dapper cdrom in ur /etc/apt/sources.list
what u have to do is 
open the file /etc/apt/sources.list using sudo so that u can write to it... 
comment the line containing the dapper cdrom line ... i.e put # at the beginning of the line containing it...
then uncomment the lines (i.e remove #) starting with deb or deb-src
now save it
now do 
apt-get update
apt-get install build-essential

hope that helps
pranith.

---

### Post by xdvx on 2006-03-23
Just [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) :)

---


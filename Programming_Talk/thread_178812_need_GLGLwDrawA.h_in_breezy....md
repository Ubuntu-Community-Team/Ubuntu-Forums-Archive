---
title: "need GL/GLwDrawA.h in breezy..."
date: 2006-05-18
forum: Programming Talk
---

### Post by STt on 2006-05-18
Hi all, I'm trying to compile a package called SUMA ( [http://afni.nimh.nih.gov/afni/suma](http://afni.nimh.nih.gov/afni/suma) ), which needs the GL/GLwDrawA.h. This file used to be part of the xlibmesa-gl-dev package in warty, but doesn't exist anymore in the package that seems to replace it, namely libgl1-mesa-dev. And of course, I can't install the old package coz it conflicts with the new one... Any idea how to install GL/GLwDrawA.h and accompanying files in breezy????
Thanks,
Sylvain

---

### Post by hod139 on 2006-05-18
Looks like it doesn't exist in breezy, but it does in [dapper]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=GLwDrawA.h&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386") in the [libgl1-mesa-swrast-dev ]("http://packages.ubuntu.com/dapper/libdevel/libgl1-mesa-swrast-dev")package.[SIZE=2]  I just recently upgraded to dapper it has been stable for me (I would think it should remain stable since it is suppose to be released in less than 2 weeks).
[/SIZE]

---


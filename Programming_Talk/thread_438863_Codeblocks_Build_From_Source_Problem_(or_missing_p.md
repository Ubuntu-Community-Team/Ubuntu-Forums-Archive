---
title: "Code::blocks Build From Source Problem (or: missing package don't exist?)"
date: 2007-05-10
forum: Programming Talk
---

### Post by daveblack on 2007-05-10
Hi

After reading good reviews of the program here on forum, I decided to try the cross platform IDE Code::blocks. I'm building it from source. It's the only way - There is no recent .deb/.gz.tr file to install. 

I've download the code from the svn. Ran bootstrap. Completed without errors. Ran configure. Came out with this:
```
checking for GTK2... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found
```

But I can't find any such package...

---

### Post by araz on 2007-05-10
I guess the package you are looking for is libgtk2.0-dev

---

### Post by hod139 on 2007-05-10
You don't have to build code::blocks by source.  There are plenty of [nightly debs available]("http://forums.codeblocks.org/index.php?board=20.0").  For some reason the "official" nightly debs have not been updated recently, but users have been providing their own debs.  For example, the May 9th 2007 Ubuntu 7.04 i386 build can be found here: [http://www.savefile.com/files/707996](http://www.savefile.com/files/707996)

Browsing the nightly builds forum will present more builds.

---

### Post by siiib on 2007-05-10
this one works

[http://forums.codeblocks.org/index.php?PHPSESSID=c92f11bc91df31c6b1ae8a36116cefe4&topic=5818.0](http://forums.codeblocks.org/index.php?PHPSESSID=c92f11bc91df31c6b1ae8a36116cefe4&topic=5818.0)

i have it running right here..

---

### Post by daveblack on 2007-05-11
Thanks alot. Manage to compile from source. Now got a couple of other problems. Guess I'll use the deb package after all.

Is there any guide for programmers coming from visual studio, how to program in linux. I mean. there is the make utility which I know, sort of. Then there is configure which is usually a bash script that does... what exactly? then there is m4 files, and makefile.in/am. As I understand it their purpose is to simplify the compilation from source on many different distros and to check and manage dependencies. But why three different scripting languages? (m4, bash and make has its own syntax), and how exactly does they all work?

I'm not dissing linux way of managing source compilation. It's just that I'm very new to linux and it's very confusing..

Thanks
Dave

---


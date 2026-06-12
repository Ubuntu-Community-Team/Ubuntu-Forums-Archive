---
title: "How can I install the C API for mysql"
date: 2009-09-23
forum: Programming Talk
---

### Post by tonmey on 2009-09-23
Hi guys,
I am a totally new for both ubuntu and mysql. But I have some homework to do on them. After using apt-get installing the mysql-client and mysql-server, I cannot still find the native mysql C API in my computer(usr/local/ as indicated), I once installed with the rmp package from the official site, but it seems that rpm does not work on debian/ubuntu. My homework is build a simple UI(even a textbox) for a database to let people browse it. And C is the only language I am familiar. I guess I have no choice, so can anyone help me? Thanks a lot!

BTW: As a OS, Unix-style system is awesome, and ubuntu makes it extreme!!
Tony

---

### Post by escapee on 2009-09-23
Did you install libmysqlclient and not just mysqlclient?


Also, this tutorial is for Eclipse, but may help out some [http://marksitblog.blogspot.com/2007/07/tour-of-mysql-c-api.html](http://marksitblog.blogspot.com/2007/07/tour-of-mysql-c-api.html)

---

### Post by TheBuzzSaw on 2009-09-23
Are you wanting to use C specifically? Or is C++ OK? I use MySQL++. It is available in the repositories under the package libmysql++-dev.

Are you familiar with linking libraries?

---

### Post by tonmey on 2009-09-24
[escapee]("http://ubuntuforums.org/member.php?u=247523"): yes, That's the thing I want to do. I don't have the headers! Just now, I was trying install c connector 6.04 with cmake, but it told me that "does not appear to contain CMakeLists.txt" I don't know fix that! I don't mind whether use the connector or libmysql, whatever I can compile it within my c projects would be ok.

---

### Post by tonmey on 2009-09-24
[TheBuzzSaw]("http://ubuntuforums.org/member.php?u=219214"): C++ is would be great, since C++ is compatible with C. I am kind of transfering myself to C++. However, still the problem: I don't know how to install either the libmysql or c/c++ connector. Terminal just told me no CMakelists.txt, and how I can get the libmysql?

---

### Post by tonmey on 2009-09-24
Here is how I installed them:

jin@Jin-R52:~/Download/mysql-connector-c-6.0.2-linux-glibc2.3-x86-32bit$ ls
bin  COPYING  EXCEPTIONS-CLIENT  include  lib  README
jin@Jin-R52:~/Download/mysql-connector-c-6.0.2-linux-glibc2.3-x86-32bit$ cmake .CMake Error: The source directory "/home/jin/Download/mysql-connector-c-6.0.2-linux-glibc2.3-x86-32bit" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.

I can barely find the error type in google. Am I missing some common sense?

---

### Post by TheBuzzSaw on 2009-09-24
```
sudo apt-get install libmysql++-dev
```

---

### Post by MadCow108 on 2009-09-24
its always easiest to use the precompiled binaries from the repositories (except you for some reason need the newest version)

for the C api type this into a terminal:
```

sudo apt-get install libmysqlclient16 libmysqlclient16-dev

```
or install them over the gui package manager synaptic

the -dev behind a package name always indicates developer files. These packages usually include all the necessary headers needed for coding

---

### Post by tonmey on 2009-09-24
Thank you guys!!
The problem solved!! Yesterday when I got despair, I type a wrong command when configure the source distribution mysql as mysql_configure(it should be configure), and you know what? The apt-get finally worked, it suggested the packaged name you told me! libmysqlclient15/16-dev, Yes, that's it!
In fact, I really hope apt-get can help manage the installing package, they are convenient and not error prone.

Thank you guys, you reply my question(maybe a simple problem for you)!! And I wish I asked earlier.

Tony

---


---
title: "Eclipse 3.1 can't find standard header files (C++)"
date: 2006-06-26
forum: Programming Talk
---

### Post by ydong on 2006-06-26
Hi,

i just installed CDT for eclipse. i can program in c++ on eclipse now. however, when i built a project, it told me that it could't find header files such as <string> <vector>...etc. but it could build through, just gave several warnings.

How can I fix this problem?

it's very important for me. because it can't compile if i use a pointer of string. such problem repeats!

I appreciate your help! Thank you!

---

### Post by noigeaR on 2006-06-27
somehow the cdt doesn't use subfolders from the include path automatically. i've solved the problem by adding **/usr/include/c++/4.0** manually to the include paths.
open your project properties, click on c/c++ build, select gcc c++ compiler/directories, then add /usr/include/c++/4.0 to the include paths and it should work. at least it did for me.

i've switched to kdevelop in the meantime because i find it more comfortable to manage c++ projects than cdt. kdevelop just has better integration for autotools, doxygen and subversion. even with lots of plug-ins eclipse still doesn't feel very comfortable for c++. still use (and really like) eclipse for java though.

---

### Post by ydong on 2006-06-27
thank you. i just found the way you told me today. i searched the web and i think this is the only way to solve this problem.

by the way. i want to try KDevelop too. and i downloaded a version from software repository. but i found it was for KDE development and there were something lost when i tried to build sample programs. since you use KDevelop, would you please tell what stuffs should i install and what to pay attention to?

my mail: [email]ydong.public@gmail.com[/email]

thank you.

---

### Post by noigeaR on 2006-06-27
kdevelop is the main ide used for kde development, but you can also use it to code for gtk (gnome), wxwidgets or simple console programs. start a new project from project/new project and choose the program template you would like to use.

to get examples running you should install the following packages: build-essentials (for gcc, make etc.), kdevelop3 (this should also install automake, autoconf and some others), some examples need libtool too.
kdbg, graphviz and doxygen are useful tools that integrate nicely with kdevelop.

depending on what kind of application you try to build you will also need the developer libraries (normaly the package name of the runtime library with a -dev ending), so if you want to build kde application you need kdebase-dev, for qt programs you need libqt3-mt-dev or libqt4-dev, for gtk you need libgtk2.0-dev etc.

---

### Post by ydong on 2006-06-27
thank you very much

---


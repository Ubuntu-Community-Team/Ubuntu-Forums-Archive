---
title: "Can't locate gtkmm.h file for C++ #include statement"
date: 2010-08-07
forum: Programming Talk
---

### Post by robogenus on 2010-08-07
Hi All, I am fairly new to C++, but familiar enough to write basic procedural code. I am wanting to test out building GUI using [COLOR=RoyalBlue]**gtkmm**[/COLOR], but when I **[COLOR=RoyalBlue]#include <gtkmm.h>[/COLOR]** the file cannot be located. I installed gtkmm on Ubuntu Jaunty via terminal [COLOR=DarkRed]sudo apt-get install[/COLOR] and everything seem to install okay, but to no avail I cannot find **[COLOR=RoyalBlue]gtkmm.h[/COLOR]** header file in the [COLOR=DarkRed]*"/usr/include/gtk--"*[/COLOR] folder. Can anyone help me out in finding the location for[COLOR=RoyalBlue] **gtkmm.h**[/COLOR] c++ header? Has it been deprecated? When I read the tutorial on using gtkmm it showed that I must include this file, but when I include it ... the compiler just throws up a mass of errors??? :) Any help much appreciated...

---

### Post by SledgeHammer_999 on 2010-08-07
from: [http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-basics-simple-example.html.en](http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-basics-simple-example.html.en)

```
g++ simple.cc -o simple `pkg-config gtkmm-2.4 --cflags --libs`
```

(pkg-config outputs the correct path for gtkmm)

---

### Post by robogenus on 2010-08-08
Thanks SledgeHammer_999 for your reply. I just found a file in ubuntu jaunty 9.04 '/usr/includes/gtk--.h' and it  seems to be a header file that mainly includes all the other gtk--  (gtkmm) header files that are found in '/usr/includes/gtk--'  folder. So  I guess they renamed the gtkmm.h file to gtk--.h or so it seems. I also realized I needed to 'sudo apt-get install  libgtkmm-2.4-dev' install the development package. Which I only had the binaries installed. Hopefully, I can get this going now. I'll be back and let all know how it goes.

---

### Post by robogenus on 2010-08-08
Finally discovered that I needed to download the Gtkmm Dev Package 'libgtkmm-2.4-dev' and then create the header 'appname.h' and source files 'appname.cpp' then compile the application on the command line using " g++ appname.cpp -o appname `pkg-config gtkmm-2.4 --cflags --libs` " command with the --cflags and --libs options. This worked great if the syntax is written correctly. Now, how to compile and run it within CodeLite and building UI with Glade and GtkBuilder.

---


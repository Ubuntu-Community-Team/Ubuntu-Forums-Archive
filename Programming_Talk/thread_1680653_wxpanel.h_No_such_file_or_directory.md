---
title: "wx/panel.h: No such file or directory"
date: 2011-02-02
forum: Programming Talk
---

### Post by gwbcomm on 2011-02-02
using -  Release 10.10 - Code Blocks 10.05

I can program and run wxwidgets apps without any problems.

I can program and run cpp apps without problems.

When I try to add a wxpanel, wxdialog or any other wxitem to ANY existing c++ project, including 'hello world', I get many errors associated with header files, " wx/panel.h: No such file or directory" and any other wx/* related header. I have tried the 'g++ hworld.cpp `wx-config --libs` `wx-config --cxxflags` -o hworld' and any other commands I can find in numerous forums. I haver performed the make install and ldconfig so many times I had to reinstall ubuntu from the ground up. I am obviously doing something wrong. I hope there  is help out there. I hate Windblows.

---

### Post by gmargo on 2011-02-02
I had no problem compiling a "hello world" program with an added '#include "wx/panel.h"' line.
I started with [http://www.wxwidgets.org/docs/tutorials/hworld.txt](http://www.wxwidgets.org/docs/tutorials/hworld.txt) and compiled it with the command you gave.

> ... performed the make install and ldconfig so many times ...
Did you compile the wxwidgets library yourself?  Or are you using the libraries from the repository? (I used the 2.8 version in the repository.)

```

$ diff -u hworld.txt hworldpanel.cpp
--- hworld.txt  2009-11-16 12:30:11.000000000 -0800
+++ hworldpanel.cpp     2011-02-02 18:56:59.519845609 -0800
@@ -3,6 +3,7 @@
  */
 
 #include "wx/wx.h" 
+#include "wx/panel.h"
 
 class MyApp: public wxApp
 {


$ g++ hworldpanel.cpp $(wx-config --libs) $(wx-config --cxxflags) -o hworldpanel

```I have these wxwidgets packages installed:
```

$ dpkg --get-selections | grep wx | sort | awk '{print $1;}'
libwxbase2.8-0
libwxbase2.8-dev
libwxgtk2.8-0
libwxgtk2.8-dev
wx2.8-headers
wx-common

```

---

### Post by gwbcomm on 2011-02-03
gmargo

I am using the libraries from the repository.

when I run the command:
     dpkg --get-selections | grep wx | sort | awk '{print $1;}'

I have;

libwxbase2.6-0
libwxbase2.6-dev
libwxbase2.8-0
libwxbase2.8-dbg
libwxbase2.8-dev
libwxgtk2.6-0
libwxgtk2.6-dev
libwxgtk2.8-0
libwxgtk2.8-dbg
libwxgtk2.8-dev
libwxsmithlib0-dev
libwxsmithlib0
wx2.6-headers
wx2.8-doc
wx2.8-examples
wx2.8-headers
wx2.8-i18n
wx-common
wxformbuilder

The "http://www.wxwidgets.org/docs/tutorials/hworld.txt" compiles and runs using  "g++ hworld.cpp $(wx-config --libs) $(wx-config --cxxflags) -o hworld".

When I try the file using codeblocks I get "wx/panel.h: No such file or directory"

When I change the #include "wx/wx.h" to #include "/home/gary/Downloads/wxX11-2.8.11/include/wx/wx.h"
the error moves to another line --#include "wx/setup.h"

I am thinking that when I add a wxpanel to a existing project, codeblocks no longer finds the header files. 

When I use codeblocks to build stand alone wxsmith programs, all files are found and the program compiles and runs.

What is missing? 

Thanks for pointing me in the right direction.



Gary

---

### Post by gmargo on 2011-02-04
You have to configure the **codeblocks** project, just like you had to tell **g++** what the additional wx options were.

Here's how to do it:  In your codeblocks window, with the project open, navigate to Project->Build options...

Under the "Compiler settings" tab, click on the "other options" sub-tab.  I have just a "-fexceptions" in there by default.  Add another line giving the wx-config command in backticks (the $() form didn't work for me):
```

`wx-config --cxxflags`

```Now click on the "Linker settings" tab, and in the "Other link options" window, add
```

`wx-config --libs`

```Now click "OK" and Build the project again.

---

### Post by gwbcomm on 2011-02-04
I had previously tried flaggs, but without the wx-config. Your info fixed the errors.


Thanks

---


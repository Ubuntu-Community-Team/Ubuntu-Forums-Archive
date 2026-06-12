---
title: "wxgtk libraries missing"
date: 2006-12-19
forum: Programming Talk
---

### Post by studiesrule on 2006-12-19
When I try to compile a program in wx, using the presribed method in the tutorial and the install notes, I keep getting this error:
```

error while loading shared libraries: libwx_gtk2_xrc-2.6.so.0: cannot open shared object file: No such file or directory

```

I've written the following makefile:
```

## Minimal WxTest

CC = gcc

#Output from wx-config --libs
WX_LIBS= -L/usr/local/lib -pthread   -lwx_gtk2_xrc-2.6 -lwx_gtk2_qa-2.6 -lwx_gtk2_html-2.6 -lwx_gtk2_adv-2.6 -lwx_gtk2_core-2.6 -lwx_base_xml-2.6 -lwx_base_net-2.6 -lwx_base-2.6

#Output from wx-config --cxxflags
WX_CXXFLAGS= -I/usr/local/lib/wx/include/gtk2-ansi-release-2.6 -I/usr/local/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA

wxhello: wxhello.o
	$(CC) -o wxhello wxhello.o $(WX_LIBS)
wxhello.o: wxhello.cpp
	$(CC) $(WX_CXXFLAGS) -c wxhello.cpp -o wxhello.o
clean:
	rm -f *.o

```

It give no compiler or linker warnings. I've been facing this problem continously now. I tried to compile using the KDevelop's automatic makefile generator and all, and that too failed.
I have the following relevant packages installed:

wx-widgets 2.6.3 (compiled version, installed with cleaninstall)
wx-common
wx-headers
libgtk-2.0 -0 -common -dev -bin -cli
libwxgtk2.6.0 -0 -dev
libwxbase2.6.0

Thanks for the help

---

### Post by studiesrule on 2006-12-19
I've found that the problem is that the repo version of wxWidgets doesn't have these files (oddly), but is the default libraries. By rerouting all the references to the new complied libary, I was able to solve to problem.
I have a question as to how to make the complied library the default library, that is referred to by other apps?

---


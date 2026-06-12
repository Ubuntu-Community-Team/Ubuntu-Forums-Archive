---
title: "how to compile windows .exe on ubuntu using mingw"
date: 2008-03-25
forum: Programming Talk
---

### Post by kalesh7 on 2008-03-25
I'm pretty new to this and I have searched but didn't get anything that could help me resolve this problem.
I want to create a windows exe using mingw (ubuntu) 
I am trying to compile a program  that uses a number of source files,
I am using wxwidgets(maybe the problem lies there)
the command I use for compiling linux is ```
g++ main.cpp `wx-config --libs` `wx-config --cxxflags` -c 
``` changing the cpp files each time then linking object files
well that works fine
the prob starts when trying to use mingw 
```
i586-mingw32msvc-g++ main.cpp `wx-config --libs` `wx-config --cxxflags` -c 
```

gives out a lot of errors
```
i586-mingw32msvc-g++: unrecognized option `-pthread'
i586-mingw32msvc-g++: unrecognized option `-pthread'
In file included from /usr/include/wx-2.8/wx/defs.h:21,
                 from /usr/include/wx-2.8/wx/wx.h:15,
                 from main.h:1,
                 from main.cpp:1:
/usr/include/wx-2.8/wx/platform.h:518:33: wx/msw/libraries.h: No such file or directory
In file included from /usr/include/wx-2.8/wx/wx.h:15,
                 from main.h:1,
                 from main.cpp:1:
/usr/include/wx-2.8/wx/defs.h:2773: error: conflicting declaration 'typedef struct GtkWidget*WXWidget'
/usr/include/wx-2.8/wx/defs.h:2564: error: 'WXWidget' has a previous declaration as `typedef void*WXWidget'
/usr/include/wx-2.8/wx/defs.h:2773: error: declaration of `typedef struct GtkWidget*WXWidget'
/usr/include/wx-2.8/wx/defs.h:2564: error: conflicts with previous declaration `typedef void*WXWidget'
/usr/include/wx-2.8/wx/defs.h:2773: error: declaration of `typedef struct GtkWidget*WXWidget'
/usr/include/wx-2.8/wx/defs.h:2564: error: conflicts with previous declaration `typedef void*WXWidget'
In file included from /usr/include/wx-2.8/wx/utils.h:21,
                 from /usr/include/wx-2.8/wx/cursor.h:41,
                 from /usr/include/wx-2.8/wx/event.h:22,
                 from /usr/include/wx-2.8/wx/wx.h:25,
                 from main.h:1,
                 from main.cpp:1:
/usr/include/wx-2.8/wx/filefn.h:379: error: zero width for bit-field `wxAssert_380::BadFileSizeType'
In file included from /usr/include/wx-2.8/wx/generic/filedlgg.h:15,
                 from /usr/include/wx-2.8/wx/gtk/filedlg.h:13,
                 from /usr/include/wx-2.8/wx/filedlg.h:210,
                 from /usr/include/wx-2.8/wx/wx.h:94,
                 from main.h:1,
                 from main.cpp:1:
/usr/include/wx-2.8/wx/listctrl.h:32:33: wx/msw/listctrl.h: No such file or directory
In file included from /usr/include/wx-2.8/wx/generic/filedlgg.h:15,
                 from /usr/include/wx-2.8/wx/gtk/filedlg.h:13,
                 from /usr/include/wx-2.8/wx/filedlg.h:210,
                 from /usr/include/wx-2.8/wx/wx.h:94,
                 from main.h:1,
                 from main.cpp:1:
/usr/include/wx-2.8/wx/listctrl.h:44: error: expected class-name before '{' token
/usr/include/wx-2.8/wx/listctrl.h: In constructor `wxListView::wxListView(wxWindow*, wxWindowID, const wxPoint&, const wxSize&, long int, const wxValidator&, const wxString&)':
/usr/include/wx-2.8/wx/listctrl.h:55: error: `Create' was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function `void wxListView::Select(long int, bool)':
/usr/include/wx-2.8/wx/listctrl.h:64: error: `SetItemState' was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function `void wxListView::Focus(long int)':
/usr/include/wx-2.8/wx/listctrl.h:70: error: `SetItemState' was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h:71: error: `EnsureVisible' was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function `long int wxListView::GetFocusedItem() const':
/usr/include/wx-2.8/wx/listctrl.h:77: error: `GetNextItem' was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function `long int wxListView::GetNextSelected(long int) const':
/usr/include/wx-2.8/wx/listctrl.h:82: error: `GetNextItem' was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function `bool wxListView::IsSelected(long int) const':
/usr/include/wx-2.8/wx/listctrl.h:88: error: `GetItemState' was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function `void wxListView::SetColumnImage(int, int)':
/usr/include/wx-2.8/wx/listctrl.h:98: error: `SetColumn' was not declared in this scope
In file included from /usr/include/wx-2.8/wx/gtk/filedlg.h:13,
                 from /usr/include/wx-2.8/wx/filedlg.h:210,
                 from /usr/include/wx-2.8/wx/wx.h:94,
                 from main.h:1,
                 from main.cpp:1:
/usr/include/wx-2.8/wx/generic/filedlgg.h: At global scope:
/usr/include/wx-2.8/wx/generic/filedlgg.h:251: error: expected class-name before '{' token

```

any ideas? please.

---

### Post by LaRoza on 2008-03-25
Well, it is linking to Linux libraries, so that won't work.

---

### Post by kalesh7 on 2008-03-25
> **LaRoza said:**
> Well, it is linking to Linux libraries, so that won't work.
Thanks, but I'm a little  to this, so I would appreciate if someone can tell me how I can make it link to windows wx libraries? and for that matter where I can get them?

---

### Post by LaRoza on 2008-03-25
> **kalesh7 said:**
> Thanks, but I'm a little  to this, so I would appreciate if someone can tell me how I can make it link to windows wx libraries? and for that matter where I can get them?

Get them here: [http://www.wxwidgets.org/downloads/](http://www.wxwidgets.org/downloads/)

Is there a reason you aren't running this in Windows?

I don't program for Windows, and I haven't cross compiled (never had to). If you write the code in Linux and use standard C++ and wxWidgets, you could just recompile it for Windows on Windows.

---

### Post by scourge on 2008-03-25
> **LaRoza said:**
> Is there a reason you aren't running this in Windows?

I actually found it easier, not to mention more convenient, to set up the cross-compiling environment, than trying to compile in Windows. And I can even test the Windows version with wine, so there's no need to boot into Windows at all.

Here's a pretty good guide for Cross-Compiling wxWidgets applications: [http://www.wxwidgets.org/wiki/index.php/Cross-Compiling_Under_Linux](http://www.wxwidgets.org/wiki/index.php/Cross-Compiling_Under_Linux)

Here's the Makefile for the Windows build of one of my projects:
```

# Mingw Makefile for Mpe


# C++ compiler 
CXX = i586-mingw32msvc-g++

# Standard flags for C++ 
CXXFLAGS = -O3 -pipe

# Standard preprocessor flags (common for CC and CXX) 
CPPFLAGS = 

# Standard linker flags 
LDFLAGS = 

# Location and arguments of wx-config script 
WX_CONFIG = /usr/local/i586-mingw32msvc/bin/wx-config

# C++ flags to use with wxWidgets code 
WX_CXXFLAGS = `$(WX_CONFIG) --cxxflags`



# -------------------------------------------------------------------------
# Do not modify the rest of this file!
# -------------------------------------------------------------------------

### Variables: ###

CPPDEPS = -MT$@ -MF`echo $@ | sed -e 's,\.o$$,.d,'` -MD
MPE_CXXFLAGS =  -I.  $(WX_CXXFLAGS) $(CPPFLAGS) $(CXXFLAGS)
MPE_OBJECTS =  \
	gui.o gui_func.o pnode.o pmaterial.o pobject.o pfile.o

### Conditionally set variables: ###



### Targets: ###

all: mpe.exe

install: all

uninstall: 

clean: 
	rm -f ./*.o
	rm -f ./*.d
	rm -f ./mpe.exe

mpe.exe: $(MPE_OBJECTS)
	$(CXX) -o $@ $(MPE_OBJECTS) $(LDFLAGS)   `$(WX_CONFIG) --libs core,base`

.cpp.o:
	$(CXX) -c -o $@ $(MPE_CXXFLAGS) $(CPPDEPS) $<

.PHONY: all install uninstall clean


# Dependencies tracking:
-include ./*.d

```

---


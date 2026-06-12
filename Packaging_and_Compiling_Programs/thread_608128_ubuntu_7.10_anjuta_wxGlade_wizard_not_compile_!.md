---
title: "ubuntu 7.10 anjuta wxGlade wizard not compile !"
date: 2007-11-09
forum: Packaging and Compiling Programs
---

### Post by queency on 2007-11-09
wxWidget anjuta not compiled ubuntu7.10
Hi guys

I recently installed ubuntu7.10, anjuta, wxGlade
I tried to build the "hello world" in new wxWidget wizard project
no luck so far

first i got the
make main.o
/home/yair/Projects/wxwin-addbook/src/main.cc:27:19: error: wx/wx.h: No such file or directory
/home/yair/Projects/wxwin-addbook/src/main.cc:30: error: expected class-name before ‘{’ token
/home/yair/Projects/wxwin-addbook/src/main.cc:37: error: expected constructor, destructor, or type conversion before ‘bool’
make: *** [main.o] Error 1

after trying to compile myself with :
g++ main.cc -I /usr/include/wx-2.8/
i got (a partial errors)

/usr/include/wx-2.8/wx/chkconf.h:598:9: error: #error "wxUSE_HYPERLINKCTRL must be defined."
/usr/include/wx-2.8/wx/chkconf.h:606:9: error: #error "wxUSE_HTML must be defined."
/usr/include/wx-2.8/wx/chkconf.h:627:9: error: #error "wxUSE_ICO_CUR must be defined."
/usr/include/wx-2.8/wx/chkconf.h:635:9: error: #error "wxUSE_IFF must be defined

In file included from /usr/include/wx-2.8/wx/wx.h:15,
from main.cc:27:
/usr/include/wx-2.8/wx/defs.h:42:13: error: #error "No Target! You should use wx-config program for compilation flags!"
In file included from /usr/include/wx-2.8/wx/memory.h:16,
from /usr/include/wx-2.8/wx/object.h:20,
from /usr/include/wx-2.8/wx/wx.h:16,
from main.cc:27:
/usr/include/wx-2.8/wx/string.h:164:4: error: #error "Please define string case-insensitive compare for your OS/compiler"
In file included from /usr/include/wx-2.8/wx/cmndata.h:17,
from /usr/include/wx-2.8/wx/wx.h:65,
from main.cc:27:

/usr/include/wx-2.8/wx/gdicmn.h:38: error: forward declaration of ‘struct wxRegion’
/usr/include/wx-2.8/wx/region.h: In member function ‘bool wxRegionBase::Xor(const wxRect&)’:
/usr/include/wx-2.8/wx/region.h:261: error: invalid use of undefined type ‘struct wxRegion’
/usr/include/wx-2.8/wx/gdicmn.h:38: error: forward declaration of ‘struct wxRegion’
/usr/include/wx-2.8/wx/window.h: At global scope:
/usr/include/wx-2.8/wx/window.h:82: error: field ‘font’ has incomplete type
/usr/include/wx-2.8/wx/window.h:85: error: field ‘colFg’ has incomplete type
/usr/include/wx-2.8/wx/window.h:89: error: field ‘colBg’ has incomplete type
/usr/include/wx-2.8/wx/window.h:1105: error: ‘WXWidget’ does not name a type
/usr/include/wx-2.8/wx/window.h:1107: error: ‘WXWidget’ has not been declared
/usr/include/wx-2.8/wx/window.h:1196: error: field ‘m_cursor’ has incomplete typ

and more !!
any suggestions ?

---


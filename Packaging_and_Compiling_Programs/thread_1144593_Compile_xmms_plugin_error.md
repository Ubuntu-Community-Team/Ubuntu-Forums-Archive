---
title: "Compile xmms plugin error"
date: 2009-04-30
forum: Packaging and Compiling Programs
---

### Post by SuperBo on 2009-04-30
I need xmms-mac plugin to play ape file so I have tried to compile it from source.
When I run ./configure everything is Ok but when I make, it show error!

```
/usr/include/mac/config.h:100:1: warning: this is the location of the previous definition
In file included from mac.cpp:7:
/usr/include/xmms/util.h:3:21: error: gtk/gtk.h: No such file or directory
In file included from mac.cpp:7:
/usr/include/xmms/util.h:9: error: expected constructor, destructor, or type conversion before '*' token
In file included from mac.cpp:8:
/usr/include/xmms/titlestring.h:80: error: expected constructor, destructor, or type conversion before '*' token
mac.cpp: In function 'char* get_tag_info(CAPETag*, wchar_t*)':
mac.cpp:68: warning: deprecated conversion from string constant to 'char*'
mac.cpp: In function 'char* mac_format_title_string(char*, CAPETag*)':
mac.cpp:114: warning: deprecated conversion from string constant to 'wchar_t*'
mac.cpp:115: warning: deprecated conversion from string constant to 'wchar_t*'
mac.cpp:116: warning: deprecated conversion from string constant to 'wchar_t*'
mac.cpp:117: warning: deprecated conversion from string constant to 'wchar_t*'
mac.cpp:118: warning: deprecated conversion from string constant to 'wchar_t*'
mac.cpp:119: warning: deprecated conversion from string constant to 'wchar_t*'
mac.cpp:120: warning: deprecated conversion from string constant to 'wchar_t*'
mac.cpp: In function 'void mac_about()':
mac.cpp:282: error: expected initializer before '*' token
mac.cpp:284: error: 'aboutbox' was not declared in this scope
mac.cpp:287: error: 'aboutbox' was not declared in this scope
mac.cpp:290: error: 'xmms_show_message' was not declared in this scope
mac.cpp:292: error: 'GTK_OBJECT' was not declared in this scope
mac.cpp:293: error: 'gtk_widget_destroyed' was not declared in this scope
mac.cpp:293: error: 'GTK_SIGNAL_FUNC' was not declared in this scope
mac.cpp:293: error: 'gtk_signal_connect' was not declared in this scope
make[2]: *** [libxmms_mac_la-mac.lo] Error 1
make[2]: Leaving directory `/home/superbo/xmms-mac-0.3.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/superbo/xmms-mac-0.3.1'
make: *** [all] Error 2 
```

sorry for my bad English. If you know, please help me solve it.
Thank you!

---


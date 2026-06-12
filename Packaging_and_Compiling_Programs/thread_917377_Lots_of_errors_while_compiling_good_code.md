---
title: "Lots of errors while compiling good code"
date: 2008-09-11
forum: Packaging and Compiling Programs
---

### Post by MiKe402 on 2008-09-11
Hello!

I am trying to install the RoboCup 2d Simulator. When I try to compile I get many, many errors.

The simulator can be found here: [http://sourceforge.net/project/showfiles.php?group_id=24184](http://sourceforge.net/project/showfiles.php?group_id=24184)

This happens when I try to compile rcssmonitor, for instance. './configure' works just fine, but 'make' doesn't. I downloaded the C compiler, C++ compiler and Boost, but it doesn't seem to work when compiling.

Here's a small example of the errors.

```
rcssmonitor.xpm:569: warning: deprecated conversion from string constant to ‘char*’
2dview.C:510: error: expected constructor, destructor, or type conversion before ‘*’ token
2dview.C:511: error: ‘Pixmap’ does not name a type
2dview.C:512: error: ‘Window’ does not name a type
2dview.C:516: error: ‘Pixmap’ does not name a type
2dview.C:517: error: ‘Pixmap’ does not name a type
2dview.C:519: error: ‘GC’ does not name a type
2dview.C: In function ‘void init_4_tree_and_display()’:
2dview.C:550: error: ‘disp’ is not a member of ‘WIN’
2dview.C:550: error: ‘pixmap’ is not a member of ‘WIN’
2dview.C:550: error: ‘gc’ is not a member of ‘WIN’
2dview.C: At global scope:
2dview.C:577: error: expected ‘,’ or ‘...’ before ‘&’ token
2dview.C:577: error: ISO C++ forbids declaration of ‘XEvent’ with no type
2dview.C: In function ‘void print_event_type(int)’:
2dview.C:579: error: ‘event’ was not declared in this scope
2dview.C:580: error: ‘KeyPress’ was not declared in this scope
2dview.C:581: error: ‘KeyRelease’ was not declared in this scope
2dview.C:582: error: ‘ButtonPress’ was not declared in this scope
2dview.C:583: error: ‘ButtonRelease’ was not declared in this scope
2dview.C:584: error: ‘MotionNotify’ was not declared in this scope
2dview.C:585: error: ‘EnterNotify’ was not declared in this scope
2dview.C:586: error: ‘LeaveNotify’ was not declared in this scope
2dview.C:587: error: ‘FocusIn’ was not declared in this scope
2dview.C:588: error: ‘FocusOut’ was not declared in this scope
2dview.C:589: error: ‘KeymapNotify’ was not declared in this scope
```

I am very frustrated by this. Any help would be extremely appreciated!

---

### Post by wgrant on 2008-09-12
One must always look for the top most error. In this case it's missing includes; install libx11-dev and libxpm-dev.

---

### Post by MiKe402 on 2008-09-13
Thank you! I asked another person meanwhile and he told me the same thing. It worked.

Thanks again :)

---


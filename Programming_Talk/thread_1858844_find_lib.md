---
title: "find lib"
date: 2011-10-13
forum: Programming Talk
---

### Post by ahso4271 on 2011-10-13
dlerror:/apps/X-Plane/bla/bla.plugin/lin.xpl: undefined symbol: _ZN13GLDebugDrawer12setDebugModeEi

Hi 

how to find the lib to include at build? The header is in /usr 
but what corresponding lib to link?
Many thanks
Michael

---

### Post by Zugzwang on 2011-10-13
> **ahso4271 said:**
> dlerror:/apps/X-Plane/bla/bla.plugin/lin.xpl: undefined symbol: _ZN13GLDebugDrawer12setDebugModeEi

Hi 

how to find the lib to include at build? The header is in /usr 
but what corresponding lib to link?
Many thanks
Michael

Provided that you are using some library that has a Ubuntu package (you didn't provide any information on which library it is): Check out in which Ubuntu package the header file is. Then, look though the package contents for .so or .a files, and use these.

---

### Post by karlson on 2011-10-13
> **ahso4271 said:**
> dlerror:/apps/X-Plane/bla/bla.plugin/lin.xpl: undefined symbol: _ZN13GLDebugDrawer12setDebugModeEi

Hi 

how to find the lib to include at build? The header is in /usr 
but what corresponding lib to link?
Many thanks
Michael

Not sure I understand the question here.  If your headers are in /usr and I assume /usr/include, then it stands to reason that the library this header, whichever it is would have a library installed in /usr/lib.

Also if you need an answer on what library the missing symbol is in you might want to provide more details such as what is this plugin for and what is it supposed to do.

---


---
title: "menu and toolbar basic question in qt...."
date: 2009-07-13
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-13
in Qt 4.5, we can create menus and toolbars both in Qt designer and by writing c++ code,
so are both having same efficency or what?
which option is better one to use?? 
for big projects is it worth making menus and toolbars using Qt designer??
please explain this, i'm really din't understand.
thanks

---

### Post by JordyD on 2009-07-14
> **abhilashm86 said:**
> in Qt 4.5, we can create menus and toolbars both in Qt designer and by writing c++ code,
so are both having same efficency or what?
which option is better one to use?? 
for big projects is it worth making menus and toolbars using Qt designer??
please explain this, i'm really din't understand.
thanks

Using Qt Designer creates .ui files, when you build your project, you turn those files into c++ header files. Thus, there is no loss in efficiency.

Using Qt Designer just makes it easier to create your GUIs. Plus, it organizes everything for you.

---


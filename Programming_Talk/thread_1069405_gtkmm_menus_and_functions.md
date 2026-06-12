---
title: "gtkmm menus and functions"
date: 2009-02-13
forum: Programming Talk
---

### Post by r4z0rw0lf on 2009-02-13
hello, if i had a c++ function, say, void X(int x,int y);
and i wanted to add to a gtk menu to execute how would do this?
i am fairly new to gtkmm.:confused:

---

### Post by r4z0rw0lf on 2009-02-14
alright sigc::bind(sigc::mem_fun(*this,&X),1,1); works, but when i receive the variable it is blank :(
EDIT the ints work but not chars sorry bout that :(

---


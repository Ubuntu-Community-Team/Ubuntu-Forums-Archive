---
title: "[SOLVED] Anjuta Help"
date: 2008-05-23
forum: Programming Talk
---

### Post by MDSmith2 on 2008-05-23
Hello Everyone.
I am using Anjuta and i want to use the gtkmm library's but i can't find out how to change the compile command so i can add the right arguments.

Thanks you.

---

### Post by cdekter on 2008-05-25
> **MDSmith2 said:**
> Hello Everyone.
I am using Anjuta and i want to use the gtkmm library's but i can't find out how to change the compile command so i can add the right arguments.

Thanks you.

If you switch to the Project view in the left pane, you can right click on your build target/binary and select properties. There is a section in the properties dialog where you can specify compiler flags (by clicking the expander). 

You shouldn't really need to change anything in there though, Anjuta is pretty well set up for shared library support etc, chances are that what you are trying to do by changing the compile command manually can be achieved some other way.

---

### Post by MDSmith2 on 2008-05-26
Great thanks!

---


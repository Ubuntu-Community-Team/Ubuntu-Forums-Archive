---
title: "Generate extra keystrokes from one key press"
date: 2012-09-07
forum: Programming Talk
---

### Post by thombark on 2012-09-07
I would like to generate the "CTRL-B" keystroke whenever any key is pressed. This would then be passed onto the application. For example, I would type ABC and this would be seen by the editor application as CTRL-B a CTRL-B b CTRL-B c.
I do not need to have any logging functionality. 

Thanks.

---

### Post by conradin on 2012-09-10
have a look at xmacros Im not sure if that can do what you want easily. Otherwise youll be looking at cooking your IO with raw vs cooked I/O.
[http://www.lafn.org/~dave/linux/terminalIO.html](http://www.lafn.org/~dave/linux/terminalIO.html)
special characters like ^B

---


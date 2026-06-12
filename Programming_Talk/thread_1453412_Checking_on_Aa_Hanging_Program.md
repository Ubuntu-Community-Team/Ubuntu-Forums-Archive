---
title: "Checking on Aa Hanging Program"
date: 2010-04-13
forum: Programming Talk
---

### Post by newport_j on 2010-04-13
I have a large program - 55 modules or functions. It hangs way into the program. I can walk through it to locate that point, and maybe I will reach t before the next presidential election. I doubt it. 
What tools are available to allow one to get to that hanging point in a large program and not have to go step by step until it is found?

Stepping through it slowly step by step too horrible to contemplate. I know there must be an easier way. What is it?

Newport_j

---

### Post by newport_j on 2010-04-13
no this problem has not been resolved. Please answer if you have an idea.
 
Newport_j

---

### Post by talonmies on 2010-04-13
Compile it for debugging, run it in gdb, wait a sufficient time for the program to reach the "hung" state, then hit control-c. The debugger will show you where in the code it stopped, and typing bt will show the back trace from through all the calling functions to main(), so you can see what code path the program must have followed to reach the point where it is hanging. You also can inspect the contents of variables and see the contents of each function/frame in the call stack.

It should allow you to pinpoint where things are going wrong.

---

### Post by lavinog on 2010-04-13
what language are you using?

---


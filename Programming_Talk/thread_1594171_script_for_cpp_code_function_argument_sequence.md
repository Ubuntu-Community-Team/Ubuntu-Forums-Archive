---
title: "script for cpp code function argument sequence"
date: 2010-10-12
forum: Programming Talk
---

### Post by Blackbug on 2010-10-12
I have a cpp code.
 
code snippet..
 
```

class XYZ
{
    void func1(int arg1, int arg2, string arg3, char* arg4);
};

```
 
I need to write a script which could check the sequence of arguments arg1 and arg2.
Since, arg1 and arg2 are both int types, compiler wont give any error if values are swapped by the callee. Like this there are various other functions in the code base using these arg1 and arg2.
 
But, for my applications functionality the proper sequence is very crucial.
The code base is big and thus I want to write a script which could check the sequence of arg1 and arg2 in all the functions using these arguments.
 
I hope I could narrate what exactly i want to do..

---

### Post by Some Penguin on 2010-10-12
It's not exactly clear how you'd expect a program to actually do that (i.e. understand the *meaning* of arguments), especially in a language which doesn't support annotations (unless I've missed some major changes in the standard, which is possible).

One could use a script to check in the very particular case where callers and callees actually agree on the names of the variables, but that's it.

---


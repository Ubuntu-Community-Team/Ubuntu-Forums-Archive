---
title: "Segmentation Fault?"
date: 2008-09-16
forum: Programming Talk
---

### Post by armageddon08 on 2008-09-16
I've just started C++ programming. While compiling some programs in Linux, I'm having this "Segmentation Fault" which I don't get while compiling those in Turbo C++ in Windows. What is this "Segmentation Fault"? Why does this happen?:confused:

---

### Post by monkeyking on 2008-09-16
You're trying to use memory you haven't allocated,
or you don't have access to.

an example
```

int main(){
int var[5]
var[5]=3;//might cause segfault
return 0;
}

```

This might or might not happen, since the compiler will normally allocate to the nearest zero offset of your arch.

An excellent tool for finding these error are gdb and valgrind.
And always remember to compile with -g or -ggdb.

good luck

edit:
you should gdb like this, compile the program with -ggdb, thiw will make debugging a lot easier. If you program is called ./a.out then you woulde invoke gdb with gdb ./a.out . And afterward run followed by the pars your program needs

---

### Post by armageddon08 on 2008-09-16
> **monkeyking said:**
> You're trying to use memory you haven't allocated,
or you don't have access to.

an example
```

int main(){
int var[5]
var[5]=3;//might cause segfault
return 0;
}

```

This might or might not happen, since the compiler will normally allocate to the nearest zero offset of your arch.

An excellent tool for finding these error are gdb and valgrind.
And always remember to compile with -g or -ggdb.

good luck

edit:
you should gdb like this, compile the program with -ggdb, thiw will make debugging a lot easier. If you program is called ./a.out then you woulde invoke gdb with gdb ./a.out . And afterward run followed by the pars your program needs

Then why don't I get this fault while compiling in Turbo C++?

---

### Post by NovaAesa on 2008-09-17
You will have to post the code, otherwise there's not really much we can do. When you have coded something incorrectly, sometimes a segfault will occur and sometimes it wont. If it doesn't occur, then there is a change you are going to have logic errors instead or system instability. Believe me, tracking down why a segfault is happening is much easier than working out why you programme's output isn't quite right.

---

### Post by Zugzwang on 2008-09-17
> **NovaAesa said:**
> Believe me, tracking down why a segfault is happening is much easier than working out why you programme's output isn't quite right.

...and the reason for that is that you have this nice tool called "valgrind" which helps you finding the problem in your program. Use the search function in this forum (or google) to search for explanations how to use it.

---

### Post by Mordred on 2008-09-17
As mentioned before, try using a debugger to find your error.
You can use gdb from the command line or you can choose for a
graphical frontend:

ddd : data display debugger - an X frontend for gdb
nemiver : a gtk frontend for gdb

next to these also eclipse and netbeans have C/C++ plugins that
provide debugging support.

A segmentation fault occurs when your program tries to access memory
that it is not allowed to.
Try stepping through your code until the error occurs.
Then find out why it is writing to memory you did not allocate.

Good luck!

---


---
title: "The exit() function in C"
date: 2007-03-22
forum: Programming Talk
---

### Post by akudewan on 2007-03-22
I've made a program that has exit codes of 1, 2 etc. in places where an error is encountered. Is there anyway I can find out the return code or exit code when a program ends? Would this help me find out where exactly the program terminated, and help me fix the problem?

What is the approach generally used by programmers? Is the exit() function used to diagnose where the program has quit?

---

### Post by po0f on 2007-03-22
akudewan,

If you run your program from a terminal, you can get the return code of the last command with:

```
$ my_program
$ echo $?
```

'**$?**' is a special bash variable that holds the return code of the last run command.  It's useful to use in your scripts as well.

---

### Post by akudewan on 2007-03-22
Sweet :) Thanks

---

### Post by j_g on 2007-03-22
I think that the best approach to fixing errors in a program is to become adept with a debugger (and get the best debugger you can find). Being able to look at the values of variables, in particular, can identify many of your errors. And all decent debuggers will show you the values of any of your variables, at any point in the program. (Usually, the debugger has some window where you can enter the name of the variable whose value you want to see. And the debugger will display the variable's current value next to the name. As you "step", ie, execute, each one of the instructions in your source code, the debugger will update its display of the variable's value).

Usually, you set a breakpoint on an instruction before where you're getting the crash, and then start "stepping" into each instruction, while observing the values of pertinent variables. Eventually, you'll see something you don't expect, and there's your bug.

---

### Post by lnostdal on 2007-03-22
I'd never use the exit-function for that.

__FILE__ and __LINE__ ( [http://gcc.gnu.org/onlinedocs/cpp/Standard-Predefined-Macros.html](http://gcc.gnu.org/onlinedocs/cpp/Standard-Predefined-Macros.html) ) might be more suitable. Also see `man 3 perror' and `man 3 strerror' .. etc.

If the program terminates by ways of a signal or condition you can use a debugger. Remember to compile with -g, you'll then get more info from a backtrace. From plain GDB getting a backtrace works something like this:

```

gcc -o prog -g -Wall prog.c
gdb prog
run
(program crashes: because of a SIGSEGV for instance)
bt

```

..typing bt and pressing enter reveals a backtrace with filename and line-numbers mentioned. Consider using a front-end to GDB like DDD or KDBG.

---

### Post by akudewan on 2007-03-22
Thanks, I'm looking into it right now.

---


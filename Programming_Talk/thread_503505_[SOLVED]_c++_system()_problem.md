---
title: "[SOLVED] c++ system() problem??"
date: 2007-07-18
forum: Programming Talk
---

### Post by rbprogrammer on 2007-07-18
ok, so lets say i want to write some code in c++ that will execute a system command, but the problem is that there is no way that i know of to catch the output from system()..

how would i execute a system command and be able to catch the output if there should be any??

also, this is probably a OS specific question, so i would like to know how to do this in linux and windows as well.  i want to know this for linux b/c it would help me a lot, and i would like to know how to do it in windows only to be more flexible should something come up where i have to write a windows program :( ..

any help is greatly appreciated,

---

### Post by geraldm on 2007-07-18
Well, you did say you wanted the result in C++, and since you also want
portability between OSes, you could embed ruby in C++, then let ruby
execute the command within IO.popen("ls\n").  There are helpful hints
on the main ruby websites.  It is simpler to understand passing a command
to a ruby program which creates a regular text file.  Then from C++,
just open the filename.
Gerald

---

### Post by Modred on 2007-07-18
Check out the [GNU C Library Manual](http://www.gnu.org/software/libc/manual/html_node/index.html).  Scroll down to the section on processes and read up on the different uses of system(), fork() and exec() functions.

As for actually getting output from a command just using system(), you could do something like the following:

[list]
[*]Call a process with system() and in the command, redirect the output to a temporary filename you generate
[*]Have your program wait until the external command finishes
[*]Load and parse the temporary file
[/list]

---

### Post by Mr. C. on 2007-07-18
```
man 3 popen
```

MrC

---

### Post by Oliver_FF on 2007-07-18
In Windows, you can call CreateProcess() - look it up in the MSDN - the last two parameters it takes are STARTUPINFO and PROCESS_INFORMATION.

In the STARTUPINFO object you can define the standard input and output streams hStdInput and hStdOutput.

---

### Post by rbprogrammer on 2007-07-25
> **Modred said:**
> Check out the [GNU C Library Manual](http://www.gnu.org/software/libc/manual/html_node/index.html).  Scroll down to the section on processes and read up on the different uses of system(), fork() and exec() functions.

As for actually getting output from a command just using system(), you could do something like the following:

[list]
[*]Call a process with system() and in the command, redirect the output to a temporary filename you generate
[*]Have your program wait until the external command finishes
[*]Load and parse the temporary file
[/list]

so doing something like:
```
ls -a >> TEMPFILE
```
seems so easy, why didn't i think of that earlier :lolflag: ??

---


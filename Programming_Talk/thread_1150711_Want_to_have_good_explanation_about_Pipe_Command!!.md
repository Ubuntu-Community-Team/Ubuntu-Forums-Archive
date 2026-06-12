---
title: "Want to have good explanation about Pipe Command!!"
date: 2009-05-06
forum: Programming Talk
---

### Post by r1e1z1a on 2009-05-06
Hello My Friends !

I want to have good Documentation about "pipe"
command!
I want to use it for sorting array on disk.(in c++)

Can you give me a link or file about it!? 

Thanks!!:P

---

### Post by zacktu on 2009-05-06
Terminal-oriented programs read standard input (stdin) and write standard output (stdout).  For example, the command

man pipe

prints the manual page in your terminal window (stdout).  If you write

man pipe | wc

the the output of the man command is piped into the wc (wordcount) command.  The result is

125 929 6538

indicating that the man page for pipe has 125 lines, 929 words, and 6538 bytes.

Whatever your C++ program reads from stdin can be piped into it from another program that writes stdout.  Whatever your C++ program writes to stdout can be piped into another program that reads stdin.

---

### Post by benj1 on 2009-05-06
thats why you have

cin (stdin)
cout (stdout)
cerr (stderr) (not handed to a pipe, you don't want awk processing error messages)

```
info coreutils Putting the tools together
```

has a fairly good explanation

---


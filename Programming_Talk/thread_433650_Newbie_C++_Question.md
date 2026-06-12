---
title: "Newbie C++ Question"
date: 2007-05-05
forum: Programming Talk
---

### Post by bobbocanfly on 2007-05-05
I am writing a simple command line password generator in C++. I have just started learning C++ so not really sure with most things.

I have written 2 applications "pwgen" (For generating one password) and "pwgenbatch" (For generating lots at the same time). But i am wanting both of them to be in the same executable, so batch mode could be run by typing "pwgen -b".

Can i do this with C++?

---

### Post by DnasTheGreat on 2007-05-05
Look into getopt and getopt_long. It lets you parse command line options easily. (It's in libc, but you can use it in C++ just fine.)

[http://www.gnu.org/software/libc/manual/html_node/Getopt.html](http://www.gnu.org/software/libc/manual/html_node/Getopt.html)

(BTW, there's already a program call pwgen (in apt) that does just that. :) Except that it also has heuristics to make pronounceable passwords like aed5Eegh.)

---

### Post by bobbocanfly on 2007-05-05
Thanks for that link, ill have to rename mine to passgen then :D

---

### Post by DnasTheGreat on 2007-05-05
No problem.

There was some better documentation in some book I found in the library once, but I forget what it was. (GNU docs are sometimes kinda technical and hard to read if you're not used to such things.)

The man pages are also good. Install manpages-dev.

Might also want to mention:
To get command line arguments, you need a slightly different prototype for main.

Instead of
```
int main()
```

You want
```
int main(int argc, char *argv[])
```

argc (argument count) then becomes the number of arguments sent, including the name the program was called by.
argv (argument vector) becomes an array of arrays of chars. :) In other words, an array of strings. (std::string is part of C++. In C one uses arrays of NUL-terminated chars for strings)

So, for
```
echo foo bar baz
```
argc is 4, argv[0] is "echo", argv[1] is "foo", etc.

You can parse argc and argv yourself, but this is sometimes a pain. getopt and getopt_long do this for you and this way all programs parse the same way.

getopt is part of POSIX and does the -a -bc, etc. getopt_long is a GNU extension and can also do --some-long-option. getopt is completely portable across UNIXes while getopt_long might not be, but most places implement it if I recall correctly.

In any case, I wouldn't let that be much of a problem. If you decide to release your program and someone yells at you for using getopt_long, there is a way of including the GNU version into your build system so that it gets compiled if the system doesn't have it.

---

### Post by bobbocanfly on 2007-05-05
Finished the program, in batch mode it can generate 1 million 8 character passwords in around 47 seconds. Does anyone know where i could host it for free, so i can share it with family/friends?

---


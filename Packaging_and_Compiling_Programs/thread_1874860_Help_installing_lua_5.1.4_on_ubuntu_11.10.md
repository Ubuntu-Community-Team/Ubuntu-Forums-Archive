---
title: "Help installing lua 5.1.4 on ubuntu 11.10"
date: 2011-11-03
forum: Packaging and Compiling Programs
---

### Post by natethegreat131 on 2011-11-03
I am having trouble building lua 5.1.4 on ubuntu 11.10.  When i run ```
make linux
``` or ```
make linux test
```, i get the following:

> luaconf.h:275:31: fatal error: readline/readline.h: No such file or directory
compilation terminated.

---

### Post by SevenMachines on 2011-11-04
Looking for the missing header
```
$ apt-file search readline/readline.h
guile-1.6-dev: /usr/include/guile-readline/readline.h
libreadline-gplv2-dev: /usr/include/readline/readline.h
libreadline6-dev: /usr/include/readline/readline.h
```

So I'd use libreadline6-dev out of those
```
$ sudo apt-get install libreadline-dev
```

---

### Post by R_MIR on 2011-12-16
Hey i was just 
having that same 
problem and i found the 
answer for it.


first of all you must go in your selected folder ex :
CODE: cd /home/robert

then you must take lua
CODE: wget [http://www.lua.org/ftp/lua-5.1.4.tar.gz](http://www.lua.org/ftp/lua-5.1.4.tar.gz)

then you must unpack it
CODE: tar xzvf lua-5.1.4.tar.gz

then enter the selected directory
CODE: cd /home/robert/lua-5.1.4

then install a required library
CODE: sudo apt-get install libreadline5-dev

the you can install lua by running
CODE: sudo make linux install

then close terminal using
Ctrl + - 
then Ctrl + d

after you closed the terminal 
open it again using Ctrl + Alt + t

then just Run lua
and it should be working.
:D

---


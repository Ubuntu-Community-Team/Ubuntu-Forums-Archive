---
title: "g++ issues"
date: 2007-12-21
forum: Programming Talk
---

### Post by soluphobe on 2007-12-21
This must be one of the silliest issues ever, but I'm a newbie at  writing/compiling c++ and I've been having some problems trying to compile from the command line.

I have a file: hello.cpp, that is the standard Hello World program.
```
#include <iostream>

int main(){
  std::cout << "Hello world!\n";
  return(0);
}
```

I try to compile and run with:
```
stephen@sg-ubuntu:~/Documents/c++$ g++ -g -Wall -ohello -hello.cpp
stephen@sg-ubuntu:~/Documents/c++$ hello
The program 'hello' can be found in the following packages:
 * hello-dbs
 * hello-dehelper
 * hello
Try: sudo apt-get install <selected package>
bash: hello: command not found
stephen@sg-ubuntu:~/Documents/c++$
```

I've looked though the g++ manpage and I seem to be compiling correctly.   I tried running the .o file and got a 'command not found' error.  If I try 'c++ hello' I get about 10-15 lines of errors.  Is there something I'm just ignoring like a file extension?

---

### Post by Kimm on 2007-12-21
When executing the program, you should use "./hello" instead of "hello" :)

---

### Post by soluphobe on 2007-12-21
Wow...I can't believe I hadn't tried that...

Thanks a ton.  <goes off to beat head against wall>

---


---
title: "Unable to compile, cout not part of std?"
date: 2017-01-10
forum: Programming Talk
---

### Post by fedora-refugee2 on 2017-01-10
I'm trying to compile a program using a makefile and getting the following error: Socket.cpp:135:7: error: ‘cout’ is not a member of ‘std’.

[ATTACH]273111[/ATTACH]

I found this when googling, 
[https://ubuntuforums.org/showthread.php?t=1873791](https://ubuntuforums.org/showthread.php?t=1873791)
The makefile uses g++ as opposed to gcc so that can't be my issue. I tried adding #include "iostream" but it did not help. Is there something wrong with the makefile?

---

### Post by spjackson on 2017-01-10
I can't tell whether there's something wrong with your Makefile without the source code. I suspect not, but even if there is it isn't causing your fault. If your source code uses
```

std::cout

```
then you need
```

#include <iostream>

```
at file scope before your use of std::cout, as per the thread you refer to. Note that that is not
```

#include "iostream"

```
nor iostream.h

For more help, source is needed.

---

### Post by fedora-refugee2 on 2017-01-10
The makefile is included as makefile.txt. I believe I added the include with the <>, but get this:

bob_keane@bobs-laptop:~$ cd networking
bob_keane@bobs-laptop:~/networking$ make
g++    -c -o Socket.o Socket.cpp
g++    -c -o simple_server_main.o simple_server_main.cpp
simple_server_main.cpp:5:5: warning: second argument of &#8216;int main(int, int*)&#8217; should be &#8216;char **&#8217; [-Wmain]
 int main ( int argc, int argv[] )
     ^~~~
simple_server_main.cpp: In function &#8216;int main(int, int*)&#8217;:
simple_server_main.cpp:7:3: error: &#8216;cout&#8217; is not a member of &#8216;std&#8217;
   std::cout << "running....\n";
   ^~~
simple_server_main.cpp:35:7: error: &#8216;cout&#8217; is not a member of &#8216;std&#8217;
       std::cout << "Exception was caught:" << e.description() << "\nExiting.\n";
       ^~~
<builtin>: recipe for target 'simple_server_main.o' failed
make: *** [simple_server_main.o] Error 1

---

### Post by spjackson on 2017-01-11
> **spjackson said:**
> 
For more help, source is needed.
Since you are either unwilling or unable to post simple_server_main.cpp, I cannot really help. Sorry.

This ought to work for you:
```

$ cat hello.cpp
#include <iostream>

int main()
{
    std::cout << "Hello\n";
}

$ make hello
g++     hello.cpp   -o hello
$ ./hello
Hello

```

And this ought to give you the error you are seeing:
```

$ cat hello2.cpp
int main()
{
    std::cout << "Hello\n";
}

$ make hello2
g++     hello2.cpp   -o hello2
hello2.cpp: In function ‘int main()’:
hello2.cpp:3:2: error: ‘cout’ is not a member of ‘std’
  std::cout << "Hello\n";
  ^
<builtin>: recipe for target 'hello2' failed
make: *** [hello2] Error 1

```

---

### Post by fedora-refugee2 on 2017-01-11
Here is the source for simple_server_main.cpp. I had to change it to a text file because I got an invalid file format when attaching the file. I copied it from another website.

---

### Post by Olav on 2017-01-14
It looks like you are working with the examples from [http://tldp.org/LDP/LG/issue74/tougher.html](http://tldp.org/LDP/LG/issue74/tougher.html)

The programs that you downloaded from that page can only be compiled if you add ```
#include <iostream>
``` to both Socket.cpp and simple_server_main.cpp. There will still be some warnings though.

---


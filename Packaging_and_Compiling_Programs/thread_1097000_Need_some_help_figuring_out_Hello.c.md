---
title: "Need some help figuring out Hello.c"
date: 2009-03-15
forum: Packaging and Compiling Programs
---

### Post by 10Zav01 on 2009-03-15
root@BlackMagicBox:/# gcc -o Hello Hello.c
Hello.c:1:20: error: iostream: No such file or directory
Hello.c: In function ‘main’:
Hello.c:5: error: expected expression before ‘:’ token
Hello.c:5: error: stray ‘\342’ in program
Hello.c:5: error: stray ‘\200’ in program
Hello.c:5: error: stray ‘\235’ in program
Hello.c:5: error: stray ‘\’ in program
Hello.c:5: error: stray ‘\342’ in program
Hello.c:5: error: stray ‘\200’ in program
Hello.c:5: error: stray ‘\235’ in program



I once got this to work. But I updated ubuntu and it didn't work any longer. Does someone know if there are files I need to re-download? I d/led some that looked related to C++ programming but I am a newbie and am trying to learn it. Also I used gedit to make it and before it didnt have the \342 and other errors, it just had the iostream ones. i wish i knew more about this stuff, so i didnt have to ask you guys this

ty in advance for advice.

---

### Post by Siph0n on 2009-03-15
Can you post Hello.c ? or is it too big?

---

### Post by 10Zav01 on 2009-03-15
woops--

#include <iostream>

int main()
{
    std::cout <<”Hello World!\n”;
    return 0;
}

---

### Post by Sukarn on 2009-03-15
Compile it with g++ instead of gcc.

Also, gcc does not expect you to use C++ header files in a C source files. The .c extension makes the source file look like a C source file. If you change it to .cpp then it should be seen as a C++ source file by gcc.

---

### Post by 10Zav01 on 2009-03-15
root@BlackMagicBox:/# g++ -o hello hello.cpp
hello.cpp:5: error: stray &#8216;\342&#8217; in program
hello.cpp:5: error: stray &#8216;\200&#8217; in program
hello.cpp:5: error: stray &#8216;\235&#8217; in program
hello.cpp:5: error: stray &#8216;\&#8217; in program
hello.cpp:5: error: stray &#8216;\342&#8217; in program
hello.cpp:5: error: stray &#8216;\200&#8217; in program
hello.cpp:5: error: stray &#8216;\235&#8217; in program
hello.cpp: In function &#8216;int main()&#8217;:
hello.cpp:5: error: &#8216;Hello&#8217; was not declared in this scope
hello.cpp:5: error: expected `;' before &#8216;World&#8217;

When I did it. 

It worked before I installed the latest updates to Ubuntu when I was first reading about C++.
Trying to figure out if there's files I need that were replaced, and if that is why I am having problems now.

ps. Im not an idiot am I that I compile it in the command line right?

---

### Post by run1206 on 2009-03-15
it worked for me :?
you sure you have the latest g++ installed?

```
sudo apt-get install g++
```

and if you're using gedit to edit the file, make sure the output and include header are different colors. might have to manually retype the program to run correctly. At first, just copying right from uf.org didn't work for me; i had to retype the quotations to get the output to show the right way.

---

### Post by 10Zav01 on 2009-03-15
Okay thanks everyone. I got it working :) Now time to learn more, so may be one day I can give advice (LOL).

---


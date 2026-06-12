---
title: "I can not run C program on Ubuntu"
date: 2007-03-23
forum: Programming Talk
---

### Post by dongkhoi on 2007-03-23
Hello all,
i installed Ubuntu on Virtual PC 2007 few days ago.I've tried a hello world C program like 

#include <stdio.h>
int main(void)
{
printf("Hello world");
return 0;
}

It was ok.But today when i try

make hello
 it generated an error :
error:stdio.h:No such file or directory
In main function:
warning : incompatible implicit declaration of built-in funtion "printf"
I dont know why?Can anyone help me?Thanks a lot

---

### Post by Ramses de Norre on 2007-03-23
What's the output when you execute this command first:
```
sudo aptitude install build-essential
```

---

### Post by Wybiral on 2007-03-23
No "stdio.h"
Definitely build-essential!

---

### Post by alex_albino on 2007-03-23
I have the same problem. When I run "sudo aptitude install build.essential" I get the answer that it needs 0B of files and anfter unpacking it will be used 0B

Can you please help?

Thanks

---

### Post by Wybiral on 2007-03-23
I'ts "build-essential" not "build.essential"

---

### Post by alex_albino on 2007-03-23
Yes.. my mistake on the post. I wrote it correctly on the console window.

I can't seem to compile even a simple hello world program in c.
The error is this:
(I am translating here for my msgs are in Portuguese)

hello.c:1:19: error: stdio.h : file our folder unexistent
hello.c: In function 'main':
hello.c:6: warning: incompatible implicit declaration of built-in function 'printf'

Thanks again.
Alex

---

### Post by Wybiral on 2007-03-23
Oh, try: "sudo apt-get install build-essential"

---

### Post by alex_albino on 2007-03-23
I got the following messages:

Reading list of packages...done
Building dependency tree
reading state information...done
E: Impossible to find package build-essential

---

### Post by invalid on 2007-03-23
> **alex_albino said:**
> I got the following messages:

Reading list of packages...done
Building dependency tree
reading state information...done
E: Impossible to find package build-essential

Be sure to have the extra repos enabled.

---

### Post by dongkhoi on 2007-03-23
I've tried sudo apt-get install buid-essential before successfully.But now it generates error like it can not connect to the website to download.What should i do now

---

### Post by pmasiar on 2007-03-23
> **dongkhoi said:**
>  now it generates error like it can not connect to the website to download.

1) google the error message - maybe someone found solution or has a clue
2) post error message here

---

### Post by j_g on 2007-03-23
This problem seems to come up once a week. Clearly, naming an essential C++/C package as "build-essential" just isn't registering with new C/C++ developers. There should be a package named "C/C++ development" that installs the C compiler/linker, C/C++ header files and libs. This would be much more intuitive.

---

### Post by Wybiral on 2007-03-23
> **j_g said:**
> This problem seems to come up once a week. Clearly, naming an essential C++/C package as "build-essential" just isn't registering with new C/C++ developers. There should be a package named "C/C++ development" that installs the C compiler/linker, C/C++ header files and libs. This would be much more intuitive.

I agree, it should be named "install-this-package-if-you-plan-to-compile-anything"

But even then people will probably still ignore it.

---

### Post by j_g on 2007-03-23
> it should be named "install-this-package-if-you-plan-to-compile-anything"
But even then people will probably still ignore it.

People seem to be finding the C/C++ compiler with no problem. What they're not finding is the standard C/C++ headers and libs. I strongly suspect that this has to do with the fact that a C/C++ compiler is pretty much useless without any headers/libs, so one normally expects the latter to be installed along with C/C++ compiler. It makes sense that one would assume that installing gcc would install the standard C library headers/libs. But of course, this doesn't happen. That's why there should be a package named "C/C++ development" which installs the minimum stuff needed for a functional C/C++ dev system. Neither the "build-essential" package name, nor its description, mentions anything about C/C++, so I don't know why anyone would assume that its purpose was as I describe for a "C/C++ development" package.

---

### Post by Wybiral on 2007-03-23
> **j_g said:**
> People seem to be finding the C/C++ compiler with no problem. What they're not finding is the standard C/C++ headers and libs. I strongly suspect that this has to do with the fact that a C/C++ compiler is pretty much useless without any headers/libs, so one normally expects the latter to be installed along with C/C++ compiler. It makes sense that one would assume that installing gcc would install the standard C library headers/libs. But of course, this doesn't happen. That's why there should be a package named "C/C++ development" which installs the minimum stuff needed for a functional C/C++ dev system. Neither the "build-essential" package name, nor its description, mentions anything about C/C++, so I don't know why anyone would assume that its purpose was as I describe for a "C/C++ development" package.

Well, the first thing I did when I started developing on ubuntu was google how to start, and I found tons of links. I don't see why that isn't peoples first reaction when they see the compiler say "stdio.h" cannot be found.

The compiler has nothing to do with the standard libraries. The people packaging the compiler shouldn't be responsible for that stuff.

---


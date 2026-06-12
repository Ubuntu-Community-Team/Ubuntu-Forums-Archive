---
title: "error: 'printf' was not declared in this scope"
date: 2007-06-02
forum: Programming Talk
---

### Post by ankakusu on 2007-06-02
Hi, 

I want to try the code below and It is a code with preprocessors. I get an error. 

Can anyone can tell me the reason?

```
#define HATALI(A) A*A*A /* Kup icin hatali makro */
#define KUP(A) (A)*(A)*(A) /* Dogusu ... */
#define KARE(A) (A)*(A) /* Karesi icin dogru makro */
#define START 1
#define STOP 9

main()
{
int i,offset;

offset = 5;

for (i = START;i <= STOP;i++) {
printf("%3d in karesi %4d dir, ve kubu ise %6d dir..\n",
i+offset,KARE(i+offset),KUP(i+offset));

printf("%3d in HATALIsi ise %6d dir.\n",i+offset,HATALI(i+offset));
}
}

```

the error:

```
'printf' was not declared in this scope
```

---

### Post by WW on 2007-06-02
You forgot
```

#include <stdio.h>

```

---

### Post by ankakusu on 2007-06-02
WW , 
Thanks for help :D

when included the <studi> header file

it returned an error:

```
studio.h: No such file or directory
```


I am using gcc compiler. Can this be the reason?

---

### Post by WW on 2007-06-02
**stdio.h**  (not studio.h)

---

### Post by ankakusu on 2007-06-02
WW,thanks.
I'm so inattentive :( 

anyway, the program give a more garbled error...

what does this error mean?

how can I fix the problem?

```
/tmp/ccGQNcoh.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld output returned 1
```

---

### Post by WW on 2007-06-02
What command did you use that results in that error?

---

### Post by ankakusu on 2007-06-02
I'm using vi editor and first of all I created a file like this:

```
user@user-desktop:~$ vi example_macro.cpp
```

then I compiled the file by the command:

```
sh-3.1$ gcc example_macro.cpp -o objmacro
```



by the way I have a off topic question, 
I have created a file:

user@user-desktop:~$ mkdir make_file_work

then I go and look both the 'user' file and to the 'desktop' I cannot find such a directory? But if I write the command:

user@user-desktop:~$ cd make_file_work

I can go inside that file, but I cannot see it in the file browser...

why?

thanks again for your help WW...

---

### Post by WW on 2007-06-02
You appear to be writing C, not C++.  Rename the file to **example_macro.c**, and try again. (I just tried it both ways; I got the same error that you did when the file was called example_macro.cpp, and it compiled fine when I called it example_macro.c.)

---

### Post by Mime on 2007-06-02
It'll compile as a .cpp if you put the line...

```
using namespace std;
```

under the include for stdio.h, or preface printf with "std::" in order to tell the compiler that you're using a function from the standard namespace.

---

### Post by ankakusu on 2007-06-03
Yes, it compiled when I changed the extesion from .cpp to .c. But I dont know the diferrences between the c and cpp.

Does the reason depends to 'printf' function? Because, as far as I remember I use cout function instead of printf in cpp. I guess printf is a c function...

But when I tried with 
#include <stdio>
using namespace std;

it gave an error again. the error the same:

```

/tmp/ccubDW3d.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld output return 1 
```

what does this error mean anyway?

"/tmp/ccubDW3d.o" :..........................................what is the object ccubDW3d.o in the 'tmp'  directory?

"(.eh_frame+0x11)" :......................................... can this be an address?

"undefined reference to `__gxx_personality_v0'" : it says '__gxx_personality_v0' and says there is an undefined reference to this 'thing'. But I've not use that thing in my               .                                                                      .........................................................................code. What does it refer to in my code?
"collect2: ld output return 1" :                             what is collect 2? What is ld output? What does returning 1 means?

WW and Mime thanks for help :D

---

### Post by FuturePast on 2007-06-03
A compiler like gcc does a few things behind the scenes. 
By naming the file .cpp you "confused" gcc, and the error messages are a result of that.
I'm not sure it would really benefit you at this stage to offer a fuller explanation of those messages.

---

### Post by Mime on 2007-06-03
Those look like linking errors.  As FuturePast said, gcc does a couple things when you tell it to compile something.  Linking is usually the last step in the process that combines all the assembled pieces of the application into the final executable.  If the linker can't find one of the pieces that's the kind of error message you'll get.

One difference in C and C++ is that C++ has namespaces where C doesn't.  When you tried to compile the program as a .cpp gcc got confused as to where it should look to find all the pieces of the application.  That looks more like C code than C++ code, so the easiest thing to do would be to rename it to a .c file and call everything good.  ;)

---

### Post by WW on 2007-06-15
I just replied to thread with a similar problem: [http://ubuntuforums.org/showthread.php?t=474537](http://ubuntuforums.org/showthread.php?t=474537)

---

### Post by the_unforgiven on 2007-06-15
> **Mime said:**
> Those look like linking errors.  As FuturePast said, gcc does a couple things when you tell it to compile something.  Linking is usually the last step in the process that combines all the assembled pieces of the application into the final executable.  If the linker can't find one of the pieces that's the kind of error message you'll get.

One difference in C and C++ is that C++ has namespaces where C doesn't.  When you tried to compile the program as a .cpp gcc got confused as to where it should look to find all the pieces of the application.  That looks more like C code than C++ code, so the easiest thing to do would be to rename it to a .c file and call everything good.  ;)
No, there are substantial differences in C and C++ - not just the support of namespaces.
In short, C++ is a superset of C - meaning that a valid C program is also a valid C++ program, but not vice versa. For example, the concepts of class, User-defined data types, templates, exceptions are absent in C whereas these are core features of the ISO C++ specification.

You just had to compile the C code (saved in a file with .cpp extension) with g++ and it will still work fine.
However, that is stupid because g++ will link it to the standard C++ library which has a lot more code that you are not using (and don't need) here.

---

### Post by the_unforgiven on 2007-06-15
> **Mime said:**
> It'll compile as a .cpp if you put the line...

```
using namespace std;
```

under the include for stdio.h, or preface printf with "std::" in order to tell the compiler that you're using a function from the standard namespace.
That's wrong.
C headers like stdio.h have nothing to do with namespaces.

The namespaced version of stdio is <cstdio> which is a C++ header.

---

### Post by the_unforgiven on 2007-06-15
> **ankakusu said:**
> Yes, it compiled when I changed the extesion from .cpp to .c. But I dont know the diferrences between the c and cpp.

Does the reason depends to 'printf' function? Because, as far as I remember I use cout function instead of printf in cpp. I guess printf is a c function...

But when I tried with 
#include <stdio>
using namespace std;

it gave an error again. the error the same:

```

/tmp/ccubDW3d.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld output return 1 
```

what does this error mean anyway?

"/tmp/ccubDW3d.o" :..........................................what is the object ccubDW3d.o in the 'tmp'  directory?

"(.eh_frame+0x11)" :......................................... can this be an address?

"undefined reference to `__gxx_personality_v0'" : it says '__gxx_personality_v0' and says there is an undefined reference to this 'thing'. But I've not use that thing in my               .                                                                      .........................................................................code. What does it refer to in my code?
"collect2: ld output return 1" :                             what is collect 2? What is ld output? What does returning 1 means?

WW and Mime thanks for help :D
o. "/tmp/ccubDW3d.o" is the object (binary) code that the compiler (assembler, to be more precise) generated - this is then passed to linker to create the final executable.

o. (.eh_frame+0x11) is the location of the symbol in the binary object file for which the linker could not resolve the reference. Most modern executable file formats comprise of multiple sections - like **.data** for initialized global or static data, **.text** for the actual executable instructions. .eh_frame is a section generated by the g++ compiler (for C++) for supporting the mechanism of exceptions - hence the name .eh_frame (***e***xception ***h***andler frame).

o. __gxx_personality_v0 is a symbol used by the g++ compiler - I don't know the actual use of it :( - I suppose it has something to do with the version of C++ exception specification?

o. collect2 is the actual controller process that executes the various parts of the modern modular compiler backends (like pre-processor, compiler, assembler and linker). ld is the link-editor (linker) - it returned a status of 1 (some error) - traditionally, a return code of 0 signifies success - any other code is an error.

HTH ;)

---

### Post by caoinan on 2007-08-29
its not <stdio>  its <stdio.h>

---


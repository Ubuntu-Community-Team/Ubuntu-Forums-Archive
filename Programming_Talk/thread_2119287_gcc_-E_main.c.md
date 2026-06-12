---
title: "gcc -E main.c"
date: 2013-02-23
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-23
Hello,
I understand that the main.i file contains the preprocessed code. 
Some of the things this stage I know theoritically includes
1) Expanding macros/Macro substitution
2) Removing comments
3) Expanding the include files etc.

But would it be possible to give me a brief overview of the attached file. 

My source is as follows
```

#include <stdio.h>
#define string "hello world\n"

int main(void)
{
 printf(string);

 return 0;
}

```

My only valuable observation is that in the .i file
a) string, the macro is replaced by "hello world\n"
b)extern int printf means that it is declared in another file.

Apart from that, I couldn't make much sense of the file.

Please advise.
Thanks

---

### Post by MadCow108 on 2013-02-23
all the rest are the expanded contents of stdio.h and the files it again included.

the # <number> lines contain information what was included so the compiler which only sees the expanded source can give better error messages.

> b)extern int printf means that it is declared in another file.

this is just the signature of the function you are calling, it is needed to the compiler knows how to setup the registers and the stack before calling into the function. The extern before a function signature is implicit in C, the standard headers contain it for better compatibility to old compilers.
The signature is also called the function declaration.

The actual code for the function, the function definition, is not contained in header files, it is stored in compiled object files, in this case the libc shared or static library.
the merging of your code with the function call and libc is done by the linker (gcc file.c calls both the compiler and the linker for you)

---

### Post by IAMTubby on 2013-02-23
> **MadCow108 said:**
> all the rest are the expanded contents of stdio.h and the files it again included.
Thanks MadCow108, I just wanted a brief overview and your explanation fits the purpose.

> 
the # <number> lines contain information what was included so the compiler which only sees the expanded source can give better error messages.

Would it possible to explain that once again ?

Thanks.
Shall mark as solved upon the reply.

---

### Post by MadCow108 on 2013-02-23
file a includes header b
header b has an syntax error
the compiler only sees an intermediate file which consists of file a and header b preprocessed
to be able to tell the user that the error is in file b the preprocessing must maintain the information that the preprocessed file included header b, thats what the # <number> lines are for.
the formating is compiler specific.

---

### Post by IAMTubby on 2013-02-23
> **MadCow108 said:**
> file a includes header b
header b has an syntax error
the compiler only sees an intermediate file which consists of file a and header b preprocessed
to be able to tell the user that the error is in file b the preprocessing must maintain the information that the preprocessed file included header b, thats what the # <number> lines are for.
the formating is compiler specific.
MadCow108, thanks. I get the overall idea, I made a similar scenario and made a syntax error in my header file. It still generated the .i file. But for me to be able to better relate, can you tell me taking one of the #lines. 
eg. # 28 "/usr/include/stdio.h" 1 3 4

---

### Post by MadCow108 on 2013-02-23
you probably have to look throught the gcc souce code to see what exactly it means, its not relevant for any purpose but writing compiler frontends.

---

### Post by IAMTubby on 2013-02-23
> **MadCow108 said:**
> you probably have to look throught the gcc souce code to see what exactly it means, its not relevant for any purpose but writing compiler frontends.
MadCow108, thanks, as I said, from your previous post, I get the overall idea. I am not sure if I'm skilled to go through the gcc source code. Anyways I have downloaded eglibc and taking a look at it. If I understand something deeper at some point, I shall post it here.
Thanks.

---

### Post by MadCow108 on 2013-02-23
digging through the source to find what the numbers mean is a pointless waste of time. Why do you want to know what the numbers represent in gcc?

its just an arbitrary representation of some information gcc creates and later uses.
Even if the representation were be mandated by the standard its still irrelevant for all intents and purposes unless you want to write a compiler or parse this for some other reason.

---

### Post by gnusci on 2013-02-23
$ gcc -v

---

### Post by IAMTubby on 2013-02-23
> **MadCow108 said:**
> digging through the source to find what the numbers mean is a pointless waste of time. Why do you want to know what the numbers represent in gcc?

its just an arbitrary representation of some information gcc creates and later uses.
Even if the representation were be mandated by the standard its still irrelevant for all intents and purposes unless you want to write a compiler or parse this for some other reason.
Okay, I was actually going through the source of ldconfig.c from eglibc to get a feel of what happens. Thanks.

---


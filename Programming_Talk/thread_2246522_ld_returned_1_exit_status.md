---
title: "ld returned 1 exit status"
date: 2014-10-01
forum: Programming Talk
---

### Post by Ayush_Agrawal on 2014-10-01
This is my first post on this forum so kindly overlook any mistake that I make.

I was working on a very simple problem: taking a string value from the user and printing its lowercase form.

Here's my **code**:

#include <stdio.h>
#include <string.h>

main()
{
    char s[100];
    printf("Enter a Sttring: ");
    gets(s);
    strlwr(s);
    printf("%s",s);
}

I am working on** ubuntu 14.04**. I used the text editor **Sublime text 2**.

I tried to compile the program in the** terminal **with the code: [B]make eg
[/B]
It returned:


eg.c:(.text+0x3f): undefined reference to `strlwr'
collect2: error: ld returned 1 exit status
make: *** [eg] Error 1

I even tried with **gcc** and **clang** but ended up getting the same error.

Thanks in advance.

---

### Post by ofnuts on 2014-10-01
If you compile with more warnings:

> 
warning: implicit declaration of function &#8216;strlwr&#8217; [-Wimplicit-function-declaration]


In other words, strlwr() doesn't exist (it's not standard C).

---

### Post by dataformsaction on 2014-10-01
> **Ayush_Agrawal said:**
> This is my first post on this forum so kindly overlook any mistake that I make.

I was working on a very simple problem: taking a string value from the user and printing its lowercase form.

Here's my **code**:

#include <stdio.h>
#include <string.h>

main()
{
    char s[100];
    printf("Enter a Sttring: ");
    gets(s);
    strlwr(s);
    printf("%s",s);
}

I am working on** ubuntu 14.04**. I used the text editor **Sublime text 2**.

I tried to compile the program in the** terminal **with the code: [B]make eg
[/B]
It returned:


eg.c:(.text+0x3f): undefined reference to `strlwr'
collect2: error: ld returned 1 exit status
make: *** [eg] Error 1

I even tried with **gcc** and **clang** but ended up getting the same error.

Thanks in advance.


There's no such function as strlwr, unless you write it (?), so you're going to have to loop through the
string in your array (rather sparsely name s[]) and call tolower() on each char  (#include <ctype.h> for that function)

That will do the job.

---

### Post by Ayush_Agrawal on 2014-10-02
Thank you guys for your valuable response.

I know what you are getting at but my point is why am I not able to user the particular function strlwr() although it is defined in the string.h header file.

Actually, in our college they use **DevC++** as an IDE and we are taught thorugh it. The same code works perfectly fine in it. I encountered a similar problem with the functions defined in **math.h** so I googled it. I came up with an answer to link the math.h file during compilation. So the compilation code would look like **gcc -o eg eg.c -lm** and it all worked fine. So I was wanting to know what to link so that I can use the string functions.

Sorry for missing out on these details earlier.

---

### Post by ofnuts on 2014-10-02
From the error message you get, it's not(*)... it may be defined in some compilers that have added it to their runtime library, but since it's not standard C it is not defined in GCC. DevC++ is a Windows thing that uses the Microsoft runtime library, that may have additional functions.

(*)"warning: implicit declaration of function &#8216;strlwr&#8217; [-Wimplicit-function-declaration]" means the function hasn't been declared (which implies it hasn't been found in the files you included) and the compiler assumes a default definition (which is usually sufficiently wrong to introduce nasty bugs, when the function actually exists).

---

### Post by steeldriver on 2014-10-02
FYI adding the -lm compiler flag does **not** "link the math.h file during compilation" - it links the libm math **library** during linking. 

If you are learning development imho it is important to understand the difference between the two phases (compilation versus linking) and the associated types of errors you are likely to see (e.g. **declaration** errors versus **definition** errors).

[Although in this case the object (function) is neither declared nor defined, for the reasons mentioned by ofnuts.]

---

### Post by dataformsaction on 2014-10-02
It looks like it really doesn't exist on most Unix compilers - I've checked OS X and Linux

The best thing for you to do is look through the string.h header file on the machine you're trying to compile on.

Looking at the MSDN website: [http://msdn.microsoft.com/en-us/library/ms235455.aspx](http://msdn.microsoft.com/en-us/library/ms235455.aspx) 

... states that it's a deprecated POSIX function. In that case maybe it's declared in your string.h but you have to #define one of the posix conformance macros
to enable it.

---


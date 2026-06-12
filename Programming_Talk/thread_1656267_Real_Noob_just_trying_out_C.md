---
title: "Real Noob just trying out C"
date: 2010-12-30
forum: Programming Talk
---

### Post by CaptainMark on 2010-12-30
Hi, id say im still a beginner in python at the moment but I wanted to try C aswel so i just got a book (which unfortunately is not linux specific) and im getting stuck in on the compiling which is totally new to me, i have this C file ```
// beginning with c
// a first test with the c language 
// mark skinner 30 dec 2010

#include <stdio.h>

main()
{
printf("Hello C World. ");
}

```ive named it test.c and then ive run this ```
gcc test.c
```Which has produced a file a.out, heres my probably stupid noob question: What do I do then? Im assuming this is a type of executable but running it in a terminal does nothing, this small hitch is stopping me from getting too far, im sure ill be off making c programs left right and centre as soon as i figure this out.
Thanks for your help,
Mark

---

### Post by bouncingwilf on 2010-12-30
To execute a.out just type ./a.out in the terminal

if you compile with gcc -o test test.c  you will generate an executable called test  (./test to run)

Bouncingwilf

---

### Post by kknd on 2010-12-30
Strange, it worked here. Try the following (adding a line break):

[PHP]

#include <stdio.h>

int main()
{
    printf("Hello C World.\n");
    return 0;
}
[/PHP]

The a.out is the executable. You can change the name of the output file by using: gcc code.c -o myappname.

It is a good practice to compile with -Wall to (gcc -Wall code.c ...) to show more warnings.

---

### Post by CaptainMark on 2010-12-30
Thanks, all i wasnt doing was the ./test.out i got how to name your executable but adding -Wall to the options wont compile it i get this error ```
mark@mark-desktop:~/Documents/programming/c/chapter_1$ gcc -Wall test.c -o test.out
test.c:8: warning: return type defaults to ‘int’
test.c: In function ‘main’:
test.c:10: warning: control reaches end of non-void function
mark@mark-desktop:~/Documents/programming/c/chapter_1$ 




```
edit: i see youve added int before main() and a return line, i guess this makes the difference but i wont go into why yet, ive literally just picked the book up 20 mins ago

---

### Post by trent.josephsen on 2010-12-30
Terminology:  Warnings are non-fatal diagnostics.  A compilation with warnings is still a compilation.  Errors are fatal.  Even with the warnings, you should still be able to successfully compile and run your code.

... actually, the reason you didn't see any output was because of the lack of a "\n" at the end of the string.  Technically, it was (probably) overwritten by the bash prompt, but C won't guarantee anything gets printed to stdout until you push that newline character to it.

---

### Post by ziekfiguur on 2010-12-31
> **trent.josephsen said:**
> Terminology:  Warnings are non-fatal diagnostics.  A compilation with warnings is still a compilation.  Errors are fatal.  Even with the warnings, you should still be able to successfully compile and run your code.
That's why i usually advise to also use -Werror, that way warnings will be fatal, like errors, and you are forced to write decent code.

The default return type of a c function is int, so if you dont specify that your main function returns void, your compiler will assume an int should be returned. 
But, your function does not have a return statement, so the compiler warns you that you forgot it.
If you don't include the return statement in a function an arbitrary value is returned, which can lead to unexpected behavior.

---


---
title: "cant compile 'hello world'"
date: 2010-04-26
forum: Programming Talk
---

### Post by Max Destruction on 2010-04-26
hi, i am brand new to programming.

i am working through the book 'Beginning Linux Programming'

i am having trouble compiling the first example: The text reads:

'Let’s start developing for Linux using C by writing, compiling, and running our first Linux program.
It might as well be that most-famous of all starting points, Hello World.
   1.    Here’s the source code for the file hello.c:
    #include <stdio.h>
    int main()
    {
          printf(“Hello World\n”);
          exit(0);
    }

2.   Let’s compile, link, and run our program.
 $ gcc -o hello hello.c '

_________________________________________________________

When I compile this I get:

```
gcc -o hello hello.c
hello.c: In function ‘main’:
hello.c:4: error: stray ‘\342’ in program
hello.c:4: error: stray ‘\200’ in program
hello.c:4: error: stray ‘\234’ in program
hello.c:4: error: ‘Hello’ undeclared (first use in this function)
hello.c:4: error: (Each undeclared identifier is reported only once
hello.c:4: error: for each function it appears in.)
hello.c:4: error: expected ‘)’ before ‘World’
hello.c:4: error: stray ‘\’ in program
hello.c:4: error: stray ‘\342’ in program
hello.c:4: error: stray ‘\200’ in program
hello.c:4: error: stray ‘\235’ in program
hello.c:5: warning: incompatible implicit declaration of built-in function ‘exit’
```

What am I doing wrong?

---

### Post by lisati on 2010-04-26
edit: never mind, dirt on laptop screen

---

### Post by MadCow108 on 2010-04-26
these "stray" messages always mean you have some unsupported character in your file
in your case its:
&#8220;
use " (double quote) instead
this often happen when copy-pasting from bad formated tutorials

and you also have to include stdlib.h for the exit function
you could also just return 0; instead of exit(0); in the main which does the same

---

### Post by Max Destruction on 2010-04-26
hmmm. ok, I made the changed to talked about (as best i understood them)
I am getting errors still, albeit different ones.
this is my code

```
#include <stdlib.h>   
#include <stdio.h>
   
int main()
{
    printf("Hello World\n&#8221;);
    exit(0);
}
```errors:


```
hello.c:6:12: warning: missing terminating " character
hello.c: In function &#8216;main&#8217;:
hello.c:6: error: missing terminating " character
hello.c:7: error: expected &#8216;)&#8217; before &#8216;;&#8217; token
hello.c:8: error: invalid use of void expression
hello.c:8: error: expected &#8216;;&#8217; before &#8216;}&#8217; token
```:(

I think I understand what the error is saying but I dont see how it is in the code.

---

### Post by lisati on 2010-04-26
Both the opening and closing quotes should be regular double quotes..... :)

---

### Post by Max Destruction on 2010-04-26
haha ok i got it - exit instead of return *slaps head*

thanks.

---

### Post by Max Destruction on 2010-04-26
> **lisati said:**
> Both the opening and closing quotes should be regular double quotes..... :)


isnt that what i had ...? i copy pasted the example from wikipedia and it worked:
which was:


 
```


#include <stdio.h>
int main(void)
{
    printf("hello, world\n");
    return 0;
}
```this code doesnt work:

```
#include <stdio.h>
int main()
{
    printf("Hello World\n&#8221;);
    exit(0);
}
```where is the difference, besides the exit/return? (t doesnt work with no brackets around 0 either)

---

### Post by lisati on 2010-04-26
On my screen the closing quotes look different in your second example.

---

### Post by Max Destruction on 2010-04-26
oh yes, i see. you are right. it's like a different sort of closing quote ... weird.

thanks a lot man.

---

### Post by dragos2 on 2010-04-26
> **Max Destruction said:**
> oh yes, i see. you are right. it's like a different sort of closing quote ... weird.

thanks a lot man.

At least for the Hello World you can write it by hand and not copy paste it, it will
spare a lot of time in the future :)

---

### Post by Compyx on 2010-04-26
Are you by any chance using a word processor (OO Writer/MS Word) to write your code in? I've seen word processors translate normal double quotes into 'fancier' quotes. Copying/pasting from the web or PDF-files is also a known source of incorrect quotes.

---

### Post by Max Destruction on 2010-04-27
Nah I was using gedit to write this. I did copy and paste it out of a pdf though. But it also turned out that wasn't the only problem. The reason i didnt pick up on it was because the syntax highlighting recognized as correct. It actually doesn't compile if I use exit instead of return.

---

### Post by Compyx on 2010-04-27
exit() is declared in stdlib.h, so an '#include <stdlib.h>' should fix that.

---

### Post by Max Destruction on 2010-04-27
ahhh k thanks

---


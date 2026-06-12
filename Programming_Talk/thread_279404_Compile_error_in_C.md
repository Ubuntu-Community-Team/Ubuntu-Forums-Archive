---
title: "Compile error in C"
date: 2006-10-17
forum: Programming Talk
---

### Post by tetsuo84 on 2006-10-17
Hello, I am getting error compiling in C. I'm new and this is my first program. I installed gcc and g++ (Just to check if it was possible to compile with g++). I did everything I could think of...I also searched the boards and did some google research but I couldn't find an answer to my problem

Heres the code

```
#include <stdio.h>

main()
{
    int num, result = 0;

    scanf("%d", &num);

    for(i = 1; i <= num; i++) { 
        result += i;
    }

    printf("%d\n", result); 
}
```

and when I do gcc -o calc calcu.c or gcc calcu.c I get the following error:

calcu.c: In function &#8216;main&#8217;:
calcu.c:9: error: &#8216;i&#8217; undeclared (first use in this function)
calcu.c:9: error: (Each undeclared identifier is reported only once
calcu.c:9: error: for each function it appears in.)

Help would be very appreciated, thanks in advance

---

### Post by Dimitar on 2006-10-17
Hi tetsuo,
```

    for(i = 1; i <= num; i++)

```

The problem is in your for loop. i needs to be declared, so the correct syntax would be 

```

for(int i = 1; i <=num; i++)

```

hope this helps.

Regards,
Dimitar

---

### Post by hod139 on 2006-10-17
First, make sure you install the package build-essential.  This will install everything required to program C or C++.  Next, there are two problems with your code.  The first is that the return should be an int.  The C standard does not technically require this, but it is good habit.  The other problem is the compilation error you are getting.  You are trying to use i undeclared.  I have fixed your code, and pasted below.

```

#include <stdio.h>

int main()
{
    int num, result = 0;

    scanf("%d", &num);

    int i;
    for(i = 1; i <= num; i++) {
        result += i;
    }

    printf("%d\n", result);

    return 0;
}

```

**Edit:** Looks like I was a bit too slow in my reply, however the code posted by Dimitar is incorrect C code.  What he wrote will work in C++, but not in C.

---

### Post by tetsuo84 on 2006-10-17
Thanks a lot, both of you. It was a problem with the code. I don't understand why every code I try to compile doesn't work, even if it is from tutorials or books..

Do you know where can I find good tutorials?,

Thanks

---

### Post by rplantz on 2006-10-18
> **hod139 said:**
> 
```

#include <stdio.h>

int main()
{
    int num, result = 0;

    scanf("%d", &num);

    int i;
    for(i = 1; i <= num; i++) {
        result += i;
    }

    printf("%d\n", result);

    return 0;
}

```


In the past, C required you to declare all variables (within a {...} block) before having any "active" code. I think this requirement has been relaxed in newer compilers, but just to be safe, I would do:
```

#include <stdio.h>

int main()
{
    int num;
    int result = 0;
    int i;

    scanf("%d", &num);
  .....
}

```

Notice that I placed each variable on a separate line. That makes it easier to add/remove variables as you change your code. It's also easier to add a comment about a variable.

I like having all my variables listed at the beginning. I think of it as sorta like a recipe. The first thing I want to see is a list of the "ingredients."

---

### Post by Dimitar on 2006-10-18
ahhh yeah sorry, i compile with -std=c99 now and it does have alot of the loop warnings relaxed. and rplantz makes a good point, listing all your variables on their own line is a really good habit to get into.

---

### Post by tetsuo84 on 2006-10-18
Thank you all for your answers. They were really helpful. 

Until the next question! :D 

Tetsuo

---

### Post by scourge on 2006-10-18
> the code posted by Dimitar is incorrect C code. What he wrote will work in C++, but not in C.

It works fine in C, assuming that we're using the C99 standard (GCC's default setting is C89 I think).


> i compile with -std=c99 now and it does have alot of the loop warnings relaxed.

It's not really more relaxed, it's just that there's nothing to warn about if the code fully obeys the C99 standard. And why use -std=c99 (with GCC) when you can use -std=gnu99? Then you can use library functions like strtok_r (a better strtok) etc.

---

### Post by hod139 on 2006-10-18
> **scourge said:**
> It works fine in C, assuming that we're using the C99 standard (GCC's default setting is C89 I think).

Good point.  How many compilers support the newer standard?  How good is GNU's support?  I know Microsoft does not support the standard, focusing on C++, so sticking with the C90 (or 89, what's the difference) standard will produce more portible code.

---

### Post by Dimitar on 2006-10-19
the main reason i use std=c99 rather than -std=gnu99 is purely because that is how our code is marked at uni. if we compile fine with -ansi -pedantic -Wall -g -std=c99 we dont lose any marks for syntax/bad programming. you know, like multiple returns or something.

---

### Post by JonahRowley on 2006-10-22
> **tetsuo84 said:**
> Thanks a lot, both of you. It was a problem with the code. I don't understand why every code I try to compile doesn't work, even if it is from tutorials or books..

Do you know where can I find good tutorials?,

Thanks

The amount of material out there for C is pretty impressive.  The amount of *good* material out there is another story.  I learned from the K&R book ("The C Programming Language") long ago, but there are probably more gentle texts.

I would say skip "tutorials" altogether.  Most of them aren't much more than "type this to do this" and some very poorly written, half-assed explanation.  While this might actually pass in other languages, C is unforgiving, and GCC will spit confusing error messages at you for the smallest mistakes.  I would avoid simply copying example programs from a book as well (except the most basic ones to get you started), you'll run into problems like this one.  If you take the time to write your own little programs with whatever little you do know, it'll both reinforce what you do know, and give you an excuse to push yourself to learn new aspects of the language as you need them.  If you just copy, you can copy code you don't understand, and it doesn't help you at all.

---


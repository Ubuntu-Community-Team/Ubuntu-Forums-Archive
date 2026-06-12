---
title: "[SOLVED] a basic C question"
date: 2008-03-04
forum: Programming Talk
---

### Post by Balazs_noob on 2008-03-04
hi guys i have a little program with my tiny C program
```

#include <stdio.h>
#include <stdlib.h>

int main (void) {
    char* str ;
    str = malloc(255) ;
    scanf("%s",str);
    printf("%s\n",str);
    free(str);
    return 0 ;
}

```the code  would just read a string and write it to the screen but whenever i give it a string with spaces like "this is C"
then it only puts "this" like spaces would be newline characters...

thanks in advance...

---

### Post by LaRoza on 2008-03-04
Try using fgets for a single string, it would be simpler.

---

### Post by Balazs_noob on 2008-03-04
Thanks LaRoza, it worked
the new code is:
[php]
int main (void) {
    char* str ;
    str = malloc(255) ;
    while (fgets(str,255,stdin) != NULL) {  
        printf("%s\n",str);
    }
    free(str);
    return 0 ;
}
[/php]

now it reads more then 1 line but this is only a part of a bigger program
so it is not a problem..

---

### Post by rye_ on 2008-03-04
hi,

out of interest what's the advantage of using free over dealloc?

Thanks,

Ryan

---

### Post by LaRoza on 2008-03-04
> **rye_ said:**
> hi,

out of interest what's the advantage of using free over dealloc?

Thanks,

Ryan

I can't find that function in the standard headers, so the advantage of using "free" must be that it exists, unlike dealloc.

---

### Post by mike_g on 2008-03-04
> int main (void) {
    char* str ;
    str = malloc(255) ;
    while (fgets(str,255,stdin) != NULL) {  
        printf("%s\n",str);
    }
    free(str);
    return 0 ;
}  
Just a few pointers here. 

First, each time the loop runs you would be overwriting the string. If you want to get a sequence of strings you may want to make an array or strings.

Secondly, AFAIK I don't think you can enter null via stdin so you way wish to compare the string to a newline ("\n") or something to check when to quit the loop. 

Cheers.

---

### Post by Balazs_noob on 2008-03-04
> **mike_g said:**
> Just a few pointers here. 
First, each time the loop runs you would be overwriting the string. If you want to get a sequence of strings you may want to make an array or strings.

Secondly, AFAIK I don't think you can enter null via stdin so you way wish to compare the string to a newline ("\n") or something to check when to quit the loop. 
Cheers.
1, i know :) my task was to do work with the string
it wasn't a problem that i lost the original string
because i have already got the information i needed
until the loop ended

2, fgets gives a null pointer when you give it a EOF
signal with ctrl+D, my task was to terminate the program then

but thanks that you tried to help :KS

---

### Post by mike_g on 2008-03-04
>  fgets gives a null pointer when you give it a EOF
Cool, I dident know that (obvioulsy) :)

---

### Post by ruy_lopez on 2008-03-04
Why are you using malloc() over "char str[255]"?

---

### Post by Balazs_noob on 2008-03-05
no real reasons,  i just like it more:)

---

### Post by ruy_lopez on 2008-03-05
> **Balazs_noob said:**
> no real reasons,  i just like it more:)

That's as good a reason as any.

---


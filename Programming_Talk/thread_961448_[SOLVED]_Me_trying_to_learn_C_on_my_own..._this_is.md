---
title: "[SOLVED] Me trying to learn C on my own... this is hopeless"
date: 2008-10-28
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-28
I am going to learn C programming language on my own, without a specific teacher or anything.
I tried to wrote a program with a basic function. Here it goes:
```
[color=#BC7A00]#include <stdio.h>
[/color]
[color=#B00040]int[/color] [color=#0000FF]main[/color] ()
{
arhonfunktio ([color=#666666]2[/color], [color=#666666]3[/color]);
[color=#008000]**return**[/color] [color=#666666]0[/color];
}

[color=#B00040]void[/color] [color=#0000FF]arhonfunktio[/color] ([color=#B00040]float[/color] a, [color=#B00040]float[/color] b)
{
[color=#B00040]float[/color] value;
value [color=#666666]=[/color] a[color=#666666]*[/color]b;
printf ([color=#BA2121]"value = %d[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], value);
}

```
But when I try to compile:
> arho@ohra-laptop:~/Työpöytä$ gcc test.c -o test.o
test.c:10: warning: conflicting types for ‘arhonfunktio’
test.c:5: warning: previous implicit declaration of ‘arhonfunktio’ was here
arho@ohra-laptop:~/Työpöytä$ 

What are those errors? I checked my code a million times and over but found nothing that could cause those warnings.

However, when I run that it works.

---

### Post by curvedinfinity on 2008-10-28
Heya, "warnings" are just the compiler saying something like "you're doing something that might be dangerous, but we're going on ahead anyway." :)

> conflicting types for &#8216;arhonfunktio&#8217;

This one is because you are passing integers to a function that takes floats.

> previous implicit declaration of &#8216;arhonfunktio&#8217; was here

This one is because you should define your function above where you use it. :)

By the way, it takes some balls to teach yourself C. Congrats for getting as far as you have.

---

### Post by swappo1 on 2008-10-28
Here try this:
[PHP]#include <stdio.h>

void arhonfunktio (float a, float b);	// function prototype

int main ()
{
arhonfunktio (2, 3);
return 0;
}

void arhonfunktio (float a, float b)
{
float value;
value = a*b;
printf ("value = %f\n", value);	// %f for floating point variable
}[/PHP]

You want to add the function prototype before main(). This tells the compiler a function will be defined later.  Also use %f for floating point variables.

---

### Post by crazyfuturamanoob on 2008-10-28
> **curvedinfinity said:**
> Heya, "warnings" are just the compiler saying something like "you're doing something that might be dangerous, but we're going on ahead anyway." :)
> 
conflicting types for ‘arhonfunktio’ 

This one is because you are passing integers to a function that takes floats.
[quote]
previous implicit declaration of ‘arhonfunktio’ was here 

This one is because you should define your function above where you use it. :)

By the way, it takes some balls to teach yourself C. Congrats for getting as far as you have.[/QUOTE]

Thanks.

---

### Post by wmcbrine on 2008-10-28
> **curvedinfinity said:**
> This one is because you are passing integers to a function that takes floats.No, it's because the implicit function declaration (like all implicit function declarations) has an int for its return value, while the actual function says it returns void. It's only one warning, on two lines.

Passing integers to a function that takes floats results in silent promotion, not warnings.

---


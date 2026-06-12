---
title: "How can I create a executable from a C program."
date: 2008-08-16
forum: Programming Talk
---

### Post by Windy Peaks on 2008-08-16
Ladies and Gentlemen of the forum:

Two C programming base questions for Your consumption.

1. After I have created a C program does anyone know which command or ubuntu program I can use to create a executable. (so I can run it outside of the terminal window)

2. This is more a C programming question than Ubuntu but I figured that the person able to answer the first question would know the second as well.
How do we create the exponent function ie. In a mortgage calculation I need to have ( 1 - monthly interest) to the negative exponent of the number of months of the loan. 

When I used [X = double pow( double( 1- monthly interest), double - number of months))].

The response is that there needs to be a equation before the double, which of course they already is.

while (term !=0) 
{ X = double pow( double( 1- monthly interest), double - number of months)) }

:confused:

Thanks in Advance
Windy:

---

### Post by NovaAesa on 2008-08-16
Using gcc should allow you to create an exectutable file. Of course, it's still going to have to run in a terminal window unless you include some kind of GUI in your code.

I have never used C, but I know a bit of C++, so I'm not really sure if the following will apply. I think you second problem is because of the word double out the front. I'm not really sure what you're trying to archive by putting it there. If it's for casting purposes shouldn't there be parentheses around it?

Also, you might want to report you own thread asking for it to be moved to the programming talk section. You will probably have better luck getting a good answer there.

---

### Post by Oldsoldier2003 on 2008-08-16
Moved from ABT to Programming talk. consider it a free bump :)

---

### Post by WW on 2008-08-16
> **Windy Peaks said:**
> 
2. This is more a C programming question than Ubuntu but I figured that the person able to answer the first question would know the second as well.
How do we create the exponent function ie. In a mortgage calculation I need to have ( 1 - monthly interest) to the negative exponent of the number of months of the loan. 

When I used [X = double pow( double( 1- monthly interest), double - number of months))].

This is not valid C syntax.  pow is a function that takes two double arguments and returns a double, but your code should not be using the word "double" like that.  Here's a simple example:

**powtest.c**
```

#include <stdio.h>
#include <math.h>

int main()
    {
    double x,y,z;
    
    x = 12.0;
    y = 2.0;
    z = pow(x,y);
    printf("z=%10.4f\n",z);
    return 0;
    }

```
Compile and run:
```

$ gcc -Wall powtest.c -lm -o powtest 
$ ./powtest 
z=  144.0000
$ 

```
Note that the C file includes the header math.h, and the gcc command uses the option -lm to link the math library with the program.

---


---
title: "2 C question; declaring vars -- formatting in vi"
date: 2006-04-23
forum: Programming Talk
---

### Post by halfvolle melk on 2006-04-23
Hi,
I'm into my 3rd day of C hobbying and have thes questions:

If i'd declare 2 variables like this:
```
double bla, huaarrrg=0;
```
will they both become doubles or will the later become intger? It's probably bad practice but I'm wondering anyway.

To my delight, Vi does the indenting for you, however, I just found it to do this:
```
main()
{ double in;    /* input value */
        double av;      /* average
```
Is that 'the right way' or doesn't Vi understand and should I add some C parse thingy to Vi?

Thanks

---

### Post by nanotube on 2006-04-23
[QUOTE=halfvolle melk]Hi,
I'm into my 3rd day of C hobbying and have thes questions:

If i'd declare 2 variables like this:
```
double bla, huaarrrg=0;
```
will they both become doubles or will the later become intger? It's probably bad practice but I'm wondering anyway.
[/QUOTE]
they will both be doubles.

---

### Post by thumper on 2006-04-23
[QUOTE=nanotube]they will both be doubles.[/QUOTE]
But only the second is initialised to zero.

---

### Post by kh4nh on 2006-04-23
[QUOTE=halfvolle melk]

To my delight, Vi does the indenting for you, however, I just found it to do this:
```
main()
{ double in;    /* input value */
        double av;      /* average
```
Is that 'the right way' or doesn't Vi understand and should I add some C parse thingy to Vi?

Thanks[/QUOTE]

should not have "double in" on the same line with "{". make it like this
```
main()
{ 
        double in;    /* input value */
        double av;      /* average
```

---

### Post by halfvolle melk on 2006-04-23
Cool, thanks all!

---

### Post by nanotube on 2006-04-23
and don't forget to put the closing */ after "average" :)

---

### Post by LordHunter317 on 2006-04-23
VIM's indenting in the above example is clearly broken.
Seeing as it's not a fully language parser, it's not suprising, but '{ double foo;' on a line is legal.

---

### Post by halfvolle melk on 2006-04-23
Woohoo! I'v just finished my 4th C program! I'd really like to get this right so if any of you could be bothered to look through my code and tell me about bad practice or stupidity in the making I'd appreciate it!

```
/* Calculate average of given positive reals
 */

#include <stdio.h>

main()
{
        double in;      /* input value */
        double num=0;   /* numerator */
        int den=0;      /* denominator */
        while(1)
        { scanf("%lf", &in);
                if (in <= 0) break;
                num += in;
                den++;
        }
        printf("The average is %lf\n", (num/den));
}
```

@ LordHunter
What suggestion would you make for this kind of stuff under Gnom?

---

### Post by LordHunter317 on 2006-04-23
I don't use GNOME, so I can't recommend anything.  I use EMACS, personally.

BTW, I wouldn't actually format my code like that, I'd either fold the brace on the line with the brace expression (i.e., the if, while, for, etc.) or have it on a line all by itself.  I was just noting the code is legal.

---

### Post by nanotube on 2006-04-23
well, for one, there is no reason that a program to calculate an average should exclude negative numbers. you should think about this and come up with another quit signal, and use negative numbers as well as positives. 

for two, rather than use numerator/denominator as your comments, you should be more descriptive and say "sum of values" and "number of values". in general, you want your comments to tell why you are doing stuff, not the simple mechanistic aspects, which anyone can see from the code. (of course, in this short piece of code it doesn't matter, but it's good practice to start thinking this way). 

now, to extend this program and make it more "useful", try making it read a list of space-separated numbers from a text file, and averaging those. 

as to the editor, vim is pretty decent for c, but you could also try the scite editor (package "scite"). 
if you want a full development environment type software, look at dev-cpp ([http://sourceforge.net/projects/dev-cpp/)](http://sourceforge.net/projects/dev-cpp/)).

good luck. ;)

---

### Post by LordHunter317 on 2006-04-23
> **nanotube]well, for one, there is no reason that a program to calculate an average should exclude negative numbers.[/quote]The requirements may not mandate it, and seeing how hard correct I/O is in C, for the purpose of learning programming, a sentinel is perfectly acceptable.

> you should think about this and come up with another quit signal, and use negative numbers as well as positives. The code to do this correctly would more than double or triple the current application.  No, he shouldn't do this.

> for two, rather than use numerator/denominator as your comments, you should be more descriptive and say "sum of values" and "number of values".No, you're wrong on two points.  First off, there shouldn't be a comment at all, the variable name is infinitely descriptive.  Second off, your comments would just add confusion.   The correct thing is to say he should rename his variables to be:```
double sum said:**
>  in general, you want your comments to tell why you are doing stuff, not the simple mechanistic aspects, which anyone can see from the code.And you never want redundant comments as they're a liability.

---

### Post by nanotube on 2006-04-23
[QUOTE=LordHunter317]The requirements may not mandate it, and seeing how hard correct I/O is in C, for the purpose of learning programming, a sentinel is perfectly acceptable.

The code to do this correctly would more than double or triple the current application.  No, he shouldn't do this.[/quote]
his code certainly does what he claims - average non-negative numbers. i was suggesting this extension  as a further learning exercise. (though i suppose i did not phrase it as such in my original post, so your point is well taken).

> 
No, you're wrong on two points.  First off, there shouldn't be a comment at all, the variable name is infinitely descriptive.  Second off, your comments would just add confusion.   The correct thing is to say he should rename his variables to be:```
double sum;
int count;
```or similar.

And you never want redundant comments as they're a liability.
of course, your suggestion for significant variable names is the more proper one in this case (and essentially a good idea always). i was making my "meaningful commenting" suggestion more for the "future", once the original poster gets to writing longer, and not so obvious, code.

---

### Post by LordHunter317 on 2006-04-23
[QUOTE=nanotube]his code certainly does what he claims - average non-negative numbers. i was suggesting this extension  as a further learning exercise.[/quote]Right, I understand that.  My point is that to do that in C isn't easy, input is probably the most difficult thing in the language.  Especially of say, floating point numbers.

My issue isn't you're suggesting further activites, but the ones you suggest aren't easy ones, they're rather hard ones, in C anyway.

>  i was making my "meaningful commenting" suggestion more for the "future", once the original poster gets to writing longer, and not so obvious, code.I'm of the mind to cross that bridge when it comes time, but whatever :)

---

### Post by nanotube on 2006-04-24
hmm, well, maybe i was a bit overoptimistic on the learning curve... i am generally in favor of trying to take big bites when learning stuff. but it's been a while since i was starting to learn C, so maybe i was stretching it, for someone's 4th program in C. :) 
so thanks for your sober POV. ;)

---

### Post by halfvolle melk on 2006-04-24
The breaking at <=0 isn't very elegant, but my book (from 1989 :mrgreen: ) suggested to break at non positive. I'll see if I can get it to accept any numbr and break at something else for exercise.
Thank you both for your input!

---

### Post by lovebyte on 2006-04-24
Just two little advises:

When using doubles or floats, assign to them floating point values, i.e. instead of
double val = 0;
do
double val = 0.0; /* easier to see it's a double and not an int */

likewise, instead of 
printf("The average is %lf\n", (num/den));

use explicit casting, for clarity's sake:
printf("The average is %lf\n", (num/(double)den));

You need to get good clear coding habits early on! ;)

---

### Post by DoktorSeven on 2006-04-24
And to be absolutely pedantic, main() should return an int (**int main()**), which means you need **return 0;** (or **return EXIT_FAILURE;**  if your program bombs; EXIT_FAILURE is in stdlib.h) at the end of main.

---

### Post by LordHunter317 on 2006-04-24
> **lovebyte]Just two little advises:

When using doubles or floats, assign to them floating point values, i.e. instead of
double val = 0 said:**
> No, it isn't.  **Nothing is clearer than the word 'double' on the LHS.**

> use explicit casting, for clarity's sake:
printf("The average is %lf\n", (num/(double)den));Adds no clarity.

[quote=DoktorSeven]And to be absolutely pedantic, main() should return an int (int main()), which means you need return 0; While he should add a 'return 0;', he doesn't need to include the 'int' declaration, it is implict in C89.

However, he should include it.

---

### Post by halfvolle melk on 2006-04-25
[edit]
D'oh! Removing **\n]** from **scanf("%d\n"...** got rid of the second input request. The \n bit appears to ask for another and then throw it away or something.
[/edit]


I thankfully applied the suggestions to my latest endeavors (haven't got sensible commenting down yet though ;) ). Now my question is: how do I debug it?

Below is a program that ask for a digit (0/9) and tells what what numbers (0/99) and their square contain this digit. It sort of works.

Somehow it asks for input twice and ignores the second. What did I do wrong, or better yet, how do I learn to debug it myself? Example:
```
asdf
3
5
ikkiikki
37, 1369
63, 3969
73, 5329
```

Please note (some disclaimers) that I don't know how to make a function yet so thats why i've written the same thing several times. Also, using integers as booleans I'm sure is stupid. I will correct this behaviour when I know how to use booleans.
```
/* Check for given digit
 * if it's in x and x*x
 * for 0 <= x < 100 */

# include <stdio.h>

int main()
{
        int Input;
        int Loop = 0;
        int Range;
        int Rest;
        int xBool = 0;
        int xxBool = 0;

        printf("asdf\n");
        scanf("%d\n", &Input);
        printf("ikkiikki\n");
        while(Loop < 100)
        {
                Range = Loop;
                Rest = Range % 10;
                if (Rest == Input)      /* Check if digit in x is true */
                {
                        xBool = 1;
                }

                while (Range > 9 && xBool == 0)
                {
                        Range -= Rest;
                        Range /= 10;
                        Rest = Range % 10;
                        if (Rest == Input)
                        {
                                xBool = 1;
                        }
                }

                Range = Loop * Loop;
                Rest = Range % 10;
                if (Rest == Input)      /* Check if digit in x*x is true */
                {
                        xxBool = 1;
                }

                while (Range > 9 && xxBool == 0)
                {
                        Range -= Rest;
                        Range /= 10;
                        Rest = Range % 10;
                        if (Rest == Input)
                        {
                                xxBool = 1;
                        }
                }

                if (xBool && xxBool)
                {
                        printf("%d, %d\n", Loop, Loop * Loop);
                }

                xBool = 0;
                xxBool = 0;
                Loop++;
        }
        printf("Done.\n");
        return 0;
}
```

---

### Post by lovebyte on 2006-04-27
For debugging you can use gdb or graphical debuggers that are on top of gdb such as ddd.

As for booleans, they don't exist in C.  It's fine to use an int or a char and use 0 for false and 1 (or anything other than 0) for true.

---

### Post by halfvolle melk on 2006-04-27
Hey Lovebyte,
Thanks, I'll try those out!

[QUOTE=lovebyte]As for booleans, they don't exist in C.  It's fine to use an int or a char and use 0 for false and 1 (or anything other than 0) for true.[/QUOTE]
Ok, that's good then. Chars are only 1 byte so I think I'll use chars in the future.

---

### Post by nanotube on 2006-04-27
[QUOTE=lovebyte]For debugging you can use gdb or graphical debuggers that are on top of gdb such as ddd.
[/QUOTE]

another good debugging tool is simply using a lot of printf statements around your code of interest when you are trying to figure it out. :)

---


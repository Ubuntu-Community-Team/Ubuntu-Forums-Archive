---
title: "[SOLVED] What is g++ actually doing?"
date: 2008-06-23
forum: Programming Talk
---

### Post by _sphinx_ on 2008-06-23
Here is my short testing code
```

  1 #include<stdio.h>
  2 int main(void){
  3     char st[20];
  4     st[0]='d';
  5     st[1]='0';
  6     st[2]='0';
  7     printf("%s\n", st);
  8     return 0;
  9 }

```
It prints:```
d0
```
why not:```
d00
```???
And on the other hand C compiler prints:```
d00<garbage until '\0'>
```
If g++ sees '0' as end of the string then why does it prints one zero?:popcorn:

---

### Post by _sphinx_ on 2008-06-23
I am totally confused the way g++ handles the NULL and '0'. Can some tell me the difference?

---

### Post by Tony Flury on 2008-06-23
My guess (and it is only a guess) is that the g++ version of the stdio library handles the "garbage" in a slightly different way -and even the rubbish may be different between different compilers - and something in the rubbish causes it to loose last "valid" character, although without the Null termination it has no way of knowing what is valid and what isn't.

Bear in mind though that since your string is not NULL terminated correctly (certainly not within the bounds of the character array) the standard probably says that the behaviour of printf is undefined - i would imagine there is a good chance that cout << would do different things as well between compilers etc.

---

### Post by Tony Flury on 2008-06-23
> **_sphinx_ said:**
> I am totally confused the way g++ handles the NULL and '0'. Can some tell me the difference?

NULL (or in a character array it is normally specified as '\0') is a character with ASCII code of 0 - it is used to specify the end of a character string.

'0' is the character which corresponds to the digit '0' entered via the keyboard - it has an Ascii code of 48.

so to get a string that shows as d00 in the console, the string in C needs to be a set of characters 'd' '0' '0' '\0' concatenated together.

in your example you would initialise this as : 
```

st[0] = 'd' ;
st[1] = '0' ;
st[2] = '0' ;
st[3] = '\0' ;

```

or even simpler : 
```

char *st = "d00" ; 
/* remove lines 4,5,6 */

```
when you put a string in double quotes (as above) it automatically adds in the '\0' to NULL terminate the string.

Does that help ?

Does that help ?

---

### Post by Jessehk on 2008-06-23
In C, *char* arrays need to be null-terminated. It is the only way that programs can know when the string ends since arrays are just blocks of memory.
The '\0' character is used as the terminating byte.

So your example would correctly be written as:
```

#include <stdio.h>

int main( void ) {
    char st[20];

    st[0] = 'd';
    st[1] = 'o';
    st[2] = 'o';
    st[3] = '\0';

    printf( "%s\n", st );
    return 0;
}

```

EDIT: or more simple than that:
```

#include <stdio.h>

int main( void ) {
    char st[] = "doo";

    printf( "%s\n", st );
    return 0;
}

```

or even like Tony above me suggested like this:
```

char *st = "doo";

```

but I'd advise against that unless you learn more about C because now *st* points to a constant string
in memory and things can get complicated unless you understand pointers.

---

### Post by _sphinx_ on 2008-06-23
OK I think I am not able to explain you all what I actually want, I know that I can always terminate a string with '\0' but I want to know is the difference between NULL and int 0.
Here is a test code
```
#include<iostream>
int main(void){
    int st[20];
    st[0]=1;
    st[1]=2;
    st[2]=0;
    st[3]=4;
    st[4]='\0';
    int i=-1;
    while(st[i++]!=NULL)
        std::cout<<st[i]<<'\n';
    return 0;
}

```
I get the warning: NULL used in arithmetic
Why can't I use NULL to check for the termination.
And also the ouput I get is the following
```
1
2
0
```and no 4. It matches int 0 with NULL. HOW??

---

### Post by _sphinx_ on 2008-06-23
OK I think I got it, please tell me if I am wrong.
NULL is a pointer to a memory location which has bits 00000000.
int 0 is memory location with bits 00000000.
and g++ takes the value pointed by the NULL pointer to compare it with the expression and side by side gives the warning that it is doing so. While c compiler also gives the warning that you are attempting to compare pointer with interger but it does not compare it with it since when you compile above test program with c compiler with little modifications for printing it does not print anything. 
Am I true here?

---

### Post by Tony Flury on 2008-06-23
> **_sphinx_ said:**
> OK I think I am not able to explain you all what I actually want, I know that I can always terminate a string with '\0' but I want to know is the difference between NULL and int 0.
Here is a test code
```
#include<iostream>
int main(void){
    int st[20];
    st[0]=1;
    st[1]=2;
    st[2]=0;
    st[3]=4;
    st[4]='\0';
    int i=-1;
    while(st[i++]!=NULL)
        std::cout<<st[i]<<'\n';
    return 0;
}

```
I get the warning: NULL used in arithmetic


Why can't I use NULL to check for the termination.


NULL is effectively declared as a <void *> - it is inteded to be used as a pointer.

Also you are now using a int array - not a character array (which you were in your first example). int arrays don't have terminations (unless you specifically decide that the logic of your program states that the contents for instance can't be negative).

> 
And also the ouput I get is the following
```
1
2
0
```and no 4. It matches int 0 with NULL. HOW??

NULL is zero numerically - although they are inteded for different uses, and the compiler warning is letting you know that you might have then mixed up 

You will also find that the values of st[2] and st[4] are the same - remember that '/0' is ASCII code 0.

so : 
0 is a numeric zero.

NULL is effectively a pointer value which equates to zero - but I would suggest it is bad practice to use it where you actually mean 0 (as an integer) ; 

'\0' is a NULL character - used to terminate strings - it has the ASCII code of zero. 

In my opinion it is better to be explicit about what types you are using. don't use 0 to terminate a string  - use '\0', don't use 0 to intialise a pointer - use NULL. don't use '\0' to intialise a integer value - use 0.

I hope you are able to follow that.

---

### Post by Tony Flury on 2008-06-23
> **_sphinx_ said:**
> OK I think I got it, please tell me if I am wrong.
NULL is a pointer to a memory location which has bits 00000000.

No - NULL is a pointer to the memory location at address 0 (which by definition cannot be accessed)

> 
int 0 is memory location with bits 00000000.

Correct - yes it is an integer with value of zero.

> 
and g++ takes the value pointed by the NULL pointer to compare it with the expression and side by side gives the warning that it is doing so. 

If i understand you correctly - then no that is not correct. Your code does not follow the NULL pointer - and so the the compiler does not either. to follow a pointer (i.e. get the contents pointed at by a pointer) your code would need to use the * operator.

> 
While c compiler also gives the warning that you are attempting to compare pointer with interger but it does not compare it with it since when you compile above test program with c compiler with little modifications for printing it does not print anything.

The compiler does do the comparison - it silently converts the NULL pointer into an integer 0 and compares the two values as requested - which is why it stopped at st[2] in the last code.

BTW : what "little modifications for printing" - the code you posted before did exactly what i expected it to do - printed 1, 2, 0 and then stopped.

---

### Post by _sphinx_ on 2008-06-23
> **Tony Flury said:**
> BTW : what "little modifications for printing" - the code you posted before did exactly what i expected it to do - printed 1, 2, 0 and then stopped.

With little modifications for printing I meant that you have to use stdio.h and printf instead of iostream and cout. :)
And many thanks for your help

---

### Post by Tony Flury on 2008-06-23
Sphinx - are you happy now that you understand the distinctions ?

Let me know if i can help you any further.

---

### Post by _sphinx_ on 2008-06-23
> **Tony Flury said:**
> BTW : what "little modifications for printing" - the code you posted before did exactly what i expected it to do - printed 1, 2, 0 and then stopped.

I think you didn't got me here, I was saying that g++ prints 1   2   0 but cc (after making little modifications) does not prints anything at all.
EDIT: This thing still confuses me.

---

### Post by JupiterV2 on 2008-06-23
> **_sphinx_ said:**
> With little modifications for printing I meant that you have to use stdio.h and printf instead of iostream and cout. :)
And many thanks for your help

1. Out of curiosity, why are you using g++ to compile pure c code. Ideally, if you are not using ANY C++ conventions, you should probably use the gcc c compiler.

> ```
#include<iostream>
int main(void){
    int st[20];
    st[0]=1;
    st[1]=2;
    st[2]=0;
    st[3]=4;
    st[4]='\0';
    int i=-1;
    while(st[i++]!=NULL)
        std::cout<<st[i]<<'\n';
    return 0;
}
```

2. You should use std::endl in place of '\n' as it is considered better practice in C++. The only general exception when you are terminating a string:

```

std::cout << "This is a string with a newline.\n";

vs.

int x = 5;
std::cout << "This string has a variable whose value is " << x << std::endl;

```

...even then, the string should probably omit the '\n' and append std::endl instead.

---

### Post by Tony Flury on 2008-06-23
> **_sphinx_ said:**
> I think you didn't got me here, I was saying that g++ prints 1   2   0 but cc (after making little modifications) does not prints anything at all.
EDIT: This thing still confuses me.

Can you show us the code that does not print anything. We can help you if we can see the code.

---

### Post by _sphinx_ on 2008-06-23
Here is the code
And I am compiling it with cc.
And yes it gives the warning that you are trying to compare pointer with integer. But then if g++ prints 1   2    0   then this should also print.
```
#include<stdio.h>
int main(void){
    int st[20];
    st[0]=1;
    st[1]=2;
    st[2]=0;
    st[3]=4;
    st[4]='\0';
    int i=-1;
    while(st[i++]!=NULL)
        printf("%d\n",st[i]);
    return 0;
}

```

---

### Post by jim_24601 on 2008-06-23
You have a rather strange loop there. Remember that 'i++' returns the value of i *before* it was incremented, so what your loop is actually doing is testing the value at array index -1, and if it is non-zero printing out the value at index 0, then testing the value at array index 0, and so on ... since the first value it tests isn't actually part of the array, then anything might be there. If it happens by coincidence to contain a zero, then the program will print nothing at all.

The C and C++ runtime environments both perform various housekeeping tasks before your program ever sees the light of main(); obviously whatever the C runtime is doing happens to insert a 0 in the relevant location, but the C++ runtime does not. If you used '++i', or recast as a for loop:

```

for (i = 0; st[i] != 0; i++)
{
  ...
}
```

you'd get the result you expect with either compiler.

edit: Actually, that's not quite the same thing as it doesn't print the final 0. You really wanted a do loop:

```

int i = 0;
do
{
  printf ("%d\n", st[i]);
} while (st[i++] != 0);
```

---

### Post by _sphinx_ on 2008-06-23
OK I knew this but if i replace the line 
int i=-1;
with
int i=0;
I get output
2
0

And if I execute the above code with line int i=-1; with g++ I get the output
1
2
0

Oh its so messy.

---

### Post by jim_24601 on 2008-06-23
> **_sphinx_ said:**
> OK I knew this but if i replace the line 
int i=-1;
with
int i=0;
I get output
2
0

Indeed. Now you have a perfectly valid program (aside the bit where you use NULL as an integer, of course) whose behaviour is well defined. Let's step through the loop by hand.

You start off with i=0, and the 'while' line tests st[i] against NULL, as a side effect incrementing i. st[0] == 1, so we proceed into the loop body.

Now i is 1, because it was incremented by the i++. So the printf line prints st[1], which is 2.

Back we go to the 'while' line, which is now testing st[1], i.e. the value 2 again. So we run the loop again, incrementing i as we go.

Now i is 2, and we print st[2], which is 0.

The third time the 'while' line runs, i is 2, and we test st[2], which is zero. So the loop terminates. But i is incremented anyway, so it will be 3 afterwards.

The point is, you're incrementing 'i' but using its value from before it was incremented. So the value you're printing is at the array position 1 greater than the one you tested.

---

### Post by _sphinx_ on 2008-06-23
aaahh
Oh man how can I not notice this. Yup this resolved the whole issue. Many thanks to all of you.
Once again "How can I not notice this?"
I am so stupid.

---

### Post by _sphinx_ on 2008-06-23
But then I also need to say g++ and cc has many hidden differences. And it becomes very messy when we hit one of those.

---

### Post by CptPicard on 2008-06-23
> **_sphinx_ said:**
> But then I also need to say g++ and cc has many hidden differences. And it becomes very messy when we hit one of those.

Now *that* is because C and C++ are two different languages. Things get messy when you try to compile some other language using a compiler written for a different language. :)

---

### Post by WW on 2008-06-23
> **_sphinx_ said:**
> 
Once again "How can I not notice this?"
I am so stupid.
No, just learning.  ++ is an operator with side effects, and side effects are often a source of confusion and bugs.
> 
But then I also need to say g++ and cc has many hidden differences. And it becomes very messy when we hit one of those. 

I wouldn't say the problem was because of a "hidden difference".  You had a bug in which you accessed st[-1].  Apparently this location happened to be nonzero when compiled by g++, but was zero when compiled by cc.  Since the value that it "should" have is undefined, I wouldn't call this a "hidden difference" between g++ and cc.  Once the bug is fixed, the program should work the same with either compiler.

---

### Post by dwhitney67 on 2008-06-23
When you write a C program, stick to using the gcc compiler.  If you decide to write C++ programs, then use g++.

The odd behaviour that you witnessed in your programs is due to a lack of understanding of character and integer arrays; to summarize, arrays in general.

When dealing with a character values, the value '\0' is not the same as 0 (zero), unless an implicit cast is performed.  For instance, I typically will initialize a character array using this format:
[PHP]char myString[20] = {0};   // zero implicitly casted to character null[/PHP]
Another bit of advice is to spend more time understanding how to index arrays.  Also, understand the difference between pre-incrementing and post-incrementing a value.
[PHP]int value1 = 10;
++value1;                // value1 is now 11
int value2 = value1++;   // value2 is 11; value1 is 12;[/PHP]
Avoid using the post-increment in a for-loop statement; the pre-increment form is more efficient.

To conclude, don't blame the compiler for odd behaviour in your code; look/scrutinize your code first!

---

### Post by heikaman on 2008-06-23
> **dwhitney67 said:**
> 
When dealing with a character values, the value '\0' is not the same as 0 (zero)

I think you mean the value '0' is not the same as 0 (zero), not '\0' because '\0' == 0 == NULL

---

### Post by dwhitney67 on 2008-06-23
Yeah, your right.  All this medication I'm taking to battle a head-cold has the wheels in my head spinning the wrong way today.

---


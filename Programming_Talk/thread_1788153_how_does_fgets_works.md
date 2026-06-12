---
title: "how does fgets works"
date: 2011-06-22
forum: Programming Talk
---

### Post by jamesbon on 2011-06-22
I want to know how does fgets works why is fgets able to accept space entered in strings but not scanf?

Here is my program

```

#include<stdio.h>
#include<string.h>
int main ()
{
char rt[100];
char temp,*op;
printf("enter a string\n");
**fgets(rt,11,stdin);**
printf("the string you entered is %s\n",rt);
int i,k,length;
i=0;k=strlen(rt);
printf("strlen gives =%d\n",k);
length=k;
length--;
for(;i<k/2;i++)
{
temp=rt[i];
rt[i]=rt[length-i];
rt[length-i]=temp;
}
printf("the reverse string is %s\n",rt);
//printf("expt %s\n\n",rt+6);
op=strrchr(rt,'B');
printf("strrchr gives %c\n",*op);
}

```

To the above program my input string is 

> James Bond
so it is able to reverse it to 

>  dnoB semaJ
but when I use scanf(); instead of fgets then only upto the space the string is stored i.e. only James and not the word " Bond".
So scanf is not scanning after the " " blank character.Where as fgets does not have this limitation.
I want to understand how is fgets working i.e. what is the background code or logic which is running behind fgets() so that it is able to store the space also with the string.

---

### Post by r-senior on 2011-06-22
fgets reads a line from a file. From the manual page for fgets:

> char *fgets(char *s, int size, FILE *stream);
...
fgets() reads in at most one less than size characters from stream  and stores  them  into  the buffer pointed to by s.  Reading stops after an EOF or a newline.  If a newline is read, it is stored into the  buffer. A '\0' is stored after the last character in the buffer.


The scanf, fscanf functions read sequences of characters according to "conversion specifications". The "%s" conversion specification (which I assume you are using to try to match "James Bond") is defined thus:

> Matches a  sequence  of  [COLOR="Red"]non-white-space[/COLOR]  characters;  the  next    pointer must be a pointer to character array that is long enough to hold the input sequence and the  terminating  null  character ('\0'), which is added automatically.  The input string stops at white space or at the  maximum  field  width,  whichever  occurs first.

To match "James Bond", you need a conversion specification like "%s %s" and the result is two null terminated strings: "James" and "Bond".

So hopefully it's obvious that scanf is intended for breaking predictable lines of input into tokens, whereas fgets is for reading whole lines (including whitespace).

---

### Post by jamesbon on 2011-06-22
> **r-senior said:**
> fgets reads a line from a file.
So how does it stores space ?

---

### Post by StephenF on 2011-06-22
> **jamesbon said:**
> So how does it stores space ?
Wrong question. You should be asking what is it about scanf that causes it to behave oddly with space.

The characters that display space are just characters that the terminal is programmed to respond to in a particular way, but have a numerical representation no different in kind from that of printable characters.

[http://www.asciitable.com/](http://www.asciitable.com/)

---

### Post by r-senior on 2011-06-22
It's your responsibility to allocate a buffer. How you do that is up to you - it could be a char array, or you could allocate with malloc/calloc.

Either way, you give fgets the char pointer and it fills the characters in.

There is an example using a char array here:

[http://en.wikipedia.org/wiki/Fgets](http://en.wikipedia.org/wiki/Fgets)

You might also need to deal with lines in the input that are too large to fit in the buffer. Such lines are read in parts (with the final part having a '\n' as the last character).

EDIT: Ah, I thought you meant space as in allocated memory. I suspect StephenF has interpreted you correctly.

---

### Post by zobayer1 on 2011-06-22
Another thing to care about is, how gets and fgets terminate the buffer.

gets converts the terminating \n to null i.e. \0 but on the other hand, fgets stores the \n and appends null character after that.

This is important, because, it is a common habit to traverse a cstring like this:
```

for(i = 0; buff[i]; i++) {
    // do something with buff[i];
}

```

So, fgets might cause some trouble. And for the same reason, when allocating buffer, make sure that, you have enough space for the characters and an extra \n and \0.

I think it is a good habit to use fgets instead of gets. Also, fgets tends to be faster.

---

### Post by StephenF on 2011-06-22
> **zobayer1 said:**
> I think it is a good habit to use fgets instead of gets. Also, fgets tends to be faster.
It is a good habit to use neither. getline gets the job done safely but is a GNU extension. The standard C methods are inherently risky and have been the source of numerous buffer overflow exploits.

---

### Post by johnl on 2011-06-22
> **StephenF said:**
> It is a good habit to use neither. getline gets the job done safely but is a GNU extension. The standard C methods are inherently risky and have been the source of numerous buffer overflow exploits.

Please explain what security issues there are with **fgets**.  The issue with **gets** is obvious and well-known, but I have never heard anyone claim there is a problem with fgets.

---

### Post by Arndt on 2011-06-22
> **zobayer1 said:**
> 
I think it is a good habit to use fgets instead of gets. Also, fgets tends to be faster.

Why should fgets be faster than gets?

---

### Post by jamesbon on 2011-06-22
Ok I have got what I was looking for an fgets implementation

[http://www.koders.com/c/fidEB3507945463053CEFCD518EA0CDFF9EB78E24C9.aspx?s=fgets.c#L1]("http://www.koders.com/c/fidEB3507945463053CEFCD518EA0CDFF9EB78E24C9.aspx?s=fgets.c#L1")

have a look on above link I do not know how it works in Ubuntu.

```
char* fgets(char* s, int n, FILE* f)
{
  int c = 0;
  char* cs;

  cs = s;
  while (--n>0 && (c = getc(f)) != EOF) {
**    *cs++ = c;**
    if (c == '\n')
      break;
  }
  if (c == EOF && cs == s)
    return NULL;
  *cs++ = '\0';
  return s;
}


```
From the above code I want to understand the line which I have marked in Bold
```
*cs++=c
```

I have used arrays as ```
cs[i]
``` but how is *cs++ being manipulated that I am not able to understand.

---

### Post by Arndt on 2011-06-22
> **jamesbon said:**
> Ok I have got what I was looking for an fgets implementation

[http://www.koders.com/c/fidEB3507945463053CEFCD518EA0CDFF9EB78E24C9.aspx?s=fgets.c#L1]("http://www.koders.com/c/fidEB3507945463053CEFCD518EA0CDFF9EB78E24C9.aspx?s=fgets.c#L1")

have a look on above link I do not know how it works in Ubuntu.

```
char* fgets(char* s, int n, FILE* f)
{
  int c = 0;
  char* cs;

  cs = s;
  while (--n>0 && (c = getc(f)) != EOF) {
**    *cs++ = c;**
    if (c == '\n')
      break;
  }
  if (c == EOF && cs == s)
    return NULL;
  *cs++ = '\0';
  return s;
}


```
From the above code I want to understand the line which I have marked in Bold
```
*cs++=c
```

I have used arrays as ```
cs[i]
``` but how is *cs++ being manipulated that I am not able to understand.

Doesn't your C book show examples of this idiom?

```
*cs++ = c;
```
does the same thing as

```
*cs = c;
cs = cs+1;
```

*cs can be written or thought of as cs[0], too.

---

### Post by StephenF on 2011-06-22
> **johnl said:**
> Please explain what security issues there are with **fgets**.  The issue with **gets** is obvious and well-known, but I have never heard anyone claim there is a problem with fgets.
The problem arises from the need to specify an identical size to the one allocated and maintaining those values in sync as the program ages. It is much less of a problem than gets however.

The other problem with fgets is that it can't deal with lines longer than those thought adequate by the programmer.

---

### Post by JupiterV2 on 2011-06-22
The notation you see of *c++ is pointer arithmetic. *c++ is analogous to *c+1. The following can be used to iterate through an array:
```
int array[] = {1,2,3,4,5};
int* arrptr1 = array;
int* arrptr2 = array;

for (i = 0; i < sizeof (array) / sizeof (int); i++) {
  printf ("%d, %d, %d\n",
    array[i],
    *arrptr1++,
    *arrptr+i);
}
```

The above should print out:
1,1,1
2,2,2
...
5,5,5

When you assign an array to a pointer, the pointer points to the first element in the array. By incrementing the pointer (++) or (+number) then you move the pointer to the next address in the array.

---

### Post by jamesbon on 2011-06-23
> **Arndt said:**
> Doesn't your C book show examples of this idiom?

```
*cs++ = c;
```
does the same thing as

```
*cs = c;
cs = cs+1;
```

*cs can be written or thought of as cs[0], too.
I am still not able to understand.
I know that 
```
*cs=cs[0];
```
but is 
```
*cs++==cs[1]
```
and in subsequent instructions 
```
+cs++==cs[2]
```
is that what you want to say.

---

### Post by jamesbon on 2011-06-23
> **JupiterV2 said:**
> The notation you see of *c++ is pointer arithmetic. *c++ is analogous to *c+1. The following can be used to iterate through an array:


I checked your program I changed the numbers to some random numbers
```

#include<stdio.h>
int main()
{
        int array[] = { 10, 20, 30, 40, 50 };
        int *arrptr1 = array;
        int *arrptr2 = array;
        int *arrptr = array;
        int i;
        for (i = 0; i < sizeof(array) / sizeof(int); i++) {
                printf("%d, %d, %d\n", array[i], *arrptr1++, *arrptr + i);
        }
}
```
 and the output is 
```

10, 10, 10
20, 20, 11
30, 30, 12
40, 40, 13
50, 50, 14

```
Just want to know when we wrote 
```
*arrptr++; 
```
then my understanding is value stored at ```
*arrptr
``` should get incremented by 1.
Where as what I observe is the pointer is moving to next location.So just want to know what is wrong in my understanding?

I mean I am not clear on this point and in case of ```
*arrptr + i
```
the increase is different than the ```
*arrptr++
```

---

### Post by zobayer1 on 2011-06-23
> **jamesbon said:**
> I checked your program I changed the numbers to some random numbers
```

#include<stdio.h>
int main()
{
        int array[] = { 10, 20, 30, 40, 50 };
        int *arrptr1 = array;
        int *arrptr2 = array;
        int *arrptr = array;
        int i;
        for (i = 0; i < sizeof(array) / sizeof(int); i++) {
                printf("%d, %d, %d\n", array[i], *arrptr1++, *arrptr + i);
        }
}
``` and the output is as you mentioned.
Just want to know when we wrote 
```
*arrptr++; 
```then my understanding is value stored at ```
*arrptr
``` should get incremented by 1.
Where as what I observe is the pointer is moving to next location.So just want to know what is wrong in my understanding?
I mean I am not clear on this point.
Nope
*arrptr++ is a shorhand, what is does is:
x = *arrptr; arrptr++;

And what you thought about could also be done like
x = *(arrptr++)

I suggest you take a look on using pointers, arrays and **[COLOR=Red]operator precedence[/COLOR]**. Any C/C++ book will contain those.

Here is an easy trick to remember this:
x = a++;
++ will be effective after the whole instruction is completed.
x = ++a;
++ will be effective just before using the operator on which it is applied.

If you have time, you can play with these, they are really interesting.. and obviously, dont forget that ++ and -- are assignment operators at the same time, so you should take a look on
++*arrptr
++(*arrptr)
*(++arrptr)
etc....

And to your confusion about array subscript, that is just another way to write, in short:
x = a[n] is same as x = *(a + n)

You know, the name of array itself is nothing but a pointer to the first element.
so incrementing the pointer will take you to new index, no matter how you do that, either by [] operator or +
so, these two lines are essentially same

for(i = 0; i < n; i++) scanf("%d", &a[i]);
and
for(i = 0; i < n; i++) scanf("%d", a + i);

And I think, the later one is simpler to write;

Also,
a[n] = x is same as *(a + n) = x.

Hope they are clear now.

---

### Post by jamesbon on 2011-06-23
Well many thanks for your explanation.Here is one simple program after your reply I wanted to know if operator precedence is working here as I understand.

What I understand is in following statement evaluation of operators is from right to left.

```
    print("%d", *arrptr1++);
```


Hence in ***arrptr1++**  the **++** will get evaluated first and then **arrptr** and then *****
So to confirm the same I wrote another program

```
    #include<stdio.h>
    int main()
    {
            int array[] = { 10, 20, 30, 40, 50 };
            int *q1 = array;
            printf("q1 = %p\n",q1);
          printf("*q1++ = %d\n",*q1++);
            printf("q1 = %p\n",q1);
          printf("*q1++ = %d\n",*q1);
    }

```
The output of above program is different than the expected operator precedence by above logic.
The output  I got is 

```
    q1 = 0x7ffffcff02e0
    *q1++ = 10
    q1 = 0x7ffffcff02e4
    *q1++ = 20

```
So in the 2nd line of output is *q1++ = 10  I was expecting *q1++ = 20
so did the operator precedence not happened right to left?

---

### Post by JupiterV2 on 2011-06-23
> **jamesbon said:**
> 
...
```
    q1 = 0x7ffffcff02e0
    *q1++ = 10
    q1 = 0x7ffffcff02e4
    *q1++ = 20

```
So in the 2nd line of output is *q1++ = 10  I was expecting *q1++ = 20
so did the operator precedence not happened right to left?
Your program produced the correct output, despite that it isn't what you expected. By putting the increment operator after your pointer it post-increments the pointer. That means the pointer arithmetic happens AFTER the current line is executed. To pre-increment the pointer, to make the arithmetic happen BEFORE the line is executed, prefix the increment operator like so: *(++q1).

There was a bug in my last example, which you pointed out, that can be corrected as: *(arrptr + i). My original code, *arrptr + i, was incorrect. Due to operator precedence, my pointer is de-referenced and then i is added to it. That obviously was not the desired result. That's what I get for posting untested code from work on my lunch. =)

You'll note that, even if unnecessary, using brackets to enforce operator precedence can help to provide clarity. *ptr++ and *(ptr++) may produce the same result but the latter is more clear. Increment the pointer then de-reference it to get the value at that address. It can also help to eliminate potential bugs, like the one I produced. =)

---

### Post by jamesbon on 2011-06-23
> **JupiterV2 said:**
> That means the pointer arithmetic happens AFTER the current line is executed. 
I want to understand this point more I need more links or some thing which you can give as in what cases these kind of post operations happen i.e. in case some one had used ++ or -- or say % or / but still that gets executed only when the current line has finished.

> **JupiterV2 said:**
> 
There was a bug in my last example, which you pointed out, that can be corrected as: *(arrptr + i). My original code, *arrptr + i, was incorrect. Due to operator precedence, my pointer is de-referenced and then i is added to it. That obviously was not the desired result. That's what I get for posting untested code from work on my lunch. =)
To be honest I really **thank you** for posting the buggy code because to understand your code,I had played here with a lot of examples and other references and got a better insight to what I was trying to understand.If you would not have had that bug I might have missed that part.I am clear that ***arrptr+i **
is value at arrtptr+ the value of i
that is why the last column of output was 1 ,2 ,3,4,5 and since we never printed the a[5]+5 stage so it did not gave any error.

> **JupiterV2 said:**
> 
You'll note that, even if unnecessary, using brackets to enforce operator precedence can help to provide clarity. *ptr++ and *(ptr++) may produce the same result but the latter is more clear. Increment the pointer then de-reference it to get the value at that address. It can also help to eliminate potential bugs, like the one I produced. =)

Now here is the thing.Even if I put these brackets as you mentioned so that *(ptr++) gets executed the output does not change here is new code
```
#include<stdio.h>
int main()
{
        int array[] = { 10, 20, 30, 40, 50 };
        int *q1 = array;
        printf("q1 = %p\n",q1);
      printf("*q1++ = %d\n",***(q1++)**);
        printf("q1 = %p\n",q1);
      printf("*q1++ = %d\n",*q1);
}

```
The result is still the same note the use of braces as you mentioned.
Still the output is 

```
q1 = 0x7fff043f2120
***q1++ = 10** <-- I expected *q1++ = 20//since we use ()
q1 = 0x7fff043f2124
*q1++ = 20

```
So even after we used *(ptr++) that operation ++ was still executed after the current line was executed.So did curly brace () not work?


My observation is ++ on the right is behaving as follows

```

printf("*q1++ = %d\n",*q1++);
```
is the same as

```

printf("*q1++ = %d\n",*q1);
++q1;
```
irrespective of the fact that I used braces i.e. even if you change


```

printf("*q1++ = %d\n",***(**q1++**)**);
```
then also the behavior does not change and works same as 
```

printf("*q1++ = %d\n",*q1);
++q1;
```

So using braces did not helped here.
Did I miss some thing?What can be reason for these braces being not effecting in post increment condition?

---

### Post by JupiterV2 on 2011-06-23
Ok, I see where you're getting confused. There are two separate issues that you believe are the same issue.

Issue #1: Post/prefix increment operators. Whether you're using a pointer or a normal variable, these operators act the same. This has nothing to do with precedence of operators but how the operators themselves are designed to work. Let's use the following example:

```
#include <stdio.h>

int main (void)
{
  int num = 5;

  /* printf() is executed before ++ operator of num++ */
  printf ("num++ = %d", num++); /* should = 5 */
  printf ("after num++ = %d", num); /* should = 6 */

  /* ++ of ++num is executed prior to printf() */
  printf ("++num = %d", num++); /* should = 7 */
  printf ("after ++num = %d", num); /* should = 7 */

  return 0;
}
```

#2 Reference/Increment Operators: The reason brackets are used with pointers is because of operator precedence. See the example below:

```
#include <stdio.h>

int main (void)
{
  int  num[]  = {5,6,7};

  /* because of brackets num+1 takes precedence over *num */
  printf ("*(num+1) = %d", *(num+1)); /* should = 6 (2nd element */

  /* *num takes precedence over num+5 */
  printf ("*num+5 = %d", num); /* should = 10 (5+5)*/

  return 0;
}
```

De-referencing a variable takes precedence over adding whereas the increment operators both take precedence over the de-reference operator.

Here is a website which shows operator precedence: [http://en.wikipedia.org/wiki/Operators_in_C_and_C%2B%2B#Operator_precedence]("http://en.wikipedia.org/wiki/Operators_in_C_and_C%2B%2B#Operator_precedence")

You can see that addition/subtraction is below (lower precedence) than derefencing. Pre/Post fix operators take precedence (higher precedence) over dereferencing.

---


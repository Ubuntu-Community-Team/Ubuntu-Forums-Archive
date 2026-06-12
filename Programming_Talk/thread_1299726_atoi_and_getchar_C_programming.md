---
title: "atoi and getchar C programming"
date: 2009-10-24
forum: Programming Talk
---

### Post by mang109 on 2009-10-24
I am trying to get input from the user in answer to a question
 
printf("press 1 for yes and 2 for no/n");
char charr=getchar();
int key=atoi(charr);
 
if (key=  etc etc etc ...
 
the error tells me im "making a pointer from an int withoput a cast" - This means nothing to me. 
 
I am not allowed to use scanf ( arghhhhhhhh) 
 
I KNOW this code is wrong, I do not know how to fix it - I have never used either of these functions before
 
I found this question asked here : [http://ubuntuforums.org/showthread.php?t=523504](http://ubuntuforums.org/showthread.php?t=523504)
 
I KNOW I am not giving atoi the right input- but I do not even slightly understand what I am meant to give it . Id really appreciate some help here, ive been trying to fix this for hours and hours
 
Thanks in advance

---

### Post by MadCow108 on 2009-10-24
atoi expects a pointer to a null terminated cstring (aka char *) and not a plain char
[http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/](http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/)

if you only need a single char then you can use the value of the char directly without atoi:
```

char ch = getchar();
if (ch == '1')
// dostuff

```
it has to be single quotes, as single quotes means char and double quote char*
or```

char ch = getchar()-'0'; // convert ascii code to normal char integer (range -127 to 127)
if (ch == 1) // now we can check against a regular integer
// dostuff

```

---

### Post by CptPicard on 2009-10-24
> **mang109 said:**
>  
I KNOW I am not giving atoi the right input- but I do not even slightly understand what I am meant to give it .

Man page sayeth:

```

NAME
       atoi, atol, atoll, atoq - convert a string to an integer

SYNOPSIS
       #include <stdlib.h>

       int atoi(const char *nptr);

```

It wants a C-style string representation of what to convert into an integer. That is, it's a pointer to the first character, and the string should be terminated by a null, '\0'.

---

### Post by Paul Miller on 2009-10-26
Unless the assignment specifies you must do so, why bother converting the char to an int at all?  Just check to see if it's '1', or '2', or something else, and act accordingly. :-)

---

### Post by bostonaholic on 2009-10-26
It's been awhile since I've used C, but try this
```
printf("press 1 for yes and 2 for no/n");
char charr=getchar();
int key=atoi(*charr);
```

---

### Post by Arndt on 2009-10-26
> **bostonaholic said:**
> It's been awhile since I've used C, but try this
```
printf("press 1 for yes and 2 for no/n");
char charr=getchar();
int key=atoi(*charr);
```

Let's see if we can repair this. Your idea may be to supply atoi with the kind of input it wants, a pointer to char. &charr achieves this. *charr does the opposite - it follows a pointer to what it points to. Sending &charr doesn't work, though, because atoi expects not just a pointer to one char, but a pointer to a Nul-terminated string of characters, and the byte after charr is not defined by anyone to be Nul, although it may be that entirely by chance.

We can introduce such a string.

char tmp[2]; tmp[0] = getchar(); tmp[1] = '\0';
int key = atoi(tmp);

No & since tmp itself names the address to the start of the string.

The result from getchar() should be put into an int, by the way, not into a char, since the result needs to hold all possible character value, _and_ the value -1 which indicates end of file.

---

### Post by dwhitney67 on 2009-10-26
> **Arndt said:**
> ...

The result from getchar() should be put into an int, by the way, not into a char, since the result needs to hold all possible character value, _and_ the value -1 which indicates end of file.

Based on the API doc for getchar(), you are correct; it does return an int.  However placing the result directly into a char will not affect the outcome of say, a -1 (EOF) result.
```

#include <stdio.h>
int main() {
   char ch = EOF;
   printf("%c %02x %d\n", ch, ch, ch);
   return 0;
}

```

---

### Post by Arndt on 2009-10-26
> **dwhitney67 said:**
> Based on the API doc for getchar(), you are correct; it does return an int.  However placing the result directly into a char will not affect the outcome of say, a -1 (EOF) result.
```

#include <stdio.h>
int main() {
   char ch = EOF;
   printf("%c %02x %d\n", ch, ch, ch);
   return 0;
}

```

Do you mean that, if somewhere along the way, the EOF value is treated as if it were an actual char value, it may as well be stored in a char to begin with? Yes, but then that code is simply wrong.

Or maybe I missed your point.

---

### Post by dwhitney67 on 2009-10-26
> **Arndt said:**
> Do you mean that, if somewhere along the way, the EOF value is treated as if it were an actual char value, it may as well be stored in a char to begin with? Yes, but then that code is simply wrong.

Or maybe I missed your point.

EOF is define as -1.  An EOF is equivalent to 0xFFFFFFFF.  So whether you are interpreting it as an int or a char, it really doesn't matter.  Every bit is set.

So when getchar() is used to acquire input, and a ctrl-d is entered, an EOF is returned.
```

#include <stdio.h>
#include <assert.h>

int main()
{
   printf("Enter ctrl-d: ");
   char val = getchar();
   printf("value entered is: %x\n", val);
   assert(val == EOF);
   return 0;
}

```
As for my point, I was merely indicating that declaring the variable used to hold the value returned by getchar() as an int is overrated; a char will do.

---

### Post by MadCow108 on 2009-10-26
is it defined in the standard that EOF is -1?
I would guess that thats up to the implementation (although it would be a pretty stupid implementation to set it to something bigger than char :) )

also (signed char)-1 = 0xFFFFFF is architecture dependant

---

### Post by Arndt on 2009-10-26
> **dwhitney67 said:**
> EOF is define as -1.  An EOF is equivalent to 0xFFFFFFFF.  So whether you are interpreting it as an int or a char, it really doesn't matter.  Every bit is set.

So when getchar() is used to acquire input, and a ctrl-d is entered, an EOF is returned.
```

#include <stdio.h>
#include <assert.h>

int main()
{
   printf("Enter ctrl-d: ");
   char val = getchar();
   printf("value entered is: %x\n", val);
   assert(val == EOF);
   return 0;
}

```
As for my point, I was merely indicating that declaring the variable used to hold the value returned by getchar() as an int is overrated; a char will do.

255 is actually a valid character code. Are you saying it's alright to confuse it with EOF? It's not.

---

### Post by dwhitney67 on 2009-10-27
Direct from /usr/include/stdio.h:
```

...

/* End of file character.
   Some things throughout the library rely on this being -1.  */
#ifndef EOF
# define EOF (-1)
#endif

...

```

---

### Post by dwhitney67 on 2009-10-27
> **Arndt said:**
> 255 is actually a valid character code. Are you saying it's alright to confuse it with EOF? It's not.

For a signed char, the largest positive discrete value that can be held is 0x7F.  Any value in which the most significant bit is set (ie. 0x80 through 0xFF) are considered negative values.  If you set a char to 0xFF (ie 255), then this is equivalent to EOF.

```

#include <stdio.h>
#include <assert.h>

int main() {
   char ch = 0xFF;
   assert(ch == EOF);
   return 0;
}

```

P.S.  The code above generates a warning.  One way to circumvent it:
```

#include <stdio.h>
#include <assert.h>

int main() {
   char ch = 0x00;
   assert(--ch == EOF);
   return 0;
}

```

---

### Post by lisati on 2009-10-27
Instead of messing around with atoi, why not something like this?
```

.... some stuff ....
char ch=getchar();
int result=0;
... some more stuff....
if ((ch>='0') && (ch<='9')
    {
    result=ch-'0';
    ... process result ...
    }
else
    ... throw a wobbly ....

```

---

### Post by Arndt on 2009-10-27
> **dwhitney67 said:**
> For a signed char, the largest positive discrete value that can be held is 0x7F.  Any value in which the most significant bit is set (ie. 0x80 through 0xFF) are considered negative values.  If you set a char to 0xFF (ie 255), then this is equivalent to EOF.



Signed or not, a char can hold 256 different values, for example the 256 ones of Latin-1. If you want to call the code of the ÿ character -128 instead of 255, that's up to you.

The fact remains that getchar() can return 257 different values, and a char is not big enough to hold them.

---

### Post by dwhitney67 on 2009-10-27
> **Arndt said:**
> Signed or not, a char can hold 256 different values, for example the 256 ones of Latin-1. If you want to call the code of the ÿ character -128 instead of 255, that's up to you.

It is up to the code that needs to interpret the value.  If an application needs to interpret ASCII data entered from the typical US keyboard, then a char will suffice.  

> 
The fact remains that getchar() can return 257 different values, and a char is not big enough to hold them.

getchar() returns either an unsigned char or EOF.  EOF is defined to be -1, and this is equivalent to 0xFF when looking at it in the context of an unsigned 8-bit value.

As it is currently implemented, there is no way you could EVER get a return value from getchar() that is equal to 256 (or greater).  If you believe I am wrong, then please show me an example.  :)

---

### Post by MadCow108 on 2009-10-27
you are wrong in this case dwhitney:
here's your example:
```

#include <stdio.h>

int main()
{
  
  FILE * fp;
  fp = fopen("test.txt","w");
  fprintf(fp,"%c",77);
  fprintf(fp,"%c",77);
  fprintf(fp,"%c",255); // this is in theory a legit character code which is not indicating EOF
  fprintf(fp,"%c",77);
  fprintf(fp,"%c",77);
  fclose(fp);
  
  fp = fopen("test.txt","r");
  while (1) {
    signed char c = getc(fp); // wrong
    //unsigned char c = getc(fp); // wrong
    //int c = getc(fp); // right
    if (c == EOF)
      break;
    printf("%c\n",c);
  }
}
```
the char version clearly give a wrong result, it stops when encountering the legit 3rd character (this is also dependant on signed integer representation!).
the unsigned char version even goes in an infinite loop.

you could fix it by using feof(fp) but that just hides a coding error

truncating values is mostly wrong, stick to the defined return types.

---

### Post by dwhitney67 on 2009-10-27
> **MadCow108 said:**
> 
the char version clearly give a wrong result, it stops when encountering the legit 3rd character (this is also dependant on signed integer representation!).

A 255 is not a legit char value; it is however a legit unsigned char value.

> 
the unsigned char version even goes in an infinite loop.

An attempt to compare an unsigned char with a signed value (in this case EOF) without the proper casting is not wise.  Either way, it is up to the application to discern what a 255 represents... is it legit data, or an EOF?

> 
you could fix it by using feof(fp) but that just hides a coding error.

feof() is preferable to use than comparing against EOF.  But there's no error; it's a perception issue.  If I am reading signed data and I come across a 255, wtf?  If I am reading unsigned data and I come across a 255, the application's requirements will dictate what I do... either treat it as regular data or something special.  Either way, I will depend on feof() to let me know when I have reached the end of the stream.

> 
truncating values is mostly wrong, stick to the defined return types.
I agree.  However when I am cognizant of what return values I can expect from a function call, I am confident in my ability to declare the appropriate variable type required to meet the needs of the application.  99.44% of the time, the variable type I choose does fit the API documentation for the function.  But in cases where I use getchar() (or getc()), or even when I use the result of time() within an srand() call, I do not worry too much about whether I am violating some God-given commandment.

Anyhow, I think we can agree that one should use care in developing code.

---

### Post by Arndt on 2009-10-27
> **dwhitney67 said:**
> A 255 is not a legit char value; it is however a legit unsigned char value.


An attempt to compare an unsigned char with a signed value (in this case EOF) without the proper casting is not wise.  Either way, it is up to the application to discern what a 255 represents... is it legit data, or an EOF?


feof() is preferable to use than comparing against EOF.  But there's no error; it's a perception issue.  If I am reading signed data and I come across a 255, wtf?  If I am reading unsigned data and I come across a 255, the application's requirements will dictate what I do... either treat it as regular data or something special.  Either way, I will depend on feof() to let me know when I have reached the end of the stream.


I agree.  However when I am cognizant of what return values I can expect from a function call, I am confident in my ability to declare the appropriate variable type required to meet the needs of the application.  99.44% of the time, the variable type I choose does fit the API documentation for the function.  But in cases where I use getchar() (or getc()), or even when I use the result of time() within an srand() call, I do not worry too much about whether I am violating some God-given commandment.

Anyhow, I think we can agree that one should use care in developing code.

In other words, we either use feof() to detect EOF immediately and can then safely keep the read character in a char, or we use the return value from getchar() to detect EOF. In either case there is no representation problem.

---

### Post by MadCow108 on 2009-10-27
> **dwhitney67 said:**
> A 255 is not a legit char value; it is however a legit unsigned char value.

I said legit character (code) and not char. char is just an implementation dependant name, char can also be unsigned.
You can easily design an encoding scheme where 255 is a printable character like X
ascii even does this, just 255 is non printable.
[http://www.asciitable.com/](http://www.asciitable.com/)
So a file containing a byte with value 255 does not indicate a EOF!


> feof() is preferable to use than comparing against EOF. But there's no error; it's a perception issue. If I am reading signed data and I come across a 255, wtf? If I am reading unsigned data and I come across a 255, the application's requirements will dictate what I do... either treat it as regular data or something special. Either way, I will depend on feof() to let me know when I have reached the end of the stream.

it is an error because you expect to compare to -1 but in the representation -1 is also 255 which does not mean the same.
If your reading byte data you will be surprised to find 257 unique values.
getchar reads byte data (256 unique values) but returns 257 unique values. by casting it to data which can only hold 256 unique values you introduce an ambiguity and this is a mistake in almost all cases.
You then have 2 values which can indicate an EOF (or any other condition) where one of them actually means something completely different (e.g. a valid data byte in a file vs an error/condition representation code).

---


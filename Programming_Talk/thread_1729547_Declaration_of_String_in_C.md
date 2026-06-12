---
title: "Declaration of String in C"
date: 2011-04-15
forum: Programming Talk
---

### Post by chaoprokia on 2011-04-15
char s2[] = "Apple";
    char s3[5] =  "Apple";
     char s4[6] = {'A','p','p','l','e','\0'};

Are all the above valid charactor declaration?
 
Why when i do a printf?
char s3[5] = "Apple";
printf("%s\n",s3);
There a weird Symbols at the end

when i do a print for these
     char s2[] = "Apple";
 printf("%s\n",s2);
    char s3[5] =  "Apple";
 printf("%s\n",s3);
     char s4[6] = {'A','p','p','l','e','\0'};
 printf("%s\n",s4);
Why my s3 giving me 2 Apple printout?

---

### Post by r-senior on 2011-04-15
You haven't left space for the null terminating character in s3, so s3 is running into s4. If you must specify the length, you need:

```

char s3[6] = "Apple";

```

There's a similar thread already going on, which you might find interesting.

[http://ubuntuforums.org/showthread.php?t=1729013](http://ubuntuforums.org/showthread.php?t=1729013)

---

### Post by lisati on 2011-04-15
You might want to read up on the way strings are handled in C. For one thing, when using the standard library functions (strlen, printf, etc.) it is common to use a (number) zero to mark the end of strings. 

For the word "Apple" you will need to allow for 6 characters: 5 for the letters of the word, and one for the terminating zero.

---

### Post by chaoprokia on 2011-04-15
> **r-senior said:**
> You haven't left space for the null terminating character in s3, so s3 is running into s4. If you must specify the length, you need:
 
```

char s3[6] = "Apple";

```
 
There's a similar thread already going on, which you might find interesting.
 
[http://ubuntuforums.org/showthread.php?t=1729013](http://ubuntuforums.org/showthread.php?t=1729013)
 
When i use Codepad.org to run my code
there no problem.

---

### Post by lisati on 2011-04-15
> **chaoprokia said:**
> When i use Codepad.org to run my code
there no problem.

Perhaps you got lucky. C uses a zero to mark the end of the string: printf keeps on going until it finds one, and pays no attention to how large you've declared the variable.

---

### Post by chaoprokia on 2011-04-15
char s3[5] = "Apple";
So in C when i declare, i need to have 5 space for my string i need to declare [6]?
Otherwise it is a invalid string declaration?
So in such a case is this consider a declaration error?
C Compiler can run through it fine.
 
Ok Thanks.

---

### Post by Blackbug on 2011-04-15
Yes, it will be considered as declaration error, and compiler will certainly cry for it..
 
i have compiled it using gcc and you can see the error below:
 
"error: initializer-string for array of chars is too long"

---

### Post by _niai on 2011-04-17
> **chaoprokia said:**
> 
So in such a case is this consider a declaration error?
C Compiler can run through it fine.
Hi there :)

Just something to consider: if you use a C compiler and get a correct result,
this doesn't necessarily mean your code follows the C standard you are trying to follow.
I am fairly new to C programming, but I believe I am right about this. (Somebody correct me if not, please :) )
I find it's best to study the standard and stick to it, instead of relying on not getting errors.

Cheers :)

---

### Post by dazman19 on 2011-04-17
> **chaoprokia said:**
> char s2[] = "Apple";
    char s3[5] =  "Apple";
     char s4[6] = {'A','p','p','l','e','\0'};

Are all the above valid charactor declaration?
 
Why when i do a printf?
char s3[5] = "Apple";
printf("%s\n",s3);
There a weird Symbols at the end

when i do a print for these
     char s2[] = "Apple";
 printf("%s\n",s2);
    char s3[5] =  "Apple";
 printf("%s\n",s3);
     char s4[6] = {'A','p','p','l','e','\0'};
 printf("%s\n",s4);
Why my s3 giving me 2 Apple printout?

you cant assign a string to a char.
char s3[5] = "Apple";

use
char s3 = "Apple";

---

### Post by r-senior on 2011-04-17
> **dazman19 said:**
> you cant assign a string to a char. ```
char s3[5] = "Apple";
```
Your statement is correct but the example you quote is not doing that, it is initializing a char array from a string constant.

> use ```
char s3 = "Apple";
```
That is not correct. That *would* be assigning a string constant to a char and will produce a compilation error.

---

### Post by stchman on 2011-04-17
Initiaiizing a character array that way the C compiler adds the \0 null terminator on to the end.

[PHP]
#include <stdio.h>
#include <string.h>

int main( void ) {
    int i = 0;
    char s3[] = "Apple";
    
    printf( "%s\n", s3 );
    
    for( i = 0; i < sizeof( s3 ) / sizeof( char ); i++ ) {
        printf( "%d\n", s3[ i ] );
    }
    
    return 0;
} 

[/PHP]

Output:
```

Apple
65
112
112
108
101
0

```

The last character in the s3 array is a 0 or a null.

---

### Post by nvteighen on 2011-04-17
Yeah, for cases like this use the following syntax:

```

char my_string[] = "Whatever";

```

That will allow you to use sizeof() correctly and it will place the trailing '\0' automatically.

But, be aware that that syntax means something different in function declarations:

```

int some_func(char str[])
{
    /* ... */
}

```

In that case, you'll be declaring a pointer and therefore, sizeof(str) will be the size of your pointer data type; this is why I prefer to use char * for string parameters. So, use char [] only for declaring initialized strings.

---


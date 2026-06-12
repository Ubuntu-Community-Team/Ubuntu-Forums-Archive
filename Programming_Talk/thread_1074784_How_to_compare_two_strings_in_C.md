---
title: "How to compare two strings in C?"
date: 2009-02-19
forum: Programming Talk
---

### Post by Tek-E on 2009-02-19
Hi everyone.

I have continued studying C and have once again ran into another problem with strings.  I cant figure out how to use the string comparison function...I have tried a few times on my own....but Im kinda lost.

So before I asked for help I figured I would show you what I tried doing.....
```

#include <stdio.h>
#include <string.h>
int main()
{
    int strcmp ( const char *string1, const char *string 2 );
    {
        // I have gotten this far but am lost..
        // How do I actually compare the strings?

```
Do I pre-define the strings inside the function using
char *string1[256]; and so on???
Any Suggestions??

Please dont give me the answer.  I really am only looking for advice... A hint if you will.

Thank you!

---

### Post by grepgav on 2009-02-19
My hint would be to reconsider how you are using strcmp. You do indeed pass it two strings, but the key to the comparison is to analyze the return value (the integer value). I would recommend looking up the documentation for strcmp and see if you can understand how it would allow you to use it.

---

### Post by Tek-E on 2009-02-19
Then thats exactley what I shall do.
Thank you. Your help is much appreciated! :)

---

### Post by Tek-E on 2009-02-19
So I read some documentation on strcmp like you advised me to.
This is what I came up with.

Usage:
```

strcmp( string, string )
strcmp( string, string, option )

```
 0 is case-sensitive
 1 is not case-sensitive
 0 is Default

So this is what I have come up with now with the program.
```

#include <stdio.h>
#include <string.h>
int main()
{
    char string1[256];
    char string2[256];
    printf( "Enter String 1: " );
    fgets( string1, 256, stdin );
    printf( "Enter String 2: " );
    fgets( string2, 256, stdin );
    //Compare Strings
    strcmp( string1, string2, 1 );

```
So now that I have gotten this far. What would I do to get the feedback from the function? to tell wether they are different, or the same...
would this work??
```

    if ( strcmp == 0 )
    {
        printf( "The strings are the same!" );
    }
    else
    {
        if ( strcmp == 1 )
        {
            printf( "The Strings are different from eachother" );
        }
    }
}

```
Of course their or three return signals.
0
-1
and 1 but I am only worried about 0 and 1 in this case.

Soooo am I somewhat headed in the right direction?
I would try to compile it right now myself, but I am in school and away from a C compiler.

---

### Post by Krupski on 2009-02-19
> **Tek-E said:**
> Hi everyone.

I have continued studying C and have once again ran into another problem with strings.  I cant figure out how to use the string comparison function...I have tried a few times on my own....but Im kinda lost.

So before I asked for help I figured I would show you what I tried doing.....
```

#include <stdio.h>
#include <string.h>
int main()
{
    int strcmp ( const char *string1, const char *string 2 );
    {
        // I have gotten this far but am lost..
        // How do I actually compare the strings?

```
Do I pre-define the strings inside the function using
char *string1[256]; and so on???
Any Suggestions??

Please dont give me the answer.  I really am only looking for advice... A hint if you will.

Thank you!

STRCMP takes two strings as input and returns an INT based of if string1 is less than, greater than or equal to string2.

Since you don't want "the answer" this is all I'll tell you.

-- Roger

---

### Post by Krupski on 2009-02-19
> **Tek-E said:**
> 
Soooo am I somewhat headed in the right direction?
I would try to compile it right now myself, but I am in school and away from a C compiler.

Try this:

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(void)
{

    int n;

    char string1[] = "Hello";
    char string2[] = "HELLO";
    char string3[] = "There";

    n = strcmp(string1, string3);
    printf("STRCMP(%s, %s) returns %d\n", string1, string3, n);

    n = strcmp(string3, string1);
    printf("STRCMP(%s, %s) returns %d\n", string3, string1, n);

    n = strcmp(string1, string2);
    printf("STRCMP(%s, %s) returns %d\n", string1, string2, n);

    n = strcmp(string2, string1);
    printf("STRCMP(%s, %s) returns %d\n", string2, string1, n);

    n = strcmp(string1, string1);
    printf("STRCMP(%s, %s) returns %d\n", string1, string1, n);

    exit(0);

}

```


When run, it prints this:

```

STRCMP(Hello, There) returns -1
STRCMP(There, Hello) returns 1
STRCMP(Hello, HELLO) returns 1
STRCMP(HELLO, Hello) returns -1
STRCMP(Hello, Hello) returns 0

```


For fun, make a case INSENSITIVE version of strcmp (that is, "Hello" and "HELLO" compare as equal (returns 0).

-- Roger

---

### Post by Tek-E on 2009-02-19
Okay thank you very much!

---

### Post by Can+~ on 2009-02-19
strcmp just retunrs 0 if both strings are equal

```

    if (strcmp == 0 )
    {
        printf( "The strings are the same!" );
    }
    else
    {
        if ( strcmp == 1 )
        {
            printf( "The Strings are different from eachother" );
        }
    }

```

should be:

```

    if (strcmp(string1, string3) == 0)
    {
        printf("The strings are the same!");
    }
    else
    {
        printf("The Strings are different from eachother");
    }

```

also notice the existance of "[FONT="Courier New"]if () { } else if() { } else if(){} .... else {}[/FONT]" or "[FONT="Courier New"]switch { case:break;... default:break;}[/FONT]"

---

### Post by Tek-E on 2009-02-19
Thank you can+~ that cleared things up a bit more!  Thank you all very much! I am very thankful for all the help you guys have offered!

---

### Post by Tek-E on 2009-02-20
So from the help you guys offered me this is what I have come up with..... Still haven't tested it yet though.

```

//Compares Two Strings
#include<stdio.h>
#include<string.h>
int main()
{
	char string1[256];
	char string2[256];
	printf( "Enter String 1: " );
	fgets( string1, 256, stdin );
	printf( "Enter String 2: " );
	fgets( string2, 256, stdin );
	//Compare Strings
	if ( strcmp(string1, string 2) == 0)
	{
		printf( "The strings are the same\n" );
	}
	else
	{
		printf( "The strings are different from eachother!\n" );
	}
}

```

---


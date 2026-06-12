---
title: "short int datatye"
date: 2010-03-19
forum: Programming Talk
---

### Post by LittleU on 2010-03-19
Hi ,
 
it seems the below code looks fine.
 
but the out put it is generating for the last printf statement is for NUM1 is 0.
 
i cant get the problem.
 
please any remarks.
 
 
```
 
#include <stdio.h>
int main()
{
        short int num1,num2;
        printf("\n ENTER THE VALUE OF NUM1 : ");
        scanf("%d",&num1);
        printf("\n NUM1 = %d ",num1);
        printf("\n ENTER THE VALUE OF NUM2 : ");
        scanf("%d",&num2);
        printf("\n NUM2 = %d ",num2);
        printf("\n NUM1 = %d NUM2 = %d",num1,num2);
}

```
 
if i change %d to %hd in scanf its working fine.

---

### Post by MadCow108 on 2010-03-19
%d in scanf tells it to read an integer of the sizeof(int) (mostly 4 byte) into the buffer provided as argument. It assumes the buffer is big enough for the 4 byte integer.
but your buffer has the size of a short int (usually 2 byte)
so you overwrite your buffer leading to undefined behavior.

you have to tell scanf exactly which type of integer it should read.
So you need the h modifier to tell scanf only to write sizeof(short int) bytes into the provided buffer

some modifiers are listed here:
[http://www.cplusplus.com/reference/clibrary/cstdio/scanf/](http://www.cplusplus.com/reference/clibrary/cstdio/scanf/)

---

### Post by Compyx on 2010-03-19
> **LittleU said:**
> Hi ,
 
it seems the below code looks fine.
 
but the out put it is generating for the last printf statement is for NUM1 is 0.
 
i cant get the problem.
 
please any remarks.
 
 
```
 
#include <stdio.h>
int main()
{
        short int num1,num2;
        printf("\n ENTER THE VALUE OF NUM1 : ");
        scanf("%d",&num1);
        printf("\n NUM1 = %d ",num1);
        printf("\n ENTER THE VALUE OF NUM2 : ");
        scanf("%d",&num2);
        printf("\n NUM2 = %d ",num2);
        printf("\n NUM1 = %d NUM2 = %d",num1,num2);
}

```
 
if i change %d to %hd in scanf its working fine.

Like MadCow108 told you, it's important to specify exactly what needs to be read or written when using scanf() and friends. If you turn up the warnings of your compiler, you'd have gotten a few warnings:
```

compyx@aspire7730g:~$ gcc -g -Wall -Wextra -pedantic -ansi /tmp/shorty.c 
/tmp/shorty.c: In function ‘main’:
/tmp/shorty.c:6: warning: format ‘%d’ expects type ‘int *’, but argument 2 has type ‘short int *’
/tmp/shorty.c:9: warning: format ‘%d’ expects type ‘int *’, but argument 2 has type ‘short int *’
/tmp/shorty.c:12: warning: control reaches end of non-void function

```

Additionally, as you can see from the last warning: you need to return a value from main: either 0, EXIT_SUCCESS or EXIT_FAILURE. The definition of main is also incorrect: it should be either `int main(void)' or `int main(int argc, char *argv[])'. But you define main as a function taking an unspecified number of arguments returning int. If I'm not mistaken, in C++ the empty argument list does mean it takes no arguments, but it's been a long time since I've done any C++, so I could be mistaken.

---

### Post by LittleU on 2010-03-22
> **MadCow108 said:**
> %d in scanf tells it to read an integer of the sizeof(int) (mostly 4 byte) into the buffer provided as argument. It assumes the buffer is big enough for the 4 byte integer.
but your buffer has the size of a short int (usually 2 byte)
so you overwrite your buffer leading to undefined behavior.
 
you have to tell scanf exactly which type of integer it should read.
So you need the h modifier to tell scanf only to write sizeof(short int) bytes into the provided buffer
 
some modifiers are listed here:
[http://www.cplusplus.com/reference/clibrary/cstdio/scanf/](http://www.cplusplus.com/reference/clibrary/cstdio/scanf/)
 
 
Thank you for your reply.
 
i also have doubt regarding float and double.
 
when i want to read float value using scanf i use the format specifier as %f.
 
but if i want to read any double value what is the correct format specifier to use.

---

### Post by soltanis on 2010-03-22
You should read the manpage for scanf. (sudo apt-get install manpages-dev)

For a double (long float) you need the specifier %lf (that's ell-eff).

EDIT: apologies for "%ld", yes that is for **l**ong integers.

---

### Post by LittleU on 2010-03-22
> **soltanis said:**
> You should read the manpage for scanf. (sudo apt-get install manpages-dev)
 
For a double (long float) you need the specifier %ld (that's ell-dee).
 
 
please have a look at the below program:
 
i think %ld format specifier is not correct for reading double args.
 
> [spark@localhost DATATYPE]$ gcc -Wall dbl.c
dbl.c: In function `main':
dbl.c:13: warning: long int format, double arg (arg 2)
dbl.c:14: warning: long int format, double arg (arg 2)
dbl.c:18: warning: long int format, double arg (arg 2)
[spark@localhost DATATYPE]$ cat dbl.c

 
```

#include<stdio.h>
int main( void ) {
        double d ;
        printf("Enter a double value :");
        scanf("%ld",&d);
        printf("double : %ld \n", d);
        return 0;
}
 

```

---

### Post by schauerlich on 2010-03-22
Use "%lf" for doubles (which are **l**ong **f**loats)

"%ld" is for long ints.

---

### Post by LittleU on 2010-03-22
> **schauerlich said:**
> Use "%lf" for doubles (which are **l**ong **f**loats)
 
"%ld" is for long ints.
 
do we have any specifeir called %lf .
 
in one of the forums its mentioned that there is no such specifier.
 
[http://www.daniweb.com/forums/thread241546.html](http://www.daniweb.com/forums/thread241546.html)
 
 
Thanks.

---

### Post by Compyx on 2010-03-22
> **LittleU said:**
> do we have any specifeir called %lf .
 
in one of the forums its mentioned that there is no such specifier.
 
[http://www.daniweb.com/forums/thread241546.html](http://www.daniweb.com/forums/thread241546.html)
 
 
Thanks.

For scanf() there is, for printf() there isn't, as is implied in one of the replies in that particular thread. scanf() needs '%lf' to scan a double, while print() uses  %e, %E, %f, %g and %G to print doubles, the 'l' length modifier doesn't apply for doubles in the case of printf(). So in order to print a float with printf(), you need to cast the float to double before passing it to printf, ie:
```

float f = 1.23f;
printf("this is a float: %f\n", (double)f);

```

Confusing, isn't it? That's what I love about C: it's a relatively 'small' language, only a handful of keywords and constructs and a small standard library, but quite difficult to really master.

---


---
title: "Variables in array subscript"
date: 2010-01-07
forum: Programming Talk
---

### Post by pokebirdd on 2010-01-07
According to this faq ([http://c-faq.com/ansi/constasconst.html](http://c-faq.com/ansi/constasconst.html)), I shouldn't be able to use variables in array subscripts in C. But when I try to compile
[php]#include <stdio.h>

int main(){
    const int maxline = 10;
    char line[maxline];
    printf("%s\n", line);
    return 0;
}[/php]using the command ```
gcc -Wall buf.c
``` , it compiles perfectly without error. This isn't part of any larger program, I'm simply curious as to why there isn't an error when the faq I read says:
> One mild surprise is that const variables are *not* ``constant expressions'' as defined on page 38. You can't say something like 
[PHP]	const int maxline = 1000;
	char line[maxline+1];		/* WRONG */[/PHP]


---

### Post by PaulM1985 on 2010-01-07
Do you need to have char[] line[maxline]?

Paul

EDIT:  After looking this up, I think I am wrong.  Please ignore this post.

---

### Post by PaulM1985 on 2010-01-07
To make amends for my dodgy post I have done some googling.  For dynamic memory allocation on execution I think you need to use a pointer.  This link explains it:

[http://www.cs.bu.edu/teaching/cpp/string/array-vs-ptr/](http://www.cs.bu.edu/teaching/cpp/string/array-vs-ptr/)

I think you need point 4 "Dynamically-allocated string".  If you are using C I think you will need to use free() on the pointer rather than delete which I believe is C++.

Paul

---

### Post by pokebirdd on 2010-01-07
I probably didn't clarify what I wanted to do with this. To be honest, I know about dynamically allocating memory and stuff. It's just that I was reading up on K&R and some notes to accompany it when I came across something saying that you can't use variables as the array size in an array declaration. 

So I just did some experimenting and found that gcc let's me declare an array with a variable size if I don't initialize it. I'm just a bit curious as to why you can declare such an array without problems when what I read([http://c-faq.com/ansi/constasconst.html](http://c-faq.com/ansi/constasconst.html)) clearly says you cannot.;)

---

### Post by SeanHodges on 2010-01-07
> **pokebirdd said:**
> According to this faq ([http://c-faq.com/ansi/constasconst.html](http://c-faq.com/ansi/constasconst.html)), I shouldn't be able to use variables in array subscripts in C. But when I try to compile
[PHP]#include <stdio.h>

int main(){
    const int maxline = 10;
    char line[maxline];
    printf("%s\n", line);
    return 0;
}[/PHP]

using the command ```
gcc -Wall buf.c
``` , it compiles perfectly without error. It's only when I try to initialize line that I get the error:
```
buf.c: In function ‘main’:
buf.c:19: error: incompatible types when assigning to type ‘char[(unsigned int)maxline]’ from type ‘char *’

```

Can someone pleases explain to me why gcc accepts the original declaration?

What compiler version are you using?

I compiled your example code with

> gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

and it compiles and runs for me with no errors (-Wall enabled as well). In fact, I'm able to copy strings into it and it still doesn't complain.

Perhaps you are running a more recent (and supposedly more standards compliant) GCC?

---

### Post by dwhitney67 on 2010-01-07
> **pokebirdd said:**
> According to this faq ([http://c-faq.com/ansi/constasconst.html](http://c-faq.com/ansi/constasconst.html)), I shouldn't be able to use variables in array subscripts in C. But when I try to compile
[PHP]#include <stdio.h>

int main(){
    const int maxline = 10;
    char line[maxline];
    printf("%s\n", line);
    return 0;
}[/PHP]

using the command ```
gcc -Wall buf.c
``` , it compiles perfectly without error. It's only when I try to initialize line that I get the error:
```
buf.c: In function &#8216;main&#8217;:
buf.c:19: error: incompatible types when assigning to type &#8216;char[(unsigned int)maxline]&#8217; from type &#8216;char *&#8217;

```

Can someone pleases explain to me why gcc accepts the original declaration?

Why don't you show the complete program you are using?  The error you presented is a **compiler** error, and it occurs on line 19 of your code.  Earlier you stated that you compiled without errors.  :confused:

P.S.  I bet you attempted something like:
```

line = "foo";

```
You can't do that; use strcpy() or the more IA-friendly strncpy().

---

### Post by pokebirdd on 2010-01-07
I'm running
```
gcc (Ubuntu 4.4.1-4ubuntu8) 4.4.1
```and the thing is, I'm pretty sure my example code **should** produce an error. The thing is that there isn't one. Could it be that my resources are outdated (i.e. you **can** declare arrays with variable lengths instead of using pointers and dynamically allocating memory)?

Because this is what I've read says:
> One mild surprise is that const variables are *not* ``constant expressions'' as defined on page 38. You can't say something like 
[php]const int maxline = 1000;
    char line[maxline+1];        /* WRONG */
[/php]EDIT: Your right, I did assign a string to the array, my bad. But still, I understand why there** isn't** a compiler error

---

### Post by dwhitney67 on 2010-01-07
> **pokebirdd said:**
> 
EDIT: Your right, I did assign a string to the array, my bad. So there's no errors then.

A compiler error would be produced if you were to attempt to compile your code using the -ansi option.  This forces the compiler to adhere to the ISO C90 standards, which forbids that type of declaration.  Here's the warning:
```

warning: ISO C90 forbids variable length array &#8216;line&#8217;

```
To rectify the problem, you have two options:

Option 1:
```

#define MAXLINE 10

...

int main()
{
   char line[MAXLINE];
   ...
}

```

Option 2:
```

#include <stdlib.h>

...

int main()
{
   const int maxline = 10;
   char* line = malloc(maxline);

   ...

   free(line);

   ...
}

```

IMO, Option 2 is more widely used, and is more versatile.  For instance, it allows one to grow the size of the array when/if needed.

---

### Post by pokebirdd on 2010-01-07
Oh, so it's okay to use that type of declaration if I don't use the -ansi option? I assume it's bad practice though correct?

Also, if say I wanted to store constant strings (e.g. the dialogue in an adventure game), which would be preferred?
[php]
int main(){
char *dialogue = "Hello";
...
}
[/php]or

[php]#define MAXLINE 100
...

int main(){
const char dialogue[MAXLINE] = "Hello";
...
}[/php]

---

### Post by dwhitney67 on 2010-01-07
> **pokebirdd said:**
> Oh, so it's okay to use that type of declaration if I don't use the -ansi option? I assume it's bad practice though correct?

Yep.

> 
Also, if say I wanted to store constant strings (e.g. the dialogue in an adventure game), which would be preferred?
[php]
int main(){
char *dialogue = "Hello";
...
}
[/php]or

[php]#define MAXLINE 100
...

int main(){
const char dialogue[MAXLINE] = "Hello";
...
}[/php]
Neither format; the preferred format (which is very close to your first choice) is:
```

const char* dialogue = "Hello";

```

---

### Post by pokebirdd on 2010-01-07
Ok, thanks a lot, that really helped! :D

---

### Post by SeanHodges on 2010-01-07
> **dwhitney67 said:**
> A compiler error would be produced if you were to attempt to compile your code using the -ansi option.  This forces the compiler to adhere to the ISO C90 standards, which forbids that type of declaration.  Here's the warning:
```

warning: ISO C90 forbids variable length array ‘line’

```


Adding the "-ansi" option does nothing for me:

```
[13:13:49 #520] sean@SEAN-PC:~/Desktop$ tee < test.c 
#include <stdio.h>

int main(){
	const int maxline = 10;
	char line[maxline];
	printf("%s\n", line);
	return 0;
}
[13:14:07 #522] sean@SEAN-PC:~/Desktop$ gcc -ansi -Wall test.c -o test
[13:14:20 #523] sean@SEAN-PC:~/Desktop$ ./test

[13:14:22 #524] sean@SEAN-PC:~/Desktop$
```

Any idea why the -ansi switch does not produce that warning for me? Have I missed something?

---

### Post by dwhitney67 on 2010-01-07
> **SeanHodges said:**
> ...

Any idea why the -ansi switch does not produce that warning for me? Have I missed something?

I think I goofed earlier; it is not the -ansi, but the -pedantic that produces the error.

Try
```

gcc -Wall -pedantic test.c
test.c: In function 'main':
test.c:5: warning: ISO C90 forbids variable-size array 'line'

```
Here's the info on pedantic:
```

       -pedantic
           Issue all the warnings demanded by strict ISO C and ISO C++; reject all pro-
           grams that use forbidden extensions, and some other programs that do not follow
           ISO C and ISO C++.  For ISO C, follows the version of the ISO C standard speci-
           fied by any -std option used.

           Valid ISO C and ISO C++ programs should compile properly with or without this
           option (though a rare few will require -ansi or a -std option specifying the
           required version of ISO C).  However, without this option, certain GNU exten-
           sions and traditional C and C++ features are supported as well.  With this
           option, they are rejected.

```

---

### Post by SeanHodges on 2010-01-07
> **dwhitney67 said:**
> Try
```

gcc -Wall -pedantic test.c
test.c: In function 'main':
test.c:5: warning: ISO C90 forbids variable-size array 'line'

```

Great, that works thanks! I didn't think to check the manual.

---


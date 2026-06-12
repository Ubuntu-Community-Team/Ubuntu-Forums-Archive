---
title: "Issue with c language - about iostream"
date: 2012-05-21
forum: Programming Talk
---

### Post by pellyhawk on 2012-05-21
I met a weird issue when running a function, so I write a c language test code to verified it. Those codes in red output different results. 

BTW, how to clear up the warning: format ‘%d’ expects type ‘int *’, but argument 2 has type ‘unsigned char *’(scanf("%d", &t1); I also marked it in red in the following source code)?

Any help will be welcome. Thanks.

Makefile related to compiling is as follows.
```
#PREFIX = arm-none-linux-gnueabi-

CC = $(PREFIX)gcc

$(EXE): $(OBJS)
	$(CC) -o $(EXE) $(OBJS) 
$(OBJS): $(SOURCES) 
	$(CC) -c $(SOURCES) 
clean:
	-$(RM) -f $(OBJS)
	-$(RM) -f $(EXE)
```

Related source code is as follows:
```
  unsigned char t1 = 0;
  unsigned char t2 = 0;
  unsigned char t3 = 0;
  unsigned char t4 = 0;
  
  printf("t1: ");
  [COLOR="Red"]scanf("%d", &t1);// how to clear the warning?[/COLOR]
  printf("t1 = %d\n", t1); //
  
  printf("t2: ");
  [COLOR="Red"]scanf("%d", &t2);// how to clear the warning?[/COLOR]
  printf("t2 = %d\n", t2); //
  
  printf("t3: ");
  [COLOR="Red"]scanf("%d", &t3);// how to clear the warning?[/COLOR]
  printf("t3 = %d\n", t3); //
  
  printf("t4: ");
  [COLOR="Red"]scanf("%d", &t4);// how to clear the warning?[/COLOR]
  printf("t4 = %d\n", t4); //
  
  printf("\n");
  
  [COLOR="Red"]//get different results[/COLOR]
[COLOR="Red"]  printf("t1 = %d\n", t1);
  printf("t2 = %d\n", t2);
  printf("t3 = %d\n", t3);
  printf("t4 = %d\n", t4);[/COLOR]
  
  printf("\n");
  
  [COLOR="Red"]//get different results[/COLOR]
  [COLOR="Red"]printf("t1 = %d t2 = %d t3 = %d, t4 = %d\n", t1, t2, t3, t4);[/COLOR]
```

---

### Post by zombifier25 on 2012-05-21
I can't help with your problems (I'm a C++ and Python person) but the title is misleading. C uses stdio.h, not iostream like C++.

---

### Post by pellyhawk on 2012-05-21
yep!

I have modified the thread title. Thanks.

BTW, while see this thread from [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39), it is still "iostream".

---

### Post by steeldriver on 2012-05-21
format specifier %d is a (signed) int - try %c ?

---

### Post by Bachstelze on 2012-05-21
Do Not Use scanf()&#8482;

[http://c-faq.com/stdio/scanfprobs.html](http://c-faq.com/stdio/scanfprobs.html)

---

### Post by dwhitney67 on 2012-05-21
> **steeldriver said:**
> format specifier %d is a (signed) int - try %c ?

Actually, try %hhu when dealing with unsigned char types.

---

### Post by trent.josephsen on 2012-05-21
+1 vote for not using scanf. I advise using fgets+strtol and converting to unsigned char afterward.

Speaking of which, unsigned char seems an odd choice for an integer value entered by a user. Any reason to not simply use int or unsigned? (Wait, nvm, you said you wrote this to test something -- I'll assume there was a reason.)

---

### Post by pellyhawk on 2012-05-21
I changed unsigned char to unsigned short, but the result still very weird. What's the matter?

```
t1: 1
t1 = 1
t2: 2
t2 = 2
t3: 3
t3 = 3
t4: 4
t4 = 4

[COLOR="Red"]t1 = 0
t2 = 0
t3 = 0
t4 = 4[/COLOR]

[COLOR="Red"]t1 = 0 t2 = 0 t3 = 0, t4 = 4[/COLOR]

```

fgets+strtol seems not very convenient(2 functions will be called, while scanf() is called only once), especially if there are spaces in string, strtol() will ignore them. 

So is there alternative funtion?

---

### Post by pellyhawk on 2012-05-21
dwhitney67 and stilldriver,

I have tried your proposals, it works very well:)

But if I ignore those warnings, only changed ussinged char to unsigned short, results are still very weird. I have posted my results at my last post.

---

### Post by dwhitney67 on 2012-05-21
> **pellyhawk said:**
> ...

But if I ignore those warnings, only changed ussinged char to unsigned short, results are still very weird. I have posted my results at my last post.

If you have modified your code, and the results are still incorrect (they appear so), then you should have re-posted your latest code.

For what it is worth, here's an example using unsigned short types; note that there is NO error checking.
```

#include <stdio.h>

int main()
{
    unsigned short t1, t2, t3, t4;

    printf("Enter t1: ");
    scanf("%hu", &t1);
    printf("Enter t2: ");
    scanf("%hu", &t2);
    printf("Enter t3: ");
    scanf("%hu", &t3);
    printf("Enter t4: ");
    scanf("%hu", &t4);

    printf("t1 = %hu, t2 = %hu, t3 = %hu, t4 = %hu\n", t1, t2, t3, t4);

    return 0;
}

```

And here's a way that uses fgets() and sscanf():
```

#include <stdio.h>
#include <stdlib.h>

unsigned short getValue(const char* prompt)
{
    char input[20];
    unsigned short value = 0;

    printf("%s", prompt);

    fgets(input, sizeof(input), stdin);

    if (sscanf(input, "%hu", &value) != 1)
    {
        fprintf(stderr, "Cannot read value!\n");
        exit(0);
    }

    return value;
}

int main()
{
    unsigned short t1 = getValue("Enter t1: ");
    unsigned short t2 = getValue("Enter t2: ");
    unsigned short t3 = getValue("Enter t3: ");
    unsigned short t4 = getValue("Enter t4: ");

    printf("t1 = %hu, t2 = %hu, t3 = %hu, t4 = %hu\n", t1, t2, t3, t4);

    return 0;
}

```

---

### Post by pellyhawk on 2012-05-21
Thank you very much for your feedback!

I repost my code and result. 
My code is as follows
```
  unsigned short t1 = 0;
  unsigned short t2 = 0;
  unsigned short t3 = 0;
  unsigned short t4 = 0;
  
  printf("t1: ");
  scanf("%d", &t1);
  printf("t1 = %d\n", t1); //
  
  printf("t2: ");
  scanf("%d", &t2);
  printf("t2 = %d\n", t2); //
  
  printf("t3: ");
  scanf("%d", &t3);
  printf("t3 = %d\n", t3); //
  
  printf("t4: ");
  scanf("%d", &t4);
  printf("t4 = %d\n", t4); //
  
  printf("\n");
  
  printf("t1 = %d\n", t1);
  printf("t2 = %d\n", t2);
  printf("t3 = %d\n", t3);
  printf("t4 = %d\n", t4);
  
  printf("\n");
  
  printf("t1 = %d t2 = %d t3 = %d, t4 = %d\n", t1, t2, t3, t4);
```

and results is as follows
```
t1: 1
[COLOR="Red"]t1 = 1
t2: 2
t2 = 2
t3: 3
t3 = 3[/COLOR]
t4: 4
t4 = 4

[COLOR="Red"]t1 = 0
t2 = 0
t3 = 0
t4 = 4

t1 = 0 t2 = 0 t3 = 0, t4 = 4[/COLOR]

```

I notice all these errors seem they are result from "%d", but I do not know why. your code are "%hu" or "hhu".

> **dwhitney67 said:**
> If you have modified your code, and the results are still incorrect (they appear so), then you should have re-posted your latest code.

For what it is worth, here's an example using unsigned short types; note that there is NO error checking.
```

#include <stdio.h>

int main()
{
    unsigned short t1, t2, t3, t4;

    printf("Enter t1: ");
    scanf("%hu", &t1);
    printf("Enter t2: ");
    scanf("%hu", &t2);
    printf("Enter t3: ");
    scanf("%hu", &t3);
    printf("Enter t4: ");
    scanf("%hu", &t4);

    printf("t1 = %hu, t2 = %hu, t3 = %hu, t4 = %hu\n", t1, t2, t3, t4);

    return 0;
}

```

And here's a way that uses fgets() and sscanf():
```

#include <stdio.h>
#include <stdlib.h>

unsigned short getValue(const char* prompt)
{
    char input[20];
    unsigned short value = 0;

    printf("%s", prompt);

    fgets(input, sizeof(input), stdin);

    if (sscanf(input, "%hu", &value) != 1)
    {
        fprintf(stderr, "Cannot read value!\n");
        exit(0);
    }

    return value;
}

int main()
{
    unsigned short t1 = getValue("Enter t1: ");
    unsigned short t2 = getValue("Enter t2: ");
    unsigned short t3 = getValue("Enter t3: ");
    unsigned short t4 = getValue("Enter t4: ");

    printf("t1 = %hu, t2 = %hu, t3 = %hu, t4 = %hu\n", t1, t2, t3, t4);

    return 0;
}

```

---

### Post by dwhitney67 on 2012-05-21
%d is for an int type

%u is for an unsigned int type

%hu is for an unsigned short type (h = half of an int)

%hhu is for an unsigned char type (hh = half of half of an int)

%lu is for an unsigned long int type

Just Google for "print format codes" (or scanf); some resources are more detailed than others.

---

### Post by pellyhawk on 2012-05-22
I know these format code. I was only surprised by the result of my code such as printf("%d", t); t1, t2, t3 have very different result with t4(t1, t2, t3 are all equal to 0, while t4 is equal to 4). 

What do you know result in these weird results?

---

### Post by dwhitney67 on 2012-05-22
> **pellyhawk said:**
> I know these format code. I was only surprised by the result of my code such as printf("%d", t); t1, t2, t3 have very different result with t4(t1, t2, t3 are all equal to 0, while t4 is equal to 4). 

What do you know result in these weird results?

Weird results can happen when the application attempts to stuff 4-bytes of data (a signed int) into a 2-byte area (unsigned short).  Frankly, it's amazing your application did not crash.

Next time, consider compiling your code with the -Wall option, perhaps even with the -pedantic one too.

---

### Post by steeldriver on 2012-05-22
> **pellyhawk said:**
> fgets+strtol seems not very convenient(2 functions will be called, while scanf() is called only once), especially if there are spaces in string, strtol() will ignore them. 

So is there alternative funtion?

it's str**tok**() not str**tol**() that you want here - get a string and then **tok**enize it (i.e. break it down into lexical unit separated by some delimiter - which could be whitespace)

tokenizing is more robust than scanf / sscanf because it can handle multiple delimiters (space, tab, comma etc.) whereas scanning only works if the user types EXACTLY what's in the fixed format string

if you really want to go crazy look at the true lexical scanning tools (lex or flex)

---

### Post by pellyhawk on 2012-05-22
I list all the changes during running and cannot see the stuff and transform process because no bit is lost and just add 0 at high byte(MSB). Specially, why t1, t2, t3 are so different from t4(t1, t2, t3 all changed to 0 while t4 not)?

         t1          t2         t3           t4
1)scanf: 0x0001      0x0002     0x0003       0x0003    (2-byte unsigned short)                    
2)printf:0x00000001, 0x00000002, 0x00000003, 0x00000004(4-byte signed int)
3)printf:[COLOR="Red"]0x00000000, 0x00000000, 0x00000000[/COLOR], 0x00000004(4-byte signed int)
4)printf:[COLOR="Red"]0x00000000, 0x00000000, 0x00000000[/COLOR], 0x00000004(4-byte signed int)

I tried compiling my code with -Wall and -pedantic(gcc -o convertor -Wall convertor.c/gcc -o -pedantic convertor.c), no more warning appeared and the application did not crash.

> **dwhitney67 said:**
> Weird results can happen when the application attempts to stuff 4-bytes of data (a signed int) into a 2-byte area (unsigned short).  Frankly, it's amazing your application did not crash.

Next time, consider compiling your code with the -Wall option, perhaps even with the -pedantic one too.

---


---
title: "C language error on Ubuntu,but Ok with DOS according to book"
date: 2016-01-28
forum: Programming Talk
---

### Post by itpro007ca on 2016-01-28
In "C For Dummies Volume 1" by Dan Gookin c. 1994,page 46-50,the following program works fine(according to the book):

```
#include <stdio.h>

void main()

{

	char me[20];

	printf("What is your name?");
	scanf("%s",&me);
	printf("Pleased to meet you,%s!\n",me);
}
```

Yet in Ubuntu 15.10,trying to compile it gets the following error:

whoru.c: In function &#8216;main&#8217;:
whoru.c:10:8: warning: format &#8216;%s&#8217; expects argument of type &#8216;char *&#8217;, but argument 2 has type &#8216;char (*)[20]&#8217; [-Wformat=]
  scanf("%s",&me);


I'm just learning C,so I'm stuck,but,the error message seems to do with "char me[20], which the author says: "...the preceding lines tells the compiler to create a string variable.*char* short for *character*,identifies a storage place for characters.The name of the string is *me*,The number in the bracket tells the compiler to set aside 20 characters of storage space...to be used by the *me* variable."


        I need to solve this,because there is another program called colour.c,which has a few similar lines on page 80,ie:

char name[20]
char colour[20]

followed by printf and scanf statesments to extract name and favorite colour,then say,ie: Popeye's favorite colour is white!"

---

### Post by matt_symes on 2016-01-28
Hi

I have a new version of gcc.

```

matthew-xu-16-04:/home/matthew:0 % gcc --version
**gcc (Ubuntu 5.3.1-7ubuntu1) 5.3.1 20160121**
Copyright (C) 2015 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

matthew-xu-16-04:/home/matthew:0 %
```

This is the code you posted and compiled with no options.

```

matthew-xu-16-04:/home/matthew:0 % cat tmp.cc
#include <stdio.h>

void main()
{

        char me[20];

        printf("What is your name?");
        scanf("%s",&me);
        printf("Pleased to meet you,%s!\n",me);
}

matthew-xu-16-04:/home/matthew:0 % gcc tmp.cc
tmp.cc:3:11: error: ‘::main’ must return ‘int’
 void main()
           ^
tmp.cc: In function ‘int main()’:
tmp.cc:9:16: warning: format ‘%s’ expects argument of type ‘char*’, but argument 2 has type ‘char (*)[20]’ [-Wformat=]
  scanf("%s",&me);
                ^
matthew-xu-16-04:/home/matthew:0 % 
```

Th above has one error and one warning.

Modified below.

```

matthew-xu-16-04:/home/matthew:0 % cat tmp.cc 
#include <stdio.h>

**int **main()
{

        char me[20];

        printf("What is your name?");
        scanf("%s",** me);**
        printf("Pleased to meet you,%s!\n",me);
}

matthew-xu-16-04:/home/matthew:0 % gcc tmp.cc 
matthew-xu-16-04:/home/matthew:0 % 
```

Running the modified code.

```

matthew-xu-16-04:/home/matthew:0 % ./a.out 
What is your name?matthew
Pleased to meet you,matthew!
matthew-xu-16-04:/home/matthew:0 % 
```

Kind regards

---

### Post by itpro007ca on 2016-01-28
Thanks!

That works.

---

### Post by Odexios on 2016-01-29
If the line
```
	scanf("%s",&me);
```
is actually written like that in the book, and it's not a copy error, I'd heartily recommend you to look for another book to learn from. If you're learning C from scratch, you need a reliable resource, and that clearly isn't.

---


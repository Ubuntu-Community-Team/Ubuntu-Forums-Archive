---
title: "Beginning C question."
date: 2007-07-28
forum: Programming Talk
---

### Post by triele on 2007-07-28
first off heres the code:

```

int main( void )
{
	int i = 0;
	scanf( "%d", &i );
	
	printf( "%d%d\n", i++, i++ );
	
	return 0;
}

```

why does the it come out like this when i enter a number? (11 for example)
11
12     11

shouldn't it be :
11
12     13

Thanks.

---

### Post by Bluetech on 2007-07-28
C has two increment (and decrement) operators, specificly postfix (i++) and prefix (++i).
The difference between them isthe precedence. In postfix, the increment operator has very low precedence. For exemple,
int i = 0;
int a = i++;
Here, i ends up as 1, but a is 0, because the ++ happens after the assignment. In prefix:
int i = 0;
int a = ++i;
here, i = 1, a = 1
So, in order to make your program work like you expected, change the i++ to ++i.

---

### Post by triele on 2007-07-28
just changed it. now it comes out:

11
13  12

the part that gets me is why does it print out 13 before 12?

the code is: printf( "%d  %d", ++i, ++i );

shouldn't it be:

11
12  13

---

### Post by runningwithscissors on 2007-07-28
[Does this answer your question?](http://c-faq.com/expr/evalorder2.html)

---

### Post by GarlicFish on 2007-07-28
I think it is due to the way values go onto and off the stack.
Just because we read it from left to right doesn't mean the compiler does.
From what little I have learned, it seems best to keep it simple when it comes to ++i and --i

also did you compile with warnings enabled "gcc -Wall"  I tried your code and got the following.
increment.c: In function 'main':
increment.c:7: warning: operation on 'i' may be undefined

the following works as you want.

#include <stdio.h>
int main( void )
{
        int i = 0;
        scanf( "%d", &i );
        
        printf( "%d", ++i);
        printf( "%d\n", ++i);
        
        return 0;
}

---


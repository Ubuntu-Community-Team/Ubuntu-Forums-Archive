---
title: "Why is the output different?"
date: 2012-06-16
forum: Programming Talk
---

### Post by vanangamudi on 2012-06-16
Look at the follwing code  both are same(atleast to some extent) but the output seems to be different. Why???
```
#include<stdio.h>
//#include<iostream>
//#include<conio.h>

void main()
{
    //clrscr();

    int c, a = 7;
    int b = a++ + ++a + a++ + a++ - ++a;
    printf("\n%d",b);
    printf("\n%d",a);
    a = 7;
    c = a++ + ++a + a++ + a++ - ++a;
    a = 7;
    printf("\n%d",c);
    printf("\n%d",a);
    printf("\n%d %d %d %d %d", a++, ++a , a++ , a++ , ++a);

}


``````

23
12
23
7
11 12  9 8  12

```
```
#include<stdio.h>
//#include<iostream>
//#include<conio.h>

void main()
{
    //clrscr();

    int c, a = 7;
    int b = a++ + ++a + a++ + a++ - ++a;
    printf("\n%d",b);
    printf("\n%d",a);
    a = 7;
    c = a++ + ++a + a++ + a++ - ++a;
    a = 7;
    printf("\n%d",c);
    printf("\n%d",a);
    printf("\n%d", a++);
    printf(" %d", ++a);
    printf(" %d", a++);
    printf(" %d", a++);
    printf(" %d", ++a);

}


``````

23
12
23
7
7 9 9 10 12


```
can anyone explain why???

---

### Post by Simian Man on 2012-06-16
Welcome to the wonderful world of undefined behavior!  The compiler is allowed to evaluate arguments in any order it chooses.  So just don't write code that depends on the output of argument evaluation.

---

### Post by NovaAesa on 2012-06-16
Recompile your code with warnings turned on, and the compiler will give you some hints. As Simian Man said, there's lots of undefined behaviour in your code. For example, your first program:

```

ps@pris:~$ vim test.c
ps@pris:~$ gcc -Wall test.c 
test.c:5:6: warning: return type of &#8216;main&#8217; is not &#8216;int&#8217;
test.c: In function &#8216;main&#8217;:
test.c:10:37: warning: operation on &#8216;a&#8217; may be undefined
test.c:10:37: warning: operation on &#8216;a&#8217; may be undefined
test.c:10:37: warning: operation on &#8216;a&#8217; may be undefined
test.c:10:37: warning: operation on &#8216;a&#8217; may be undefined
test.c:14:28: warning: operation on &#8216;a&#8217; may be undefined
test.c:14:28: warning: operation on &#8216;a&#8217; may be undefined
test.c:14:28: warning: operation on &#8216;a&#8217; may be undefined
test.c:14:28: warning: operation on &#8216;a&#8217; may be undefined
test.c:18:55: warning: operation on &#8216;a&#8217; may be undefined
test.c:18:55: warning: operation on &#8216;a&#8217; may be undefined
test.c:18:55: warning: operation on &#8216;a&#8217; may be undefined
test.c:18:55: warning: operation on &#8216;a&#8217; may be undefined
ps@pris:~$ 

```

---

### Post by NovaAesa on 2012-06-16
> **NovaAesa said:**
> Recompile your code with warnings turned on, and the compiler will give you some hints. As Simian Man said, there's lots of undefined behaviour in your code. For example, your first program:

```

ps@pris:~$ vim test.c
ps@pris:~$ gcc -Wall test.c 
test.c:5:6: warning: return type of ‘main’ is not ‘int’
test.c: In function ‘main’:
test.c:10:37: warning: operation on ‘a’ may be undefined
test.c:10:37: warning: operation on ‘a’ may be undefined
test.c:10:37: warning: operation on ‘a’ may be undefined
test.c:10:37: warning: operation on ‘a’ may be undefined
test.c:14:28: warning: operation on ‘a’ may be undefined
test.c:14:28: warning: operation on ‘a’ may be undefined
test.c:14:28: warning: operation on ‘a’ may be undefined
test.c:14:28: warning: operation on ‘a’ may be undefined
test.c:18:55: warning: operation on ‘a’ may be undefined
test.c:18:55: warning: operation on ‘a’ may be undefined
test.c:18:55: warning: operation on ‘a’ may be undefined
test.c:18:55: warning: operation on ‘a’ may be undefined
ps@pris:~$ 

```


EDIT: I'll elaborate. When you do something such as:
```

foo++;

```
the value of the expression is simply "foo + 1", however foo then gets incremented. When does it get incremented though? It gets incremented *some* time before the next sequence point. Exactly when it gets incremented before the next sequence point is undefined. Have a read about it here [http://en.wikipedia.org/wiki/Sequence_point](http://en.wikipedia.org/wiki/Sequence_point)

---

### Post by hakermania on 2012-06-17
Normally, as I know it,
```

int a=0;
cout << a++ <<endl;

```
will show
```

0
```
but value of 'a' will be 1 after this.

Conversely, if you do
```

int a=0;
cout << ++a << endl;

```
then it will show 1 and the value of 'a' will be 1 afterwards...

Screenshot:
[IMG]http://i47.tinypic.com/2vmgind.jpg[/IMG]

---

### Post by trent.josephsen on 2012-06-17
> **NovaAesa said:**
> EDIT: I'll elaborate. When you do something such as:
```

foo++;

```
the value of the expression is simply "foo + 1", however foo then gets incremented. When does it get incremented though? It gets incremented *some* time before the next sequence point. Exactly when it gets incremented before the next sequence point is undefined. Have a read about it here [http://en.wikipedia.org/wiki/Sequence_point](http://en.wikipedia.org/wiki/Sequence_point)
I'm sure you mean that the value of the expression

```
++foo;
```

is (foo + 1). The value of foo++ is still just foo.

---

### Post by NovaAesa on 2012-06-17
> **trent.josephsen said:**
> I'm sure you mean that the value of the expression

```
++foo;
```

is (foo + 1). The value of foo++ is still just foo.

You're absolutely right, my mistake! I should really reread my posts more thoroughly before hitting submit.

---


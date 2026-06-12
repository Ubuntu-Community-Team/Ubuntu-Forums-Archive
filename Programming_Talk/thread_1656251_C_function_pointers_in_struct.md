---
title: "C function pointers in struct"
date: 2010-12-30
forum: Programming Talk
---

### Post by cyber2791 on 2010-12-30
Hi, i need some help with function pointers inside a struct in C. I really don't know why i get this errors with this code. 

```
#include <stdio.h>
#include <stdlib.h>

typedef struct
{
    int a,b,s;
    void  (*sum) (func*);
    void (*af) (func);
}func;

void function(func*);
void afi(func);

int main()
{
func ne;
ne.a=1;
ne.b=2;
ne.sum = function;
ne.af = afi;
ne.sum(ne);
ne.af(ne);
return 0;
}

void function(func* this)
{
    this->s = this->a+this->b;
}
void afi(func this)
{
    printf("%d",this.s);
}

```This is what i get : 
/ftest/main.c:7: error: expected ‘)’ before ‘*’ token
/ftest/main.c:8: error: expected ‘;’ before ‘void’
/ftest/main.c: In function ‘main’:
/ftest/main.c:19: error: ‘func’ has no member named ‘sum’
/ftest/main.c:20: error: ‘func’ has no member named ‘af’
/ftest/main.c:21: error: ‘func’ has no member named ‘sum’
/ftest/main.c:22: error: ‘func’ has no member named ‘af'

Please help me if you know what's wrong here.

---

### Post by Arndt on 2010-12-30
> **cyber2791 said:**
> Hi, i need some help with function pointers inside a struct in C. I really don't know why i get this errors with this code. 

```
#include <stdio.h>
#include <stdlib.h>

typedef struct
{
    int a,b,s;
    void  (*sum) (func*);
    void (*af) (func);
}func;

void function(func*);
void afi(func);

int main()
{
func ne;
ne.a=1;
ne.b=2;
ne.sum = function;
ne.af = afi;
ne.sum(ne);
ne.af(ne);
return 0;
}

void function(func* this)
{
    this->s = this->a+this->b;
}
void afi(func this)
{
    printf("%d",this.s);
}

```This is what i get : 
/ftest/main.c:7: error: expected ‘)’ before ‘*’ token
/ftest/main.c:8: error: expected ‘;’ before ‘void’
/ftest/main.c: In function ‘main’:
/ftest/main.c:19: error: ‘func’ has no member named ‘sum’
/ftest/main.c:20: error: ‘func’ has no member named ‘af’
/ftest/main.c:21: error: ‘func’ has no member named ‘sum’
/ftest/main.c:22: error: ‘func’ has no member named ‘af'

Please help me if you know what's wrong here.

At the point where you use 'func' first, it is still being defined. You need to forward declare it, this way:

```
struct func;

typedef struct
{
    int a,b,s;
    void  (*sum) (struct func*);
    void (*af) (struct func);
}func;
```

---

### Post by cyber2791 on 2010-12-30
I get the same error if i do that :confused:. I really don't understand what happens.

---

### Post by handheld-penguin on 2010-12-30
What happens if you put these two:
```
void function(func*);
void afi(func);
``` above the struct declaration?

---

### Post by Arndt on 2010-12-30
> **cyber2791 said:**
> I get the same error if i do that :confused:. I really don't understand what happens.

I get quite different errors, since the rest of the code doesn't hang together:

```
forw.c: In function ‘main’:
forw.c:21: warning: assignment from incompatible pointer type
forw.c:22: warning: assignment from incompatible pointer type
forw.c:23: error: incompatible type for argument 1 of ‘ne.sum’
forw.c:23: note: expected ‘struct func *’ but argument is of type ‘func’
forw.c:24: error: type of formal parameter 1 is incomplete

```

---

### Post by cyber2791 on 2010-12-30
Unfortunately i get more errors:


ftest/main.c:4: error: expected ‘)’ before ‘*’ token
ftest/main.c:5: warning: parameter names (without types) in function declaration
ftest/main.c:10: error: expected ‘)’ before ‘*’ token
ftest/main.c:11: error: expected ‘;’ before ‘void’
ftest/main.c: In function ‘main’:
ftest/main.c:20: error: ‘func’ has no member named ‘sum’
ftest/main.c:20: error: ‘function’ undeclared (first use in this function)
ftest/main.c:20: error: (Each undeclared identifier is reported only once
ftest/main.c:20: error: for each function it appears in.)
ftest/main.c:21: error: ‘func’ has no member named ‘af’
ftest/main.c:22: error: ‘func’ has no member named ‘sum’
ftest/main.c:23: error: ‘func’ has no member named ‘af’

---

### Post by cyber2791 on 2010-12-30
> **Arndt said:**
> I get quite different errors, since the rest of the code doesn't hang together:

```
forw.c: In function ‘main’:
forw.c:21: warning: assignment from incompatible pointer type
forw.c:22: warning: assignment from incompatible pointer type
forw.c:23: error: incompatible type for argument 1 of ‘ne.sum’
forw.c:23: note: expected ‘struct func *’ but argument is of type ‘func’
forw.c:24: error: type of formal parameter 1 is incomplete

```

It would have something to do with the compiler? I have gcc 4:4.4.4

---

### Post by Arndt on 2010-12-30
> **cyber2791 said:**
> It would have something to do with the compiler? I have gcc 4:4.4.4

It shouldn't; this is classical C stuff. What does your code look like now, exactly?

---

### Post by Milliways on 2010-12-30
> **cyber2791 said:**
> Hi, i need some help with function pointers inside a struct in C. I really don't know why i get this errors with this code. 

```
#include <stdio.h>
#include <stdlib.h>

typedef struct
{
    int a,b,s;
    void  (*sum) (func*);
    void (*af) (func);
}func;


```This is what i get : 
/ftest/main.c:7: error: expected ‘)’ before ‘*’ token
/ftest/main.c:8: error: expected ‘;’ before ‘void’

Please help me if you know what's wrong here.

The problem is that you are trying to use a typdef (in the function arg list) before it has been defined.

This can be avoided by using a named structure e.g.:-

```
typedef struct xxxx
{
    int a,b,s;
    void  (*sum) (struct xxxx*);
    void (*af) (struct xxxx);
} FUNC;

```

I won't comment on the rest of your code, but why do you make it so difficult for yourself and other by poor choice of names.

If function() adds 2 things give it a name like add2.

It is common practice to use CAPITALS in typedef so they are not confused with variables or functions, and func is also a poor choice - give it a meaningful name.

---

### Post by nvteighen on 2010-12-31
I'd personally go for this:
```

typedef struct FUNC func;

struct FUNC
{
    int a, b, s;
    void  (*sum)(func *);
    void (*af)(func);
};

```

The reason is that it splits the declaration of the type **func** (which is the type you want to be visible) and the implementation of that type as **struct FUNC**. The benefit is mainly that it makes it possible to refer only to **func**, therefore hiding **struct FUNC**. This also affects compiler error messages, for example... The thing is that if you were writing a library and you're using a typedef'ed type, only that typedef'ed type should be known by the user.

Now, as soon as you solve that, you'll face a compiler warning. If you don't solve it, your program segfaults.

---

### Post by cyber2791 on 2010-12-31
> **nvteighen said:**
> I'd personally go for this:
```

typedef struct FUNC func;

struct FUNC
{
    int a, b, s;
    void  (*sum)(func *);
    void (*af)(func);
};

```The reason is that it splits the declaration of the type **func** (which is the type you want to be visible) and the implementation of that type as **struct FUNC**. The benefit is mainly that it makes it possible to refer only to **func**, therefore hiding **struct FUNC**. This also affects compiler error messages, for example... The thing is that if you were writing a library and you're using a typedef'ed type, only that typedef'ed type should be known by the user.

Now, as soon as you solve that, you'll face a compiler warning. If you don't solve it, your program segfaults.

Thank you ! This solved my problem and helped me understand the errors.

---


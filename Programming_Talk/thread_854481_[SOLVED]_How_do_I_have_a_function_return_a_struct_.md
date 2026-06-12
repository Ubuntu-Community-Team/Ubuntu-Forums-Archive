---
title: "[SOLVED] How do I have a function return a struct in C?"
date: 2008-07-09
forum: Programming Talk
---

### Post by Yes on 2008-07-09
I have this in a header file:

```
struct enemy { 
	int health, bulletRate, y, x, cols, rows;
	bool movingLeft, alive;
};

enemy initEnemy (int health, int bulletRate);
```

but when I compile I get the error 'expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initEnemy’'.  Is that not how you declare a function that returns a struct?

Thanks.

---

### Post by tornado89 on 2008-07-09
You're Using The Right Way..
The Issue Is That In C.. You Have To Use The Keyword 'struct'
before Every Definition...


Your Code :
[PHP]
enemy initEnemy (int health, int bulletRate);
[/PHP]

Correct 'C' Code : 
[PHP]
struct enemy initEnemy (int health, int bulletRate);
[/PHP]

As For "bool" .. The 'C' Doesn't Natively Support Booleans
So You Need To Declare It Like This : 
[PHP]
typdef int bool
#define true 1
#define false 0
[/PHP]

Or You Can ByPass All These Problems By Using 'C++'
Where You Can Use Any Structure without the Keyword 'struct' before it... and native support for boolean 

cheers....

---

### Post by WW on 2008-07-09
To use the struct that you have defined, you must refer to it as **struct enemy**, e.g.
```

struct enemy initEnemy (int health, int bulletRate);

```
You might find it nicer to use a **typedef**, which allows you to use the name enemy in the way you originally wrote it:
```

typedef struct enemy_struct { 
	int health, bulletRate, y, x, cols, rows;
	int movingLeft, alive;
} enemy;

enemy initEnemy (int health, int bulletRate);

```

By the way, there is no **bool** data type in C.

You might be happier with C++ :) .


EDIT: Heh, looks like tornado89 had the same thought:
> **tornado89 said:**
> 
Or You Can ByPass All These Problems By Using 'C++'
Where You Can Use Any Structure without the Keyword 'struct' before it... and native support for boolean 


---

### Post by Yes on 2008-07-09
Alright, thanks.  Are you sure gcc doesn't support bool?  I read on Wikipedia that the C99 standard of C does have the bool data type, and gcc supports a lot of the stuff in C99.

Or is that the reason I get the error 'expected specifier-qualifier-list before &#8216;bool&#8217;' in my struct, because gcc doesn't support bool?

---

### Post by Can+~ on 2008-07-09
> **Yes said:**
> Alright, thanks.  Are you sure gcc doesn't support bool?  I read on Wikipedia that the C99 standard of C does have the bool data type, and gcc supports a lot of the stuff in C99.

Or is that the reason I get the error 'expected specifier-qualifier-list before ‘bool’' in my struct, because gcc doesn't support bool?

[FONT="Courier New"]#include <stdbool.h>[/FONT]

---

### Post by Yes on 2008-07-09
Great, thanks!

---

### Post by bruce89 on 2008-07-09
> **WW said:**
> 
```

struct enemy initEnemy (int health, int bulletRate);

```
You might find it nicer to use a **typedef**, which allows you to use the name enemy in the way you originally wrote it:
```

typedef struct enemy_struct { 
	int health, bulletRate, y, x, cols, rows;
	int movingLeft, alive;
} enemy;

enemy initEnemy (int health, int bulletRate);

```


I'm a pedant, but usually structures have capitalised names. For instance, here it would be *Enemy*.

---


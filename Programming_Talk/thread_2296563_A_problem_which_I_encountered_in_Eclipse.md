---
title: "A problem which I encountered in Eclipse"
date: 2015-09-26
forum: Programming Talk
---

### Post by NoWeDoR on 2015-09-26
[TABLE]
[TR]
[TD="class: votecell"]I have written a simple code in Eclipse/C Project as below:

[/TD]
[/TR]
[/TABLE]

```
#include <stdio.h>

typedef struct list
{
    int data;
    struct list *next;
};

 list Listptr;

int findTheSmallest()
{

}

int main()
{
    printf("Trying");
}
```

However, ```
list Listptr;
``` line cannot be read by the Eclipse/C compiler.  I am using Eclipse Mars and CDT 8.7.0 

  Eclipse wants me to add struct definition in front of the ```
list Listptr;
``` but when I try the program in Visual Studio it works without any problem. What can I do for Eclipse? I want to use how I wrote.

---

### Post by spjackson on 2015-09-27
What you have written is not valid C, although it is valid C++. Perhaps Visual Studio is treating it as C++, or perhaps it has an extension to C that permits this form. Two ways to make it valid C are as follows.
```

typedef struct list
{
    int data;
    struct list *next;
};

struct list Listptr;

```
The typedef above is pointless and could be removed.
```

typedef struct list
{
    int data;
    struct list *next;
} list;

 list Listptr;

```

---


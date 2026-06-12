---
title: "[SOLVED] C - Call function when name in variable"
date: 2008-09-12
forum: Programming Talk
---

### Post by bobbocanfly on 2008-09-12
I have this code, which I am trying to use to generate truth tables for boolean functions (I have written the code for these, boolean.h).

I need to be able to "dynamically" call a function, when the function name is in a variable (the argument to generate_table(), char** function). In python I could do it like:

```
exec "%s(1, 0)" % function
```

But I cant find out how to do it in C.
```

#include <stdio.h>
#include "boolean.h"

struct table 
{
    char** title;
    int xy;
    int xo;
    int oy;
    int oo;
};

int
print_table (struct table t)
{
    printf("%s\n", t.title);
    printf("X Y - Out\n");
    printf("0 0 -  %i\n", t.oo);
    printf("0 1 -  %i\n", t.oy);
    printf("1 0 -  %i\n", t.xo);
    printf("1 1 -  %i\n", t.xy);
    return 0;
}

void
generate_table (char** function)
{
    struct table t;
    t.title = function;
    t.xy = 1;
    t.xo = 0;
    t.oy = 0;
    t.oo = 0;
    print_table(t);
}

int
main ()
{
    generate_table("NOT");
}
```

---

### Post by slavik on 2008-09-12
> **bobbocanfly said:**
> I have this code, which I am trying to use to generate truth tables for boolean functions (I have written the code for these, boolean.h).

I need to be able to "dynamically" call a function, when the function name is in a variable (the argument to generate_table(), char** function). In python I could do it like:

```
exec "%s(1, 0)" % function
```

But I cant find out how to do it in C.
```

#include <stdio.h>
#include "boolean.h"

struct table 
{
    char** title;
    int xy;
    int xo;
    int oy;
    int oo;
};

int
print_table (struct table t)
{
    printf("%s\n", t.title);
    printf("X Y - Out\n");
    printf("0 0 -  %i\n", t.oo);
    printf("0 1 -  %i\n", t.oy);
    printf("1 0 -  %i\n", t.xo);
    printf("1 1 -  %i\n", t.xy);
    return 0;
}

void
generate_table (char** function)
{
    struct table t;
    t.title = function;
    t.xy = 1;
    t.xo = 0;
    t.oy = 0;
    t.oo = 0;
    print_table(t);
}

int
main ()
{
    generate_table("NOT");
}
```
I have never seen this done ... in C

---

### Post by rnodal on 2008-09-12
Have you considered using function pointers and naming the pointers NOT, OR etc?

-r

---

### Post by bobbocanfly on 2008-09-12
> **rnodal said:**
> Have you considered using function pointers and naming the pointers NOT, OR etc?

-r

I have had that suggested, but I am just new to C, so not sure where to start with that. DO you know where I could find examples? (My google-fu sucks :()

---

### Post by issih on 2008-09-12
Not quite what you need, but it might be feasible with function pointers and a call table:

[http://www.newty.de/fpt/intro.html#what](http://www.newty.de/fpt/intro.html#what)

Hope that helps

---

### Post by rnodal on 2008-09-12
If you want sample tutorials on function pointers then a Google search on "C Function Pointers" would give you a lot. If you don't want to deal with function pointers then have you considered going a different way? For example if the user call your function like this:
yourFunction("NOT"); 

Store the NOT string in your struct then in the function that takes the struct as a parameter call the appropriate function based on what the string is equal to.

-r

---

### Post by mike_g on 2008-09-12
Funnily enough I was working on something similare yesterday, although I dident need to call the functions by string names. This makes things a little more complex, but I came up with an example.

I basically did it by creating a stuct that maps a string to a function pointer. For your prog you would need to make an extra function that accepts a string then calls the mapped function. 

heres an example:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int and_gate(int a, int b) { return a&b; }
int or_gate(int a, int b)  { return a|b; }
int not_gate(int a, int b) { return (a)?0:1; }
int xor_gate(int a, int b) { return a^b; }
int nor_gate(int a, int b) { return !(a|b); }
int nand_gate(int a, int b){ return !(a&b); } 

typedef struct
{
    int (*func)(int, int);
    char name[6];
}Map;

Map* map_function(char* name, int(*func)(int, int) )
{
    if(strlen(name) > 5) return NULL;
    Map* new_map = (Map*)malloc(sizeof(Map));
    strcpy(new_map->name, name);
    new_map->func = func;
    return new_map; 
}

int main()
{
    Map* map[6];
    map[0] = map_function("And", and_gate);
    map[1] = map_function("Or",  or_gate);
    map[2] = map_function("Not", not_gate);
    map[3] = map_function("Xor", xor_gate);
    map[4] = map_function("Nor", nor_gate);
    map[5] = map_function("Nand",nand_gate);        

    int i;
    for(i=0; i<6; i++)
        printf("Function name %s mapped to address %p result of function(1, 0) is: %d\n",
            map[i]->name, map[i]->func, map[i]->func(1, 0));

    for(i=0; i<6; i++)
        free(map[i]);

    getchar(); getchar();
    return 0;
}
```
If theres anything you find unclear about the code i'll try and explain it for you.

---

### Post by rnodal on 2008-09-12
Are you sure it needs to be that complicated? Couldn't you just say:
pointer = &functionName;

-r

---

### Post by mike_g on 2008-09-12
Yes, you could. And thats what I was doing, but from what I could tell of the original post the op wanted to use a string generated at runtime to identify the function name.

---

### Post by rnodal on 2008-09-12
> **mike_g said:**
> Yes, you could. And thats what I was doing, but from what I could tell of the original post the op wanted to use a string generated at runtime to identify the function name.

I see. I got you know. Thanks for taking the time to clarify.

-r

---

### Post by Yannick Le Saint kyncani on 2008-09-12
Hi all, AFAIK, the only practical way to use a function by name in C is to use the dlopen()/dlsym() mechanism.

But in this case, it's like using an atomic bomb to kill a kitty (not that I kill kitties).

---

### Post by bobbocanfly on 2008-09-12
Thanks for your help everyone! I used mike_g's idea and setup an array of structs with function pointers. I cycle through the array and strcmp the argument name and the name in the struct. Certainly much better than a huge if .. else if .. else mess.

Here is the code I have ended up with:

```
#include <stdio.h>
#include <string.h>
#include "boolean.h"

typedef struct
{
    int (*func)(int, int);
    char name[6];
} map;

struct table
{
    char** title;
    int xy;
    int xo;
    int oy;
    int oo;
};

map* map_function(char* name, int(*func)(int, int) )
{
    if(strlen(name) > 5) return NULL;
    map* new_map = (map*)malloc(sizeof(map));
    strcpy(new_map->name, name);
    new_map->func = func;
    return new_map; 
}

int
print_table (struct table t)
{
    printf("%s\n", t.title);
    printf("X Y - Out\n");
    printf("0 0 -  %i\n", t.oo);
    printf("0 1 -  %i\n", t.oy);
    printf("1 0 -  %i\n", t.xo);
    printf("1 1 -  %i\n", t.xy);
    return 0;
}

void
generate_table (char** function)
{
    map* map[7];
    map[0] = map_function("and", and);
    map[1] = map_function("or",  or);
    map[2] = map_function("not", not);
    map[3] = map_function("xor", xor);
    map[4] = map_function("nor", nor);
    map[5] = map_function("nand", nand);   
    map[6] = map_function("xnor", xnor);

    struct table t;
    t.title = function;
    
    int i;
    
    for (i = 0; i < 8; i++)
    {
        if (!strcmp(map[i]->name, t.title))
        {
            t.xy = map[i]->func(1, 1);
            t.oo = map[i]->func(0, 0);
            t.oy = map[i]->func(0, 1);
            t.xo = map[i]->func(1, 0);
        }
    }


    print_table(t);
}
```

---

### Post by mike_g on 2008-09-12
> Thanks for your help everyone! I used mike_g's idea and setup an array of structs with function pointers. I cycle through the array and strcmp the argument name and the name in the struct. Certainly much better than a huge if .. else if .. else mess.
While it is a novelty, for what you are using it for in your example I'd say you would be much better with a plain old if statement. For three reasons: less overhead, the code would be easier to read, and less lines of code; 71 compared to 48:
```
#include <stdio.h>
#include <string.h>
#include "boolean.h"

struct table
{
    char** title;
    int xy;
    int xo;
    int oy;
    int oo;
};

int
print_table (struct table t)
{
    printf("%s\n", t.title);
    printf("X Y - Out\n");
    printf("0 0 -  %i\n", t.oo);
    printf("0 1 -  %i\n", t.oy);
    printf("1 0 -  %i\n", t.xo);
    printf("1 1 -  %i\n", t.xy);
    return 0;
}

void
generate_table (char** function)
{
    struct table t;
    t.title = function;

    if(!strcmp("and", t.title))
        and(t);
    else if (!strcmp("or", t.title))
        or(t);
    else if (!strcmp("not", t.title))
        not(t);
    else if (!strcmp("xor", t.title))
        xor(t);
    else if (!strcmp("nor", t.title))
        nor(t);
    else if (!strcmp("nand", t.title))
        nand(t);
    else if (!strcmp("xnor", t.title))
        xnor(t);

    print_table(t);
}
```

---

### Post by bobbocanfly on 2008-09-12
> **mike_g said:**
> While it is a novelty, for what you are using it for in your example I'd say you would be much better with a plain old if statement. For three reasons: less overhead, the code would be easier to read, and less lines of code; 71 compared to 48:


But where would the fun be in that?! :P

If I was writing this for a project, I probably would just go with the If statement, but I am trying to learn as much of C as I can and this way is a lot more fun.

---

### Post by redicon on 2009-04-07
I've got the same problem but using variables.
Something like:
int var = 4;

And i want to print on screen 4 using a string with "var" inside.
My idea is to declare extern int var and use dlopen and dlsym to load it in runtime.

Can anyone help me to find a better solution?

---

### Post by CptPicard on 2009-04-07
You can't resolve things dynamically by name in C. What you are trying to do seems to essentially call for the use of a hashtable...

---


---
title: "Problem with structs in C"
date: 2008-10-31
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-31
I am trying to make a simple game, while learning C and OpenGL.
That's why I use struct instead of an array. I got this:
```

/* player */
typedef struct
{
    /* position */
    int x;
    int y;
    /* hitpoints */
    int hp;
} player;

player p1;

p1.x = 320;
p1.y = 380;
p1.hp = 100;

```
And now it says:
> 
gltest.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘.’ token
gltest.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘.’ token
gltest.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘.’ token

I did it exactly as this tutorial says [http://crasseux.com/books/ctutorial/Using-structures.html#Using%20structures](http://crasseux.com/books/ctutorial/Using-structures.html#Using%20structures)

---

### Post by rnodal on 2008-10-31
Could you please post the whole source code? It seem that the problem is somewhere else.

-r

---

### Post by Bichromat on 2008-10-31
You can't put such instructions as p1.x = 320 outside of a function.

Either initialize p1 when declaring it:
```

player p1={320, 380, 100};

```

Or initialize it inside your main().

---

### Post by crazyfuturamanoob on 2008-10-31
> **Bichromat said:**
> You can't put such instructions as p1.x = 320 outside of a function.

Either initialize p1 when declaring it:
```

player p1={320, 380, 100};

```

Or initialize it inside your main().

Thanks, that works. :)

If I can't do p1.x = 320 then that tutorial is WRONG. :mad:

---

### Post by Delever on 2008-10-31
> **crazyfuturamanoob said:**
> Thanks, that works. :)

If I can't do p1.x = 320 then that tutorial is WRONG. :mad:

Or maybe tutorial assumed that you would know where to write it :).

---

### Post by nvteighen on 2008-10-31
Please, that tutorial is the best one... it may have errors, but if there are, they won't be that grotesque.

---

### Post by Tony Flury on 2008-10-31
In defence of the OP, the tutorial does not explicitly say that the initialisation has to be in a function.

Quoted verbatim from the page : 

> 
In the following example, the year 1852 is assigned to the year_of_birth member of the structure variable person1, of type struct personal_data. Similarly, month 5 is assigned to the month_of_birth member, and day 4 is assigned to the day_of_birth member.
```

struct personal_data person1;

person1.year_of_birth = 1852;
person1.month_of_birth = 5;
person1.day_of_birth = 4;

```

Tags added to aid readership.

as you can see - for a complete beginner it could be misleading.

---

### Post by crazyfuturamanoob on 2008-11-01
Like this?
```

typedef struct
{
int x = 320;
int y = 380;
int hp = 100;
} player;

player p1;

```
Is there any way to do **p1.hp -= 5** without having to re-assing all variables in that struct?

---

### Post by lisati on 2008-11-01
Flash of inspiration: is the "typedef" necessary in the declaration?

---

### Post by Bichromat on 2008-11-01
crazyfuturamanoob: Yes you can. But, as I said, you must put that instruction inside a function.
lisati: typedefs are not necessary, but they help make your code more readable.
```

struct player{
   int x,y;
   int hp;
};

typedef struct player Player;

int main(){

   struct player p1;
   #vs.
   Player p2;
}

```

---

### Post by crazyfuturamanoob on 2008-11-01
But if I make a function inside a structure to change it's variables, how would I do that?

As I know, there are no "self" or "this" in C.

---

### Post by Bichromat on 2008-11-01
C structures don't have methods (you can however emulate a method with a pointer to a function). You need to pass your struct to the function that changes it.

---

### Post by crazyfuturamanoob on 2008-11-01
> **Bichromat said:**
> C structures don't have methods (you can however emulate a method with a pointer to a function). You need to pass your struct to the function that changes it.

I can't define methods/functions inside structures? But they are actually variables too. :confused:

---

### Post by scourge on 2008-11-01
> **crazyfuturamanoob said:**
> I can't define methods/functions inside structures? But they are actually variables too. :confused:

You can have function pointers in structs, and they can be used as a poor man's methods. But you probably don't want to do that.

---

### Post by nvteighen on 2008-11-01
> **crazyfuturamanoob said:**
> I can't define methods/functions inside structures? But they are actually variables too. :confused:
Ok, let's see. You want Object-Orientated Programming: to have some sort of "place" (usually called a "class") where some variables and functions interact within eachother and also with the outside.

Well, C doesn't have an **explicit** OOP model as C++ does. But we can easily emulate one with structures. Even with public/private member access restriction (encapsulation)!

Let me introduce you to the Opaque Pointer technique:

0. Separate the code for your new data type into a new source file. We'll take advantage from the compiler's behaivor to get an illusion of private members during compilation (there's no run-time encapsulation... using a debugger will show it to you).

1. After defining your struct, write the functions you want to be part of the "class". You need a constructor (like __init__ in Python) that allocates the new struct variable into memory (usually you'll need malloc, as you don't want the object to be lost after the call stack is popped), sets the attributes and returns a pointer to that new variable. If you use malloc() for allocation, also write a destructor function that cleans up memory.

2. Because usually malloc() is needed, you'll always use pointers. Write the "methods" always accepting a pointer to the struct data type and the rest of arguments. To access stuff inside the struct, use a->b, which is shorthand for (*a).b

3. For those attributes you want to be public, write functions that take a pointer to a struct data type variable of yours and return the desired values ("getters"). Also if you want to give write-access to some attribute ("setters").

Any attribute without any selector (getter and/or setter) will be private and only accessable from the module where the struct definition sits.

4. On the contrary, to make a "method" private, you have to declare it explicitly as such, by declaring it as a static function ("static int blahblah(...)").

5. Now, we need a header file that will allow the other modules be aware of the new API you created. In the header file, just include a "forward" declaration of your struct: **struct mystruct;** (or **typedef struct my_struct player;**). Don't include the definition! And then, just include the declarations (aka "signatures") of your **public** functions (i.e. don't include those you declared as static... otherwise, it will render a compile error... also, why would you want to show private stuff? :p). Example: **int abc(player *, int, int, char *);** (just include the arguments' data types, not their names...).

So, to use this module into another one, #include the header file and use your own defined API; compile all modules together. And if you're kind enough and your API is great, share it by making a library with it so everybody can use it! (but that's another story).

---

### Post by jimi_hendrix on 2008-11-01
@nvteig...

couldnt you then...in theory...make objects in any language that supports importing functions and such from a library

---

### Post by nvteighen on 2008-11-01
> **jimi_hendrix said:**
> @nvteig...

couldnt you then...in theory...make objects in any language that supports importing functions and such from a library
Of course :)

Do you now understand why that much people, like me, aren't impressed with OOP languages? What that languages (C++, Java, Python, etc.) offer are features that make your life easier, they don't give you a "new concept".

---


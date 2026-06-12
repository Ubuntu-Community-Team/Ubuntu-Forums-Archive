---
title: "pointer to function in C/C++"
date: 2006-03-08
forum: Programming Talk
---

### Post by krypto_wizard on 2006-03-08
I am little confused as to how to use the "pointer to function" concept. I looked at couple of books but couldn't get completely out of it.

Could you please throw some light.

thanks

---

### Post by thumper on 2006-03-08
Well, a pointer to a function can be passed as an argument to another function.

Let's say we had something like this:
```

void some_func(int param);
void another_func(int param);

void do_a_func(int (*func)(int), int param)
{
   func(param);
}
```
Then you could pass a function to another function like:
```

do_a_func(some_func, 42);
do_a_func(another_func, 23);

```
Hopefully I haven't fubared the syntax.

More interesting are the pointers to member functions or pointers to member variables.  That way you can pass around the pointer without having it bound to an actual object, and only bind it to the object when you want to use it.

Not something that you use frequently, but handy to know about for when it becomes useful.

---

### Post by Lux Perpetua on 2006-03-08
You didn't fubar it, but the compiler would complain that some_func and another_func return void, but are being passed as int (*)(int).  ;)

You can think of it this way: when you write a function, its code gets compiled into machine code and resides somewhere in processor memory while your program executes. The pointer to the function can be thought of as a pointer to the beginning of the code for the function (although it isn't guaranteed to be exactly this). That information, along with the number and type of its arguments and return type, is all the information you need to be able to use the function. So C lets you specify the arguments/type information at compile time and gives you the freedom to change the actual function being called (the memory address of the beginning of the code) at runtime via these "pointers to functions."

Make any more sense?

---

### Post by thumper on 2006-03-08
Bugger!

I'll leave that obvious error so your post doesn't refer to changed code ;)

---

### Post by rplantz on 2006-03-08
I've found that typedef comes in handy here. The declaration ```

int (*func_t)(int);

```
creates a variable named func_t that can hold an address of a function that takes one int as an argument and returns an int.

Place typedef in front
```

typedef int (*func_t)(int);

```
and func_t becomes a type name. So now you can do things like
```

func_t your_function;   /* a variable for pointers to these function */
int my_function(func_t a_func); /* pass one of these functions to my_function */

```

I once used this technique when programming the DUART on a single-board computer. I needed to install an interrupt handler. Note that an interrupt handler takes no arguments and returns void. In this example, the name of the handler function is "duart_handler". Here are the relevant statements:
```

typedef void (*handler)(void);
 ----
/* location in vector table */
#define DUART_INT_NUM 64
#define DUART_INT_ADDR (4 * DUART_INT_NUM)
#define DUART_INT *(handler*)DUART_INT_ADDR
 ----
DUART_INT = duart_handler;      /* install handler */

```

It took me a little while to figure out how to type cast the absolute address, DUART_INT_ADDR, so that I could treat DUART_INT like a variable name.

---

### Post by pharcyde on 2006-03-09
The other thing that's nice about function pointers/callbacks is putting them into more advanced data structures.  For example you could put function pointers in a hash table or array.

For example:
in C you could use an array or some hash function
```

typedef void (*myFunct)(void);

myFunct arrayFunct[3] =
{
 &funct1,
 &funct2,
 &funct3,
};

arrayFunct[0](); /* calls funct1 */
arrayFunct[1](); /* calls funct2 */
arrayFunct[2](); /* calls funct3 */

```

in C++ you could use std Maps or some other structure
```

typedef void (*myFunct)(void);

std::map<string, myFunct> myMap;

myMap["abc"] = &funct1;
myMap["asdf"] = &funct2;
myMap["foo"] = &funct3;

myMap["abc"](); /* runs funct1 */
myMap["asdf"](); /* runs funct2 */
myMap["foo"](); /* runs funct3 */

```

---

### Post by rplantz on 2006-03-09
> **pharcyde]The other thing that's nice about function pointers/callbacks is putting them into more advanced data structures.  For example you could put function pointers in a hash table or array.

For example:
in C you could use an array or some hash function
```

typedef void (*myFunct)(void) said:**
>  =
{
 &funct1,
 &funct2,
 &funct3,
};

arrayFunct[0](); /* calls funct1 */
arrayFunct[1](); /* calls funct2 */
arrayFunct[2](); /* calls funct3 */

```


Neat. You can build a vector table this way.

Notice that the '&' is optional. C treats function names a little like array names. That is, they are seen as addresses. Notice that I did not use the & operator in my code. Another place where this comes up is when working with signal handlers.

---


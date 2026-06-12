---
title: "Store operators in variables?"
date: 2011-08-22
forum: Programming Talk
---

### Post by shashanksingh on 2011-08-22
Can we store an operator in a variable?

I was thinking if we could do something like this...

if user says ascending
   operater=> "greater than"
else
   operator=< "less than"


...code where i could directly choose statements like

if x "a" y... implying if x > y or x <y depending on the condition?
This could skip quite a few repetitive if conditions.
Its just a vague idea, if at all anyone has seen any implementation of it??

---

### Post by Bachstelze on 2011-08-22
Which language?

---

### Post by cgroza on 2011-08-22
In interpreted languages such as Python or Ruby were functions are objects it should be very easy.

---

### Post by schauerlich on 2011-08-22
This is possible in many languages, although not always convenient. It's fairly simple in lisp, python, ruby, etc (any language with first-class functions), and more of a pain (but entirely possible) in languages like C.

---

### Post by shashanksingh on 2011-08-22
C/C++?
Even Java.

---

### Post by Bachstelze on 2011-08-22
In C you can store a pointer to a function in a variable. Since all operators can be implemented as functions, you can use that to achieve the same purpose:

```
firas@applejack ~ % cat test.c 
#include <ctype.h>
#include <stdio.h>
#include <string.h>

int add(int a, int b)
{
        return a+b;
}

int multiply(int a, int b)
{
        return a*b;
}

int main(void)
{
        int a = 2,
            b = -3;
        int ch; /* To flush input if needed */
        char input[2];
        /* 
         * operation is a pointer to a function taking two int arguments
         * and returning an int.
         */
        int (*operation) (int, int); 

        for (;;) {
                printf("The numbers are %d and %d. What do you want to do with them?\n"
                        "(a)dd or (m)ultiply? ", a, b);
                fgets(input, 2, stdin);
                while ((ch = getchar()) != EOF && ch != '\n')
                        ;
                input[0] = tolower(input[0]); /* Handle uppercase */
                if (strcmp(input, "a") == 0) {
                        operation = add;
                } else if (strcmp(input, "m") == 0) {
                        operation = multiply;
                } else { /* Invalid */
                        printf("Invalid input!\n");
                        continue;
                }
                printf("The result is %d.\n", operation(a, b));
        }
}
firas@applejack ~ % cc -std=c99 -pedantic -Wall -Werror -o test test.c     
firas@applejack ~ % ./test
The numbers are 2 and -3. What do you want to do with them?
(a)dd or (m)ultiply? a
The result is -1.
The numbers are 2 and -3. What do you want to do with them?
(a)dd or (m)ultiply? m
The result is -6.
The numbers are 2 and -3. What do you want to do with them?
(a)dd or (m)ultiply? ^C
firas@applejack ~ % 

```

I don't know enough abut C++ or Java to answer.

---

### Post by r.darwish on 2011-08-22
This functionality can be easily achieved using dynamic languages like Python:

```

#!/usr/bin/env python

OPERATORS = {
    "add" : lambda x, y : x + y,
    "greater-than" : lambda x, y : x > y
    }
    
def parse(s):
    args = s.split(' ')
    return OPERATORS[args[1]](int(args[0]), int(args[2]))
    
print parse("1 add 2")
print parse("2 greater-than 1")

```

---

### Post by dazman19 on 2011-08-25
I have never done this,  but my understanding is that an operator is essentially a function. 
And a function is pointed to by a piece of memory.

So if you knew the start/end of that piece of memory, then yeh you probably could do it.

---

### Post by nvteighen on 2011-08-25
> **dazman19 said:**
> I have never done this,  but my understanding is that an operator is essentially a function. 
And a function is pointed to by a piece of memory.


That's exactly the problem why you can't do it in C: in that languages, operators aren't functions.

But you can do this in C++, which surprised me a lot. Ok, the syntax is horrible, but this works:
```

#include <iostream>

class MyClass
{
public:
    int z, y;

    MyClass(int data1, int data2) : z(data1), y(data2) {}
    
    MyClass operator+(MyClass& myobj)
    {
        return MyClass(z + myobj.z, y + myobj.y);
    }

    void print()
    {
        std::cout << z << " " << y << std::endl;
    }
};

int main()
{
    MyClass something(7, 9);
    MyClass another_something(1, 2);
    
    MyClass (MyClass::*add)(MyClass&) = &MyClass::operator+;

    MyClass result = (something.*add)(another_something);
    result.print();

    return 0;
}

```

---


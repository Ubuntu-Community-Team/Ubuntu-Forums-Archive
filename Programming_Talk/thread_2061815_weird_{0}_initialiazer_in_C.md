---
title: "weird {0} initialiazer in C"
date: 2012-09-23
forum: Programming Talk
---

### Post by vikkyhacks on 2012-09-23
```

#include<stdio.h>
struct A
{
        int a;
        int b;
        char c;
};

void main()
{
struct A sA = **{0}**;
printf("%d %d %c\n",sA.a,sA.b,sA.c);
}

```
what does that {0} do .. and if i try to use it this way as
```

struct A sA;
sA = {0};

```
it flashes me an error, 
I have used it to initialize arrays but what does that do here in structures, it is a bit different and cannot understand it ... any help is appreciated !!!):P

---

### Post by Tony Flury on 2012-09-23
{0} will in your case initialise the first named field to 0, the other fields are implementation dependent i think.

So in your case sA.a will be 0, and sA.b and sA.c could be anything.

The {<value>} syntax is only valid as an initialiser, which is why your 2nd example generates an error.

---

### Post by spjackson on 2012-09-23
> **Tony Flury said:**
> {0} will in your case initialise the first named field to 0, the other fields are implementation dependent i think.

So in your case sA.a will be 0, and sA.b and sA.c could be anything.

sA.b and sA.c are 0 initialised; this is not implementation dependent. For any aggregate (array or structure), if you supply fewer values in the initialiser list than there are elements in the aggregate, the remaining members are 0 initialised. Strictly speaking, "all subobjects that are not initialized explicitly shall be initialized implicitly the same as objects that have static storage duration", but at least in this case that means 0 initialised. That quote is from the C99 standard, but I am pretty sure that the principle dates back to the early days of C.

---

### Post by Tony Flury on 2012-09-23
> **spjackson said:**
> sA.b and sA.c are 0 initialised; this is not implementation dependent. For any aggregate (array or structure), if you supply fewer values in the initialiser list than there are elements in the aggregate, the remaining members are 0 initialised. Strictly speaking, "all subobjects that are not initialized explicitly shall be initialized implicitly the same as objects that have static storage duration", but at least in this case that means 0 initialised. That quote is from the C99 standard, but I am pretty sure that the principle dates back to the early days of C.
I stand corrected - the source I read implied that the initialisation was implementation dependent. Serves me right for not reading it properly :-).

---

### Post by vikkyhacks on 2012-09-24
well thanks for the reply but can u make it IN SIMPLE ENGLISH, i am a beginner,

     1.what about the **char c**, how does that get initialised, 

     2.Why does the second code not work
```

struct A sA;
sA = {0};

```

---

### Post by spjackson on 2012-09-24
I doubt that I can explain this IN SIMPLE ENGLISH but I'll do my best.

sA.c gets the value 0. Because it is of type char, this is sometimes written as '\0', which is often called the NUL byte. It is special in C in that it indicates the end of a string. It is a non-printing character, which means that you won't necessarily see anything when you print it out with printf.

Printable characters are those with a numeric value between 32 and 126. See [http://www.asciitable.com/]("http://www.asciitable.com/")

An equivalent assignment statement would be:
```

sA.c = 0;
/* or */
sA.c = '\0';

```

The following is not allowed
```

sA = {0};

``` because this is not initialization. It is assignment. As far as the C language is concerned, initialization only happens when a variable is created, i.e. within the statement that defines the variable. Because it is an assignment, not an initialization, you cannot use an initialization list.

---

### Post by trent.josephsen on 2012-09-24
A little note to add to spjackson's post -- {0} is a valid *initializer* for any object, including arrays, structs, integers, and pointers. It's kind of a special case in the C standard. The following initializations will always be valid:
```
int x = { 0 }; /* equivalent to int x = 0; */
struct foo y = { 0 }; /* zero-initializes every member of y */
```

But that's different from *assignment*. This is an assignment statement:
```
z = {0};
```
That won't compile unless z is of a type that "makes sense" in this context. It's just saying "Make the first object in z equal 0". It won't work if z is an int, because ints don't contain other objects; it won't work if z is an array, because arrays can't be assigned to; and it won't work if z is a struct with more than one member, because it would leave the other members uninitialized.

I kind of doubt this qualifies as simple English, but hope it helps anyway...

---

### Post by Bachstelze on 2012-09-24
> **vikkyhacks said:**
> well thanks for the reply but can u make it IN SIMPLE ENGLISH, i am a beginner,


Since you are a beginner, I would suggest you find some other learning material, because the one you are currently using is either outdated, or just plain bad. main() does not return void nowadays.

---

### Post by vikkyhacks on 2012-09-25
Ahh.... that was great I GET IT CLEAR NOW, thanks @spjackson and @trent.josephsen ... @Bachstelze I will take your advice ...
many Thanks :P

---


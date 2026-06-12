---
title: "using void* in sqlite callback function"
date: 2007-10-09
forum: Programming Talk
---

### Post by moshy on 2007-10-09
I have a program in C++ that queries a sqlite database using sqlite_exec and has a callback function that executes for each row.
The sqlite documentation says that the signature for the callback function should look like this:
```
int (*callback)(void*,int,char**,char**)
```
That pointer to void wold be very useful if I could actually make use of it. The program passes to it the address of a float, however inside the callback function I can't get the number back as I take it you can't dereference a pointer to void.
Trying to change all occurrences of void* with float* results in
```
invalid conversion from 'int (*)(float*, int, char**, char**)' to 'int (*)(void*, int, char**, char**)'
```
So this arbitrary pointer seems a bit useless to me at the moment.

---

### Post by archivator on 2007-10-09
Well, that's how void pointers work - you can turn any pointer to void implicitly but would have to explicitly convert it back to the original type.

In other words, ```
void call_me(void* a)
{
    float * num = (float*) a;
    (*num)++; // I never learned operator precedence :)
}

float num=3.14;
call_me(&num); // don't ever pass objects on the stack by their 
               // pointers without considering the consequences!
```
Hope that helped!

---

### Post by moshy on 2007-10-09
I did try casting it to (float*) initially but I got some error blah is not a pointer-to-object type, or something, I can't exactly remember, so I just assumed that you weren't supposed to cast void pointers.

---

### Post by Wybiral on 2007-10-09
This looks more like C then C++ to me. In C, casting pointers is common, in C++ you should avoid it (and avoid using pointers when you can).

---

### Post by moshy on 2007-10-09
OK, doing what you said worked, I realised I was trying to cast and dereference at the same time or something.
And the actually program is C++, its much bigger than what you can see, but the sqlite API is in C yes, I've had to wrap it.

---


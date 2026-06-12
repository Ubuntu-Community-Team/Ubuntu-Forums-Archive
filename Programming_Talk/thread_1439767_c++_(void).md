---
title: "c++ (void*)"
date: 2010-03-26
forum: Programming Talk
---

### Post by akvino on 2010-03-26
What does (void *) do, and what does it do when it is placed before the array?

---

### Post by WillFerrellLuva on 2010-03-26
a void* is a void pointer - a pointer that can be used to point to any data type.  Usually you have to use casts in conjunction with void pointers.  Not sure what you mean "when it is placed before the array?"

---

### Post by not_a_phd on 2010-03-26
Sometimes it is used in software stubs as a do-nothing instruction to prevent compiler warnings. For example:

```

double myFunction(double *myArray) {
   (void*)myArray;
   return 0.0;
}

```

The first statement in the function "touches" the myArray argument. Therefore, the compiler will not give an 'Unused Argument' warning.

---

### Post by MaxIBoy on 2010-03-26
An array is really just represented as a pointer to the first element. So a string (or cstring for you C++ users) is really just a char*, an array of integers is an int*. Which means that this code: ```
first_character = string[0];
third_number = int_list[2];
``` is the exact same as this code: ```
 first_character = *string;
third_number = *( int_list + 2 );
```The reason to convert it to a void array is that you can put whatever types of values into the array that you want. For this reason, all memory-management related functions in the standard library (malloc, realloc, calloc, free, etc.) both accept and return void pointers. You could give them other types of pointers if you like, and it wouldn't matter. Unless you are writing some kind of general purpose memory management code, this isn't important to you as a programmer. Probably the most useful other thing you could do with this is have function pointers or arrays of functions, like this:
```
#include <stdio.h>
#include <stdlib.h>

// Note how these three functions are different types. 
// As long as you don't care about the return values, it's OK
// though the compiler does grumble somewhat.
void function1 (void){
    printf ("1\n");
}
int function2 (void){
    printf ("2\n");
}
char function3 (void){
    printf ("3\n");
}


void *((*functions)(void)); //list of function pointers

void *add_function_to_list (void *((*list)(void)), void (function_to_add)(void), int amount_already_added) {
    void **newlist;
    newlist = realloc (list, sizeof (void *));
    newlist[amount_already_added] = function_to_add;
    return newlist;
}



int main () {
    int i = 0;
    int num_functions = 0;
    void (*temp_function) (void);
    functions = add_function_to_list (functions, function1, num_functions);
    num_functions++; 
    functions = add_function_to_list (functions, function2, num_functions);
    num_functions++;
    functions = add_function_to_list (functions, function3, num_functions);
    num_functions++;
    for (i = 0; i < num_functions; i++){
        temp_function = *(void**)(functions+i*sizeof(int));
        temp_function();
    }
    return 0;
}
```

---

### Post by Compyx on 2010-03-26
> **MaxIBoy said:**
> An array is really just represented as a pointer to the first element. So a string (or cstring for you C++ users) is really just a char*, an array of integers is an int*. Which means that this code: ```
first_character = string[0];
third_number = int_list[2];
``` is the exact same as this code: ```
 first_character = *string;
third_number = *( int_list + 2*sizeof(int) );
```

Incorrect: when you have a pointer to int and you need to access the n'th int after it, you simple add n, you don't add n * sizeof(int). Your example would access the 2 * sizeof(int)'th element, on my system that would be 2 * 4 = the 8'th element.

> 
The reason to convert it to a void array is that you can put whatever types of values into the array that you want.
No. First of all 'void' is not a type, it signals the absense of a type. A void array does not exist, nor does an array of void.
You can however cast a pointer to the first element of an array to a pointer to void * and pass that around, but you can't perform pointer-arithmetic on pointers to void, you can only test them for (in)equality.

GCC allows arithmetic on pointers to void, it assumes void has a size of 1, this contradicts the C standard, void has no size since it does not exist. This feature is probably meant to ease porting of pre-ANSI C code, when void and pointers to void did not exist, but the generic pointer type was a pointer to char (and sizeof(char) is by definition 1).

---

### Post by MaxIBoy on 2010-03-26
> **Compyx said:**
> Incorrect: when you have a pointer to int and you need to access the n'th int after it, you simple add n, you don't add n * sizeof(int). Your example would access the 2 * sizeof(int)'th element, on my system that would be 2 * 4 = the 8'th element.Whoops, thanks for catching that, I'll fix it. 

> No. First of all 'void' is not a type, it signals the absense of a type. A void array does not exist, nor does an array of void.Semantics, semantics. It's functionally equivalent to what I said. While you can't have an array of void per se, such an array would be useless and in fact I only learned this limitation when you posted it (never tried that kind of thing before.) The entire use of void "literals" as far as I can tell is for void pointers, and you *can* have arrays of those. 
> GCC allows arithmetic on pointers to void, it assumes void has a size of 1, this contradicts the C standard, void has no size since it does not exist. This feature is probably meant to ease porting of pre-ANSI C code, when void and pointers to void did not exist, but the generic pointer type was a pointer to char (and sizeof(char) is by definition 1).1 byte is an entirely sane size for a generic type-ish thing, not sure how anyone could justify any different size. Also, GCC is the only compiler I care about.  Have a nice day. :D

---

### Post by Sockerdrickan on 2010-03-27
> **not_a_phd said:**
> Sometimes it is used in software stubs as a do-nothing instruction to prevent compiler warnings. For example:

```

double myFunction(double *myArray) {
   (void*)myArray;
   return 0.0;
}

```The first statement in the function "touches" the myArray argument. Therefore, the compiler will not give an 'Unused Argument' warning.
A better way would be to just not set the variable name in the parameter

---

### Post by not_a_phd on 2010-03-28
> **Sockerdrickan said:**
> A better way would be to just not set the variable name in the parameter

If it is not needed perhaps, but sometimes during development, we stub out all of the functions that will be required (with their associated arguments) and then later populate the functions with algorithms. If the function in question is not needed until a later phase in development, it is annoying to have the compiler shooting off warnings, that might mask warnings that need attention.

---

### Post by dwhitney67 on 2010-03-28
> **not_a_phd said:**
> If it is not needed perhaps, but sometimes during development, we stub out all of the functions that will be required (with their associated arguments) and then later populate the functions with algorithms. If the function in question is not needed until a later phase in development, it is annoying to have the compiler shooting off warnings, that might mask warnings that need attention.

I agree to a certain point as to what you stated, but there are still easier ways to accomplish what you want.  I would suggest that you fiddle with the compiler flags.  For example, to warn about unused variables, except those that are parameters, one could use the following flags:  -Wall -Wextra -Wno-unused-parameter

IMO, inserting code into stubbed functions should only be done when a value needs to be returned, but for void functions, I wouldn't touch it.

---


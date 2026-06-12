---
title: "C programming explanation"
date: 2013-10-20
forum: Programming Talk
---

### Post by cp43tcW on 2013-10-20
Hi everyone, I would really appreciate it if someone could explain the following C code line by line.

```


#include <stdio.h> 
#include <stdlib.h> 
#define ARRAY_SIZE 10 
 
 
float max(int length, float *pointer) {  
    float result; 
    float *end; 
 
    result = * pointer; 
    pointer++; 
    for (end= pointer + length; pointer <end; pointer ++) { 
        if (*pointer > result) { 
            res = * pointer; 
        } 
    } 
    return result; 
} 
 
int main() { 
    float p[ARRAY_SIZE];  
    int i; 
 
    for (i=0; i< ARRAY_SIZE; i++) { 
        printf("%2d. broj: ",i+1); 
        scanf("%f", p+i); 
    } 
    printf("The largest number is: %f\n", max(ARRAY_SIZE, p)); 
    return EXIT_SUCCESS; 
}


```

---

### Post by sanderj on 2013-10-20
> **cp43tcW said:**
> ... line by line.


Hahaha! Sounds like your homework.

If you want help, tell what you do understand, and what you don't.

---

### Post by edouardtavinor on 2013-10-20
> **cp43tcW said:**
> Hi everyone, I would really appreciate it if someone could explain the following C code line by line.

```


#include <stdio.h> 
#include <stdlib.h> 
#define ARRAY_SIZE 10 
 
 
float max(int length, float *pointer) {  
    float result; 
    float *end; 
 
    result = * pointer; 
    pointer++; 
    for (end= pointer + length; pointer <end; pointer ++) { 
        if (*pointer > result) { 
            res = * pointer; 
        } 
    } 
    return result; 
} 
 
int main() { 
    float p[ARRAY_SIZE];  
    int i; 
 
    for (i=0; i< ARRAY_SIZE; i++) { 
        printf("%2d. broj: ",i+1); 
        scanf("%f", p+i); 
    } 
    printf("The largest number is: %f\n", max(ARRAY_SIZE, p)); 
    return EXIT_SUCCESS; 
}


```

There's one bug in your code: "res = * pointer;" should read "result = * pointer;"

When you read a program, find the main method and read all the definitions before hand. This tells you that there is a constant called ARRAY_SIZE which has the value 10, As this is a #define macro, you can replace the text ARRAY_SIZE everywhere in the program with the value 10 (it's what the precompiler does). There is also a function called max which is called using two arguments, an int called 'length' and the position of a float in memory called 'pointer'. It returns a float. a float is (probably) a 32-bit floating-point number.

now we can start reading main. this is where the computer starts execution of the code. the first thing it does is reserve some space. ARRAY_SIZE * the size of a float is reserved at a location and the address is saved in p. space is also reserved for an int called i. 

in the next lines we see why i was necessary. It's being used as a counter to let a loop be run ARRAY_SIZE times. in this loop, the user is asked to input a number in serbo-croatian. this input is then converted into a float and saved at the location p + i* the size of a float. C is quite clever here and understands that i times the size of a float should be added to the address in p to save the next number. 

After the array p has been filled with numbers the function max is called with the arguments ARRAY_SIZE and p. If you recall p is the location of the space reserved for 10 ints. This is a standard pun when programming in C. 

So now we have to look at the function max. space is reserved for a float in result and the address of a float in end. the number stored at the location 'pointer' points to is stored in result. then the address stored in pointer is incremented (by the size of a float on your system! because C knows the memory pointed to by 'pointer' contains floats). 

a for-loop in C is declared as follows: for( <things to do before starting the loop> ; <thing which while true will mean the loop continues> ; <thing to be performed before starting each iteration of the loop after the first iteration> ) { <loop instructions> }
Before the loop is started, 'end' is set to the number of 'pointer'  plus length times the size of a float. this is one past the address of the last element in the memory pointed at by 'pointer'. 
This is then used as the test condition. The loop will continue running while the value of 'pointer' is smaller than this number. that means while the address saved in pointer is below the first invalid address.
In each iteration pointer is incremented by the size of a float.
the test means that if the number stored at the address found in 'pointer' is larger than the number stored in result, this number should be saved in result.

after the loop has finished, result is returned.

That's basically how the program works. Maybe worth mentioning is that <stdio.h> defines the functions 'scanf' and 'printf' used in the program and <stdlib.h> defines EXIT_SUCCESS (which is just the number 0 on a linux system).

Hope this helps!

---

### Post by cp43tcW on 2013-10-20
Thanks for the reply, now I have to analyze it!

---


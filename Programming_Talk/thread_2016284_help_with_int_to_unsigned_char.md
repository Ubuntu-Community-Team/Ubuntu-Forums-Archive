---
title: "help with int to unsigned char"
date: 2012-07-04
forum: Programming Talk
---

### Post by spanlength1 on 2012-07-04
I am implementing this function below , but unclear about the correctness of it. 
```

#ifndef TWO5_H
#define TWO5_H

#include <stddef.h>
unsigned char* two5Encode(const int* array, size_t length);


void two5Print(const unsigned char* data, size_t length);

#endif


```

```

/* DESCRIPTION:
 * ------------
 * The function encodes an integer array using two-out-of-five 01236 encoding.
 * Every element in the integer array must be between 0 and 9. The function
 * returns a byte array that contains the encoding. 
 *
 * The returned array is allocated with malloc/calloc, and it is the 
 * responsibility of the caller to free this memory.
 *
 * PARAMETERS:
 * ------------
 * const int *array: an array of integers. Every integer value is between 
 * 0 and 9 (inclusive).
 *
 * size_t length: the number of elements in the array.
 *
 * RETURNS:
 * ------------
 * The source data encoded with two-out-of-five 01236 encoding.
 */

unsigned char* two5Encode(const int* array, size_t length) {
    unsigned char encode[10] = {'01100', '11000', '10100', '10010', '01010', '00110', '10001', '01001', '00101', '00011'};
    unsigned char* a = (unsigned char*) malloc(sizeof (unsigned char) *length);
    for (size_t i = 0; i < length; i++) {
        switch (array[i]) {
            case 0:
                a[i] = encode[0];
                break;
            case 1:
                a[i] = encode[1];
                break;
            case 2:
                a[i] = encode[2];
                break;
            case 3:
                a[i] = encode[3];
                break;
            case 4:
                a[i] = encode[4];
                break;
            case 5:
                a[i] = encode[5];
                break;
            case 6:
                a[i] = encode[6];
                break;
            case 7:
                a[i] = encode[7];
                break;
            case 8:
                a[i] = encode[8];
                break;
            case 9:
                a[i] = encode[9];
                break;
        }
    }
    two5Print(a,length);
    return a;
}

/* DESCRIPTION:
 * ------------
 * The function prints the bits in groups of five in a byte array. The groups
 * are separated by a single space ' ' character. Newline '\n' is printed after
 * the last group.
 *
 * PARAMETERS:
 * ------------
 * const unsigned char* data: the byte array to be printed.
 * size_tlength: the number of groups that should be printed.
 *
 * RETURNS:
 * ------------
 * Nothing.
 */
void two5Print(const unsigned char* data, size_t length){
    for(size_t i = 0 ; i < length ; i++){
        printf("%u ",data[i]);
    }
    printf("\n");
}


```

```

#include <stdio.h>
#include <stdlib.h>

#include "2outof5.h"

/*
 * 
 */
int main() {
    int data[10] = {0,1,2,3,4,5,6,7,8,9};
    two5Encode(data,10);
    
    return 0;
}

```

But i get lot of warnings at defination of encode array
" warning: character constant too long for its type [enabled by default] "

Please sujjest what modification needs to be done

---

### Post by ofnuts on 2012-07-04
> **spanlength1 said:**
> ```

    unsigned char encode[10] = {'01100', '11000', '10100', '10010', '01010', '00110', '10001', '01001', '00101', '00011'};

```

I dont know what you are trying to declare there, but either these are strings, or you are missing some indication of the binari{ness|tude} of  the literals. In fact I don't see any way to express numbers in binary form in C constants, you may have to use octal or hex or decimal (and drop the apostrophes):
```

    unsigned char encode[10] = {12, ... }; // decimal
    unsigned char encode[10] = {0x0C, ... }; // hex
    unsigned char encode[10] = {014, ... }; // octal

```

Unless you meant:
```

char *encode[10] = {"01100", ...};

```

---

### Post by spanlength1 on 2012-07-04
> **ofnuts said:**
> I dont know what you are trying to declare there, but either these are strings, or you are missing some indication of the binari{ness|tude} of  the literals. In fact I don't see any way to express numbers in binary form in C constants, you may have to use octal or hex or decimal (and drop the apostrophes):
```

    unsigned char encode[10] = {12, ... }; // decimal
    unsigned char encode[10] = {0x0C, ... }; // hex
    unsigned char encode[10] = {014, ... }; // octal

```

Unless you meant:
```

char *encode[10] = {"01100", ...};

```

I want to encode the value of each integer to a unsigned char array . If you read this article , [http://en.wikipedia.org/wiki/Two-out-of-five_code](http://en.wikipedia.org/wiki/Two-out-of-five_code)

it shows the representation of the numbers in 2outof5 encoding.
In the switch case i check the integer and put the corresponding value from the encode array to the char array.I know i am doing something wrong. if you can modify then it will be nice.

---

### Post by ofnuts on 2012-07-04
So that will be one of the decimal/hex/octal integers above. And you can replace your whole switch statement by:
```

a[i] = encode[array[i]];

```
... after of course checking that 0<=array[i]<10 (but you switch statement needs a default: clause for he same purpose).

PS: it is considered bad practice to cast the return value of malloc(). If the function is defined, the compiler knows it returns a "void *" that fits into any pointer without requiring  cast. And if you forgot the necessary header, you won't get the message about trying to shoehorn an int into a pointer.

---

### Post by 11jmb on 2012-07-04
> **ofnuts said:**
> I dont know what you are trying to declare there, but either these are strings, or you are missing some indication of the binari{ness|tude} of  the literals. In fact I don't see any way to express numbers in binary form in C constants, you may have to use octal or hex or decimal (and drop the apostrophes):
```

    unsigned char encode[10] = {12, ... }; // decimal
    unsigned char encode[10] = {0x0C, ... }; // hex
    unsigned char encode[10] = {014, ... }; // octal

```


as another option:
```

unsigned char encode[10] = {0b1100, ... }; // binary

```

These all mean the same thing once compiled, they are just represented differently in the source code.

---

### Post by Bachstelze on 2012-07-04
> **11jmb said:**
> as another option:
```

unsigned char encode[10] = {0b1100, ... }; // binary

```

These all mean the same thing once compiled, they are just represented differently in the source code.

This is a non-standard GNU extension.

---

### Post by Bachstelze on 2012-07-04
Also, I am not sure it would be very useful to store in two-out-of-five encoding. Storing is one thing, but what are you going to do with it? C does not use that format, so you will need a special function if you want to print them or do any kind of arithmetic, so you might as well encode on the fly instead of wasting memory in storing it.

---


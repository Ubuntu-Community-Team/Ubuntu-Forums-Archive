---
title: "valgrind error: Invalid read of size 4"
date: 2012-06-28
forum: Programming Talk
---

### Post by spanlength1 on 2012-06-28
Hello , I am doing a small vector assignment and facing this valgrind error . The program is working fine but no idea why there is valgrind error.
```

#ifndef TKK_AS_C_VECTOR_H
#define TKK_AS_C_VECTOR_H

#include <stdlib.h>
#include <stddef.h>

/*  This is just a typedef for the Data
*/
typedef int Data;

/*  Implement your struct for vector in .c file
    The vector contains elements which are defined as Data
*/
typedef struct Vector_s Vector;

/*  Create a new, empty vector
    @return the pointer to the new vector
*/
Vector* vectorConstruct(void);

/*  Destructs the vector and frees all memory allocated to it
    @param vector to destruct
*/  
void vectorDestruct(Vector* this);

/*  @param pointer to the vector
    @return the size of the vector
*/
size_t vectorSize(const Vector* this);

/*  Puts the data to the end of the vector
    @param vector where the data should be put
    @param data to put into the vector
*/
void vectorPushBack(Vector* this, const Data value);

/*  Puts the data to the beginning of the vector
    @param vector where the data should be put
    @param data to put into the vector
*/
void vectorPushFront(Vector* this, const Data value);

/*  Returns the data from the end of the vector and removes it from the vector
    @param vector from where the data is taken
    @return the data at the end of the vector or 0 if the vector is empty
*/
Data vectorPopBack(Vector* this);

/*  Returns the data from the beginning of the vector and removes it from the vector
    @param vector from where the data is taken
    @return data at the beginning of the vector or 0 if the vector is empty
*/
Data vectorPopFront(Vector* this);

/*  Returns the pointer to the data at given index
    @param vector from where the data is fetched
    @param index of data element to fetch
    @return pointer to data with given index or NULL if index is out of bounds
*/
Data* vectorDataAt(const Vector* this, size_t index);

/*  Swaps the data elements with given indexes, doesn't swat if either of indexes is out of bounds
    @param vector in which the data is swapped
    @param index of data to be swapped
    @param index of data to be swapped
*/
void vectorSwapData(Vector* this, size_t first, size_t second);

/*  Insert the data to vector into the place represented with index and moves the data from index and all consecutive elements one step to the end. If insert is out of bounds inserts the element as last element
    @param vector where to insert the data
    @param data to insert into the vector
    @param index where to insert the data
*/
void vectorInsertData(Vector* this, const Data value, size_t index);

/*  Copies the contents of a vector to a new vector
    @param source vector
    @return pointer to the new vector which contains the same information as thethe source vector
*/
Vector* vectorCopy(const Vector* src);

#endif

```

Below is the source file
```

#include <stdlib.h>
#include <stdio.h>
#include <assert.h>
#include "vector.h"
#include <ctype.h>

typedef struct Vector_s {
    Data *vectorval;
    size_t count;
} Vector_s;

Vector* vectorConstruct(void) {
    Vector *newv = malloc(sizeof (Vector));
    newv->vectorval = NULL;
    newv->count = 0;
    return newv;
}

void vectorDestruct(Vector* this) {
    assert(this);
    if (this) {
        free(this->vectorval);
        free(this);
    }
}

size_t vectorSize(const Vector* this) {
    assert(this);
    return this->count;
}

void vectorPushBack(Vector* this, const Data value) {
    assert(this);
    size_t num = this->count + 1;
    this->vectorval = realloc(this->vectorval, (sizeof(Data))*(num));
    this->vectorval[this->count] = value;
    this->count = num;
}

void vectorPushFront(Vector* this, const Data value) {
    assert(this);
    size_t num = this->count + 1;
        this->vectorval = realloc(this->vectorval, (sizeof(Data))*(num));
        for (size_t i = this->count; i > 0; i--) {
        this->vectorval[i] = this->vectorval[i - 1];
        }
    this->vectorval[0] = value;
    this->count = num;
}

Data vectorPopBack(Vector* this) {

    assert(this);
    size_t num = this->count ;
    int data = 0;
    if (num > 0) {
        data = this->vectorval[num-1];
        this->vectorval = realloc(this->vectorval, (sizeof(Data))*(num - 1));
        this->count = num -1;
    }
    return data;
}

Data vectorPopFront(Vector* this) {
    assert(this);
    size_t num = this->count ;
    int data = 0;
    if (num > 0) {
        data = this->vectorval[0];
        for (size_t i = 0; i < num; i++) {
            this->vectorval[i] = this->vectorval[i + 1];
        }
        this->vectorval = realloc(this->vectorval, (sizeof(Data))*(num - 1));
        this->count = num -1;
    }
    return data;
}

Data* vectorDataAt(const Vector* this, size_t index) {
    size_t count = this->count;
    Data* indexdata = NULL;
    Data value = 0;
    if (count < index)
        return indexdata;
    else {
        value = this->vectorval[index];
        indexdata = &value;
    }
    return indexdata;
}

void vectorSwapData(Vector* this, size_t first, size_t second)
{
    assert(this);
    size_t count = this->count;
    if ( count > first && count > second ){
        int temp = this->vectorval[second];
        this->vectorval[second] = this->vectorval[first];
        this->vectorval[first] = temp;
    }
}

void vectorInsertData(Vector* this, const Data value, size_t index) {
    assert(this);
   size_t count = this->count;
    this->vectorval = realloc(this->vectorval, (sizeof(Data))*(count + 1));
    if (count < index)
        this->vectorval[count] = value;
    else {
        for (size_t i = count; i > index ; i--) {
            this->vectorval[i] = this->vectorval[i-1];
        }
        this->vectorval[index] = value;
    }
    this->count = count+1;
}

Vector* vectorCopy(const Vector* src) {
    size_t count = src->count;
    Vector *newvector = malloc(sizeof (Vector));
    newvector->count = count;
    newvector->vectorval = malloc((sizeof(Data))*count);
    for (size_t i = 0; i < count; i++) {
        newvector->vectorval[i] = src->vectorval[i];
    }
    return newvector;
}

```


and the valgrind error

==18306== Memcheck, a memory error detector
==18306== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==18306== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==18306== Command: ./cvector
==18306== 
==18306== Invalid read of size 4
==18306==    at 0x804876B: vectorPopFront (vector.c:71)
==18306==    by 0x8048AD5: main (main.c:26)
==18306==  Address 0x419a354 is 0 bytes after a block of size 36 alloc'd
==18306==    at 0x4025016: realloc (vg_replace_malloc.c:525)
==18306==    by 0x80486DB: vectorPopBack (vector.c:58 )
==18306==    by 0x8048AC5: main (main.c:24)
==18306== 
==18306== 
==18306== HEAP SUMMARY:
==18306==     in use at exit: 0 bytes in 0 blocks
==18306==   total heap usage: 16 allocs, 16 frees, 376 bytes allocated
==18306== 
==18306== All heap blocks were freed -- no leaks are possible
==18306== 
==18306== For counts of detected and suppressed errors, rerun with: -v
==18306== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 12 from 7)

---

### Post by dwhitney67 on 2012-06-28
I did not bother testing your code through the debugger (or valgrind), but I suspect that the issue lies within vectorPopFront() at line 70; in other words, I believe this line is it:
```

for (size_t i = 0; i < num; i++) {

```
Change it to the following to see if the warning is cleared up:
```

for (size_t i = 0; i < **num - 1**; i++) {

```

---

### Post by spanlength1 on 2012-06-29
Thats correct, i modified that for loop.
Also should I do a memcopy for the array elements pointed by Data* after the realloc statements in the vectorPushFront,  vectorPushBack, vectorPopFront and vectorPopBack functions.

Is it necessary , because my school grading system still gives valgrind error but my system gives none. I cannot see the errors but only recieve that there are valgrind errors.

---

### Post by dwhitney67 on 2012-07-02
> **spanlength1 said:**
> 
Also should I do a memcopy for the array elements pointed by Data* after the realloc statements in the vectorPushFront,  vectorPushBack, vectorPopFront and vectorPopBack functions.

I can see using memcpy() within vectorPushFront() and vectorPopFront(), however I do not see how it would need  to be applied to the other two functions you mentioned.  Perhaps you meant vectorInsertData() and vectorCopy()?

> **spanlength1 said:**
> 
Is it necessary , because my school grading system still gives valgrind error but my system gives none. I cannot see the errors but only recieve that there are valgrind errors.
I've ran you code with a simple program, and I did not encounter any valgrind errors.  It would be helpful if you would supply a main() so that your code could be exercised.  It would also be helpful to know what version of valgrind (and system platform) your school is using.

---


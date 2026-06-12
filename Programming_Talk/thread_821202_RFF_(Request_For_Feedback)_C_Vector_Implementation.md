---
title: "RFF (Request For Feedback) C Vector Implementation"
date: 2008-06-07
forum: Programming Talk
---

### Post by JupiterV2 on 2008-06-07
In order to improve my C skills, I've attempted to implement a C version of C++'s STL vectors. Mainly I wanted to get used to pointer manipulation and memory management. I've run it a few times with valgrind and have no mem leaks.

I'm interested in any constructive criticism.

** vector.h **

[PHP]#ifndef VECTOR_H
#define VECOTR_H

typedef struct Vector
{
    void** elem;
    int index;
    int size;
} vector_t;

// return value at iterator/index without removing value
void* vector_at(vector_t* v, int i);

// test if vector is empty
int vector_empty(vector_t* v);

// free any memory allocated to the vector
// WARNING: Any dynamically allocated memory on behalf of the user will be
// lost!
void vector_free(vector_t* v);

// test if vector is full and in need of resizing
static int vector_full(vector_t* v);

// initialize vector's variables and allocate memory to store elements
void vector_init(vector_t* v);

// push new elements on the back of the vector
void vector_push_back(vector_t* v, void* new_elem);

// remove element from the back of the vector and return result
void* vector_pop_back(vector_t* v);

// resize the vector to conserve, or increase, memory
static void vector_resize(vector_t* v, int size);

// return the actual size (# of available elements in memory) of the vector
int vector_size(vector_t* v);

// swap two elements
void vector_swap(vector_t* v, int iter1, int iter2);

#endif[/PHP]


** vector.c **
[PHP]#include "vector.h"

#include <stdio.h>
#include <stdlib.h>
#include <assert.h>


//*****************************************************************************
// Constructors/Initializers and Helper Functions
//*****************************************************************************

void vector_init(vector_t* v)
{
    v->index = 0;
    v->size = 5;
    assert(v->elem = (void**) calloc(v->size, sizeof(void*)));
}

int vector_empty(vector_t* v) { return !v->index; }

void vector_free(vector_t* v) { if( v->size >= 5 ) free(v->elem); }

static int vector_full(vector_t* v) { return v->index == v->size; }

static void vector_resize(vector_t* v, int size)
{
    if( v->size + size < 5) return;
    
    v->size += size;
    assert(v->elem = (void**) realloc(v->elem, v->size * sizeof(void*)));
}

int vector_size(vector_t* v) { return v->size; }


//*****************************************************************************
// Modifier Functions
//*****************************************************************************

void* vector_at(vector_t* v, int i)
{
	if( v->size < 5 ) 
	{ 
	    printf("ERROR: Bad call to vector_at(): vector not "
	    	"initialized\n"); 
	    exit(1); 
	}
	
    if( i > v->index || i < 0 )
    {
        printf("ERROR: Bad index to vector: index out of bounds\n");
        exit(1);
    }
    else return v->elem[i];
}

void vector_push_back(vector_t* v, void* new_elem)
{
	if( v->size < 5 ) 
	{ 
	    printf("ERROR: Bad call to vector_push_back(): vector not "
	    	"initialized\n"); 
	    exit(1); 
	}
    if( vector_full(v) ) vector_resize(v, 5);
    v->elem[v->index++] = new_elem;
}

void* vector_pop_back(vector_t* v)
{
	if( v->size < 5 ) 
	{ 
	    printf("ERROR: Bad call to vector_pop_back(): vector not "
	    	"initialized\n"); 
	    exit(1); 
	}
	
    if( vector_empty(v) ) 
    {
        printf("ERROR: Bad call to vector_pop_back(): vector empty\n");
        exit(1);
    }

    void* elem = vector_at(v, --(v->index));
	
    if( v->size - v->index >= 5 ) vector_resize(v, -5);

    return elem;
}

void vector_swap(vector_t* v, int iter1, int iter2)
{
	if( v->size < 5 ) 
	{ 
	    printf("ERROR: Bad call to vector_swap(): vector not "
	    	"initialized\n"); 
	    exit(1); 
	}
	
    if( vector_empty(v) )
    {
        printf("ERROR: Bad call to vector_swap(): vector empty\n");
        exit(1);
    }

    if( iter1 == iter2 ) return;

    if( iter1 > v->index || iter1 < 0 )
    {
        printf("ERROR: Bad call to vector_swap(): iterator 1 out of "
        	"bounds\n");
        exit(1);
    }

    if( iter2 > v->index || iter2 < 0 )
    {
        printf("ERROR: Bad call to vector_swap(): iterator 2 out of "
        	"bounds\n");
        exit(1);
    }

    void* tmp_elem;
    tmp_elem = v->elem[iter1];
    v->elem[iter1] = v->elem[iter2];
    v->elem[iter2] = tmp_elem;
}[/PHP]

** main.c ** (test suite)
[PHP]#include "vector.h"
#include <stdio.h>

int main()
{
    vector_t vec;
    int x, size;

    // test1: push value onto uninitialized vector (should fail)
    //printf("test1: push value onto uninitialized vector (should fail)\n");
    //vector_pop_back(&vec);

    // test2: init vector and push 1000 values onto stack and check size
    printf("test2: init vector and push 1000 values onto stack and check size\n");
    vector_init(&vec);

    x = 0;
    while( x < 1000 ) 
    {
    	vector_push_back(&vec, (void*) x);
    	x++;
    }

    size = vector_size(&vec);

    printf("vector size = %d\n", size);
    // test3: swap 2 elements
    vector_swap(&vec, 200, 700);

    // test4: pop all values from stack and check size
    printf("test4: pop all values from stack and check size\n");
    while( !vector_empty(&vec) )
    {
        int n = (int) vector_pop_back(&vec);
        if( n % 100 == 0 ) printf("elem = %d\n", n);
        //printf("elem = %d\n", n);
    }

    size = vector_size(&vec);

    printf("vector size = %d\n", size);

    // test5: attempt to pop value off empty stack (should fail)
    //printf("test5: attempt to pop value off empty stack (should fail)\n");
    //void* v = vector_pop_back(&vec);

	vector_free(&vec);
    return 0;
[/PHP]

---

### Post by LaRoza on 2008-06-07
I didn't run it, but I noticed the lack of return values and the use of exit() in many functions.

That is a poor design and reduces the use of the library. If it works as it is supposed to (as you probably wanted) that is good, but I think you should make it more structured.

[http://en.wikipedia.org/wiki/Structured_programming](http://en.wikipedia.org/wiki/Structured_programming)

---

### Post by nvteighen on 2008-06-07
** vector.h **

[PHP]#ifndef VECTOR_H
#define VECOTR_H /*!!!! Should say VECTOR_H!!!!*/

typedef struct Vector
{
    (...)
[/PHP]

*EDIT* I notice you declared static functions in the header file too. Is that necessary? I mean: static functions are restricted to the module they're declared, so by prototyping them in vector.h, aren't you also making them available for main.c? (I'm writing a big integer library and have doubts on that).

---

### Post by dwhitney67 on 2008-06-07
I had quite a few comments last night, but somewhere before posting them, I got distracted and lost them.  So here's a list from memory:

1)  Use 'size_t' as the data type when referring to sizes, not 'int'.  Sizes/lengths should never be negative values, thus no need to use 'int'.

When referring to an index (or array position), define these as 'unsigned int'.  This indicates (via the API) to the caller to provide values greater than or equal to 0.


2)  The vector_size() function should return 'index'and not 'size', which represents the allocated space for the 'elem' array.  Consider renaming 'index' to something more descriptive, such as 'numElements'.


3)  As LaRoza stated, exit() calls are not appropriate in your design.  Use assert() to verify data, and if the function requires that data be returned which doesn't exist, return a 0 or null-pointer (also 0).  Hopefully the assert() will trap errors thus eliminating the need to worry about what is returned.


4)  Check the if-condition in vector_resize().  Something about the first conditional doesn't seem right.  How about:
[PHP]
if ( size == 0 ) return;

v->size += size;

assert( v->elem = realloc( v->elem, v->size * sizeof(void*) ) );
[/PHP]


5)  IMO, the vector_free() method should also free() each of the elements contained within the "elem" array and initialize the vector such that it cannot be used again.  Thus:
[PHP]
for ( unsigned int i = 0; i < v->numElements; ++i )
{
  free( v->elem[ i ] );
}
free( v->elem );

v->size = 0;
v->numElements = 0;
v->elem = 0;
[/PHP]

Anyhow, that's all I can remember at this time.

---

### Post by JupiterV2 on 2008-06-07
Excellent, thanks guys! I really appreciate the feedback! I'll make the changes and re-submit for further critiquing.

---

### Post by JupiterV2 on 2008-06-07
> **nvteighen said:**
> ** vector.h **

[PHP]#ifndef VECTOR_H
#define VECOTR_H /*!!!! Should say VECTOR_H!!!!*/

typedef struct Vector
{
    (...)
[/PHP]

*EDIT* I notice you declared static functions in the header file too. Is that necessary? I mean: static functions are restricted to the module they're declared, so by prototyping them in vector.h, aren't you also making them available for main.c? (I'm writing a big integer library and have doubts on that).

LOL, thanks for catching the typo! As for declaring the function static in the header, if you attempt to call them from outside vector.c the compiler emits a warning that the function exists but has no definition.

---

### Post by nvteighen on 2008-06-07
> **JupiterV2 said:**
> LOL, thanks for catching the typo! As for declaring the function static in the header, if you attempt to call them from outside vector.c the compiler emits a warning that the function exists but has no definition.

Thanks to you too!

I'll try to understand a bit more of your code when I've some more time. Now, I've got to study Latin... (exam on Monday)!

---

### Post by scourge on 2008-06-07
> ```
assert(v->elem = (void**) realloc(v->elem, v->size * sizeof(void*)));
```

You should never use assert like this, because your app won't work correctly if NDEBUG is defined.

---

### Post by JupiterV2 on 2008-06-07
Instead of assert, I should check to see if result was NULL?

---

### Post by moma on 2008-06-07
Hello,

Very good in deed. 

Take a look at "adt-0.1.tar.gz" tar ball in [http://www.futuredesktop.org/adt/](http://www.futuredesktop.org/adt/)  (read the README if you want to compile it)
It contrains an implementation of a dynamic array. Look for files parray.[ch] in the src/ directory.

1) Put all calloc, realloc to a common function. It's easier to debug when all memory functions are in the same place. 
See the parray.c, function 
int parray_alloc(parray_t *a, u32 _length)
----------

2) There is no need to check 
```
if( vector_full(v)) 
{
   vector_resize(v, 5);
}
```

Just call the resize function vector_resize(...) directly and let it do its job (do extend the array if necessary). Check the return value from it. 
Again, read parray.c. I use an ASSERT# macro to check the return value. 
```
 ASSERT2(parray_alloc(a, len), 0); 
```
----------

3) Use ASSERT macros to check validity of variables and function calls.  Study the lassert.h file.
ASSERT function should also report 
Which source filename (__FILE__), 
Which function ( __ASSERT_FUNCTION ) 
And which line number (__LINE__) the exception occured.


Functions should return a value (error/ok). Exit(1) is in most cases too strong punishment. 
----------

4) Be accurate with types.
Vector/array indeces are unsigned int [ 0 ... MAXINT ].
See the latype.h in the example code. I stole the type names from the Linux kernel.
```
...
typedef signed int s32;
typedef unsigned int u32;
```
----------

5) Set newly allocated vector slots to NULL (or 0) so they do not look like a valid pointer.
 memset(some_pointer, NULL, num_slots);
 calloc(...) <--- nullifies allocated memory.
 malloc() <--- does not nullify allocated memory.
 realloc() <--- does not nullify new, allocated memory. Copies over memory area from the original pointer. The original pointer can be NULL.
 free() <--- does not change the freed memory.
----------

6) You are doing just fine ;-)
----------

7) Implement also doubly linked list in C.
As an example, study the plist.[ch] and ptree.[ch] in "adt-0.1.tar.gz". (REDAME file)

---

### Post by scourge on 2008-06-07
> **JupiterV2 said:**
> Instead of assert, I should check to see if result was NULL?

That would be better, or if you want to use assert you could also do this:
```

v->elem = (void**) realloc(v->elem, v->size * sizeof(void*));
assert(v->elem != NULL);

```

Now the code would still work correctly if the assertion is removed. But I wouldn't use assert at all here. All builds of your app (not just debug) should check the return value of realloc.

---

### Post by nvteighen on 2008-06-07
(After some latin...)

Well, I'm struggling with something related to this in my bignum library project... I need to implement or emulate some dynamic array functionality, basically resizing.

Having looked deeper in your code:

What I personally don't like is that your library outputs text instead of only returning an error code. That may interfere with valid output by a program that uses this library, don't you think?

Is there a reason why you initalize vector_t with size = 5 and to malloc immediately? I'd set it to zero and elem = NULL, so we can get vectors for less than 5 elements. And let the user initialize maybe using a string as a buffer, take strlen() for size, allocate enough memory and let the pointer point there. (This is what I'm doing in my library... by the way, why the double pointer?).

---

### Post by Lux Perpetua on 2008-06-07
I would also take issue with the way you handle resizing of vectors in your push_back function. Increasing the space by a constant increment only makes sense if the user is expected not to use push_back to populate the vector. If you start with an empty vector and push back N elements, then you will do about N/5 reallocations, some or all of which may require moving all the vector's contents to a new address. That's a lot of copying. The standard way to do resizing is to double the allocated space every time space runs out. It may seem wasteful, but you never have more unused allocated space for a vector than used space. (If the vector shrinks a lot, you could consider occasionally halving the allocated space, but I don't know if standard implementations do this.) The benefit to this is that you will do many fewer allocations: only about log_2(N) reallocations (vs. N/5) for pushing back N items. It adds up to a big performance gain at the expense of higher, but not obscenely higher, memory use.

---

### Post by JupiterV2 on 2008-06-08
> **Lux Perpetua said:**
> I would also take issue with the way you handle resizing of vectors in your push_back function. Increasing the space by a constant increment only makes sense if the user is expected not to use push_back to populate the vector. If you start with an empty vector and push back N elements, then you will do about N/5 reallocations, some or all of which may require moving all the vector's contents to a new address. That's a lot of copying. The standard way to do resizing is to double the allocated space every time space runs out. It may seem wasteful, but you never have more unused allocated space for a vector than used space. (If the vector shrinks a lot, you could consider occasionally halving the allocated space, but I don't know if standard implementations do this.) The benefit to this is that you will do many fewer allocations: only about log_2(N) reallocations (vs. N/5) for pushing back N items. It adds up to a big performance gain at the expense of higher, but not obscenely higher, memory use.

The intent of using a constant of 5 was to conserve memory usage but what you say is true. I'm just learning, hence why I'm asking for input on the library (this is a practice exercise I devised for myself not a library I actually planned on releasing).

nvteighen - The purpose of the double pointer (I assume your refer to void**) is because I'm creating an array of void pointers. I want the user (programmer) to be able to assign any type of data (akin to C++ templates) to the vector.

---

### Post by dwhitney67 on 2008-06-08
> **JupiterV2 said:**
> The intent of using a constant of 5 was to conserve memory usage but what you say is true. I'm just learning, hence why I'm asking for input on the library (this is a practice exercise I devised for myself not a library I actually planned on releasing).

nvteighen - The purpose of the double pointer (I assume your refer to void**) is because I'm creating an array of void pointers. I want the user (programmer) to be able to assign any type of data (akin to C++ templates) to the vector.
Good answers!

---

### Post by JupiterV2 on 2008-06-08
I took everyone's suggestions to heart and updated as best I understood. ;) The only issue I had was:

How to handle an uninitialized vector? Since there is no way (that I know of) to know what the initial value of the variables within the vector struct are, I can't test whether or not the vector has been initialized before working with it. Doing so results in a segfault. (Boy I miss C++ constructors...)

Latest revision:

** vector.h **
[PHP]#ifndef VECTOR_H
#define VECTOR_H

typedef struct Vector
{
    void** elem;
    unsigned int num_elems;
    unsigned int size;
} vector_t;

// return value at iterator/index without removing value
void* vector_at(vector_t* v, unsigned int i);

// test if vector is empty
int vector_empty(vector_t* v);

// free any remaining memory allocated to the vector
void vector_free(vector_t* v);

// initialize vector's variable and allocate memory to store elements
void vector_init(vector_t* v);

// push new elements on the back of the vector
void vector_push_back(vector_t* v, void* new_elem);

// remove element from the back of the vector and return result
void* vector_pop_back(vector_t* v);

// resize the vector to conserve, or increase, memory
static void vector_resize(vector_t* v);

// return the actual size (amount of allocated space in memory)
unsigned int vector_size(vector_t* v);

// swap two elements
void vector_swap(vector_t* v, unsigned int iter1, unsigned int iter2);


//*****************************************************************************
// Assertation - Move to myassert.h
//*****************************************************************************

void myassert(char* file, unsigned int line, char* msg,
	unsigned int m_type);

#define ASSERT(_expr, _msg, _type) if( _expr ) { \
	myassert(__FILE__, __LINE__, (char*)_msg, _type); }

#endif[/PHP]

** vector.c **
[PHP]#include "vector.h"

#include <stdio.h>
#include <stdlib.h>

//*****************************************************************************
// Assertation - Move to myassert.h
//*****************************************************************************
void myassert(char* file, unsigned int line, char* msg,
	unsigned int m_type)
{
	fprintf(stderr, "%s:%d: %s: %s\n", file, line, 
		(m_type ? "warning" : "error"), msg);
	
	return;
}
	

//*****************************************************************************
// Constructors/Initializers and Helper Functions
//*****************************************************************************

void vector_init(vector_t* v)
{	
    v->num_elems = 0;
    v->size = 1;
    v->elem = 0;
    
	vector_resize(v);
    
    return;
}

int vector_empty(vector_t* v) { return !v->num_elems; }

void vector_free(vector_t* v) 
{
	// since it is unknown whether or not the user has passed pointers or
	// regular values onto the vector, freeing each element isn't possible
	// without the risk of segfaults.
	free( v->elem );
	
	v->size = 0;
	v->num_elems = 0;
	v->elem = 0;
	
	return;
}

static void vector_resize(vector_t* v)
{
    ASSERT(!v->size, "cannot allocate memory to an empty vector", 1);
    
    if( v->size / 2 > v->num_elems ) v->size /= 2;
    else if( v->size == v->num_elems ) v->size *= 2;
    
    v->elem = (void**) realloc( v->elem, v->size * sizeof(void*) );
    ASSERT(v->elem == NULL, "unable to allocate memory", 0);
    
    return;
}

unsigned int vector_size(vector_t* v) { return v->num_elems; }


//*****************************************************************************
// Modifier Functions
//*****************************************************************************

void* vector_at(vector_t* v, unsigned int i)
{
	ASSERT(i > v->num_elems, "index out of bounds", 1)
	
	if( v->size > 0 ) return v->elem[i];
	else return 0;
}

void vector_push_back(vector_t* v, void* new_elem)
{
    vector_resize(v);
    v->elem[v->num_elems++] = new_elem;
    
    return;
}

void* vector_pop_back(vector_t* v)
{
    if( vector_empty(v) ) return 0;

    void* elem = vector_at(v, --(v->num_elems));
	
    vector_resize(v);

    return elem;
}

void vector_swap(vector_t* v, unsigned int iter1, unsigned int iter2)
{
	
    if( vector_empty(v) || iter1 == iter2 || iter1 > v->num_elems || 
    	iter2 > v->num_elems ) return;

    void* tmp_elem;
    
    tmp_elem = v->elem[iter1];
    v->elem[iter1] = v->elem[iter2];
    v->elem[iter2] = tmp_elem;
    
    return;
}[/PHP]

---

### Post by slavik on 2008-06-08
use errno for error values ...

make the constructor return a newly created vector, so that the user can do "var x = var_new();"

also, I would suggest returning the vector pointer (instead of a function that returns nothing) for all functions that act on the vector as a whole (resize, init, etc.)

---

### Post by nvteighen on 2008-06-08
> **JupiterV2 said:**
> 
How to handle an uninitialized vector? Since there is no way (that I know of) to know what the initial value of the variables within the vector struct are, I can't test whether or not the vector has been initialized before working with it. Doing so results in a segfault. (Boy I miss C++ constructors...)

Maybe setting size to 0 when creating the vector? When it is initialized by user, size will have to be >= 1. So, if vector->size is 0, the vector is not being used (or has been free'd, from what I see) and access to it is invalid.

The issue is what happens if the elements in elem are pointers... Isn't there any free'ing recursive pattern out there?

---

### Post by JupiterV2 on 2008-06-08
> **nvteighen said:**
> Maybe setting size to 0 when creating the vector? When it is initialized by user, size will have to be >= 1. So, if vector->size is 0, the vector is not being used (or has been free'd, from what I see) and access to it is invalid.

The issue is what happens if the elements in elem are pointers... Isn't there any free'ing recursive pattern out there?

This is exactly the problem. You can't (to my knowledge) assign default values to the variables of a struct at compile time, only runtime. Slavik may have hit upon the best solution which is to return a pointer to a new vector object via a vector_new() or vector_create() function.

[PHP]
int main()
{
  // seems to force the user to create an initialized vector (Slavik's)
  // suggestion.
  vector_t* v1 = vector_new();
  vector_t* v2;

  // via this method, if the user does something they shouldn't before
  // the vector is created, it's in their hands, not mine, since they
  // can't work with a pointer that points to nothing (or at least, not
  // the vector struct they want)
  v2 = vector_new();

  // *or* method 2:
  vector_t v; 

  // no way to know what the struct's internal variables are. Has it
  // already been initialized? What can be tested to know for sure?
  vector_init(&v);
}
[/PHP]

---

### Post by dwhitney67 on 2008-06-08
Be wary of initializing a vector_t object (that has already been initialized previously) using the vector_init() function.  You could create a memory leak.  For instance:
[PHP]...

vector_t *vec = vector_new();

vec->vector_push_back( data1 );
vec->vector_push_back( data2 );
vec->vector_push_back( data3 );

...

vector_init( vec );    // oops... memory leak will occur![/PHP]
I highly recommend that your vector_t has a member data value to hold the state as to whether it has been initialized or not.  The member data value should be examined in pretty much all of your functions, with the exception of vector_new(), where it is set.

With the vector_new() function being made available, I really do not see the need to "publish" the vector_init() function.  Perhaps you should declare vector_init() as a static function, thus keeping it's access "private".

---

### Post by JupiterV2 on 2008-06-08
> **dwhitney67 said:**
> Be wary of initializing a vector_t object (that has already been initialized previously) using the vector_init() function.  You could create a memory leak.  For instance:
[PHP]...

vector_t *vec = vector_new();

vec->vector_push_back( data1 );
vec->vector_push_back( data2 );
vec->vector_push_back( data3 );

...

vector_init( vec );    // oops... memory leak will occur![/PHP]
I highly recommend that your vector_t has a member data value to hold the state as to whether it has been initialized or not.  The member data value should be examined in pretty much all of your functions, with the exception of vector_new(), where it is set.

With the vector_new() function being made available, I really do not see the need to "publish" the vector_init() function.  Perhaps you should declare vector_init() as a static function, thus keeping it's access "private".

You're absolutely correct. Sorry, I guess I wasn't exactly clear. I was only going to present one of the two options (vector_new() or vector_init()) not both. My bad for the confusion.

---

### Post by nvteighen on 2008-06-08
> **JupiterV2 said:**
> This is exactly the problem. You can't (to my knowledge) assign default values to the variables of a struct at compile time, only runtime. Slavik may have hit upon the best solution which is to return a pointer to a new vector object via a vector_new() or vector_create() function.


I think I haven't expressed myself clearly enough: use the size member to know what's the vector state. The idea is to allocate memory for your struct at vector_new() and set void **elem to NULL/zero, size to zero and num_elems to zero (isn't that a bit redundant, though?) at run-time.

And then create a function where the user initializes data by his own. There you can detect the size of data before writting it to the vector, set size to the correct value and finally allocate memory for the data pointed by elem.

Yes, it duplicates the amount of function calls the library user needs; but it's the pretty same pattern you use when malloc'ing and then initializing.

Or maybe I'm just showing my poor programming skills? I always tend to overcomplicate designs.

Anyway, here's what I'm doing in my bignum library. This is the memory management module (separated from the maths operation module), though it lacks for a resize function yet. I know your neds are not exactly the same as mine, but I still believe they're similar. Maybe C code will be more understandable than English? :p (excuse me, English is not my mother-tongue...)

[PHP]
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

/*Copied from header file to reduce post size*/
typedef struct
{
	char sign; /*Integer sign*/
	unsigned int size; /*Integer size*/
	char *cont; /*Integer expressed as an array of char vars
                     *but not as a string. We won't use '\0' at all.
                     */
} bigint;
/****/

static char bigint_cont_alloc(bigint *bigint_var)
{
	bigint_var->cont = (char *)malloc(bigint_var->size * sizeof(char));
	
	char status = 0;	
	if(bigint_var->cont == NULL)
		status = 1;

	return status;
}

static void bigint_init(bigint *bigint_var)
{
	bigint_var->sign = 1;
	bigint_var->size = 0;
	bigint_var->cont = NULL;
}

bigint *bigint_new(void)
{
	bigint *bigint_var = (bigint *)malloc(sizeof(bigint));
	if(bigint_var == NULL)
		return NULL;
	bigint_init(bigint_var);
}

void bigint_set(bigint *bigint_var, char *raw_bigint);
{
	if(bigint_var->cont != NULL)
	{
		free(bigint_var->cont); /*Deleting previous contents*/
		bigint_init(bigint_var);
	}

	unsigned int raw_length = (unsigned int)(strlen(raw_bigint));

	unsigned int i = 0;
	while(i < raw_length)
	{
		if(!(isdigit(raw_bigint[i])) && (raw_bigint[i] != '-'))
			break; /*Triming on first non-digit character*/

		i++;
	}
	bigint_var->size = i; /*size set*/

	char cont_alloc_failure = bigint_cont_alloc(bigint_var);
	if(cont_alloc_failure == 1)
	{
		bigint_free(bigint_var);
		return NULL;
	}

	i = 0;
	while(i < bigint_var->size)
	{
		if(isdigit(raw_bigint[i]))
			bigint_var->cont[i] = raw_bigint[i] - '0';
		else if(raw_bigint[i] == '-')
			bigint_var->sign = -1; /*sign set*/

		i++;
	}
	
	return bigint_var;
}

bigint *bigint_new_set(char *raw_bigint)
{
	bigint *bigint_var = bigint_new();
	bigint_set(bigint_var, raw_bigint);

	return bigint_var;
}

void bigint_free(bigint *bigint_var)
{
	if(bigint_var->cont != NULL)	
		free(bigint_var->cont);

	free(bigint_var);
}[/PHP]

---

### Post by JupiterV2 on 2008-06-08
> **nvteighen said:**
> I think I haven't expressed myself clearly enough: use the size member to know what's the vector state. The idea is to allocate memory for your struct at vector_new() and set void **elem to NULL/zero, size to zero and num_elems to zero (isn't that a bit redundant, though?) at run-time.

And then create a function where the user initializes data by his own. There you can detect the size of data before writting it to the vector, set size to the correct value and finally allocate memory for the data pointed by elem.

Here is my counter example:
[PHP]#include <stdio.h>
#include <stdlib.h>

typedef struct
{
	int* i;
} my_struct;

int ms_resize(my_struct* m)
{
	// this function would normally be static
	m->i = (int*) realloc(m->i, 5 * sizeof(int));
	if( m-> i == NULL ) return 0;
	else return 1;
}

int ms_init(my_struct* m)
{
	// this function would normally be static; initializes variables to their
	// default
	m->i = NULL;
	return ms_resize(m);
}

my_struct* ms_new()
{
	my_struct* ms = malloc(sizeof(my_struct));
	if( ms == NULL ) return NULL;
	
	if( !ms_init(ms) ) return NULL;

	return ms;
}

int ms_free(my_struct* m)
{
	if( m == NULL ) return 0;
	
	if( m->i != NULL ) free(m->i);
	
	free(m);
	
	return 1;
}

int main()
{
	my_struct* ms = ms_new();
	ms_free(ms);
	
	// in the following 2 lines of code, foo is not assigned anything and is
	// passed to ms_free(). Free() "fails" (even though it doesn't complain)
	// as evidenced through valgrind
	my_struct* foo;
	ms_free(foo);
}[/PHP]

```
==12720== ERROR SUMMARY: 6 errors from 6 contexts (suppressed: 11 from 1)
==12720== malloc/free: in use at exit: 0 bytes in 0 blocks.
==12720== malloc/free: 2 allocs, 4 frees, 24 bytes allocated.
==12720== For counts of detected errors, rerun with: -v
==12720== All heap blocks were freed -- no leaks are possible.

```

There are no memory leaks but the two excess calls to free() provide a perfect example of code that would fail if there was an attempt to push()/pop() data onto the stack.

Is this the fault of the programmer or the library?

[PHP]
my_struct* foo;
ms_free(foo);[/PHP]

How can the above code be checked to make sure no errors occur? Is it even possible?

---

### Post by nvteighen on 2008-06-08
> **JupiterV2 said:**
> Here is my counter example:
(...)

```
==12720== ERROR SUMMARY: 6 errors from 6 contexts (suppressed: 11 from 1)
==12720== malloc/free: in use at exit: 0 bytes in 0 blocks.
==12720== malloc/free: 2 allocs, 4 frees, 24 bytes allocated.
==12720== For counts of detected errors, rerun with: -v
==12720== All heap blocks were freed -- no leaks are possible.

```

There are no memory leaks but the two excess calls to free() provide a perfect example of code that would fail if there was an attempt to push()/pop() data onto the stack.

Is this the fault of the programmer or the library?

[PHP]
my_struct* foo;
ms_free(foo);[/PHP]

How can the above code be checked to make sure no errors occur? Is it even possible?

Ehm... you're playing with a dangling pointer! Expect undefined behaivor! If I initialize foo to NULL, no problem occurs:

```

==7628== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 11 from 1)
==7628== malloc/free: in use at exit: 0 bytes in 0 blocks.
==7628== malloc/free: 2 allocs, 2 frees, 24 bytes allocated.
==7628== For counts of detected errors, rerun with: -v
==7628== All heap blocks were freed -- no leaks are possible.

```

So, the responsability is on whoever writes main(), in this case; the "invalid" code is not in your library. It's the same problem you'll have with any uninitialized pointer you declare in any C program, so don't worry. :)

I believe there's a point where you just can't block any stupidity someone else can do with your code... You must assume the users know enough C to always initialize pointers.

---

### Post by Lux Perpetua on 2008-06-08
> **JupiterV2 said:**
> You're absolutely correct. Sorry, I guess I wasn't exactly clear. I was only going to present one of the two options (vector_new() or vector_init()) not both. My bad for the confusion.
Your interface should provide vector_new, the one that returns a properly allocated and initialized pointer, not vector_init, which requires a pointer to an allocated vector_t and initializes it. The client shouldn't even need to know what vector_t is. With the vector_new idiom, the implementation of vector_t can be hidden completely from the client: the struct itself need not be defined in the header file. (This is called an "opaque pointer.") This ensures that the client's code does not depend on any implementation details of vector_t, only on its functionality (unless the client really goes out of its way to defeat your interface).

---


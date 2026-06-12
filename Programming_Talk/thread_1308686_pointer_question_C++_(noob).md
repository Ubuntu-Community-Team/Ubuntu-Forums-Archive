---
title: "pointer question C++ (noob)"
date: 2009-10-31
forum: Programming Talk
---

### Post by BramWillemsen on 2009-10-31
Hi,

I've been reading through quite some pages of C++ tutorial, but some details about pointers keep confusing me. I hope some experienced programmer could give me some info. 

I read through this [URL]("http://forum.codecall.net/c-c/12151-returning-multidimensional-arrays-function.html") and some of the code really confused me.

```

#include <iostream>

using namespace std;

int array[5] = {0, 1, 2, 3, 4};

int (&function())[5]
{
  return array;
}

int main()
{
  int *a = function();

  for (int i = 0; i < 5; i++)
    cout << a[i] << '\n';
}

```

The things that confuses me here is **int (&function())[5]**. What does this say? I don't understand how I am supposed to read a function definition like this.

This also confused me
```

const int MATS = 3;
const int ROWS = 3;
const int COLS = 3;

void function1(int *array1D);
void function2(int (*array2D)[COLS]);
void function3(int (*array3D)[ROWS][COLS]);

int main()
{
  int a[ROWS];
  int b[ROWS][COLS];
  int c[MATS][ROWS][COLS];

  function1(a);
  function2(b);
  function3(c);
}

```

The guy who wrote the code said this about it
> When passing an array to a function, the first dimension turns into a pointer. An array of int turns into a pointer to int, an array of arrays of int--a 2D array--turns into a pointer to an array of int, an array of arrays of arrays of int--a 3D array--turns into a pointer to a 2D array.

When i read **int (*array2D)[COLS]** I get stuck at the following. 
**(*array2D)**: This gives the value where the array2D pointer points towards since * before a variable name makes you access the value normally.
The rest of the expression does not make sense to me anymore then.

I hope someone could give me a tip. I've read through quite some material on the internet, but I still find the details of pointers very hard to understand. But I would love to learn it! 

kind regards, 

Bram

---

### Post by dwhitney67 on 2009-10-31
I too would find it hard to understand pointers if I were to read a tutorial similar to yours.  No disrespect to the author, but wtf was he thinking presenting this material?

When passing a two-dim array, it is not sufficient to know just one of the dimensions of the array to have a full-view of the array's size.

Anyhow, to answer your questions, I hope the one-dim example is self-explanatory.  If not, here's a diagram:
```

1-dimensional array

         pointer to first element of array
         |
         |
         v
      +-----+-----+-----+-----+-----+
      | 10  | 20  | 30  | 40  | 50  |
      +-----+-----+-----+-----+-----+
         0     1     2     3     4

```
Here, we have a pointer to an array of 5 elements, which have values 10, 20, ..., 50.  When you see the ***array**, this is the pointer to the first element.

Similarly for a two-dim array:
```

2-dimensional array

         pointer to first element of array
         |
         |
         v
      +-----+-----+-----+-----+-----+
    0 | 10  | 20  | 30  | 40  | 50  |
      +-----+-----+-----+-----+-----+
      +-----+-----+-----+-----+-----+
    1 | 60  | 70  | 80  | 90  | 100 |
      +-----+-----+-----+-----+-----+
         0     1     2     3     4

```
Once again, the ***array** is pointing to the first element of the two-dim array.  Now as for the [COLS], this is denoting that the two-dim array has COLS number of columns.  In the example above, there are 5 columns.  Unfortunately the ***array** does not convey to you that there are two rows.  Did I not state earlier that the author of the tutorial was an idiot-savant?

In C++, if you want to explicitly require that a parameter be a two dimensional array of a fixed amount of COLS and ROWS, a better way to declare the function is as:
```

void function(int (&array)[ROWS][COLS]);

```
Here, the array is passed by reference; the number of columns and rows are explicitly stated, thus preventing any other sized array from being passed to the function.

If you want to allow an array with a variable number of rows to be passed to the function, then something like:
```

void function(int (*array)[COLS], const size_t numRows);

```
Note how this declaration is very similar to that which is found in your tutorial.  The only difference is that I have specified an additional parameter so that the number of rows can be given.

There is more to pointers than discussed above, but in a nutshell, think of a pointer as fingering a mailbox slot.  If you increment the pointer by 1, then you are pointing at the next mailbox slot.  The same concept works in reverse; you can decrement a pointer to reference the previous slot.  If you attempt to reference a slot of which your program does not control/own, then it is likely that the program will abruptly end with a segmentation violation.

I'm sure someone else will weigh in with better information than what I have provided.  The bottom line... don't let pointers perturb you too much.

---

### Post by BramWillemsen on 2009-11-01
Thanks a lot for your reply **dwhitney67** , that cleared some stuff up!

I still find it strange however that ***array** is used in the function call. I always thought that when you put a * before a 'pointer variable' name , you try to get the value is points to. But it seems like it is used to indicate the variable is a pointer here instead.

It makes sense in a certain way, putting a * before means that the variable must be a pointer. But to me it feels like it is inconsistent (i'm probably wrong though).

---

### Post by Amazona aestiva on 2009-11-01
I highly advise [http://www.cplusplus.com/]("http://www.cplusplus.com/")

I guess that is among the best sites about C++.

And here is it's tutorial of pointers for you:
[http://www.cplusplus.com/doc/tutorial/pointers/]("http://www.cplusplus.com/doc/tutorial/pointers/")

---

### Post by BramWillemsen on 2009-11-01
Thanks for the suggestion :) I read that one yesterday as extra resource before I posted here. It gives this as example for instance

ted is a pointer to address 1776. An integer of 25 is stored in this address.
```

beth = ted;   // beth equal to ted ( 1776 )
beth = *ted;  // beth equal to value pointed by ted ( 25 ) 

```
***ted** gives the value where pointer 'ted' points towards because it is preceded by a * operator. That's why using a * before a variable name is a confusing way for me to indicate a pointer. A * is normally used (like above) to get the value where the pointer points to (25 in this case).

Or is there a fundamental flaw in my thinking :???:?

---

### Post by A_Fiachra on 2009-11-01
The URL you supplied is a set of questions by a newbie programmer who has no idea that C++ does not ever return arrays, as such.

A C++ function can't return a heap allocated object, well, it can, but the address of the heap allocated object won't be any use after the return statement.


This is the problem:

```


int * foo ( ) {
    // create a LOCAL variable
    int arr[3] = {0, ,1, 2 };
    // now return the local variable .. what happens?
    return &arr;
}

int * some_array = foo();

// which array are we talking about??
// the address returned by foo can't be valid anymore!!


```C and consequently C++ does NOT return arrays!

That is not so say that you cannot create a matrix class where member functions can operate on heap allocated memory.

My advice to the OP -- throw that tutorial away!

---

### Post by BramWillemsen on 2009-11-01
Yeah I discovered that too, it makes sense of course. My last question still remains though:)

---

### Post by A_Fiachra on 2009-11-01
* has two meanings in C++, it is confusing

It is used in declarations to indicated a pointer (a memory address).

It is used in non-declarations as a dereference operator.


```

#include <stdio.h>


int main() {
  // declare and initialize an int
  int foo = 1;
  // declare but do not initialize a pointer to an int
  int * bar;
  // set that value of the pointer to int, bar
  bar = & foo;
  // print the adresss
  printf ("%x\n", bar);
  // print the value, uses '*' in a different context
  printf ("%d\n", *bar);

  return 0;
}


```

I get 

./foo
bf83ea0c
1

---

### Post by BramWillemsen on 2009-11-01
Indeed, that is why the code in my first post confuses me.

```

const int MATS = 3;
const int ROWS = 3;
const int COLS = 3;

void function1(int *array1D);
void function2(int (*array2D)[COLS]);
void function3(int (*array3D)[ROWS][COLS]);

int main()
{
  int a[ROWS];
  int b[ROWS][COLS];
  int c[MATS][ROWS][COLS];

  function1(a);
  function2(b);
  function3(c);
}

```

The code works, but i have no idea what it says. If i look at **void function2(int (*array2D)[COLS]);** for instance, what does this tell me?

When you put a * before a 'pointer variable' name , you try to get the value is points to. But it seems like it is used to indicate the variable is a pointer here instead. When I read ***array2D** in the code snippet above, I would assume that he wants to have the value array2D points towards, because he puts the * before 'array2D' like we just talked about. But obviously he tries to tell the compiler it is a pointer.

---

### Post by GeneralZod on 2009-11-01
> **BramWillemsen said:**
> 
When you put a * before a 'pointer variable' name , you try to get the value is points to. But it seems like it is used to indicate the variable is a pointer here instead. 


If you're using a variable name that has already been declared, the * before it does indeed "de-reference" it ("get the value it points to").

If you're declaring a variable name, then the * indicates that it is a pointer, although there is plenty of other stuff like order of precedence etc that complicates this.

So

```

int *a; // Declaring a as a pointer to int.
int b = *a; // "De-referencing" a, which was declared as a pointer to int.

```

Edit: Oh, A_Fiachra explained this better than me :)

The rules for deciphering declarations/ declarators are pretty complex and I don't know of a good resource for them (I ended up reading the chapter in the C++ Standard which has a 20+ page section on declarators alone!).

But

 void function2(int (*array2D)[COLS])

is a function called function2 which takes a pointer to an array of COLS ints and returns void.

---

### Post by BramWillemsen on 2009-11-01
> **GeneralZod said:**
> If you're using a variable name that has already been declared, the * before it does indeed "de-reference" it ("get the value it points to").

If you're declaring a variable name, then the * indicates that it is a pointer, although there is plenty of other stuff like order of precedence etc that complicates this.

So

```

int *a; // Declaring a as a pointer to int.
int b = *a; // "De-referencing" a, which was declared as a pointer to int.

```

Edit: Oh, A_Fiachra explained this better than me :)

The rules for deciphering declarations/ declarators are pretty complex and I don't know of a good resource for them (I ended up reading the chapter in the C++ Standard which has a 20+ page section on declarators alone!).

But

 void function2(int (*array2D)[COLS])

is a function called function2 which takes a pointer to an array of COLS ints and returns void.

Ah! so during declaration (in function definition) the * actually indicates the variable name is a pointer! No dereferencing in that case. That was the answer i was looking for :) Thanks a lot!

So it seems like it's not too noob to have some trouble with the pointer things if you ended up reading 20+ pages about declarators. It was easier in java :p

---

### Post by dwhitney67 on 2009-11-01
> **A_Fiachra said:**
> The URL you supplied is a set of questions by a newbie programmer who has no idea that C++ does not ever return arrays, as such.

A C++ function can't return a heap allocated object, well, it can, but the address of the heap allocated object won't be any use after the return statement.


This is the problem:

```


int * foo ( ) {
    // create a LOCAL variable
    int arr[3] = {0, ,1, 2 };
    // now return the local variable .. what happens?
    return &arr;
}

int * some_array = foo();

// which array are we talking about??
// the address returned by foo can't be valid anymore!!


```C and consequently C++ does NOT return arrays!

That is not so say that you cannot create a matrix class where member functions can operate on heap allocated memory.

My advice to the OP -- throw that tutorial away!

Obviously, based on the example you provided, you are correct.  One cannot expect to return an array that is declared on the stack within a function.  The array would go out of scope when the function ends, and thus the memory location of the array would no longer be valid.

But can an array be returned by a function?  Yes it is possible!!!

This is legal:
```

int* alloc_array(const size_t sz)
{
   return new int[sz];
}

...

int* my_array = function(5);

my_array[0] = 10;
my_array[2] = 20;
...
my_array[4] = 50;

...

delete [] my_array;

```

P.S.  It should be noted that the example above does not produce a 'true' array, but instead a contiguous "array" of int locations.  Unfortunately the compiler sees a difference between these two types.

---

### Post by MadCow108 on 2009-11-01
edit unnecessary post by my part

---

### Post by dwhitney67 on 2009-11-01
> **MadCow108 said:**
> in above case you have to delete the returned array explicitly when finished with it to avoid memory leaks

Yes, I made the change.

---

### Post by BramWillemsen on 2009-11-01
Thanks for your suggestions all ;) really appreciated. This will get me going for a while

---

### Post by Arndt on 2009-11-02
> **BramWillemsen said:**
> Ah! so during declaration (in function definition) the * actually indicates the variable name is a pointer! No dereferencing in that case. That was the answer i was looking for :) Thanks a lot!

So it seems like it's not too noob to have some trouble with the pointer things if you ended up reading 20+ pages about declarators. It was easier in java :p

Using * for dereferencing and for declaring are actually very similar, although it seems backwards if you start with the variable being declared and want to see its type somewhere near.

int *x;
int y;

These two mean that x is a pointer to int and y is an int. "x is a pointer to int" is not what that line appears to say - it says "dereferencing x gives you an int", but that is precisely what "pointer to int" actually means.

When you use x to get what it points to, you use the expression *x, which is also what appears in the declaration.

More complicated example: we have a pointer p to a function which takes an int as argument and returns a char. It will be used like this:

char c;
int i;

c = (*p)(i);

The declaration of p is

char (*p)(int);

Same structure as its use, only with the variables replaced by their types.

If you want to declare (declare, not define) a function which takes p as an argument, the type of the argument will also be written the same way, but this time without the name of p:

void f(char (*)(int));

(Though you can have an argument name there, if you like, for documentary purposes: void f(char (*callback1)(int)); )

I tried to make it appear simple - I don't know if I succeeded. The principle, anyway, is: a declaration of an identifier has the same lexical structure as an expression using the identifier.

That's why the * means pointer.

---

### Post by A_Fiachra on 2009-11-02
> **dwhitney67 said:**
> ..P.S.  It should be noted that the example above does not produce a 'true' array, but instead a contiguous "array" of int locations.  Unfortunately the compiler sees a difference between these two types.

Agreed, there is a semantic difference ... but it is important in understanding what pointers and arrays are.  It's also important to note the difference between heap allocated memory (which has to be deleted) and stack allocated memory (that can be reclaimed by a program when a variable goes out of scope)

---

### Post by dribeas on 2009-11-04
I have just browsed over the answers, without reading in detail and it seems as if nobody really tackled the first question you posted:

```

int (&function())[5];

```

The confusing part is probably the function signature and what it says: It is a function by the name of 'function' that takes no arguments [()] and returns a reference to an array of 5 integers 'int (&)[5]'. The same syntax can be used with function arguments, and it is used for example to get the size of an array:

```

template <typename T, std::size_t N>
std::size_t array_size( T (&)[N] ) {
   return N;
}

```

Taking the template syntax away and how the compiler does type deduction, the signature of the templated method is: function by the name of 'array_size' taking an array of N elements of type T by reference as first (unnamed) argument and returning an std::size_t value. The syntax for arrays passed in other than by value or returned by a function follows the same pattern:

```

type ([const][&,*[const]] X )[ size ]

```

That defines a possibly constant pointer or reference ([&,*[const]])  to a possibly constant (the other [const]) array of size ([size]) elements of type 'type'. Now that syntax can be used when defining a variable X, or when defining a parameter X into a function, or when defining the return statement of a function, where X would be the whole function signature: name of function and list of parameters with their associated types.

Going back to the code:
```

int array[5] = {0, 1, 2, 3, 4};
int (&function())[5] {
  return array;
}

```

The function is defined as returning a reference to an array of 5 integers and the return statement is in fact an array of 5 integers, so the function is well defined. 

In this example we are dealing only with the return definition, but up to here everything applies to arguments. Now, you cannot return an array of objects by value in C++, so I will switch the discussion into the argument version: 'void f( int (&array)[5] )'. The difference between passing the array by reference or passing by value ('void f( int array[5] )') is that the array will decay into a pointer to the first element. The signature presented is in fact equivalent to 'void f( int* array )' to all respects. When the function signature takes the form of an array passed by value, it is translated into a pointer.

On the caller end, when you pass an array into a function that takes a pointer (either f( int* ) or f( int[] ) ) the compiler will 'decay' the array into a pointer to the first element which is the an automatic translation provided by the compiler.

```

void f1( int (&array)[5] ) {}
void f2( int array[5] ) {} // means: void f2( int* array )
//void f2( int *array ) {} // error: redefinition of f2!!
//void f1( int* array ) {} // correct: overload, left commented so that the compiler cannot use the overload to match f1( array4 ) later on...
int main() {
   int array5[5] = { 0, 1, 2, 3, 4 };
   int array4[4] = { 0, 1, 2, 3 };
   f1( array5 ); // correct
// f1( array4 ); // error: the argument is not an array of 4 elements
   f2( array5 ); // ok, the argument decays into &array5[0] of type int*
   f2( array4 ); // ok, same happens: f2( &array4[0] ) of type int*
}

```

Going back to the end of your first code snippet:

```

int main() {
  int *a = function();
//int (&a)[5] = function(); // possible
  for (int i = 0; i < 5; i++)
    cout << a[i] << '\n';
}

```

The first sentence of the main() function is calling a function that returns a reference to an array of 5 integers. By assigning it to a pointer (instead of another reference), the compiler is applying the translation: 'int *a = &(function())[0];' to acquire the address of the first element in the array.

The for loop is using the 'operator[]' applied to pointers that is equivalent to '*( a + i )', that is: using pointer arithmetic to get a new pointer 'i' int elements beyond the initial pointer and then dereferencing that pointer.

---


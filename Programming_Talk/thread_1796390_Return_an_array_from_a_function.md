---
title: "Return an array from a function"
date: 2011-07-03
forum: Programming Talk
---

### Post by stamatiou on 2011-07-03
Hey guys, I would like to print an array that I have edited in a function, how can I do this?

---

### Post by cgroza on 2011-07-03
What language?

---

### Post by Petrolea on 2011-07-03
to print it you don't even have to return it

---

### Post by psusi on 2011-07-03
Your question does not match your subject, and is entirely too vague and open ended to be answered.

---

### Post by stchman on 2011-07-03
> **stamatiou said:**
> Hey guys, I would like to print an array that I have edited in a function, how can I do this?

By the use of the word function maybe he means C or C++.

C and C++ use pointers to return arrays from functions.

```

#include <stdio.h>

int *rtnarray();

int main( void ) {
    int i = 0, j = 0;
    
    int array[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
    
    int *array2;
    
    for( i = 0; i < sizeof( array ) / sizeof( int ); i++ ) {
        printf( "%d\n", array[ i ] );
    }
    
    printf("\n");
    
    array2 = rtnarray();
    
    for( j = 0; j < 6; j++ ) {
        printf( "%d\n", array2[ j ] );
    }

    return 0;
}

int *rtnarray() {
    int farray[] = { 3, 5, 7, 9, 1, 4 };
    
    return farray;
}


```

---

### Post by cgroza on 2011-07-03
And then how would you know how long is your returned array after?

---

### Post by ve4cib on 2011-07-04
> **stchman said:**
> By the use of the word function maybe he means C or C++.

C and C++ use pointers to return arrays from functions.

```

#include <stdio.h>

int *rtnarray();

int main( void ) {
    int i = 0, j = 0;
    
    int array[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
    
    int *array2;
    
    for( i = 0; i < sizeof( array ) / sizeof( int ); i++ ) {
        printf( "%d\n", array[ i ] );
    }
    
    printf("\n");
    
    array2 = rtnarray();
    
    for( j = 0; j < 6; j++ ) {
        printf( "%d\n", array2[ j ] );
    }

    return 0;
}

int *rtnarray() {
    int farray[] = { 3, 5, 7, 9, 1, 4 };
    
    return farray;
}


```

It's been a while, but won't that cause errors?  farray is allocated on the stack when you call rtnarray, and as soon as that function returned the variable no longer exists.  The memory address will likely be overwritten with other stack variables.

A better solution to returning an array would probably be to use malloc and return a pointer to the memory on the heap.

> And then how would you know how long is your returned array after? 

In C and C++ you don't.  In many languages (Java, C#, Python, etc...) arrays are objects and have a length property (or function) that tells you how long they are.

In C an array is simply a block of sequential bytes of memory, starting at an arbitrary address.  You need to store the length in a separate variable.

You'll find that almost all C functions that take arrays as parameters also accept an int for the length of the array.  The reason for that is because without that extra variable there is *absolutely no way of knowing how long the array is*.

Here's another code example for you.  Again, there are two functions (main, and one that returns an array).  Main calls the function, and then prints out the returned array.

```

#include <stdio>
#define ARRAY_LENGTH 10

int* genArray(int length)
{
    // create a new array and store it on the heap
    int* arr = (int*)malloc(sizeof(int) * length);
    int i;

    // fill the array with [1, 2, 3, 4, ...]
    for(i=0; i<length; i++)
        arr[i] = i+1;

    return arr;
}

int main()
{
    int i;
    int* array;

    // create the array
    array = genArray(ARRAY_LENGTH);

    // print the array
    for(int i=0; i<ARRAY_LENGTH; i++)
        printf("%d\n",array[i]);

    // clean up the memory we allocated with malloc
    free(array);

    return 0;
}
```

---

### Post by unknownPoster on 2011-07-04
> **stchman said:**
> By the use of the word function maybe he means C or C++.



By the use of the word "function" he could mean any programming language in the world. I can't think of any non-esoteric programming language that does not have/support functions.

---

### Post by stamatiou on 2011-07-04
Sorry! I forgot to mention it is C:oops:! Also can I do it without the use of malloc?

---

### Post by ve4cib on 2011-07-04
> **stamatiou said:**
> Sorry! I forgot to mention it is C:oops:! Also can I do it without the use of malloc?

Not easily, if you want to return a new array from a function.  If you create the array as a local variable inside the function then the array is destroyed as soon as the function returns.  The only way around that is to create the array using malloc.

However, you don't necessarily need to have a function that returns an array.  You can have a function that simply accepts an array as a parameter and edits it.

Here's the same example I had before, but this time genArray is replaced by fillArray.  The array is a local variable, defined within main, and passed around as a parameter:

```
#include <stdio>
#define ARRAY_LENGTH 10

void fillArray(int* arr, int length)
{
    // fill the array with [1, 2, 3, 4, ...]
    for(i=0; i<length; i++)
        arr[i] = i+1;
}

int main()
{
    int i;
    int array[ARRAY_LENGTH];

    fillArray(array, ARRAY_LENGTH);

    // print the array
    for(int i=0; i<ARRAY_LENGTH; i++)
        printf("%d\n",array[i]);

    return 0;
}
```

---

### Post by nvteighen on 2011-07-04
Another alternative: you could create a new array data structure that holds its own length, though. It's fairly trivial to create a non-generic array like this.

Or you can use GLib's arrays :) And no, it's not cheating: learning how to use libraries is also part of learning how to program.

---

### Post by cgroza on 2011-07-04
> **ve4cib said:**
> 

In C and C++ you don't.  In many languages (Java, C#, Python, etc...) arrays are objects and have a length property (or function) that tells you how long they are.

In C an array is simply a block of sequential bytes of memory, starting at an arbitrary address.  You need to store the length in a separate variable.


Yes, but he is already returning the array, so to return the length too he would need a struct to store both assuming that the function creates a random length array.

---

### Post by Simian Man on 2011-07-04
stchman's example will indeed cause problems as he is returning a memory address from a function that has gone out of scope.  Here is a small example of returning an arbitrarily sized array from a function and keeping track of its type.

```

#include <stdlib.h>

typedef struct {
  int length;
  int* array;
} myarray;


myarray get_array( ) {
  myarray ret;
  ret.length = 10;
  ret.array = malloc(10 * sizeof(int));

  /* fill it in ... */

  return ret;
}


int main( ) {
  myarray arr = get_array( );

  /* use it ... */

  free(arr.array);
  return 0;
}

```

This is one of the many, many reasons why C shouldn't be used for general-purpose programming :).

---

### Post by stchman on 2011-07-04
> **Simian Man said:**
> stchman's example will indeed cause problems as he is returning a memory address from a function that has gone out of scope.  Here is a small example of returning an arbitrarily sized array from a function and keeping track of its type.

```

#include <stdlib.h>

typedef struct {
  int length;
  int* array;
} myarray;


myarray get_array( ) {
  myarray ret;
  ret.length = 10;
  ret.array = malloc(10 * sizeof(int));

  /* fill it in ... */

  return ret;
}


int main( ) {
  myarray arr = get_array( );

  /* use it ... */

  free(arr.array);
  return 0;
}

```This is one of the many, many reasons why C shouldn't be used for general-purpose programming :).

To be fair, I have not done much C/C++ programming in a long time.  I have been a Java programmer for the last 6-7 years and returning arrays from methods is a snap and Java's array commands are superior to C/C++ IMO. 

```

class ReturnArray {
    public static void main( String[] args ) {
        double[] stuff;
        
        ReturnArray m = new ReturnArray();
        stuff = m.rtnArray();
        
        for( int i = 0; i < stuff.length; i++ ) {
            System.out.println( stuff[ i ] );
        }
        
    }
    
    double[] rtnArray() {
        double[] exArray = { 1.2, 2.8, 6.4, 9.89, 12.44, 45.198 };        
        return exArray;
    }
}


```

---

### Post by schauerlich on 2011-07-04
> **stchman said:**
> To be fair, I have not done much C/C++ programming in a long time.  I have been a Java programmer for the last 6-7 years and returning arrays from methods is a snap and Java's array commands are superior to C/C++ IMO. 


That's because in Java, everything is allocated to the heap. In C/C++ you just have to be explicit about it. C++ vectors are more comparable to Java's ArrayLists.

---

### Post by cgroza on 2011-07-04
I don't think anyone is using the primitive C arrays in C++. It defeats the purpose of using C++ and it's standard containers are a lot more powerful and get you rid of headaches.

---

### Post by Simian Man on 2011-07-04
> **stchman said:**
> To be fair, I have not done much C/C++ programming in a long time.

Yeah, but posting misleading code is still bad.  And I agree that C and C++ arrays are extremely weak.  Pretty much ANY language has better built in data types than C.  Consider Ocaml which is also compiled to an executable and is very fast but has much better array support - and is much more concise than Java :).
```

let rtnArray () =
  [|1.2; 2.8; 6.4; 9.89; 12.44; 45.198|]
;;

let m = rtnArray () in
Array.iter (fun x -> Printf.printf "%f\n" x) m

```

---

### Post by stchman on 2011-07-04
> **Simian Man said:**
> Yeah, but posting misleading code is still bad.  And I agree that C and C++ arrays are extremely weak.  Pretty much ANY language has better built in data types than C.  Consider Ocaml which is also compiled to an executable and is very fast but has much better array support - and is much more concise than Java :).
```

let rtnArray () =
  [|1.2; 2.8; 6.4; 9.89; 12.44; 45.198|]
;;

let m = rtnArray () in
Array.iter (fun x -> Printf.printf "%f\n" x) m

```

My code was not misleading.  It did what is what was supposed to do.

Remember, the OP just wanted to return an array from a function and print it, that's what I did.

---

### Post by Simian Man on 2011-07-04
> **stchman said:**
> My code was not misleading.  It did what is what was supposed to do.

Remember, the OP just wanted to return an array from a function and print it, that's what I did.

It did what you wanted in this case, but if you do that kind of thing often enough in a big enough program, you will get segfaults.  Or maybe it will work for you, but fail when you try to give your code to someone else.  Either way it's no fun to try to find these errors and posting code which contains them as a solution is a bad idea.

---

### Post by ve4cib on 2011-07-04
> **cgroza said:**
> I don't think anyone is using the primitive C arrays in C++. It defeats the purpose of using C++ and it's standard containers are a lot more powerful and get you rid of headaches.

It depends heavily on the application.  Sometimes your primitive array will suffice.  But often it's definitely worthwhile to at least use a struct containing the data and an int for the length.

---

### Post by lisati on 2011-07-04
> **ve4cib said:**
> It depends heavily on the application.  Sometimes your primitive array will suffice.  But often it's definitely worthwhile to at least use a struct containing the data and an int for the length.

It has been a while since I've done much programming (other than a handful of PHP scripts, but does that count?), but find myself seeing a degree of wisdom in this kind of suggestion.

---


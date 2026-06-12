---
title: "Extending Arrays in C"
date: 2007-06-21
forum: Programming Talk
---

### Post by ankursethi on 2007-06-21
I'm trying to create a function that performs a push and pop operation on a simple integer array. The problem is that I have to reallocate the memory each time and extend the size of the array in order to add another element to the array. I used the realloc() function, which worked perfectly as long as I used it within the main function of my program. Since I need to do this operation very often, I tried to write a function to do it, which gives me a core dump. This is a toned down and simplified version of what I was doing :
```
#include <stdio.h>
#include <stdlib.h>

void modify (int* arr) ;

int main (int argc, char* argv) {
	int* testArray ;
	modify (testArray) ;
	printf ("%d", testArray[0]) ;
	return 0 ;
}

void modify (int* arr) {
	arr = (int*) realloc ((void*)arr, sizeof(int)) ;
	arr[0] = 200 ;
}

```
This gives a core dump as well. What am I doing wrong?

PS : Any website/book which can give more info on memory management in C? The C Programming Language only describes malloc(), realloc() and calloc() and gives *one* implementation.

---

### Post by AnRa on 2007-06-21
You have to call malloc() first to allocate some memory and the use realloc() when needed.

---

### Post by finer recliner on 2007-06-21
there is a vector class in the STL library if you'd like to use it. it is a dynamic array with lots of functions and safety checks already written for you.
[http://www.fredosaurus.com/notes-cpp/stl-containers/vector/header-vector.html](http://www.fredosaurus.com/notes-cpp/stl-containers/vector/header-vector.html)

happy programming.

---

### Post by moma on 2007-06-21
As "AnRa" says, it's good habit to call calloc() first and then extend the memory with realloc(), but this IS NOT the actual problem with your code.

The problem is:
The modify() function never returns a value in the [COLOR="SeaGreen"]arr[/COLOR] variable.

	int* testArray ;unspecified
	modify (testArray) ;

You make a call by value , **_not_** call by reference or call by address.
The pointer which you send to modify() is "call by value".  The int *arr never returns new pointer back after realloc().   And testArray points to an unspecified memory location which causes a segfault.

I have modified your code so it works correctly. Now it sends the ADDRESS of testArray to modify(int **arr).  The function returns a proper pointer back in memory location that arr points to.

**int ** arr** means: a pointer to (an integer) pointer.  

```
#include <stdio.h>
#include <stdlib.h>

void modify (int** arr) ;

int main (int argc, char* argv) {
	int* testArray = NULL;

	modify (&testArray) ;

	printf ("%d", testArray[0]) ;

	return 0 ;
}

void modify (int** arr) 
{
	*arr = (int*)realloc ((void*)*arr, sizeof(int)) ;
	// *arr[0] = 200 ;      EDIT:  see hod139's posting below. 
        (*arr)[0]  = 200;
}
```

The code is not very good or readable, but it illustrates your problem.

Notice also:
You must initialize the testArray pointer to NULL before you use it.  Then the realloc() can handle both NULL pointer and other pointers. Realloc() will call malloc() when you send it a NULL pointer. 
---------

[COLOR="DarkRed"]Suggestion:[/COLOR]
Take a look at my parray.c code here  [http://www.futuredesktop.org/adt/](http://www.futuredesktop.org/adt/)
Click on the **adt-0.1.tar.gz** ball and open the "parray.c" file.
Study the 
int parray_alloc(parray_t *a, u32 _length)
function and how it is called.  Then you can improve your code.

Think about encapsulation. Enclose array pointers and other variables in a structure or class. Then pass that structure/class to functions.
Study "parray.h" and struct _parray_t.

Read the README file for howto compile and run the parray, plist and ptree examples.

[COLOR="SeaGreen"]Anyway,  very good beginning "Ankursethi".  Keep going. 
Come back when you have a new version of your code or any other questions. Ok?  :-)
[/COLOR]

---

### Post by ankursethi on 2007-06-21
I'd tried that before, but it wasn't working. Must've been some stupid error ...

Erp, there seems to be a tiny problem. The value of testArray[0] doesn't get printed (no output for the above code). Now what?

---

### Post by moma on 2007-06-21
Re-hello,
The value is probably outputted but it is hard to spot because it's mingling with other things on the comman line.  Add a label and newline ('\n')  character to the output, like this:

printf ("\nThe value=%d\n", testArray[0]) ;
--------------------

Compile the code. 
$ [COLOR="SeaGreen"]gcc filename.c -o filename[/COLOR]

Run it
$[COLOR="SeaGreen"] ./filename[/COLOR]

---

### Post by AnRa on 2007-06-21
**moma**, you can just modify one line:

```
#include <stdio.h>
#include <stdlib.h>

void modify (int* arr) ;

int main (int argc, char* argv) {
	int* testArray[COLOR="Red"] = (int*) malloc(sizeof(int))[/COLOR];
	modify (testArray) ;
	printf ("%d", testArray[0]) ;
	return 0 ;
}

void modify (int* arr) {
	arr = (int*) realloc ((void*)arr, sizeof(int)) ;
	arr[0] = 200 ;
}

```That works fine! :)

---

### Post by hod139 on 2007-06-21
> **AnRa said:**
> **moma**, you can just modify one line:

```
#include <stdio.h>
#include <stdlib.h>

void modify (int* arr) ;

int main (int argc, char* argv) {
    int* testArray[COLOR=Red] = (int*) malloc(sizeof(int))[/COLOR];
    modify (testArray) ;
    printf ("%d", testArray[0]) ;
    return 0 ;
}

void modify (int* arr) {
    arr = (int*) realloc ((void*)arr, sizeof(int)) ;
    arr[0] = 200 ;
}

```That works fine! :)

This is wrong for exactly the reasons that moma stated earlier.  In this example, your modification allocates an int pointer (allows holding one int), calls modify with a **copy** of the pointer (call by value), reallocs the copy, set the value pointed to by the pointer to 200 and prints it.  This is OK because of the original malloc now sets aside enough room for one int.

If however the code was this:
```

#include <stdio.h>
#include <stdlib.h>

void modify (int* arr) ;

int main (int argc, char** argv) {
    int* testArray = (int*) malloc(sizeof(int));
    modify (testArray) ;
    printf ("%d\n", testArray[0]) ;
    printf ("%d\n", testArray[1]) ;  // This will read bad memory
    return 0 ;
}

void modify (int* arr) {
    arr = (int*) realloc ((void*)arr, 2*sizeof(int)) ;
    arr[0] = 200 ;
    arr[1] = 400 ;
}

```You will now have illegal reads.  You really do have to pass a pointer to the pointer as explained earlier.


**EDIT: I have now included working code in case you are interested**
```

#include <stdio.h>
#include <stdlib.h>

void modify (int** arr) ;

int main (int argc, char** argv) {
    int* testArray = (int*) malloc(sizeof(int));
    modify (&testArray) ;
    printf ("%d\n", testArray[0]) ;
    printf ("%d\n", testArray[1]) ;
    return 0 ;
}

void modify (int** arr) {
    *arr = (int*) realloc ((void*)*arr, 2*sizeof(int)) ;
    **arr = 200 ;
    *(*arr + 1) = 400 ;
}

```

---

### Post by AnRa on 2007-06-21
> **hod139 said:**
> This is wrong for exactly the reasons that moma stated earlier.  In this example, your modification allocates an int pointer (allows holding one int), calls modify with a **copy** of the pointer (call by value), reallocs the copy, set the value pointed to by the pointer to 200 and prints it.  This is OK because of the original malloc now sets aside enough room for one int.

If however the code was this:
```

#include <stdio.h>
#include <stdlib.h>

void modify (int* arr) ;

int main (int argc, char** argv) {
    int* testArray = (int*) malloc(sizeof(int));
    modify (testArray) ;
    printf ("%d\n", testArray[0]) ;
    printf ("%d\n", testArray[1]) ;  // This will read bad memory
    return 0 ;
}

void modify (int* arr) {
    arr = (int*) realloc ((void*)arr, 2*sizeof(int)) ;
    arr[0] = 200 ;
    arr[1] = 400 ;
}

```You will now have illegal reads.  You really do have to pass a pointer to the pointer as explained earlier.Did you try compiling and executing that code? It works without problems. ;)

---

### Post by hod139 on 2007-06-21
> **AnRa said:**
> Did you try compiling and executing that code? It works without problems. ;)

Did you read what I wrote?  Not causing a segfault (by luck) does not mean the code works.  The modify function is not working as expected, therefore it has problems.

---

### Post by ankursethi on 2007-06-22
@moma
Tried the '\n' already with no avail.

@hod139
That works perfectly. But why doesn't subscripting the array work inside the other function?

---

### Post by hod139 on 2007-06-22
The reason moma's solution using array indexing is not working is because of operator precedence.

```

void modify (int** arr) 
{
    *arr = (int*)realloc ((void*)*arr, 2*sizeof(int)) ;
    (*arr)[0] = 200 ;
    (*arr)[1] = 400 ;
}

```

This should work.  The [] operator has a higher precedence than the * dereference operator.

---

### Post by ankursethi on 2007-06-22
Got it. Thanks everybody :-)

---

### Post by AnRa on 2007-06-22
> **hod139 said:**
> Did you read what I wrote?  Not causing a segfault (by luck) does not mean the code works.  The modify function is not working as expected, therefore it has problems.
I realized my mistake now, I'm sorry! ;)

---


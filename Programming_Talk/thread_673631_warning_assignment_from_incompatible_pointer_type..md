---
title: "warning: assignment from incompatible pointer type...malloc();"
date: 2008-01-20
forum: Programming Talk
---

### Post by S15_88 on 2008-01-20
Hey i've googled around and havent found a solution to my specific case.

I wrote a program for school that compiled with no errors or warnings, the teacher then asked us to write the same program but using dynamic memory...malloc();

i took the same code and made the appropriate adjustments, but for some reason line 23: string = malloc(sizeof(char*) *count);  is giving me issues!  i've tried putting a cast...and just fiddling with it but i have no reached a solution.  any help would be greatly appreciated
Thanks, Alain

for school they want us to compile using gcc -ansi -Wall
here is my code:
```

#include <stdio.h>
#include <stdlib.h>

int main()
{
    int i, count;
    char **string;

    FILE * infile;

    infile = fopen("/home/alain/school/cis/2500/lab2/input2.txt", "r");

    if(infile == NULL)
    {
        printf("Error: can't open file.\n");
        return 1;
    }
    else
    {
        fscanf(infile, "%d", &count);
        /*printf("%d\n", count);*/
 
        string = malloc(sizeof(char*) *count);       

        for(i=0; i<count; i++)
        {
            string[i] = malloc(sizeof(char)*80);    
        }
        for(i=0; i<count; i++)
        {
            fscanf(infile, "%s", string[i]);
        } 
        for(i=count; i>=0; i--)
        {
            printf("%s\n", string[i]);
        }
        printf("\n");
        for(i=0; i<count;i++)
        {
            free(string[i]);
        }
        free(string);
    }
    return 0;
} 

```

---

### Post by LaRoza on 2008-01-20
HInt: malloc is used for every data type, therefore, it returns a pointer of type "void". 

Since this is for school, I won't give the code. 

Your error is a result of not using malloc correctly, any tutorial or book should cover this.

---

### Post by stroyan on 2008-01-20
Keep trying those casts.  You need to cast to the same type as the variable you are assigning to.
You should always test for a malloc returning NULL.  That will happen if the system runs out of space to allocate.
You should limit the length of strings read with fscanf so they will fit in the allocated space.  Overflows of strings is a very common problem leading to security defects in the real world.  You can use "%79s" to limit a read string to fit in 80 bytes.

---

### Post by Compyx on 2008-01-21
> **stroyan said:**
> Keep trying those casts.  You need to cast to the same type as the variable you are assigning to.

The return value of malloc should never be cast in C. Using casts to shut up the compiler is generally a very bad idea and will lead to bugs.

---

### Post by dwhitney67 on 2008-01-21
Your code appears fine; what is probably causing you grief is your compiler setting.  Try compiling your program with a statement similar to the following:

```
$ gcc -std=c99 prog.c
```

This forces the compiler to adhere to the C99 standards.  Want to know more: [http://www.ibm.com/developerworks/library/l-c99.html](http://www.ibm.com/developerworks/library/l-c99.html)

---

### Post by LaRoza on 2008-01-21
> **Compyx said:**
> The return value of malloc should never be cast in C. Using casts to shut up the compiler is generally a very bad idea and will lead to bugs.

[quote="K&R 2d Edition"]
In C, the proper method is to declare that malloc returns a pointer to void, then explicitly coerce the pointer into the desired type with a cast.
[/quote]

If this is out of date, where is your source?

---

### Post by stroyan on 2008-01-21
> **Compyx said:**
> The return value of malloc should never be cast in C. Using casts to shut up the compiler is generally a very bad idea and will lead to bugs.

I learned the C language old-school.  In the original C implementation the malloc function returned type "char *" instead of "void *".  That required casting.  Casting the return value of a malloc to any pointer type will not cause a bug.  The result of a successfull malloc has correct alignment to cast to any pointer type.

The compiler was "giving issues" with the assignment from malloc to a "char **".  I suspect that he is actually using a system that declares malloc as returning a "char *".

---

### Post by hod139 on 2008-01-22
@OP, what version of gcc are you using?

@LaRoza and stroyan
ANSI C defines malloc to return a void*.  As stroyan stated, in the old pre-standard days it would sometimes return a char* and a cast was needed.

The reason you don't have to cast it now is because ANSI C also defines implicit casting between void* and any other pointer type.  This is one of those things where C++ and C are different when people always claim that C++ is a superset of C.  If you use malloc in C++ will you have to cast the return of malloc, since the compiler will not auto cast the void* to the pointer type you want.

This is **not** valid C++ code:
```

char *string;
string = malloc(10*sizeof(char));

```

In C++ you are required to cast the return of malloc to a char*:
```

char *string;
string = reinterpret_cast<char*>( malloc(10 * sizeof(char*)) );

```

---

### Post by blucalvin on 2010-04-13
Hi guys,
I would like to know what exactly "assignment from incompatible pointer type" means. Does it mean that the pointers on either side of the assignment statement varies?

I got the same bug when I tried the code:

#include <stdio.h>
#include <stdlib.h>

#define CAP 3

int main()
{
  int **ptr;
  int i;
  ptr = (int *) malloc (sizeof(int) * CAP);
  for (i = 0 ; i < CAP ; i++)
    printf("%p ",ptr++);
  printf("\n");
  return 1;
}

Being a somewhat beginner to C, I was trying to learn how to use 2D pointers. It seems I cannot make head nor tail of it. I've tried referring to K&R, The C Programming Language, Second Edition. But I couldn't quite find the answer. 
Please help me to figure it out.
Thank you.

---

### Post by Compyx on 2010-04-13
There are no 2D pointers or arrays in C. What you need to do is something along the lines of this: (untested)

```

/**
 * this function creates an 'array' of 'arrays' of int 
 *
 * @param dimA   dimension A
 * @param dimB   dimension B
 *
 * @return pointer to 'array' or NULL on failure
 */
int **make_semi_2d_array_of_int(size_t dimA, size_t dimB)
{
    int **p = malloc(sizeof *p * dimA);
    if (p != NULL) {
        int x;
        for (x = 0; x < (int)dimA; x++) {
            p[x] = malloc(sizeof *(p[x]) * dimB);
            if (p[x] == NULL) {
                /* clean up */
                while (--x >= 0) {
                    free(p[x]);
                }
                free(p);
                p = NULL;
                break;
            }
        }
    }
    return p;
}

```

What this function does is it allocates an 'array' of pointers to 'arrays' of int. These are strictly speaking not arrays, what actually is returns is a pointer to the first of a sequence of pointers to int (dimA elements), each of these pointing to the first of a sequence of int (dimB elements).

There are no 2D arrays in C, there are however arrays of arrays.

The warning you were getting is that you assing a int* to an int**, these are two different types. You also should not cast the return value of malloc(), this can hide errors, such as failing to include <stdlib.h>.

Also don't return 1 from main, this is a non-portable number and as far as I know is an error code in Linux. Either return 0 or EXIT_SUCCESS to indicate success, or EXIT_FAILURE to indicate failure. Both EXIT_* macro's can be defined by including <stdlib.h>.


You might find the comp.lang.c FAQ useful, especially the section on pointers and arrays: [http://c-faq.com/index.html]("http://c-faq.com/index.html")

---

### Post by blucalvin on 2010-04-14
Thank you.

Although I understood the allocation, I cannot picture how **ptr lies in the memory. As it is an array of arrays, am I right in understanding *ptr gives the first column of pointers to arrays and **ptr points to the arrays of each individual pointer(rows) of *ptr? Or can't it be understood in such a manner?

And might any drastic error occur on casting the return type of malloc()? If not casted, will it automatically return the desired pointer type as is on the LHS of the assignment expression?

I still don't know to where main() is returning its return value. But I'll make sure that I won't use 1 as its return value in future.

Thanks again.

---

### Post by Compyx on 2010-04-14
> **blucalvin said:**
> Thank you.

Although I understood the allocation, I cannot picture how **ptr lies in the memory. As it is an array of arrays, am I right in understanding *ptr gives the first column of pointers to arrays and **ptr points to the arrays of each individual pointer(rows) of *ptr? Or can't it be understood in such a manner?


Think of it like this:
```

+---+---+---+---+---+
| A | B | C | D | E |
+---+---+---+---+---+
  |   |   |                 +---+---+---+---+
  +---------------------->  | a | b | c | d |
      |   |                 +---+---+---+---+
      |   |
      |   |                 +---+---+---+---+
      |   +-------------->  | i | j | k | l |
      |                     +---+---+---+---+
      |
      |                     +---+---+---+---+
      +------------------>  | e | f | g | h |
                            +---+---+---+---+

```
The uppercase letters are pointers to int, the lower case letters are integers.

int **p points to 'A', the first element of an 'array' of pointer to int. A itself is an int *, a pointer to int, which in this case points to an 'array' of integers (in the illustration 'a', 'b', 'c' and 'd'), which I allocated in the loop.

In the loop I allocate, for each element in the array of pointers, a  block of memory for int's. As you can see in the illustration, the layout of these blocks (arrays) of int is not guaranteed to be sequential, the blocks themself ofcourse are, but the order in which the blocks are located in memory can be anything. That is why you can't use [x,y] to access elements in a '2D' array, you have to use [x][y].

So, should I want to get element [2,3] from the '2D array', I would simply use:
```

p[2][3]

```
here, I treat p as if it were an array (p[2] is equivalent to *(p + 2)) and I treat the value in p[2] as another array by using 3 as an index. You could use pointers to access the same element, that would look like this:
```

*(*(p + 2) + 3)

```
Which one looks simpler? I'd go for the array notation ;)

> 
And might any drastic error occur on casting the return type of malloc()? If not casted, will it automatically return the desired pointer type as is on the LHS of the assignment expression?

In standard C, the pointer is implicitly converted to the type on the left-hand side of the assignment, so you're safe. Casting the return value can hide errors, such as not #include'ing <stdlib.h>. If <stdlib.h> is not included, the compiler assumes malloc() to return int. On my system, sizeof(int) is 4, while sizeof(void*) is 8, so casting would force a 64-bit value into a 32-bit value and assign that to the LHS. Using a cast, you tell the compiler 'I know what I'm doing, shut up', so the compiler wouldn't warn you about the missing prototype of malloc(), leaving out the cast will allow the compiler to complain about the missing prototype.

In C++, the cast is required. That's why you will sometimes see the cast used in C code; that way, the code will compile as C++ as well.

> 
I still don't know to where main() is returning its return value. But I'll make sure that I won't use 1 as its return value in future.

Thanks again.

main() returns its value to the environment, so when you start your program from a shell, the value is returned to the shell. This is useful for stringing together a number of commands, or when using your program in a conditional expression inside a script.


I hope you can make sense of what I wrote, if not, feel free to ask for clarification.

---


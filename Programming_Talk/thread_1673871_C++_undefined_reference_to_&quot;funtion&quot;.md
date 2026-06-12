---
title: "C++ undefined reference to &quot;funtion&quot;"
date: 2011-01-23
forum: Programming Talk
---

### Post by Roberto_Lapuente on 2011-01-23
Hi,

Im trying to lern c++ on my own and y have a problem while trying to do a static library:

main.cpp
```
#include <iostream>
#include "../Library/lib.h"

using namespace std;

int main()
{
    int *arr[5];
    *arr[0]=40;
    *arr[1]=2;
    *arr[2]=77;
    *arr[3]=16;
    *arr[4]=12071;

    QuickSort(arr, 0, 4);

    for (int i=0; i<5; i++)
    {
        cout << *arr[i];
    }
}
```

lib.h
```
#ifndef LIB_INCLUDED
#define LIB_INCLUDED

static void QuickSort(int *datos[], int min, int max);

static int Encontrar_Pivote(int *datos[], int min, int max);

static void Rotar(int *datos[], int primero, int segundo);


#endif // LIB_INCLUDED
```

lib.cpp
```
#include "lib.h"

static void QuickSort(int *datos[], int min, int max)
{
    int pivote;

    if ((max-min) > 0)
    {
        pivote = Encontrar_Pivote(datos, min, max);
        QuickSort(datos, min, pivote-1);
        QuickSort(datos, pivote+1, max);
    }
}

static int Encontrar_Pivote(int *datos[], int min, int max)
{
    int pivote = *datos[min++];

    while (min<max)
    {
        if (*datos[min]<=pivote && *datos[max]>=pivote)
        {
            min++;
            max--;
        }
        else if (*datos[min]>=pivote && *datos[max]<=pivote)
        {

            Rotar(datos, min, max);
            min++;
            max--;
        }
        else if (*datos[min]<=pivote && *datos[max]<=pivote)
        {
            min++;
        }
        else if (*datos[min]>=pivote && *datos[max]>=pivote)
        {
            max--;
        }
    }

    if (min>max)
        Rotar(datos, max, pivote);

    else if (min<pivote)
        Rotar(datos, min, pivote);

    else if (min>pivote)
        Rotar(datos, min-1, pivote);

    return 0;
}

static void Rotar(int *datos[], int primero, int segundo)
{
    int aux = *datos[primero];
    *datos[primero] = *datos[segundo];
    *datos[segundo] = aux;
}
```

When i try to build the  main file i get this error:
C++/Pruebas/main.cpp|15|undefined reference to `QuickSort(int**, int, int)'

---

### Post by slavik on 2011-01-23
you left out the most important piece ... how are you building it?

sounds like you are simply compiling the main file and not the library file.

---

### Post by Roberto_Lapuente on 2011-01-23
Im using Code blocks IDE and I build the library before trying to compile the main file.

Do i have to use a special command to build a library?

---

### Post by worksofcraft on 2011-01-23
You must remove the word "static" from the definitions and declarations of your functions.

"static" has the side effect of meaning it is only visible in the current module so the linker can't see it. Note: All functions always have static memory allocation in code space.

---

### Post by Roberto_Lapuente on 2011-01-23
I keep getting the same error

---

### Post by worksofcraft on 2011-01-23
> **Roberto_Lapuente said:**
> I keep getting the same error

I copied your files and removed the word "static" everywhere.

Then it compiles OK from the command line... but there is still a run time bug to fix:
```

cjs@cjs-ubuntu:~/Desktop/examples/Lapuente$ g++ main.cpp lib.cpp
cjs@cjs-ubuntu:~/Desktop/examples/Lapuente$ ./a.out
Segmentation fault
cjs@cjs-ubuntu:~/Desktop/examples/Lapuente$ 

```

would you like me to find why it seg' faults or are you still stuck on compiling it?

---

### Post by Roberto_Lapuente on 2011-01-23
thanks, I will try to compile it from the command line.

---

### Post by worksofcraft on 2011-01-23
The reason you get segmentation fault is because you create an ARRAY of POINTERS to integers. and you don't initialize the pointers.

I suspect what you really want is an array of integers:
[php]
 int main()
{
    int arr[5];
    arr[0]=40;
    arr[1]=2;
    arr[2]=77;
    arr[3]=16;
    arr[4]=12071;

    QuickSort(arr, 0, 4);

    for (int i=0; i<5; i++)
    {
        cout << arr[i] << endl;
    }
}
[/php]

Edit: you also need to change your functions:
[php]
void QuickSort(int *datos, int min, int max);

int Encontrar_Pivote(int *datos, int min, int max);

void Rotar(int *datos, int primero, int segundo);
[/php]
Note: in C and C++ pointers are used as above to pass arrays by reference.

---

### Post by Roberto_Lapuente on 2011-01-23
Thanks, i want an array if integers but i dont know how to pass an array by reference in c so i used the pointers.

---

### Post by nvteighen on 2011-01-23
> **Roberto_Lapuente said:**
> Thanks, i want an array if integers but i dont know how to pass an array by reference in c so i used the pointers.

Uh... Is this C or C++?

In C++, there's something called "references" and that works more or less as a call-by-reference system. In C, you only can do this by using pointers.

But, in both languages arrays are always passed by pointers, so...

```

// I assume you're using g++
#include <cstdio>

void oh_noes(int *array, unsigned int size)
{
    unsigned int i;
    for(i = 0; i < size; i++)
        (void)printf("%d\n", array[i]);
}

int main(void)
{
    int array[6] = {1, 2, 3, 4, 5, 6};

    oh_noes(array, 6);

    return 0;
}

```

Why? Well, because arrays fall back to pointers. An array is nothing more than a pointer to the first element in some allocated region. The next elements are accessed by using pointer arithmetic, such that array[n] is actually *(array + n). The difference between arrays and pointers is that only the first allocate the needed space to place elements in it, while pointers don't.

C++ references don't work well with this because arrays already are called by "reference" (actually, by pointer)... If you're curious about them, take a look at this: [http://cplus.about.com/od/learning1/ss/references.htm](http://cplus.about.com/od/learning1/ss/references.htm)

---

### Post by Roberto_Lapuente on 2011-01-23
> **nvteighen said:**
> Uh... Is this C or C++?

In C++, there's something called "references" and that works more or less as a call-by-reference system. In C, you only can do this by using pointers.

But, in both languages arrays are always passed by pointers, so...

```

// I assume you're using g++
#include <cstdio>

void oh_noes(int *array, unsigned int size)
{
    unsigned int i;
    for(i = 0; i < size; i++)
        (void)printf("%d\n", array[i]);
}

int main(void)
{
    int array[6] = {1, 2, 3, 4, 5, 6};

    oh_noes(array, 6);

    return 0;
}

```

Why? Well, because arrays fall back to pointers. An array is nothing more than a pointer to the first element in some allocated region. The next elements are accessed by using pointer arithmetic, such that array[n] is actually *(array + n). The difference between arrays and pointers is that only the first allocate the needed space to place elements in it, while pointers don't.

C++ references don't work well with this because arrays already are called by "reference" (actually, by pointer)... If you're curious about them, take a look at this: [http://cplus.about.com/od/learning1/ss/references.htm](http://cplus.about.com/od/learning1/ss/references.htm)

Thanks alot!;)

---


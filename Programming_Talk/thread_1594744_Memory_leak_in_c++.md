---
title: "Memory leak in c++"
date: 2010-10-12
forum: Programming Talk
---

### Post by fasoulas on 2010-10-12
I think i have a memory leak in this code and i need your help
In the increaseby function i copy the contents of the old array to the new one and return the pointer to the new array.
Will the contents of the old array stay in the heap?? 

```
#include <iostream>

using namespace std;

//finds array average
double find_avg(int* arr,int size);

//increase the size of the array
int* increaseBy(int* a,int size,int inc);

void main()
{
    //variables
    int size;

    //array size
    cout << "Enter array size : ";
    cin >> size;
    
    //allocate mamory for new array
    int* arr = new int[size];
    
    //enter values
    cout << "Enter values: ";
    for(int i=0;i<size;i++)
        cin >> arr[i];
    
    
    ///////////////////////////////////////
    
    int new_size;

    cout << "\nEnter new size: ";
    cin >> new_size;

    arr = increaseBy(arr,size,new_size);

    ///////////////////////////////////////

    //deallocate memory
    delete[] arr;

    system("pause");
}

//increase the size of the array
int* increaseBy(int* a,int size,int inc)
{
    //allocate mamory for new array
    int *p =new int[size+inc];
    
    //copy values from old array
    for(int i=0;i<size;i++)
        p[i]=a[i];

    //deallocate old memory
    delete[] a;

    //return new array location
    return p;
}
```

I know that this could be implemented with vectors but i do just to have a better understanding of pointers

---

### Post by ibuclaw on 2010-10-12
You can check for memory leaks using valgrind.

I also see this program is written for Windows? system("pause") is yucky and should be avoided. And having a 'void main()' function is illegal...

edit:
To answer your question though, I can't see there being any leaks are possible in your small program.

Regards

---

### Post by GeneralZod on 2010-10-12
```

    int *p =new int(size+inc);

```

Read this line very carefully - character by character :) Can you spot the mistake? (It's a very common one :))

---

### Post by fasoulas on 2010-10-12
> **GeneralZod said:**
> ```

    int *p =new int(size+inc);

```

Read this line very carefully - character by character :) Can you spot the mistake? (It's a very common one :))

i don't see a mistake here maybe you can help me.I am doing this to increase the size of the array.Basically create a new array with all the elements from the old one.

But i think that the old array elements just stay in the memory(heap) and i just change the value of the pointer that points to them,by making it point to the new place in memory that i allocated.

---

### Post by GeneralZod on 2010-10-12
Hint: compare it to this line:

```

    int* arr = new int[size];

```

(Brackets :))

---

### Post by fasoulas on 2010-10-12
> **ibuclaw said:**
> You can check for memory leaks using valgrind.

I also see this program is written for Windows? system("pause") is yucky and should be avoided. And having a 'void main()' function is illegal...

edit:
To answer your question though, I can't see there being any leaks are possible in your small program.

Regards

Yes this is a program that runs on windows (unfortunately).
Why is it illegal to use void main()?

---

### Post by dwhitney67 on 2010-10-12
> **fasoulas said:**
> i don't see a mistake here ...
Did you read the line "very carefully", or did you do a quick glance at it and deemed it to be correct?

---

### Post by fasoulas on 2010-10-12
> **GeneralZod said:**
> Hint: compare it to this line:

```

    int* arr = new int[size];

```

(Brackets :))

:mad: You are right,i haven't noticed it.

This program compiles and runs normally on visual studio and windows,is it a mistake in expression or i do something else without knowing it?

---

### Post by lisati on 2010-10-12
> **fasoulas said:**
> Why is it illegal to use void main()?
It's a style thing.
[LIST=1]
[*]It's "good form" to be able to return something to the OS that indicates success or otherwise of the program
[*]If you're not going to use argc & argv, it's also "good form" to use "void" for the arguments for main.
[/LIST]

---

### Post by dwhitney67 on 2010-10-12
> **fasoulas said:**
> :mad: You are right,i haven't noticed it.

This program compiles and runs normally on visual studio and windows,is it a mistake in expression or i do something else without knowing it?
Yes... you did something else without knowing it.  You allocated a _single_ int object and initialized it (by calling the int constructor) to the value equal to size + inc.

Btw, think about your program... what are the ramifications if one should type in a size of -1 or even -100?  Ditto for the incremental value.  Consider adding the checks in your code to ensure that bogus values are not inputted by the user.

---

### Post by fasoulas on 2010-10-12
> **dwhitney67 said:**
> Yes... you did something else without knowing it.  You allocated a _single_ int object and initialized it (by calling the int constructor) to the value equal to size + inc.

Btw, think about your program... what are the ramifications if one should type in a size of -1 or even -100?  Ditto for the incremental value.  Consider adding the checks in your code to ensure that bogus values are not inputted by the user.

thanks a lot for the information about my mistake.

---


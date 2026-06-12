---
title: "Array as parameter to function? (C++)"
date: 2007-04-16
forum: Programming Talk
---

### Post by ibanezix on 2007-04-16
Is it possible to pass an array as a parameter to a function in C++? 

I went through some books that I have on C++ but I did not find an explicit answer, and from some experiments I have done with gcc, it seems that it is not possible. for example this code:

```

#include <iostream>
using namespace std;

void duplicate ( int& array1[10] ) {
for ( int i=0; i<10; i++) {
array1[i] = array[i] * 2;
}
}

int main () {

int array1[10] = {1,2,3,4,5,6,7,8,9,10};

duplicate (array[10]);

}

```

produces errors. If it is not possible, how would I manipulate an array that is not local to a function, from inside that function?

---

### Post by thelinuxguy on 2007-04-16
> **ibanezix said:**
> how would I manipulate an array that is not local to a function, from inside that function?

Try this:
```

#include <iostream>
using namespace std;

void duplicate (int array[]) {
[INDENT]for ( int i=0; i<10; i++) {
array[i] = array[i] * 2;
}[/INDENT]
}

int main () {
[INDENT]int array[] = {1,2,3,4,5,6,7,8,9,10};
duplicate (array);[/INDENT]}

```

---

### Post by rbprogrammer on 2007-04-16
> **ibanezix said:**
> Is it possible to pass an array as a parameter to a function in C++? 

I went through some books that I have on C++ but I did not find an explicit answer, and from some experiments I have done with gcc, it seems that it is not possible. for example this code:

```

#include <iostream>
using namespace std;

void duplicate ( int& array1[10] ) {
for ( int i=0; i<10; i++) {
array1[i] = array[i] * 2;
}
}

int main () {

int array1[10] = {1,2,3,4,5,6,7,8,9,10};

duplicate (array[10]);

}

```

produces errors. If it is not possible, how would I manipulate an array that is not local to a function, from inside that function?

your code is alittle off.. i dont know if that was just a typo or not..

not sure if this is something you can use, but i would rather use the pointer notation than array notation.  arrays are pointers, but pointer notation is in my opinion more flexible.

```
#include <iostream>
using namespace std;

void duplicate ( int* array1, int size )
{
    for ( int i=0; i<size; i++) 
    {
        array1[i] = array1[i] * 2;
    }
}
void printArray( int* array1, int size)
{
    for ( int i=0; i<size; i++) 
    {
        cout << array1[i] << endl;
    }
}

int main () 
{
    const int size = 10;
    int array1[size] = {1,2,3,4,5,6,7,8,9,10};

    printArray(array1,size);
    duplicate (array1,size);
    cout << endl;
    printArray(array1,size);

}
```

---

### Post by IronAvatar on 2007-04-16
> **rbprogrammer said:**
> not sure if this is something you can use, but i would rather use the pointer notation than array notation.  arrays are pointers, but pointer notation is in my opinion more flexible.


The problem with using pointers like this in C++ is that some compilers will get confused if you override a function like this.  Consider the following prototypes;

```

void DoSomething(int *lpanArray, unsigned int lauSize);
void DoSomething(unsigned int *lpauArray, unsigned int lauSize);

void DoSomething(short *lpanArray, unsigned int lauSize);
void DoSomething(unsigned short *lpauArray, unsigned int lauSize);

```

Now if you were to call one of them, you would likely get an error as to which function the compiler should use.  You would have to cast the array parameter to ensure that the compiler doesn't barf (I don't know about you, but I think castng is ugly and leads to error prone code).

It would be better to use something like the following to avoid this problem.

```

void DoSomething(int lanArray[], unsigned int lauSize);
void DoSomething(unsigned int lauArray[], unsigned int lauSize);

void DoSomething(short lanArray[], unsigned int lauSize);
void DoSomething(unsigned short lauArray[], unsigned int lauSize);

```

---

### Post by ibanezix on 2007-04-16
thelinuxguy's code works.

rbprogrammer, I am learning C++ now, so it would be helpful to explain what you mean by "code is a little off"

There is something I don't understand in these examples, and it's part of what I was doing wrong before: how come the function changes the data in the original array? I thought that only happens when you pass parameters by referense, hence the int& in:

```
int duplicate ( int**&** array[10] )
```

If I am not explicitely asking it to **return** the new values, nor am I passing by reference, why does the function change a variable ( the array ) that is not local to it?

---

### Post by Tuna-Fish on 2007-04-16
the "array" in "int array[]" IS an address, to the first element of the array. &array asks for the address of address. I think.

---

### Post by thelinuxguy on 2007-04-16
> **ibanezix said:**
> 
If I am not explicitely asking it to **return** the new values, nor am I passing by reference, why does the function change a variable ( the array ) that is not local to it?

Arrays are always passed by reference since the array name can be regarded as a pointer (but one which cannot be made to point anywhere else).
So 
```

void duplicate (int array[]) 
and 
void duplicate(int *array)

```
are essentially equivalent. But I would use the array notation as in the first one to keep things clear.
Besides, you can use a pointer as an array by ensuring that sufficient memory is allocated to it.
Example:
```

int *ptr;
ptr = new int[10];
cin>>ptr[0];

```
ptr above is a pointer but can be used like an array because memory for 10 integers has been allocated and ptr points to the start of this range. When using pointers as arrays by using the 'new' keyword, care should be taken to ensure that the memory is released after use. Since ptr above is used to access a range of integer values rather than a single int, release the memory by using
```

delete[] ptr;

```
and not just
```

delete ptr;

```

I hope this explanation is helpful.

---

### Post by rbprogrammer on 2007-04-16
> **ibanezix said:**
> 
rbprogrammer, I am learning C++ now, so it would be helpful to explain what you mean by "code is a little off"


sorry about that, when i said the "code is a little off", i just mean that you used a variable that does not exist.  i assume it was just a typing mistake, but you did it twice, so i thought i might mention it.

ie:
```

#include <iostream>
using namespace std;

void duplicate ( int& array1[10] ) {
for ( int i=0; i<10; i++) {
array1[i] = **array**[i] * 2;       //where is array?
}
}

int main () {
int array1[10] = {1,2,3,4,5,6,7,8,9,10};
duplicate (**array**[10]);         //again, you mentioned it
}

```

sorry again about that, i didnt mean for it to come out as some programming lingo..

---

### Post by baltimark on 2007-04-16
> **ibanezix said:**
> thelinuxguy's code works.

rbprogrammer, I am learning C++ now, so it would be helpful to explain what you mean by "code is a little off"

There is something I don't understand in these examples, and it's part of what I was doing wrong before: how come the function changes the data in the original array? I thought that only happens when you pass parameters by referense, hence the int& in:

```
int duplicate ( int**&** array[10] )
```

If I am not explicitely asking it to **return** the new values, nor am I passing by reference, why does the function change a variable ( the array ) that is not local to it?
Because you're passing a memory address, and then modifying the things IN that chunk of memory. You have changed the things in the original memory locations. 

But, first of all, keep in mind that the syntax

```

int array[10]
```

means you're creating an array of 10 ints. You're writing
```
 int& array[10]
``` an array of 10 references! 

Now, back to what seems to be confusing you a little. I'll try to explain this without syntax. 

You can do a few things in C++:

1) Pass a value. This just passes a value to the function. You will create a new memory location, and put a value in it. You can modify that anyway you want, and it won't modify the thing you sent in. You passed in the VALUE of thing at memory location 'a'. The program created memory location 'b' and put the same value in there. You can't mess up location 'a'. Prototyped like foo(int x)

2) Pass a pointer. This time you actually passed the memory location. If you modify the thing in that memory location then when you return from the function the original thing will be modified. Prototyped like foo(int *x). You need to call with foo(&v)

3) Pass a reference. For now, just think of this as a way of passing a pointer with easier to follow syntax. Prototyped like foo(int& x). You call with foo(v). 

The advantage of passing a pointer is that if it's a pointer to a LARGE object, you just need to pass the pointer -- you don't need to create copies of the whole thing. 

The disadvantage is that you may change something you didn't want to change. 

To tackle both these problems at once, C++ has "pass by constant reference". Syntactically, it's the same as passing by reference, except the compiler will tell you that you can't modify it. Prototyped like foo(const int& x), called with foo(v), and if you try to do   x = 2*x in the function body, the compiler won't let you.

Or, you can use 

```
foo(const int* x)
```. This is probably what you want to do. Or, if you know the length of everything going in, feel free to write

```

foo(const int x[10])

```

Then, if you try to modify x in the function (like you're trying to do), you'll get a compiler error. 

Try to define a function with and without the **const**, and put something in the function like 

```

x[0] = 2*x[0];
```

Only one of the prototypes will allow you do that.

---

### Post by ibanezix on 2007-04-16
> **rbprogrammer said:**
> sorry about that

No need to say sorry, and you didn't come out as any programming lingo. I did make a typing mistake there, thanks for pointing it.

To you and the rest who have answered: thanks! You guys rock! 

I have tried to learn other languages as well, and this conflict always comes up: Learning sources (books, articles, notes, examples, etc) begin by saying the basics on various topics, to get the young programmer starting to produce some real results, and later on, when covering more complicated topics, they come back and look deeper on simple topics such as input/output, loops, and in this case the nature of arrays as pointers. 

The learner on the other hand, tries to apply whatever level of knowledge he has achieved by some time, but often the tasks that he sets to himself exceed that knowledge, and only when he learns even more, he can go back and complete his task.

Anyway, back to coding, and thanks again!

---

### Post by Wybiral on 2007-04-16
Arrays are pointers... That's all you really need to know. Just like you would pass a character array with "const char* str", you pass an int array.

---


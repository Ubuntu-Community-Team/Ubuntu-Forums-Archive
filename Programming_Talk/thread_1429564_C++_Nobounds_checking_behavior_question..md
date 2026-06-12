---
title: "C++ Nobounds checking behavior question."
date: 2010-03-14
forum: Programming Talk
---

### Post by Jonas thomas on 2010-03-14
Ok... So.. I'm compiling up all the text book examples and I run across a behaviour that has got me a bit stumped.

The example is to show how there is no bounds checking is done in C++ and how you might inadvertently crash.... Well.... I don't have a microsoft compiler in front of me at the moment, so I don't now what would happen there, but in Linux the result is not at all what I expected.

Anyway... Here the code:
(Ref. Starting out with C++ from Control Structures through Objects sixth edition, Author Tony Gaddis Program 7-5)
```

// This program unsafely accesses an area of memory by writing
// values beyond an array's boundary.
// WARNING: If you compile and run this program, it could crash.
#include <iostream>
using namespace std;

int main()
{
   const int SIZE = 3;  // Constant for the array size
   int values[SIZE];    // An array of 3 integers
   int count;           // Loop counter variable

   // Attempt to store five numbers in the three-element array.
   cout << "I will store 5 numbers in a 3 element array!\n";
   for (count = 0; count < 5; count++)
      values[count] = 100;

   // If the program is still running, display the numbers.
   cout << "If you see this message, it means the program\n";
   cout << "has not crashed! Here are the numbers:\n";
   for (count = 0; count < 5; count++)
      cout << values[count] << endl;
   return 0;
}

```

Here is the output that I consistently get whether running within the codelite IDE or directly from the terminal prompt.
> 
jonas@jonas5:~$ cd .codelite/CppClass/Chapter7/SampleCode/Pr7-05/Debug
[email]jonas@jonas5:~/.codeli[/email]te/CppClass/Chapter7/SampleCode/Pr7-05/Debug$ ./Pr7-05I will store 5 numbers in a 3 element array!
If you see this message, it means the program
has not crashed! Here are the numbers:
100
100
100
3
3
[email]jonas@jonas5:~/.codeli[/email]te/CppClass/Chapter7/SampleCode/Pr7-05/Debug$ 


So... I know this is not supposed to be done, so what you get might not be what you expect.. But does this make sense to anyone why array elements 3,4 consistently return 3 instead of the 100 that I was expecting.
I must have run this program 20 times, expecting something weird to happen. Never got the program to crash and as near as I can tell, all looks normal..

 Was I just lucky or is there something going on under the hood in Linux that is different from MS?

---

### Post by MadCow108 on 2010-03-14
you here have a stack overflow
the stack is not checked very thoroughly for violations so the program will not always crash. It depends on what your overwriting and how that is used.
Nevertheless it is of course a serious bug to go out of bounds.
Using a memory checking program like valgrind can tell you if a stack overflow occured.

you can increase the crash probability of crash by increasing amount of data on the stack you overwrite.

Also you can increase it by using heap memory by allocating with new.
The heap is more delicate to overwriting as it puts management information near the allocated block which must not be tampered with.
Also on heap the kernel aborts the process if it tries to access memory which does not belong to it (segmentation violation).

---

### Post by Dromedar on 2010-03-14
> **MadCow108 said:**
> you here have a stack overflow
the stack is not checked very thoroughly for violations so the program will not always crash. It depends on what your overwriting and how that is used.
Nevertheless it is of course a serious bug to go out of bounds.
Using a memory checking program like valgrind can tell you if a stack overflow occured.

you can increase the crash probability of crash by increasing amount of data on the stack you overwrite.

Also you can increase it by using heap memory by allocating with new.
The heap is more delicate to overwriting as it puts management information near the allocated block which must not be tampered with.
Also on heap the kernel aborts the process if it tries to access memory which does not belong to it (segmentation violation).

I just wodnder why the example does not write back 5x100 ? Can someone explain why 3 and 3 is written? what would program write if SIZE = 10 and for loop would go 0 to 12?

I know that Microsoft Visual Studio adds boudnary check bytes before and after data being reserved (only in debug mode). So wery likely runtime routines would notice overflow but after the method is being executed. Don't know if there is samy method being used in linux c++ compilers.

I think if you write more, say 10 instead of 5. The program will crash. Ofcause it depends on how compiler builds stack.

---

### Post by Jonas thomas on 2010-03-14
My 7 year old wants me to watch her play computer games...
So... I need to read up on this a little later...
I was looking at this:
[http://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap]("http://stackoverflow.com/questions/79923/what-and-where-are-the-stack-and-heap")
[http://en.wikipedia.org/wiki/Valgrind](http://en.wikipedia.org/wiki/Valgrind)

Yikes...
Even more stuff to understand...
[http://en.wikipedia.org/wiki/Stack_buffer_overflow]("http://en.wikipedia.org/wiki/Stack_buffer_overflow")

---

### Post by Jonas thomas on 2010-03-14
> **MadCow108 said:**
> you here have a stack overflow
the stack is not checked very thoroughly for violations so the program will not always crash. It depends on what your overwriting and how that is used.
Nevertheless it is of course a serious bug to go out of bounds.
Using a memory checking program like valgrind can tell you if a stack overflow occured.

you can increase the crash probability of crash by increasing amount of data on the stack you overwrite.

Also you can increase it by using heap memory by allocating with new.
The heap is more delicate to overwriting as it puts management information near the allocated block which must not be tampered with.
Also on heap the kernel aborts the process if it tries to access memory which does not belong to it (segmentation violation).

I was sorting looking for a short video explaning heap vs.. memory management.
I seaching for videos I googled "c++ stack heap" and this was one of the
videos that popped up.
[http://www.youtube.com/watch?v=Ps8jOj7diA0]("http://www.youtube.com/watch?v=Ps8jOj7diA0")
Basically it's a standford lecture series on programming paradigms.. It didn't really answer my question but darn.. is this interest interesting. Curse this internet... Too much interesting stuff... Too little time..
Wonder how hard it would be to burn this to an audio cd and listen to it in the car on the way to work...

---


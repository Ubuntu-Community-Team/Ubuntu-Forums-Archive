---
title: "C pass by value (i think)"
date: 2008-05-18
forum: Programming Talk
---

### Post by thefestival on 2008-05-18
```
 #include <stdio.h>
  2 
  3 int addNumber(int x, int y);
  4 
  5 int main(void) {
  6         int a, b;
  7         
  8         printf("Enter two numbers to add: ");
  9         scanf("%d, %d", &a, &b);
 10         
 11         printf("%d plus %d equals %d\n", a, b, addNumber(a, b));
 12         
 13         return 0;
 14 }       
 15 
 16 int addNumber(int x, int y) {
 17         int z = x + y;
 18         
 19         return z;
 20 }       

```

First off like I said I think this is pass by value. It compiles but when I enter two numbers lets say 2 and 2, it spits out 2 plus 1345137533 equals 134513735.  Can someone tell me what's wrong with my code?   

One thing that so far I have not been able to wrap my head around is pass by value/reference. Anyone come across a particular good tutorial or example of it?

Thanks.

---

### Post by CptPicard on 2008-05-18
It's the comma in your input string. It expects format "1, 2" and not "1 2" :)

Pass by value is simply a copy onto the stack of the value itself. Because inside the function you have a copy, you can't alter the value -- what you see is a copy. Pass by reference copies a pointer to the value to the stack, so that you can actually alter the memory location where the value is stored inside the function you're passing to.

---

### Post by bite on 2008-05-18
The program is correct, I think the problem is in how you write the input. Given the format string "%d, %d" you should type eg
```
2, 3
```
while you probably type
```
2 3
```
scanf doesn't match the comma and the second number remains unassigned.

---

### Post by bite on 2008-05-18
Here is your code rewritten passing arguments by pointers:
```
#include <stdio.h>
  
  int addNumber(int * x, int * y);
  
  int main(void) {
          int a, b;
          
          printf("Enter two numbers to add: ");
          scanf("%d, %d", &a, &b);
         
          printf("%d plus %d equals %d\n", a, b, addNumber(&a, &b));
          
          return 0;
  }       
  
  int addNumber(int * x, int * y) {
          int z = *x + *y;
          
          return z;
  }
```

Usually the term "pass by reference" is reserved for a third way of passing  arguments which is not available in c but in c++. Here is your code rewritten passing arguments by reference (compile it with g++, not gcc):
```
#include <stdio.h>
  
  void addNumber(int & x, int & y, int & result);
  
  int main(void) {
          int a, b;
          
          printf("Enter two numbers to add: ");
          scanf("%d, %d", &a, &b);
          int res;
					addNumber (a, b, res);
          printf("%d plus %d equals %d\n", a, b, res);
          
          return 0;
  }       
  
  void addNumber(int & x, int & y, int & result) {
          result = x + y;
  }
```

I made the result an argument to show that when passed by reference arguments can be modified, exactly as when passed by pointer.

You have the advantage that you don't need to dereference the pointer, as was instead in the previous example.

---

### Post by Can+~ on 2008-05-18
By value: Passed the value of a variable to another, it's like person A is holding a document, and it hands a copy to person B inside the function.
[PHP]int add(int a, int b)
{
	return a + b;
}

int main(int argc, char **argv)
{
	int x=2, z;
	
	z = add(x,5);
	return 0;
}[/PHP]
(x will stay as 2, z will be 7)

By reference: Passes the position of the variable to another, now person A tells B to go grab the document at your desk.
[PHP]void add(int *a, int *b)
{
	*a += *b;
}

int main(int argc, char **argv)
{
	int x=2, y=3;
	
	add(&x, &y);
	return 0;
}[/PHP]
(In this lastest example, x now will be 5, "y" will keep as 3)

---

### Post by rplantz on 2008-05-18
Pass by pointer and pass by reference are language issues that end up doing the same thing --- passing the address of the variable to the function.

In C++:
```

#include <stdio.h>
void by_reference (int &w, int &x)
{
   w = 12;
   x = 34;
}
void by_pointer (int *y, int *z)
{
   *y = 56;
   *z = 78;
}
int main()
{
   int a, b, c, d;
   by_reference(a, b);
   by_pointer(&c, &d);
   printf("%i %i %i %i\n", a, b, c, d);
   return 0;
}

```
displays
```

12 34 56 78

```

C will not allow the pass by reference syntax.

Coming from C, when I learned C++ I did not like pass by reference because it's not so obvious when you're reading the calling function's code.

Those who started with C++ find passing by pointer confusing.

My recommendation is that you learn both techniques and understand that at the machine level, they are doing the same thing --- passing the address of the variable.

---

### Post by grepgav on 2008-05-20
What you are doing is passing by value, and standard c can technically only pass by value.

What pass by value means is that a copy of the variable contents is made for specific use in that function. This means any changes made to that variable inside the function only affect that local copy, and not the variable which was passed to it.

C can simulate passing by reference by passing the value of the memory address of the variable in question. That is what the pointer is for. It acts as a value, so a copy of the address is made and then inside the function you can follow the address to the original variable. So for this reason, if you use the simulated pass by reference you can make changes to a variable inside a function that will affect the variable that was passed into the function.

---

### Post by CptPicard on 2008-05-20
> **grepgav said:**
> What you are doing is passing by value, and standard c can technically only pass by value.

Technically, so do all stack machine architectures. Stack has "only" values, and values can be addresses of values. C++'s reference passing is just a syntactic sugar on top of that, it's the same pointer-value-passing stuff under the hood. Even in Java, references to objects are copies-of-values inside your method -- you can make the parameter value point to some other object.

---

### Post by PandaGoat on 2008-05-21
I may repeat what others have said, but I am concerned with the inadequacy of what has been said.  My concerns are, of course, to my current knowledge, so correct me if I am wrong.

The aforementioned problem with input is, indeed, the only problem I see; my main concern is with the descriptions of passing by *value* and passing by *reference*.

Passing by value is what you are doing.  You pass the value of the variable into the function--*a copy of what you pass will be in the scope of the function*.

 First off let me respond to "What you are doing is passing by value, and standard c can technically only pass by value."  I do believe this has no merit, and passing by reference actually tends to be an essential part to standard c, although correct me if I am wrong.  You are right in that you cannot declare an argument like this: 'int& i' in c.  But doing 'int* i' is still considered passing by reference. 

I believe I am going to repeat someone here but for more clarity:  passing by reference simply passes the reference of a variable.  In the function we can use the reference to edit the variable with that reference by making a pointer point to it.  Making a pointer point to the reference is "automatically" done though by how we declare our arguments of the function (as pointers).  And when we call these functions we pass to them &variable.  Here is an example (probably already one like this):
[PHP]
/* takes two values ('a' and 'b') and sets the value of what 'result' points to as their sum */
void add(int a, int b, int* result)
{
    *result = a + b;
}

int main()
{
    int sum = 0;
    add(1, 2, &sum); /* 'sum' is now equal to 3 */
}
[/PHP]

---

### Post by CptPicard on 2008-05-21
> **PandaGoat said:**
> I do believe this has no merit, and passing by reference actually tends to be an essential part to standard c, although correct me if I am wrong.  You are right in that you cannot declare an argument like this: 'int& i' in c.  But doing 'int* i' is still considered passing by reference. 

It really depends on what level of abstraction one wishes to consider "passing by reference" -- posters here speak of it in slightly different terms, and it may be confusing to the OP. :)

At the highest level of abstraction "passing by reference" is just, in implementation-independent terms, the practice of passing something that "refers" to a variable, and through which the variable can be accessed. Whichever way the language actually implements this is of no concern in this POV.

All passing in C (and stack machines in general, can't really think of exceptions) is by value in the sense that the value passed *is* a reference, namely in C, a pointer. C even makes this pretty explicit in syntax. If you wanted to be even more explicit I suppose you could think of passing integers that index an array...

C++'s pass-by-reference is just additional syntactic sugar on top of that. One could take the other POV here and argue that C++ allows "passing by reference" because it's a syntactical feature that hides the pointer and makes the practice of passing a reference a bit nicer.

And then of course there all the languages where passing by reference is the default, but one should bear in mind that even in those languages, there is a stack where essentially you're putting pointers/handles to objects into...

---

### Post by Can+~ on 2008-05-21
Passing by reference is just doing this:

Define a variable:

[FONT="Courier New"]int a = 20;[/FONT]

Block allocated in 0x123456 has data 20. This are the two methods, let's say we have a function which tells us what type of that it has:

**Passing by Value:** integer of value 20.

**Passing by Reference:** an integer allocated in 0x123456, which currently holds the value 20.


Equivalent on more human example:

Nightstand contains car keys on drawer 1 (from top to bottom).

**Passing by Value:** Your car keys.

**Passing by Reference:** That your car keys are inside the drawer 1 of your nightstand.


In essence, what happens is that you just pass the reference of the variable as a **VALUE**, it's not something magical. Therefore, if passing variables by value makes a copy of the value, passing by reference makes a copy of the position where it is. Funny fact, is that you can change the value in the referenced block, but you can't change the reference itself, if you want to change the reference, you'll need a double pointer.

---

### Post by grepgav on 2008-05-21
> **Can+~ said:**
> 

Equivalent on more human example:

Nightstand contains car keys on drawer 1 (from top to bottom).

**Passing by Value:** Your car keys.

**Passing by Reference:** That your car keys are inside the drawer 1 of your nightstand.



But see part of the problem with this analogy is it misses on the KEY point that passing by value creates a localized copy of the variable, whereas passing by reference passes directions to reach the original variable.

---

### Post by rplantz on 2008-05-29
> **CptPicard said:**
> ...there is a stack where essentially you're putting pointers/handles to objects into...

Many of us are used to arguments being passed on the stack. But the ABI for the x86-64 architecture specifies that the first 6 integer arguments are passed in registers, whether they are data or addresses.

---


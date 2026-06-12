---
title: "[c++] pass by address vs. pass by reference"
date: 2006-02-26
forum: Programming Talk
---

### Post by alek on 2006-02-26
Hello all!

I understand this might sound like a very newbie question for all of you but... please bear with me :)

I am interested in the syntactic difference between the following two types of parameter passing
a) pass by address
b) pass by reference

I will first describe my understanding of pass by address, and then ask a question for pass by reference:

Okay, passing by address is straightforward, it is logical and is a pure application of pointers.
So, when we declare a function, we have
void exampleFunction (int *para);

but when we actually pass an argument, say, in main function, we say
{
...
int arg = 6;
exampleFunction (&arg);
...
}
This basically relies on the property that, if the function parameter is a pointer (int *para), when we pass an argument to it, we have to pass a memory address (pointer), and so we pass &arg.
Equivalent in saying: para = &arg;
and then we do whatever we wanted to do in our function.
Like, in order to change the value of arg, we would say:
*para = 500; 

NOW, MY QUESTION IS THE FOLLOWING:
when we do the pass by reference (which provides the same effect as the pass by address), we seem to ignore, or, even worse, violate the syntactic meanings surrounding pointers.
In the book that I am using, it says that ampersand operator "'&" returns the memory address of a variable, or, in other words, returns a POINTER to that variable.

How does this make sense, then:

void exampleFunctionTwo(int &paraTwo);

and then in main we use it as:
...
int argTwo = 10;
exampleFunctionTwo(argTwo);
...

I mean... &paraTwo returns the address of the variable paraTwo... but then, what we are saying is:
&paraTwo = argTwo; //the process of actually passing it

so, how can we assign an INTEGER VARIABLE to ADDRESS of another INTEGER VARIABLE?
in other words, if &a returns a pointer to a, then, how can we assign an INTEGER VARIABLE to a POINTER?

what is even worse, when we manipulate paraTwo in the body of the function, we use it as a regular variable, totally ignoring the fact that it is a pointer to a variable... using the same example like the one above, if I wanted to change the value of argTwo, rather than typing:
*paraTwo = 500;
we type:
paraTwo = 500;
instead.

I... I am CONFUSED... I get the pointers, and I perfectly see the validity in passing by address, from the syntactical view of pointers...
but... pass by reference, simply does not make sense...

Thanks,
Alek

---

### Post by LordHunter317 on 2006-02-26
> **alek]I am interested in the syntactic difference between the following two types of parameter passing
a) pass by address[/quote]Strictly speaking, there is no such thing.  You can either pass by value, or pass by reference.

When you pass a pointer, you pass it's value.  The value of the pointer is the address of another variable.  This is effectively pass-by-address to you, but the difference is that if C++ supported pass-by-address, it would create the pointer automatically.  IOW, you wouldn't have to say:```
int var said:**
> NOW, MY QUESTION IS THE FOLLOWING:
when we do the pass by reference (which provides the same effect as the pass by address),No, it doesn't.  It's completely different.  Consider this code:```
#include <iostream>
void foo(int *a, int *b)
{
     a = b;  // This changes the address a points to, and results no change in        
               // the variable it points to.
}

void bar(int& a, int &b)
{
    a = b; // This changes the value of whatever 'a' refers to the value of
             // whatever 'b' refers to.
}

int main()
{ 
   int a=2;
   int b=3;

   foo(&a, &b);
   std::cout << a << b << std::endl;

   bar(a, b);
   std::cout << a << b << std::endl;
}
```

> we seem to ignore, or, even worse, violate the syntactic meanings surrounding pointers.Right, because references aren't pointers.  They don't share anything in common, beyond that I can use them as a stand-in, if necessary.

A pointer is a variable holding the address of another variable.  It follows all the normal rules of a variable: I can change it's value (without changing whatever it points to), I pass it by value, etc.

A reference is an alias of a variable.  I'm essentially giving the variable another name (and scope, potentially).  Whatever modifications are made to the references are always made to whatever variable it refers to.  It's impossible to change the reference once it's created.  For example, given:```
int a = 2; 
int& b = a;
```Whatever I do to b happens to a.  If I say:```
b = 3
```Then I've really assigned that value to 'a'.   Whereas if 'b' were a pointer above, I just made it point to address 3.

That's the difference, and it's an important one.  Pass-by-reference gives a safe way to increase the mutable scope of an object (i.e., the amount of code that can change a variable) without opening ourselves up to dangerous or even potentially wrong behaviors.

> In the book that I am using, it says that ampersand operator "'&" returns the memory address of a variable, or, in other words, returns a POINTER to that variable.Correct.

> How does this make sense, then:

void exampleFunctionTwo(int &paraTwo);

and then in main we use it as:
...
int argTwo = 10;
exampleFunctionTwo(argTwo);
...
Because '&' has a totally different meaning in that context.  When you declare a variable or a parameter, '&' makes it a reference, just like '*' makes it a pointer.  This is a common complaint about C++: the orthogonality of the language is low and many things have multiple meanings.  This is one of them.  That and it reeks of declartion mimics usage (although it actually doesn't, it is in the same style).

**This is, FWIW, I think your key misconception.**  '&' means one thing when dealing with a variable, and other with it's declaration.

> what is even worse, when we manipulate paraTwo in the body of the function, we use it as a regular variable, totally ignoring the fact that it is a pointer to a variable...It's not though, it's a reference.  Completely different thing.

---

### Post by Lux Perpetua on 2006-02-26
It is confusing. You have hit on two *completely distinct* meanings of the ampersand `&' in C++. (Actually, there are more, but the others don't cause as much confusion.) When used to modify a *declaration*, such as: 
```
int b;
int & a(b); // now b is a reference to a
```the `int &' declares `a' to be a new reference to the already existing integer `b'. We refer to `a' just as we would normal integer variables (without requiring a pointer dereference). 
```
int myfunction(int & a);
```means that when call `myfunction' with an argument `someinteger', the `a' that the function uses in its body will not simply be an integer initialized to the value of `someinteger', but will instead be initialized to a new reference to `someinteger'. 

The (unary) ampersand operator used in an expression, on the other hand, means "give me the memory address of this object." ```
int a; 
int *p = &a; // now p is a pointer to a
```In this example, it is just an operator being applied to the variable `a', not a modifier for the declaration of p. 

In practice, the context always makes clear which meaning the ampersand has in any given situation.

---

### Post by vbmaster on 2006-02-26
Nice answers guys, i'm learning alone c++ and i'm right on that chapter... 

My book is a bit confusing but I already had understood that concepts..

Just a thing... I'm getting used to pass-by reference but what's the real advantages in make a thing like this:

```

#include <iostream>
using namespace std;

int plus (int& x , int& y) {
int result = x +y;
cout << result << endl;
return 0;}

int main () {
int a = 5;
int b = 6;
plus(a,b);
return 0; }

```

Basides a thing like this:

```

#include <iostream>
using namespace std;

int plus (int x , int y) {
int result = x + y;
cout << result << endl;
return 0;}

int main () {
int a = 5;
int b = 6;
plus(a,b);
return 0; }

```



I mean, is the memory advantage of the first example in the fact that a reference is just a link?

---

### Post by alek on 2006-02-26
Thank you guys SO MUCH! :D :D  :D

I get it now! I thought that the ampersand only has one meaning, and therefore was trying to explain everything in terms of pointers, not realizing that it can be used in another way, to make an alias of a variable.
I just assumed that passing by reference as provided in C++ automatically created a pointer to a variable... but what you said makes perfect sense.
I was ignorant of the fact that there actually was a different way to reference a variable, other than making a pointer that points to that variable.

You've made my day,
Alek

---

### Post by LordHunter317 on 2006-02-26
[QUOTE=vbmaster]I mean, is the memory advantage of the first example in the fact that a reference is just a link?[/QUOTE]In that case, the advantage is nothing.  The real advantage is when you're dealing with say, a vector of 1000 items.  Passing by value would require passing a completely new vector.  This involves creating the vector and copying the 1000 items.  This takes both time and space.

By passing a reference to the vector, you pass neither.

---

### Post by vbmaster on 2006-02-26
Oh... i see... thank you very much... ;)

---

### Post by Lux Perpetua on 2006-02-26
That's not the best example. The advantage comes when you (a) want a function to modify one of its arguments, or (b) have a function that operates on large objects, in which case passing by reference saves having to copy those objects.

---


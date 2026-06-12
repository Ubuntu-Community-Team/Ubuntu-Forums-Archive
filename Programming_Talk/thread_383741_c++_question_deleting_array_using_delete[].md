---
title: "c++ question: deleting array using delete[]"
date: 2007-03-13
forum: Programming Talk
---

### Post by Greykrrr on 2007-03-13
Hi

I'm having a problem in my program when I invoke the destructor of a class when I have assigned a char array address to a pointer.

In the constructor it looks like this:
foo = new char[3];
foo = "^!";

followed by the destructor:
delete[] foo;

and the decleration:
char* foo;

When I exit my program (and invoking the destructor) I get this message:
*** glibc detected *** free(): invalid pointer: 0x0000000000406484 ***

if I comment out the destructor, it exits fine but I believe I would then have a memory leak. Am I wrong to assume this? Or what else could the problem be?

---

### Post by WW on 2007-03-13
When you say
>  foo = "^!";
you have *reassigned* the pointer foo to point to a new location in memory, where the character array "^!" is stored. You have not copied "^!" to the memory that was allocated by the **new** command.

---

### Post by lnostdal on 2007-03-13
.. go grab your nearest bestest C or C++ programming book and try again ;)  spend some time checking out reviews on accu.org and amazon.com

```

foo = new char[3]; // foo now points to some allocated memory
foo = "^!"; // foo now points to a string literal (not the memory you allocated above!)
..
delete[] foo; // here you are _not_ freeing the memory returned by `new' .. you're trying to free "^!" .. 

```

..and the memory returned from `new' is now considered a leak, yes

take a step back and ask yourself why you are using char* instead of std::string in C++

if you insist on using char* you should use strncpy to copy the given string into the allocated memory

---

### Post by Wybiral on 2007-03-13
While this is nice and educational and all... One of the biggest perks about C++ is that you can forget about all of that picky malloc/free style of dealing with dynamic memory (*most* of the time... There are certainly exceptions, but usually...)

Why not use a string?

```

#include <string>

... Stuff here ...

string foo;
foo = "^!";


```

No need to free the memory at all.

I would say to only resort to using new/delete when you have to (like when speed is an issue).

And if you need it to be in C string format (a char array) just use...

```

foo.c_str();

```

EDIT:

I just noticed Inostdal said basically the same thing...
But like I said, that's why you use C++, so you don't have to deal with those low-level C style details.

EDIT AGAIN:

I feel the need to elaborate... Data doesn't just appeal when you run the program, it gets stored in the executable, and when you run your program, it gets loaded into some place in memory.

When you use a string literal in C++, such as "^!", you aren't really putting that value in the array, you are setting a pointer to the address that "^!" was moved to.

Now, if you REALLY wanted to, you could say:

foo[0] = '^';
foo[1] = '!';

Because arrays are just a simplified form of pointer arithmetic. So, foo[1] means "the memory location that the pointer 'foo' is holding, plus (1*(the size of foo's type))... Foo's type is a char, so it's just 1. If you don't believe me, try this:

*(foo) = '^';
*(foo+1) = '!';

But as I said, take advantage of C++ and just use a string.

---

### Post by Greykrrr on 2007-03-14
Hmm... it seems that my initial thought when doing this was flawed. As part of this learning thing I try to optimize my code where I see the possibility for it (to try and avoid sloppy habbits), and my thought with this was that for that particular string I wouldn't need all the fancy stuff that the string class can do. I only need that string to be held in my class as a constant, initialized when the class is created and destroyed with the class at the end of its scope. No modification of it should happen during this process using new seemed like a simple way to accomplish this. Only allocating what I needed. 

Anyway, thanks for the feedback. I have changed the code to use a const string and initializing it with the correct value before the constructor body is entered, like so:

```

Math()
: foo("^!")	{}

private:
const std::string foo;

```

I suppose that this is more c++ like anyway and the extra resources spent are, I think, negliable.

Oh, and I know the thing about *(foo + 1) Wybiral. Pointer arithmetic and iterators are my favorite features of c++ :) It's memory management and controlling streams that confuses me!

And inostdal, trust that I keep Accelerated C++ and C++ for Dummies at my side at all times when I do this. Sometimes they will only tell you so much or the understanding is off, and experimentation is the best way forward :P

And finally... just in case anyone wondered. The code is from a command line calculator (inspired by one of this forums puzzles), and foo is short for 'first order operators'. 

Thanks for your help!

---


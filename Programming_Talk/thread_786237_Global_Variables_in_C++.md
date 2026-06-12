---
title: "Global Variables in C++"
date: 2008-05-07
forum: Programming Talk
---

### Post by PhysicsNerd on 2008-05-07
Hey,

I recently installed Ubuntu mainly for learning programming (as someone advised me it was better for this purpose).  I am currently learning through the book "C++ From The Ground Up, 3rd Edition".  In going through the programs I came across a problem when entering a simple code to demonstrate global variables.

Now I know that people say "global variables bad!" but I can see it being useful instead of having to declare the variable every time.

Here is the code I entered 

> #include <iostream>
using namespace std;

void func1();
void func2();

int count;

int main()
{
  int i;
  
  for (i=0; i<10; i++) {
    count = i * 2;
    func1();
  }

  return 0;
}

void func1()
{
  cout << "count: " << count;
  cout << '\n';
  func2();
}

void func2()
{
  int count;

  for(count=0; count<3; count++) cout << ". ";
}

When I try to compile it I get many errors about the declaration of "count" being vague.

Is there something I need to download for the Ubuntu compiler that will let it recognize a global variable, or did I do something wrong in the code? (I wrote it out word for word from the book, minus the comments)

Thanks.

---

### Post by Wybiral on 2008-05-08
> **PhysicsNerd said:**
> I can see it being useful instead of having to declare the variable every time.

Do you know what function arguments are?

---

### Post by newb1e on 2008-05-08
[http://www.sgi.com/tech/stl/count.html](http://www.sgi.com/tech/stl/count.html)

Just change the name of the variable "count"

---

### Post by pedro_orange on 2008-05-08
You have declared "count" as a variable identifier twice.
Once in the top section, and once in the func2() method.
Thats why the compiler is complaining.

Although this is a very small program, and to be honest in small programs its often alot easier just to use globals to make it work, quickly. I would still recommend you don't fall into the habit of using them. As Wybrial said; pass functions parameters.

```


#include <iostream>
using namespace std;

void func1(int l_count);
void func2();

int main()
{
int i;
int l_count=0;

for (i=0; i<10; i++) {
l_count = i * 2;
func1(l_count);
}

return 0;
}

void func1(int l_count)
{
cout << "count: " << l_count;
cout << '\n';
func2();
}

void func2()
{
int m_count;

for(m_count=0; m_count<3; m_count++) cout << ". ";
}
```

Also what is the purpose of this app?
To take a number; times it by 2, print it and then print 3 dots?

```
pedro@pedro-laptop:~$ g++ -Wall -pedantic test.c -o test.o
pedro@pedro-laptop:~$ ./test.o
count: 0
. . . count: 2
. . . count: 4
. . . count: 6
. . . count: 8
. . . count: 10
. . . count: 12
. . . count: 14
. . . count: 16
. . . count: 18
. . . pedro@pedro-laptop:~$ 
pedro@pedro-laptop:~$ 
pedro@pedro-laptop:~$ 
```

---

### Post by pmasiar on 2008-05-08
OP: are you beginner programmer? Python is considered better for beginners, see poll in sticky FAQ

---

### Post by WW on 2008-05-08
Are you guys reading the original post?  It clearly says "In going through the programs I came across a problem when entering a *simple code to demonstrate global variables*" (emphasis mine).

newb1e has already given a solution: just change all occurrences of **count** to some other variable name. Try it, it works.

Other solutions: don't use **using namespace std**, and add the namespace qualifier **std::** in front of **cout**.  Or, in main() and func1(), refer to the global variable as **::count** instead of **count**.

---

### Post by pedro_orange on 2008-05-08
> **WW said:**
> Are you guys reading the original post?  It clearly says "In going through the programs I came across a problem when entering a *simple code to demonstrate global variables*" (emphasis mine).

newb1e has already given a solution: just change all occurrences of **count** to some other variable name. Try it, it works.

Other solutions: don't use **using namespace std**, and add the namespace qualifier **std::** in front of **cout**.  Or, in main() and func1(), refer to the global variable as **::count** instead of **count**.

Pffft. Reading? Totally over rated. 

Thanks for pointing this out.

---

### Post by JupiterV2 on 2008-05-08
Though well beyond the scope of this problem, passing the variable on as a pointer can be equally useful:

[php]
#include <iostream>

using std::cout; /* for clarity */
using std::endl; /* for clarity */

/* accepts an integer pointer as an argument and increments the value by
   one by dereferencing it */
void increment(int* num) { (*num)++; }

int main()
{
  int count = 0, x = 0;

  while( x < 5 )
  {
    /* '&' passes the memory address of count to increment function */
    increment(&count); 
    cout << "count = " << count << endl;
    x++;
  }

  return 0;
}[/php]

The output on my machine is:

```

count = 1
count = 2
count = 3
count = 4
count = 5

```

---

### Post by RIchard James13 on 2008-05-08
There is nothing wrong with the code, unless you are using a modern C++ compiler. The book is obviously out of date. The code is a sample program showing that the scope of the global variable does not clash with the local variable. This is no longer the case in C++ hence the errors. If you wrote that code in C it would work but in modern C++ it is wrong because the global scope is enforced in the namespace or something like that.

From: Teach Yourself C++ in 21 Days 2nd Edition (c)1997> "Local variables with the same name as global variables do not change the global variables. A local variable with the same name as a global variable hides the global variable, however. If a function has a variable with the same name as a global variable, the name refers to the local variable -- not the global -- when used within the function"


The book "C++ From The Ground Up, 3rd Edition" is a 2003 book and just as out as date as mine is.

---

### Post by Wybiral on 2008-05-08
> **WW said:**
> Are you guys reading the original post?  It clearly says "In going through the programs I came across a problem when entering a *simple code to demonstrate global variables*" (emphasis mine).

Oh, I'm not even here to answer the question being asked :) I'm here to solve an even bigger problem, namely that this global is unnecessary (and that, indeed, most usage of globals should be discouraged) if you make use of the way functions work... Which is to accept an argument ;)

But I agree with pmasiar, OP should start with something other than C++, especially if they don't understand how functions work yet.

---

### Post by WW on 2008-05-08
> **RIchard James13 said:**
> There is nothing wrong with the code, unless you are using a modern C++ compiler. The book is obviously out of date. The code is a sample program showing that the scope of the global variable does not clash with the local variable. This is no longer the case in C++ hence the errors.

This is not correct.  Here is the original code, but with "count" changed to "joe".  It compiles and runs fine.  If what you said were true, this would give the same errors as when the variable was called "count".
```

#include <iostream>

using namespace std;

void func1();
void func2();

int joe;


int main()
{
    int i;

    for (i = 0; i < 10; i++) {
        joe = i * 2;
        func1();
    }

    return 0;
}

void func1()
{
    cout << "joe: " << joe;
    cout << '\n';
    func2();
}

void func2()
{
    int joe;

    for (joe = 0; joe < 3; joe++) cout << ". ";
}

```

> **RIchard James13 said:**
> 
If you wrote that code in C it would work but in modern C++ it is wrong because the global scope is enforced in the namespace or something like that.

Or something like what?  I don't understand what you are trying to say here.

The original code exposes the std namespace with the line **using namespace std**.  In main() and func1(), **count** is not defined locally, and when the compiler tries to resolve the symbol, it finds two possibilities: the global variable **count** or the function **std::count()**.  Hence the errors.  This is why there are several ways to fix it, including: simply change the name; don't expose the std namespace; or explicitly tell the compiler that you want the global variable **count** by qualifying the symbol as **::count** in main() and func1().

---

### Post by RIchard James13 on 2008-05-08
> **WW said:**
> The original code exposes the std namespace with the line **using namespace std**.  In main() and func1(), **count** is not defined locally, and when the compiler tries to resolve the symbol, it finds two possibilities: the global variable **count** or the function **std::count()**.  Hence the errors.  This is why there are several ways to fix it, including: simply change the name; don't expose the std namespace; or explicitly tell the compiler that you want the global variable **count** by qualifying the symbol as **::count** in main() and func1().

You are right I did not realise that in the std namespace there was a function called count.

---


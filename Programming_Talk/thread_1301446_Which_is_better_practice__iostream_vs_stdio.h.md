---
title: "Which is better practice?  iostream vs stdio.h"
date: 2009-10-26
forum: Programming Talk
---

### Post by dodle on 2009-10-26
Generally I have come across "hello world" tutorials that use the iostream library, but when I was talking about it with my brother who is a C++ programmer, he was not familiar with it.  He told me that he uses stdio.h, or I think he referred to it as standard input/output.  

So I did some looking around and found a "hello world" tutorial using stdio.h and was wondering which would be better for me to practice.  Are there any benefits to using one or the other?

[php]#include <iostream>
using namespace std;

int main()
{
  cout << "Hello World!";
  return 0;
}[/php]
[php]#include <stdio.h>

int main()
{
  printf("Hello World!");
  return 0;
}[/php]

---

### Post by nvteighen on 2009-10-26
It's not about better practice. It's about language. The first one is C++, the second one is C. Of course, the second will compile in a C++ compiler, but it's still C... It'd be the same if I used an Objective-C compiler to compile C.

---

### Post by ad_267 on 2009-10-26
+1 to what nvteighen said.

If you're programming in C++ you should use iostream. If you're programming in C then use stdio.h. Also, in C++ you would include cstdio rather than stio.h.

---

### Post by dodle on 2009-10-26
Thank you both for clarifying that.  So cstdio is C++'s equivalent to C's stdio?  If so, would there be a reason to use cstdio over iostream?  Also, is one better for platform independence; Linux, Windows, Mac?

---

### Post by Tony Flury on 2009-10-26
iostream is supported on all platforms i would have thought.

cstdio gives you access to functions like printf, sscanf etc, which might be easier to get your head around, but you can replicate all of these (as far as I know) with iostream (including reading from strings etc).

Also since iostream uses the C++ operators ">>" & "<<" you can extend that functionality and provide input and output methods for your own classes - something you can't do it you insist on using cstdio - for instance with the right code in your class - this will work :

```

cin >> MyClassInstance
MyClassInstance.doStuff()
cout << MyClassInstance

```
where MyClassInstance is an instance of an object that you have designed etc, and this will allow you to develop customised input/output of your class - you can't do that simply with cstdio.

---

### Post by MadCow108 on 2009-10-26
In wouldn't call your brother a real C++ programmer if he doesn't even know iostreams. C++ is a lot more than just C with classes.

iostreams are standard C++ and are thus supported by all platforms with a reasonably standard compliant compiler.
the cstdio exists basically for legacy code and low level io where streams encapsulate to much details.

They generalize input output and make it a lot safer than C.
Although some basic stuff is a little more syntax with streams they make up for that by greatly enhanced security, easier handling of complex situations, object orientation, support for generic algorithms and less know-by-heart syntax/quirks.

---

### Post by dodle on 2009-10-26
> **MadCow108 said:**
> In wouldn't call your brother a real C++ programmer if he doesn't even know iostreams. C++ is a lot more than just C with classes.

I could be wrong about my brother.  Maybe he is a C programmer.

---

### Post by kayosiii on 2009-10-26
It depends on what your priorities are...

IOStreams are one of the most inefficient parts of C++ (from the perspective of a C programmer)... However they are generally safer to use than their C counterparts.

Which is better will depend a great deal on what you are doing. If you aren't sure you should probably use iostream but be aware of stdio as you are more than likely to come accross them in other peoples code.

---

### Post by MadCow108 on 2009-10-26
if used correctly iostreams are not much slower or even equally fast than the C counterparts for everyday problems.
(I often see people using a second buffer on already buffered streams and such kind of strange stuff, of course this will be slower than C version with a single buffer)

But it depends on the situation you can always write faster problem specific code by going to a lower level. You just lose one of the strength of the higher level implementations, like security, reusability, maintainability etc in that process.

---

### Post by SunSpyda on 2009-10-26
Strictly speaking, I *THINK* the C++ implementation of C's libs, store the functions in the std namespace, so for ISO compliant code, do this -

[PHP]#include <cstdio>
#include <cstdlib>

// This...
using std::printf;
using std::scanf;

// Or this...
// using namespace std;

// Or don't bother, since nearly all compilers will work it out anyway.

// Or prefix std:: to the C function calls.

int
main()
{
    char name_input[80];

    printf("What is your name? - ");
    scanf("%80s", name_input);
    if (name_input[strlen(name_input - 1)] == '\n')
        name_input[strlen(name_input - 1)] = '\0';
    printf("Hi, %s\n", name_input);
    return EXIT_SUCCESS;
}[/PHP]

Feel free to grill me if I'm wrong :p```

```

---


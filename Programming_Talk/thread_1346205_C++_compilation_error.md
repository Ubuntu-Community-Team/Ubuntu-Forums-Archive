---
title: "C++ compilation error"
date: 2009-12-04
forum: Programming Talk
---

### Post by Eragon0605 on 2009-12-04
I have been programming in C++ for about a year now, but it was always under Window$. Today was my first time programming under Ubuntu, and I have run into a serious error. When I try to compile a C++ program with strings in it, I get the messages: 

/home/dck/strings.o      In function 'main':
strings.cpp:(.text+0xe7)        undefined reference to '__sync_fetch_and_add_4'
=== Build finished: 1 errors, 0 warnings ===

Here is the code: 
[php]#include <string>
#include <iostream>

using namespace std;

int main()
{
    string a("Bob the Samurai is Awesome!!!");

    cout << a << endl;

    return 0;
}[/php]I can compile any program that doesn't use strings no problem. I have looked at several tutorials, and I can't see any difference between my code and their code... I am using the Code::Blocks IDE.

---

### Post by MadCow108 on 2009-12-04
what compiler version and distro do you use?
does it also happen if you compile over command line?

this is no coding error, there is probably something wrong with your libraries.

you could try reinstalling/updating the build essentials

---

### Post by A_Fiachra on 2009-12-04
Yep -- that's utterly valid C++ code.

How are you compiling and linking??

---

### Post by endBc on 2009-12-05
```
#include <string>
#include <iostream>

using namespace std;

int main()
{
    string str = "Bob the Samurai is Awesome!";
    cout << str << endl;
    return 0;
}

```

Does this piece of code produce the same output ( error ) ?

---

### Post by Eragon0605 on 2009-12-05
Sorry for not replying sooner, I was messing around with X and ran into some promblems... :)

To endBc, yes, I still get the same error.
  
To A_Fiachra, well, uh, I'm not exactly sure how i'm linking, but I compile by pressing the compile button...

To MadCow108, I am using 9.10 Karmic Koala. As for the compiler version, I know g++ is version 4.4 (maybe 4.4.1), but I don't know about GNU GCC compiler. Code::Blocks doesn't seem to support command-line compiling, or at least requires a special command. Build-essential had some updating to do, but it didn't fix my problem...

---

### Post by Eragon0605 on 2009-12-05
I reinstalled Code::Blocks and... Ta-Dah! It works fine now. 0 warnings and 0 errors. It must have been an issue with the IDE.

---

### Post by lisati on 2009-12-05
Edit (crossed posts): good news that it now works!

---

### Post by dwhitney67 on 2009-12-05
> **Eragon0605 said:**
> 
To A_Fiachra, well, uh, I'm not exactly sure how i'm linking, but I compile by pressing the compile button...

That's rich.

Consider learning what the tool does before making yourself dependent upon it.

---


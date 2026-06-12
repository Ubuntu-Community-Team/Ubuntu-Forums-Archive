---
title: "Help with a simple C++ Program"
date: 2010-01-27
forum: Programming Talk
---

### Post by smdawson on 2010-01-27
I am trying to complete some simple programs for my C++ class. I am trying to run this, but when I do, I get the message 'sh: Syntax error: word unexptected (expecting ")")'
Can someone tell me what I am doing wrong?

```
#include <iostream>
using namespace std;

int main ()
{

    int var1;
    int var2;

    cout << "Please enter the first integer now" << endl; // prompt user for first input
    cin >> var1;     // assigns input to var1

    cout << "Please enter the second integer now " << endl;  // prompt user for second input
    cin >> var2;  // assigns input to var2

    if ( var1 > var2 )
        cout << var1 << " is larger than " << var2 << endl;

    if ( var2 > var1 )
        cout << var2 << " is larger than " << var1 <<endl;

    if ( var1 == var2 )
        cout << "These numbers are equal" <<endl;

    return 0;
}
```

---

### Post by Habbit on 2010-01-27
"sh: Syntax error"? You know you have to *compile* and *link* C++ programs before using them, right?
```
$ g++ my_source.cpp -o my_app
$ ./my_app
```

---

### Post by GregBrannon on 2010-01-27
Just so you know, your code runs fine after after compiling and building.  If it's not working where you are, come back for help getting through those steps.

---

### Post by smdawson on 2010-01-27
Yea, in code::blocks I am hitting "compile" then "build" then "run". In the build log it tells me I compiled it, linked it, and there were 0 errors and 0 warnings after building. But it still comes up with the same error when I run it. I have like 5 programs that I need to turn in, and when I try to run any of them, the same thing happens.

---

### Post by MadCow108 on 2010-01-27
I'm not familiar with code blocks but are you executing what the compiler/linker outputs? you can not execute the sourcecode itself (or the file containing it)
Most IDE's have a windows where the compiling commands are printed, look for the filename behind the -o flag in the last step, this is the created executable. If there is no -o flag, its named a.out (if you are using gcc)

Also if you are learning I greatly recommend to start compiling over the command line to get a better understanding of the process.
After that it also much easier to understand what the IDE does and get it to work.

---

### Post by smdawson on 2010-01-27
Ok, I think I may have been trying to execute the sourcecode itself. I tried to follow your instructions and at some point I got it working. The only thing is, I'm all for compiling over the command line , but I don't know how at this point....(I'm all ears)

---

### Post by samjh on 2010-01-27
You compiled C++ using G++.

```
g++ -o helloworld helloworld.cpp
```

Where:
[list][*]g++ is the compiler.
[*]-o is the option switch to specify the name of resulting file.
[*]helloworld is the name of the file that the compiler should produce.
[*]helloworld.cpp is the source code file to compile.[/list]

---

### Post by nmccrina on 2010-01-27
The short answer:
Suppose you have main.cpp. You can compile it into an executable file called simply 'main' with this command:
```
g++ main.cpp -o main
```

g++ is the compiler program, main.cpp is obviously the name of the file you want to compile, and the '-o' option tells the compiler what you want the final executable to be called. You can also compile more than one file with a single command, and depending on the libraries you use (the standard libraries are all handled automagically by the compiler) you may need to throw in a '-lm' or something. '-lm', by the way, tells the compiler to link your program with the math library. That brings us to...

...the long answer:
[The GCC manual]("http://gcc.gnu.org/onlinedocs/gcc-4.4.3/gcc/")

Edit: ninja'd :P

---

### Post by smdawson on 2010-01-27
Ok. Thanks for the info. I guess you can write it both ways? Cause there are two posted, so I'm assuming that the order of those commands isn't imperative.

---

### Post by nmccrina on 2010-01-27
> **smdawson said:**
> Ok. Thanks for the info. I guess you can write it both ways? Cause there are two posted, so I'm assuming that the order of those commands isn't imperative.

Answer for now: Correct
Answer for a few months from now: Mostly correct, except that when specifying libraries to link with (using the -l option) order DOES matter.

Things are so complicated. :(

---

### Post by smdawson on 2010-01-28
Awesome. If I have more questions, can I just post in here? My homework and tests are open-book//open-internet, and I feel like my c++ class may move kind of fast. My only programming experience was Java 1 last semester, but that class was basically "introduction to java." Then Java II was the "advanced topics". I only had time to take the first class, and my C++ this semester is a one-stop-all-you-need-to-know. Anyway, if anyone is willing, I could continue to use the help. :D

---


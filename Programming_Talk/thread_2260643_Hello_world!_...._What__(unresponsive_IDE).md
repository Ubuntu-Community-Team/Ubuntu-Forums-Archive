---
title: "Hello world! .... What?  (unresponsive IDE)"
date: 2015-01-13
forum: Programming Talk
---

### Post by haplorrhine on 2015-01-13
I've decided to learn some programming, and I shouldn't have any old code files on this computer, let alone a  Hello World file.   Yet no matter what I try to build and run, Code::Blocks returns one of two outputs.

```
Hello world!

Process returned 0 (0x0)   execution time: 0.012 s
Press ENTER to continue.
```

or

```
sh: 1: /home/haplorhine/Desktop/cpp/learningcpp: Permission denied

Process returned 126 (0x7E)  execution time : 0.008 s
Press ENTER to continue.
```

The latter came after a purge and reinstall of Code::Blocks.

---

### Post by Matthew_Harrop on 2015-01-13
Are you running it as a user or super user?

---

### Post by haplorrhine on 2015-01-13
I tried opening codeblocks via "sudo codeblocks" from a terminal, but nothing changed.

---

### Post by QIII on 2015-01-13
Moved to ***Programming Talk***


There is no reason to open the IDE as a super user.  In fact, that might be problematic.

When you created your source, did you save it and build?

Did you take note of the build location?

Can you run your code in debug mode with breakpoints and see what is happening?

---

### Post by haplorrhine on 2015-01-13
I did not take note of this, but this is what the build log says whenever I click "Build", regardless of whether the code has changed or whether it is a new file.

```
Nothing to be done (all items are up-to-date).
```

However the file does update itself when I hit "Build".

What the build log says when I hit "Run".

```
Checking for existence: /home/haplorhine/Desktop/cpp/learncpp
Executing: xterm -T '/home/haplorhine/Desktop/cpp/learncpp' -e /usr/bin/cb_console_runner "/home/haplorhine/Desktop/cpp/learncpp" (in /home/haplorhine/Desktop/cpp)
Process terminated with status 0 (0 minute(s), 5 second(s))
```

- -

I gave the file execute permissions, and now, instead of "permission denied", xterm is telling me:
**syntax error: "(" unexpected**

Here is the code.

```
#include "std_lib_facilities.h"

int main()
{
cout<<"Your frickin name?\n";
string name;
cin>>name;
cout<<"How are you "<<name<<"!\n";
}


```

---

### Post by Matthew_Harrop on 2015-01-13
your main() function has no int return value. 
Add 'return 0;' to the end of that block and try again

---

### Post by haplorrhine on 2015-01-13
Adding statement "return 0;" before the closing squiggly bracket did nothing.

Execute permission is necessary otherwise xterm says "permissions denied", but chmod must be repeated after every rebuild.  What a nuisance!

And I'm still stumped as to why it was returning "Hello world!' before.  The last time I typed a Hello Word code was several reinstallations ago.

---

### Post by steeldriver on 2015-01-13
How did you create your new project in Code::Blocks? if you used the "New project ... Console application" wizard it may have created a boilerplate main.cpp containing a "Hello world!" program. Depending where you put your own source file, it may be ignoring it and simply building the boilerplate.

IMHO IDEs often unnecessarily obfuscate and complicate the build process, especially for learners: my recommendation would be to write your code in a plain text editor and compile it in a terminal

---

### Post by haplorrhine on 2015-01-13
> **steeldriver said:**
> How did you create your new project in Code::Blocks? if you used the "New project ... Console application" wizard it may have created a boilerplate main.cpp containing a "Hello world!" program. Depending where you put your own source file, it may be ignoring it and simply building the boilerplate.

Bingo

> IMHO IDEs often unnecessarily obfuscate and complicate the build process, especially for learners: my recommendation would be to write your code in a plain text editor and compile it in a terminal

Good point.  Manual compilation, linking, and executing will probably give me more insight anyway.

---

### Post by flaymond on 2015-01-14
I'll use text editor instead IDE for learning. Simple but prone to errors (you can get rid of them by enable the syntax highlighting). I'll just use the Vim and learn a plenty of basics to do -or you can try gedit or as your like.The code::blocks is suitable for an experienced developer/programmer, but it take time to learn for a beginner. (Though, I learn the commands to use gcc that help me on other pc)

---

### Post by haplorrhine on 2015-01-14
Okay, **build-essential** comes pre-installed.  To compile, just use command **gcc** (for C) or **g++** (for C++) followed by the filename (filename suffixes provided on gcc infopage).  
According to the infopage, g++ does preprocessing, proper compilation, assembly, and linking, which results in an executable file?  I'm typing my *.cpp* file into the terminal to execute it, and I'm geting this message back.

q@Q:~$ ~/o.cpp
/home/q/o.cpp: line 6: using: command not found
/home/q/o.cpp: line 8: syntax error near unexpected token `('
/home/q/o.cpp: line 8: `int main()'

Is it reading it as a C++ file?  Its code is below.  I selected those #include directives after reading[ this thread]("http://ubuntuforums.org/showthread.php?t=2228982&highlight=std_lib_facilities").

```
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
#include<cmath>
using namespace std;

int main()
{
cout<<"Your frickin name?\n";
string name;
cin>>name;
cout<<"How are you "<<name<<"!\n";
return(0);
}
```

---

### Post by steeldriver on 2015-01-14
You appear to be trying to **run the source code file** - you need to run the **executable output file** produced by the compiler

If you just ran the compiler like

```

g++ myprog.cpp

```

then the executable will be created with default name a.out so you would do

```

./a.out

```

Otherwise, you can specify an output file name e.g.

```

g++ -o myprog myprog.cpp

```

and then do

```

./myprog

```

FWIW I **highly** recommend adding -Wall to your compiler options

```

g++ -Wall -o myprog myprog.cpp

```

which will warn you about many questionable programming practices + potential coding issues

---

### Post by haplorrhine on 2015-01-14
Excellent!  It works!  Thank you!

However, abandoning the IDE is only a work-around, so it doesn't merit the [SOLVED] tag.  While I don't need Code:;Blocks now, I should note that the fixed code with new directives still wouldn't cooperate with Code::Blocks, despite functioning properly with the method outlined above.  Here is exactly what I did:

1. Create either an Empty file or a C/C++ Source file.
2. I paste the code into the editor.
3. I click compile.
(3b. Clicking "Run" will return a "permission denied" message.)
4. sudo chmod ugoa+x file.
5. Clicking "Run" returns:
/home/test: 6: /home/test: using: not found
/home/test: 8: /home/test: Syntax error: "(" unexpected

---

### Post by steeldriver on 2015-01-14
what **name** and **file extension** are you saving the source code file with? if it is C++ code (which it appears to be) you should save it with a .cpp extension e.g. test.cpp so that the IDE/compiler knows what to do with it i.e. **compile** and **link** it to produce a runnable executable called `test`.

(Although `test` is not a great choice as a program name, because there is a standard system program also called `test`.)

---

### Post by haplorrhine on 2015-01-14
That was it!  I wonder why it doesn't add the suffix automatically.  After all, it asks you C or C++ upon starting.

---

### Post by flaymond on 2015-01-17
C++ is a big language (Indeed with the OOP and other big features)..You need to be good at procedural programming. Using the commands or for short 'raw' teaching you the background of the linking and compiling.

---


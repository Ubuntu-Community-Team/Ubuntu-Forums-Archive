---
title: "[C++] include directive"
date: 2010-11-18
forum: Programming Talk
---

### Post by erotavlas on 2010-11-18
Hi,

I'm disturbed by a trivial problem (I think), but I can't resolve it. I have to merge my project in C++ with source code of other people. I'm under windows 7 with cygwin 1.7.x bash shell and gcc/g++ 4.3.4 compiler. To include a header file inside my project I must write

#include "path of file"

In some files of my project I must write #include "./data/header.h" in other #include "../data/header.h" and there are other files that the compiler can't find for inclusion.
So is there a way to set the path for all files or I have to change all source files with full path?

Thank in advance

Note
my project have a tree structure like the following:

main.cpp
file1.h
file2.h
file1.cc
file2.cc
data/filedata1.h
data/filedata1.cc
data/filedata2.h
data/filedata2.cc
utility/fileutility1.h
utility/fileutility1.cc
utility/fileutility2.h
utility/fileutility2.cc

etc.

---

### Post by Arndt on 2010-11-18
> **erotavlas said:**
> Hi,

I'm disturbed by a trivial problem (I think), but I can't resolve it. I have to merge my project in C++ with source code of other people. I'm under windows 7 with cygwin 1.7.x bash shell and gcc/g++ 4.3.4 compiler. To include a header file inside my project I must write

#include "path of file"

In some files of my project I must write #include "./data/header.h" in other #include "../data/header.h" and there are other files that the compiler can't find for inclusion.
So is there a way to set the path for all files or I have to change all source files with full path?

Thank in advance

Note
my project have a tree structure like the following:

main.cpp
file1.h
file2.h
file1.cc
file2.cc
data/filedata1.h
data/filedata1.cc
data/filedata2.h
data/filedata2.cc
utility/fileutility1.h
utility/fileutility1.cc
utility/fileutility2.h
utility/fileutility2.cc

etc.

If I was sure of the organization of the files, and could change them whenever I myself wanted, I could write like you do. Otherwise, one can write just #include "somefile.h" wherever the file is needed, and use the -I option of the compiler several times to point out where there are header files. If the project has natural subprojects, both approaches can be used. I don't know how your files will be organized after the merge.

---

### Post by C0derBear on 2010-11-18
Easiest thing is to add the -I directive at GCC invocation to put the "root" path of the whole mess in scope for every build, then each file can #include "data/file.h" and get the correct file.

The code then looks uniform in all sources, and is easier to maintain that way.

The only ambiguity this can represent is if you have different "data" directories in your code tree OR same-named files with different content at different locations in your code tree.

I strongly suggest NOT allowing for either of these as a simple policy. There is NO way to automate disambiguation of THAT problem, so simply don't create it.

---

### Post by 0AintLifeGrand0 on 2010-11-19
Hello All,

I'm a complete newbie in using compilers, with a similar but more basic problem.
I've just started a C++ course and am trying to compile a very simple hello world. 
The file starts with an inclusion of a standard header file (see below), but it appears that I have to do something to make the compiler recognize it. 
This is the output I get:
```
hello.cpp:1:22: error: iostream.h: No such file or directory
hello.cpp: In function &#8216;int main()&#8217;:
hello.cpp:5: error: &#8216;cout&#8217; was not declared in this scope
```The course material says:
check your compiler documentation for directions on setting up your include path or environment variables,
But I cannot find this subject in the man page of gcc (g++ in fact).

Anyone an idea of how I do this...
The hello.cpp code looks is as follows:

```

#include <iostream.h>

int main()
{
    cout << "Hello World!\n";
    return 0;
}

```

---

### Post by MadCow108 on 2010-11-19
@0AintLifeGrand0:
your course it outdated. the iostream.h does not exist anymore in standard c++. It is now named iostream (without the .h)
and you are missing the std:: namespace for the standard functions.
Either add a
using namespace std;
or a
using std::cout
at the top
or write std::cout instead of cout.

for more info google c++ namespace.
here's a good reference and tutorial: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by 0AintLifeGrand0 on 2010-11-19
Thanx MadCow108, 

That seems to work. Can you help me further, I now get a file called a.out as output.
I'm not able to run this file however.
How do I create an executable file?

Regards

---

### Post by trent.josephsen on 2010-11-19
```
$ ./a.out
```

---

### Post by 0AintLifeGrand0 on 2010-11-19
:p, sorry for that,

Already tried 
```
$ . a.out
```

That didn't work, I wasn't aware it should be 
```
$ ./a.out
```

Thanks, this works, now i'll manage..

Kind regards

---

### Post by 0AintLifeGrand0 on 2010-11-20
Hello All,

Thanx for the help so far, 
I need one last tip from you more experienced guys, might be a bit off topic but anyway..
I'm now writing code in Nedit, which has some nice language mode highlighting options. 
And compiling with gcc (g++) form the Xterm command line.

Would you guys recommend to continue working like this or to develop code in an IDE such as CODE::BLOCKS?

---

### Post by Arndt on 2010-11-20
> **0AintLifeGrand0 said:**
> :p, sorry for that,

Already tried 
```
$ . a.out
```

That didn't work, I wasn't aware it should be 
```
$ ./a.out
```

Thanks, this works, now i'll manage..

Kind regards

You solved your problem, but you may be interested in knowing what the first attempt actually did: the . command is a command built into bash (and sh), which reads a file of bash commands and executes them. Typically this is used for setting variables and aliases and such things in the shell, because the file is not run as a subprocess but in the shell itself. In your case, the . command got an executable binary file instead, and probably tried to read lines from it and execute them, which it could not and then reported "command not found", preceded by some binary garbage. That's what it does when I try it, anyway.

The command that works for you, ./a.out, is a special case of giving commands to the shell: if you give anything that's not a builtin command, it is treated as a filename and the shell executes it (if it is executable). If the filename does not contain any slash, it is looked up in all the directories mentioned in the PATH environment variable. You did not have the current directory in PATH, so it said that it didn't find "a.out". The form ./a.out, however, because it contains a slash, is not searched in the PATH; it's taken as a filename just as it is. So there is nothing magic about just the "./" part; it just happens to be a very common thing to do.

Some have "." in the PATH, and they can write just "a,out"; some recommend that you don't have it there, because you may fall victim to trojan horses when going to another user's directory and executing what you think is a system command, but in fact is that user's command that does something completely different (on purpose or not). At least having the "." as the last thing in PATH is probably a good idea.

Slashes are used quite generally for separating directory components in file names, but I suppose you knew that.

There may be a problem when more experienced users talk, because we often don't spell out every character, and both slash and space would be pronounced as a pause.

---

### Post by trent.josephsen on 2010-11-20
> **0AintLifeGrand0 said:**
> Hello All,

Thanx for the help so far, 
I need one last tip from you more experienced guys, might be a bit off topic but anyway..
I'm now writing code in Nedit, which has some nice language mode highlighting options. 
And compiling with gcc (g++) form the Xterm command line.

Would you guys recommend to continue working like this or to develop code in an IDE such as CODE::BLOCKS?
My personal opinion:  don't bother with an IDE.  Until you get into multi-thousand line programs, their overhead is way more than they're worth.  Stick with editor+gcc; it's simpler and you'll learn more.

(I've never heard of Nedit before, being a Vim user myself.)

---


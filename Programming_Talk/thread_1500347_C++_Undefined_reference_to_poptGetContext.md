---
title: "C++: Undefined reference to poptGetContext"
date: 2010-06-03
forum: Programming Talk
---

### Post by James78 on 2010-06-03
Any idea as to why it's doing this too me? :(

Error:
```
/home/acidburn/Projects/rsuploader/src/main.cpp:69: undefined reference to `poptGetContext'
/home/acidburn/Projects/rsuploader/src/main.cpp:72: undefined reference to `poptGetNextOpt'
/home/acidburn/Projects/rsuploader/src/main.cpp:115: undefined reference to `poptStrerror'
/home/acidburn/Projects/rsuploader/src/main.cpp:115: undefined reference to `poptBadOption'
/home/acidburn/Projects/rsuploader/src/main.cpp:119: undefined reference to `poptFreeContext'
```

main.cpp
[PHP]#include "functions.h"
#include "parseargs.h"
#include <popt.h>
#include <cstdio>
#include <iostream>

using namespace std;

int main(int argc, char* argv[])
{
    const int realNumberArgs = argc - 1;

    const bool hasArgs = (realNumberArgs == 0);
    if (hasArgs) {
        printUsage(0);
        return 1;
    }

    // Declare popt options variables..
    char login[65]; // RS max username length is 64
    char password[31]; // RS max pass length is 30
    char* uploadPath,* accountType,* writeToFile;
    int antiHack;
  //int updateMode, trashMode;

    //Set popt options
    poptContext optCon;
    poptOption optionsTable[] = {
        { "help", 'h', 0, '\0', 'h', '\0', '\0' },
        { "help-all", 'H', 0, '\0', 'H', '\0', '\0' },
        { "account-type", 'a', POPT_ARG_STRING, &accountType, 0, '\0', '\0' },
        { "disclaimer", 'd', 0, '\0', 'd', '\0', '\0' },
        { "upload", 'f', POPT_ARG_STRING, &uploadPath, 0, '\0', '\0' },
        { "login", 'l', POPT_ARG_STRING, &login, 0, '\0', '\0' },
        { "password", 'p', POPT_ARG_STRING, &password, 0, '\0', '\0' },
        { '\0', 'v', 0, '\0', 'v', '\0', '\0' },
        { "anti-hack", 'A', POPT_ARG_INT, &antiHack, 0, '\0', '\0' },
        { "create-account", 'c', 0, '\0', 'c', '\0', '\0' },
        //{ "trash-mode", 't', POPT_ARG_INT, &trashMode, 0, '\0', '\0' },
        //{ "update-mode", 'u', POPT_ARG_INT, &updateMode, 0, '\0', '\0' },
        { "write", 'w', POPT_ARG_STRING, &writeToFile, 0, '\0','\0' },
        { "points", 'y', 0, '\0', 0, '\0', '\0' },
        { '\0', 0, 0, '\0', 0, '\0', '\0' }
    };

    optCon = poptGetContext("rsuploader", argc, (const char**)argv, (const struct poptOption*)&optionsTable, 0);

    char c;
    while ((c = poptGetNextOpt(optCon)) > 0) {
        switch (c) {
            case 'h' :
                printUsage(0);
                break;
            case 'H' :
                printUsage(1);
                break;
            case 'a' :

                break;
            case 'd' :

                break;
            case 'f' :

                break;
            case 'l' :

                break;
            case 'p' :

                break;
            case 'v' :

                break;
            case 'A' :
                
                break;
            case 'c' :

                break;
            case 'w' :
                
                break;
            case 'y' :

                break;
        }
    }

    if (c < -1) {
        // an error occurred during option processing
        fprintf(stderr, "%s: %s\n", poptBadOption(optCon, POPT_BADOPTION_NOALIAS), poptStrerror(c));
        return 1;
    }

    poptFreeContext(optCon);
    return 0;
}[/PHP]

---

### Post by leg on 2010-06-03
Have you told the linker where the lib is? The compiler needs to know paths for both compilation and linking stages. It could also be that popt uses a namespace.

---

### Post by James78 on 2010-06-03
You're probably right about the linker. I'm using CMake for the configuration (KDevelop4 IDE, it uses CMake). How would I configure the linking? Just input the path to the .so libary(s) (like /usr/lib)? And I'm pretty sure I know what to do for the namespaces of course, if it does have any, I'll have to go check.

Good guess about the linker too, I forgot to include the more (relevant) error messages, and it is appearing to happen during the linking stage.

---

### Post by Some Penguin on 2010-06-03
popt looks to be a C library.  Since you're using C++, consider using extern.  You might be seeing issues with name mangling.  If this were merely a library setup issue, I would expect the message to refer to "undefined symbols" and the object file, not "undefined references" and the source file.

[http://www.cppreference.com/wiki/keywords/extern](http://www.cppreference.com/wiki/keywords/extern)

---

### Post by James78 on 2010-06-03
Yup, it is a C library. Looks like you're right after a little testing. I'll report back if I get it working. :) Thanks for the tip.

Edit: I made a new header file, and included it within the main, and also <popt.h> itself in main. And I tried this and this for all of the functions, as function prototypes... No dice. :([PHP]extern "C" poptContext poptFreeContext(poptContext con);[/PHP]Also tried this in the main.. As an easier method..[PHP]extern "C" {
    #include <popt.h>
}[/PHP]

Edit2: Took a look at the source of popt, and they already have a #ifdef __cplusplus extern "C" { #endif (and the ending bit) in place inside the header, so it doesn't look like extern can be the issue here?

How frustrating, just when I thought I had found the answer.

---

### Post by dwhitney67 on 2010-06-03
So far you have not indicated what statements (generated by Kdevelop) are being executed to build your project; thus I will have to assume they are wrong.

For now, why don't you try to build the application from the command line, instead of depending on Kdevelop?

Once you figure how to do this, then feel free to go back to Kdevelop to sort out the issue that is preventing you from building your project.

Typically an undefined reference is due to the fact that the developer neglected to specify the appropriate library when linking their code.

Do you know where popt.h and libpopt.so reside?  Assuming these are located in *PathA* and *PathB*, your command line statement may look something like:
```

g++ -IPathB -c MyProgram.cpp
g++ MyProgram.o -LPathB -lpopt -o my_exe

```

P.S.  If PathA and PathB happen to be /usr/include and /usr/lib, respectively, then there is no need to specify them when compiling and linking.  Just make sure you are linking with the popt library.

---

### Post by James78 on 2010-06-03
Includes are in /usr/include, and the library is in the usual /usr/lib. Here, I'll give you a screenshot of the complete error messages, as it's too hard to copy them all. What I'm trying to do is figure out how to link it with CMake, not from g++ (because doing it from that is easy), what exact property or string from the configuration... Hmm.. Time for some research.

And the statements executed by KDevelop are hard to figure out at the moment, let me take a look, no doubt the statements are contained within the CMake options...

Here is the CMakeCache file, it looks like where the settings are being stored..

I did the liberty of doing the commands you requested. I got it to work, and the argument parsing (that I implemented up to date anyways), works beautifully!

So there's some misconfiguration in the IDE (CMake configuration) somewhere... How would I go about linking (if that's the problem anyways)?

---

### Post by dwhitney67 on 2010-06-03
> **James78 said:**
> ...

I did the liberty of doing the commands you requested. I got it to work, and the argument parsing (that I implemented up to date anyways), works beautifully!

Great!

> **James78 said:**
> 
So there's some misconfiguration in the IDE (CMake configuration) somewhere... How would I go about linking (if that's the problem anyways)?

From your results of compiling/linking from the command line, I  definitely believe that you do indeed have a configuration issue within Kdevelop in which your application is not being linked with the popt library.  I personally do not use an IDE for any of my development needs, and since I possess zero experience with Kdevelop, I can't assist you on that front.  Hopefully someone else can.

---

### Post by James78 on 2010-06-03
Thanks anyways, you limited it down to the library not being linked. This is my first time, so everyones gotta figure this out the first time I guess. Technically it has nothing to do with KDevelop, and everything to do with CMake, since that's the configuration method.. Ohh, I hope they integrate automake soon, that'd make everything easier.

---

### Post by James78 on 2010-06-03
For future reference, after days of laboring, I finally found what to do. In KDevelop 4, I selected my project in the list, went to Project->Open Configuration, checked show advanced->show advanced values, and I changed CMAKE_CXX_FLAGS to equal -lpopt. That did the trick. I'm currently working on seeing if I can do it more specifically, through the shared library or whatever other options..

Edit: The correct option to use this in, is CMAKE_EXE_LINKER_FLAGS

---


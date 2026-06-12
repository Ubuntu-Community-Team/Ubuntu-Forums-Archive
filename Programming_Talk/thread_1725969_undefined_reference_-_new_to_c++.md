---
title: "undefined reference - new to c++"
date: 2011-04-10
forum: Programming Talk
---

### Post by jebsector on 2011-04-10
I am getting an undefined reference error compiling.  I can't see why it can't find the constructor definitions.  It's basically parsing a file into a structure.  The error happens when trying to instantiate error_line..   
I'll post some code..

main.cpp
```

#include <cstdlib>
#include <string>
#include <fstream>
#include <iostream>
#include <boost/regex.hpp>
#include <boost/regex.h>
#include <boost/regex_fwd.hpp>
#include "struct.h"
#include "error_line.h"


class t {
...
};
...
int main(int argc, char** argv) {

    t *tr = new t();
    tr->parseFile(argv);

    return 0;

}
int t::check_section(std::string line) {
    ...
    else {
        string msg = "invalid section";
        error_line *a = new error_line();
        //errors.push_back(a);
        return 0;  //indicate there is an error on this line
    }
}

```

error_line.cpp
```

#include "error_line.h"

using namespace std;

error_line::error_line() {
    line = 0;
    msg = "";
}

error_line::error_line(int l, string m) {
    line = l;
    msg = m;
}

error_line::~error_line() {
}

```
error_line.h:
```

#ifndef ERROR_LINE_H
#define	ERROR_LINE_H

#include <string>

class error_line {
public:
    int line;
    std::string msg;
    
    error_line();
    error_line(int l, std::string m);
    ~error_line();

};

#endif	/* ERROR_LINE_H */


```

Thanks for the help

---

### Post by Arndt on 2011-04-10
> **jebsector said:**
> I am getting an undefined reference error compiling.  I can't see why it can't find the constructor definitions.  It's basically parsing a file into a structure.  The error happens when trying to instantiate error_line..   
I'll post some code..

main.cpp
```

#include <cstdlib>
#include <string>
#include <fstream>
#include <iostream>
#include <boost/regex.hpp>
#include <boost/regex.h>
#include <boost/regex_fwd.hpp>
#include "struct.h"
#include "error_line.h"


class t {
...
};
...
int main(int argc, char** argv) {

    t *tr = new t();
    tr->parseFile(argv);

    return 0;

}
int t::check_section(std::string line) {
    ...
    else {
        string msg = "invalid section";
        error_line *a = new error_line();
        //errors.push_back(a);
        return 0;  //indicate there is an error on this line
    }
}

```

error_line.cpp
```

#include "error_line.h"

using namespace std;

error_line::error_line() {
    line = 0;
    msg = "";
}

error_line::error_line(int l, string m) {
    line = l;
    msg = m;
}

error_line::~error_line() {
}

```
error_line.h:
```

#ifndef ERROR_LINE_H
#define	ERROR_LINE_H

#include <string>

class error_line {
public:
    int line;
    std::string msg;
    
    error_line();
    error_line(int l, std::string m);
    ~error_line();

};

#endif	/* ERROR_LINE_H */


```

Thanks for the help

What does your compile command look like, and the exact error message? (Since you left ... here and there, I can't compile what you posted just like it is.)

---

### Post by jebsector on 2011-04-10
well, the code is kinda long.  my compile command is going through netbeans.

This is the make commands and g++ commands it executes during compilation:

"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/jeremiah/NetBeansProjects/TestTranslator'
"/usr/bin/make"  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/testtranslator
make[2]: Entering directory `/home/jeremiah/NetBeansProjects/TestTranslator'
mkdir -p build/Debug/GNU-Linux-x86
rm -f build/Debug/GNU-Linux-x86/main.o.d
g++    -c -g -I../../boost_1_46_1/boost -I../../boost_1_46_1 -MMD -MP -MF build/Debug/GNU-Linux-x86/main.o.d -o build/Debug/GNU-Linux-x86/main.o main.cpp
mkdir -p build/Debug/GNU-Linux-x86
rm -f build/Debug/GNU-Linux-x86/class_struct.o.d
g++    -c -g -I../../boost_1_46_1/boost -I../../boost_1_46_1 -MMD -MP -MF build/Debug/GNU-Linux-x86/class_struct.o.d -o build/Debug/GNU-Linux-x86/class_struct.o class_struct.cpp
mkdir -p dist/Debug/GNU-Linux-x86
g++     -o dist/Debug/GNU-Linux-x86/testtranslator build/Debug/GNU-Linux-x86/main.o build/Debug/GNU-Linux-x86/someclass.o build/Debug/GNU-Linux-x86/class_struct.o ../../boost_1_46_1/libs/regex/build/gcc/libboost_regex-gcc-1_46

Oh - i typoed the code before, should be class_struct.h

---

### Post by jebsector on 2011-04-10
eh - looking at the command it executes before generating the error, it isn't including error_line in g++...

g++     -o dist/Debug/GNU-Linux-x86/testtranslator build/Debug/GNU-Linux-x86/main.o build/Debug/GNU-Linux-x86/someclass.o build/Debug/GNU-Linux-x86/class_struct.o ../../boost_1_46_1/lib

someclass is there, as well as class_struct.  Netbeans must not have picked up the creation of the class?

---

### Post by jebsector on 2011-04-10
somehow netbeans got hosed.  I created a new project and got rid of the someclass stuff that was hanging out there, copied everything over and it compiles fine now with the following g++ command.

g++     -o dist/Debug/GNU-Linux-x86/testtranslator2 build/Debug/GNU-Linux-x86/main.o build/Debug/GNU-Linux-x86/error_line.o build/Debug/GNU-Linux-x86/class_struct.o ../../boost_1_46_1/libs/regex/build/gcc/libboost_regex-gcc-1_46.a 

Anything I should know about when working with netbeans?  I went to edit their makefile stuff first but that just caused netbeans to mess with the class files, shouldn't be having to edit their makefiles anyway.

---


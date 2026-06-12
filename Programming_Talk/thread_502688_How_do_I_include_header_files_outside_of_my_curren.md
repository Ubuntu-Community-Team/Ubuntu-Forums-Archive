---
title: "How do I include header files outside of my current directory? gcc"
date: 2007-07-16
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-07-16
This is a newbie question, but I have googled and searched this forum.  I am writing a simple program and trying to compile it with a makefile.  Trying to learn more makefile than c++ programming...

Here's the makefile:

VPATH =../sqlite-3.4.0

objects = main.o

main : $(objects)
	gcc -o main $(objects)
	
main.o : sqlite3.h

clean :
	@echo "Removing all object files..."
	/bin/rm -f $(objects)

Here's the program:

#include "sqlite3.h"
#include <stdio>

int main()
{
	cout << "Currently, there are no options." << endl;
}

When I compile, I get this:

g++    -c -o main.o main.cc
main.cc:1:21: error: sqlite3.h: No such file or directory
main.cc:2:17: error: stdio: No such file or directory
main.cc:7:2: warning: no newline at end of file
main.cc: In function ‘int main()’:
main.cc:6: error: ‘cout’ was not declared in this scope
main.cc:6: error: ‘endl’ was not declared in this scope
make: *** [main.o] Error 1


sqlite3.h is present in the directory ../sqlite-3.4.0 as mentioned in the makefile, but gcc can't find it.  I don't want to type out the entire path to that sqlite3.h header file in the main.cc file.  I know there is another way, how can I fix this?

---

### Post by jmazzarelli on 2007-07-17
The man page is admittedly a beast...
```
-I dir
           Add the directory dir to the list of directories to be searched for
           header files.  Directories named by -I are searched before the
           standard system include directories.  If the directory dir is a
           standard system include directory, the option is ignored to ensure
           that the default search order for system directories and the spe&#8208;
           cial treatment of system headers are not defeated .
```

So, gcc -I../sqlite-3.4 or whatever it was

---


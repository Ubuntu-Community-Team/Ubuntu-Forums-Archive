---
title: "Compiling Error C"
date: 2011-06-13
forum: Programming Talk
---

### Post by stamatiou on 2011-06-13
[FONT=Verdana]Hey guys,
I use ubuntu 11.04 and I installed the build-esential package and created the .c file. When I entered the command cc -c first.c it shows me 
[/FONT]```
[FONT=Verdana]first.c:1:20: warning: extra tokens at end of #include directive
first.c:1:40: fatal error: iostream: No such file or directory
compilation terminated.[/FONT]
```
What should I do?  ](*,)

---

### Post by simeon87 on 2011-06-13
Can you post the source? You most likely made a mistake on an #include line. There should not be a semi-colon at the end, if that happens to be the problem.

---

### Post by dwhitney67 on 2011-06-13
Here we go again...

If you are programming in C, please include stdio.h.

If you are programming in C++, which by the way, is a different language, then by all means include iostream.  However with C++, you need to name your source file with one of the following extensions: .C, .cxx, or .cpp (the most common).  If I missed one, then forgive me.  Also, you compile C++ code using 'g++', not 'gcc' or 'cc'.

---

### Post by stamatiou on 2011-06-13
> **simeon87 said:**
> Can you post the source? You most likely made a mistake on an #include line. There should not be a semi-colon at the end, if that happens to be the problem.
```
#include <iostream>using namespace std;

int main()
{
cout << "Hello World \n";
return 0;
}[/CODE
Also I changed it into [CODE]#include <stdio.h>

int main()
{
cout << "Hello World \n";
return 0;
}
```
and it shows me now:
```
first.c: In function ‘main’:
first.c:5:1: error: ‘cout’ undeclared (first use in this function)
first.c:5:1: note: each undeclared identifier is reported only once for each function it appears in
```

---

### Post by tbastian on 2011-06-13
> **stamatiou said:**
> ```
#include <iostream>using namespace std;

int main()
{
cout << "Hello World \n";
return 0;
}[/CODE
Also I changed it into [CODE]#include <stdio.h>

int main()
{
cout << "Hello World \n";
return 0;
}
```
and it shows me now:
```
first.c: In function ‘main’:
first.c:5:1: error: ‘cout’ undeclared (first use in this function)
first.c:5:1: note: each undeclared identifier is reported only once for each function it appears in
```

You're writing a c++ program here. Change 'stdio.h' back to 'iostream' and compile with g++.

---

### Post by stamatiou on 2011-06-13
> **tbastian said:**
> You're writing a c++ program here. Change 'stdio.h' back to 'iostream' and compile with g++.
Can you write me a code for a hello world c program and the command to compile it and execute it?

---

### Post by dwhitney67 on 2011-06-13
```

#include <iostream>

int main()
{
   std::cout << "Hello World." << std::endl;
}

```

or

```

#include <iostream>

int main()
{
   using namespace std;

   cout << "Hello World." << endl;
}

```

Say you save either of the programs above into a file called "hello.cpp", then you would compile it using:
```

g++ -Wall -pedantic hello.cpp -o hello

```
Man-pages are available for most commands; feel free to peruse them, and if afterwards you have questions, then post back here.

---

### Post by stamatiou on 2011-06-14
> **dwhitney67 said:**
> ```

#include <iostream>

int main()
{
   std::cout << "Hello World." << std::endl;
}

```or

```

#include <iostream>

int main()
{
   using namespace std;

   cout << "Hello World." << endl;
}

```Say you save either of the programs above into a file called "hello.cpp", then you would compile it using:
```

g++ -Wall -pedantic hello.cpp -o hello

```Man-pages are available for most commands; feel free to peruse them, and if afterwards you have questions, then post back here.
No, I mean in C, not C++.

---

### Post by tbastian on 2011-06-14
> **stamatiou said:**
> No, I mean in C, not C++.
```

#include <stdio.h>

int main ( int argc, char ** argv )
{
    printf ( "Hello, World!\n" );
    return 0;
}

```
```

gcc -o hello helloWorld.c
./hello

```
assuming you named your file helloWorld.c

---

### Post by velle frak on 2011-06-14
#include<stdio.h>

int main() {
   printf('Hello world.\n");
   return 0;
}

---


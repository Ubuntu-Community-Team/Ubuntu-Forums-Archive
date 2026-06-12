---
title: "&#1057;++  problem with simple program"
date: 2011-03-11
forum: Programming Talk
---

### Post by Segaman on 2011-03-11
Hi guys. 
Here`s my code:
```
#include <stdio.h>

int main()
{
    //QCoreApplication a(argc, argv);
    printf("Let me ask ya some things bro...but wait,whats your name?\n");
    char fio [10];
    scanf("%s", fio);
    printf("Every bitch has an ID...What is yours?\n");
    int i=0;
    scanf("%d",i);
    printf("Now,I know who do u are. Take a look and get a **** outta here\n");
    printf("%s %d %o",fio,i,i);
    int p=0;
    scanf("%d",p);
    return 0;
}

```

Seems to be no errors,even warnings but its not compile...I`ve tried to do it in terminal and got this:
```

./backup_C++/untitled_1/main.cpp: In function ‘int main()’:
./backup_C++/untitled_1/main.cpp:12: warning: format ‘%d’ expects type ‘int*’, but argument 2 has type ‘int’
./backup_C++/untitled_1/main.cpp:16: warning: format ‘%d’ expects type ‘int*’, but argument 2 has type ‘int’
/tmp/cctEb8Eq.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

Please,any help guys...I feel confused cause even this simple program doesnt work... :(

---

### Post by cgroza on 2011-03-11
If you are programming C++, why do you use C libraries? Cout and cin are the way to do it in C++.
Just include <iostream> and the facilities are in the std namespace.
I do not know those functions, but I think they need a pointer to your variables.

---

### Post by MadCow108 on 2011-03-11
scanf requires pointers as arguments. you are giving it integers in two cases.
```
int i=0;
scanf("%d",&i);
```

make sure to use the right compiler for the file
gcc for C (.c ending) g++ for C++ (.cc, .C or .cpp ending)

---

### Post by Segaman on 2011-03-11
Thanks) Let me try <iostream> and g++  :)  I`ll post logs if smth will go wrong...

---

### Post by Segaman on 2011-03-12
Everything seems to be ok since I use <iostream> :)
I realy didn`t know that <stdio.h> is C`s lib :D

---

### Post by nvteighen on 2011-03-12
Now here it comes my counterattack :P

Per se, there's no problem in using the C Standard Library in C++, as long as you do it correctly. One of the aspects of doing it correctly means that instead of writing:

```

#include <stdio.h> /* This is the C way! */

```

You should write:
```

#include <cstdio> // This is the C++ way!

```

It's simple: drop the '.h' extension and add the 'c-' prefix. So, stdlib.h > cstdlib, math.h > cmath, ctypes.h > cctypes, etc. Of course, this is meant just for the C standard headers.

There are a number of reasons on why you should do this. Mainly, portability. The special "cstdio" header is designed for C++, while the equivalent "stdio.h" is designed for C. If you've heard about name mangling, you'll know that under the hood C++ "changes" the functions' and methods' names in order to support overloading. But C doesn't, so there might be conflicts when using C libraries in C++ (not with gcc or g++, that I know, but just in case).

Now. In some cases, printf() can be a better solution than std::cout. Heavy formatting using the C++ std::cout can be quite annoying, whereas printf()'s format string approach can make it quite easy. On the other hand, the std::cout approach supports C++ features which printf() obviously can't.

---

### Post by Segaman on 2011-03-12
here`s one more trouble:
program has been successfuly compiling in QT Creator but nothing happening then. I dont know what the problem is but "g++  ./main.cpp" in terminal is going well...

---

### Post by stchman on 2011-03-13
The scanf function requires you pass the address of the variable.

[PHP]
#include <stdio.h>

int main( int argc, char *argv[] )
{
    //QCoreApplication a(argc, argv);
    printf( "Let me ask ya some things bro...but wait,whats your name?\n" );
    char fio[10];
    scanf( "%s", fio );
    printf( "Every bitch has an ID...What is yours?\n" );
    int i = 0;
    scanf( "%d", &i );
    printf( "Now,I know who do u are. Take a look and get a **** outta here\n" );
    printf( "%s %d %o\n", fio, i, i );
    int p = 0;
    scanf( "%d", &p );
    return 0;
}

[/PHP]The program compiles and runs.

Also, you don't need to pass the address of a character array.  Also, you need to make sure the name is less than 10 characters.

[http://www.cplusplus.com/reference/clibrary/cstdio/scanf/](http://www.cplusplus.com/reference/clibrary/cstdio/scanf/)

---


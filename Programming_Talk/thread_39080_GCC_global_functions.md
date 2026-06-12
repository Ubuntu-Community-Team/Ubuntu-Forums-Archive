---
title: "GCC global functions"
date: 2005-06-03
forum: Programming Talk
---

### Post by superhac007 on 2005-06-03
How come all my functions are global when compiling multiple source files.  For what ever reason I dont need to specficy header files for calling any function in another file.

I'm using Hoary...

Any help would be great....

---

### Post by thumper on 2005-06-03
Can you give a little more detail or some examples?

---

### Post by superhac007 on 2005-06-03
[QUOTE=thumper]Can you give a little more detail or some examples?[/QUOTE]

Sure heres my Makefile:

```

CC=gcc
LIBS=-L/usr/lib -lxml2 -lz -lpthread -lm
CFLAGS=-Wall -I/usr/include/libxml2
OBJS=toto.o xmlparse.o 
BINDIR=/usr/local/toto

all:            toto

toto:        $(OBJS)
                $(CC) $(OBJS) $(LIBS) -o runner

xmlparse.o: xmlparse.c
                $(CC) -c $(CFLAGS) xmlparse.c

toto.o: toto.c
                $(CC) -c $(CFLAGS) toto.c

```

Heres toto.c
```

#include <stdio.h>

int getsomedata(int test)
{

    return(test+test);

}

int main()
{
    getsomedata(1);
    tester();
}


```

Heres xmlparse:

```

#include <stdio.h>

int getsomedata(int test)
{
   printf("xmlparse\n");
    return(test+test);

}

void tester()
{

printf("test\n");
}


```

As you can see there are no header files between these files yet I am able the call the function tester(defined in xmlparse) from toto.c.  But when I use the same function name getsomedata() it complains that, "Warning: size of symbol `getsomedata' changed from 5 in toto.o to 8 in xmlparse.o".  This leads me to belive that all my functions are defaulting to global.

Thanks.

---

### Post by thumper on 2005-06-03
Your functions won't be defaulting to global.  It can't.  What can happen though is it might be thinking it is calling a different function when it isn't.

For example, each of your files contain
```
int getsomedata(int test)
```
and this is the cause of one of your warnings.

If the functions are private to that implementation file, then make them static functions.

```
static int getsomedata(int test)
{
   /* blah blah */
   return test;
}
```

Best to provide prototypes for your functions in a header file and at least that way you know which function it is going to call.

Maybe the linker is being a little relaxed in the multiple definition front, but this should help.

Tim

---

### Post by superhac007 on 2005-06-03
I did add static to my functions and that fixed the problem.  I am just bewildered that all functions are not static by default.

Thanks for your help!

---

### Post by thumper on 2005-06-03
[QUOTE=superhac007]I did add static to my functions and that fixed the problem.  I am just bewildered that all functions are not static by default.

Thanks for your help![/QUOTE]

Static functions do not have external linkage.  This means that they are not visible to any other translation units (normal speak, other source files).

If you have a function prototype in a header file, and implement that in a source file as a static function, then that implementation is not available to other source files.

Given that most large software systems rely on being able to call functions from other files, the default linkage is external.  

Static functions are a way to have "private" functions in a source file.  C++ handles this with anonymous namespaces.

---

### Post by superhac007 on 2005-06-03
Thats exactly what I thought.  Thanks for all your help!

---


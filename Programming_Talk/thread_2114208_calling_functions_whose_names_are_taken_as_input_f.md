---
title: "calling functions whose names are taken as input from a text file"
date: 2013-02-09
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-09
Hello,
 I was thinking of this scenario.
There is a c file having say, 100 function definitions.
There is a text file having names of 5 of these functions.
 Is is possible to call these 5 functions alone.

Basically, the names of the functions to execute come as input from a text file.

I'm not referring to a multiple if-else construct approach, like
```

if(strcmp(line_read_from_file,"fun1"))
 fun1();
else if(strcmp(line_read_from_file,"fun2"))
 fun2();
..
..

```
but something which is more automated/intelligent.

I am aware of function pointers but not sure if it can be used here.

Thanks. :)

---

### Post by dwhitney67 on 2013-02-09
> **IAMTubby said:**
> 
I am aware of function pointers but not sure if it can be used here.


They can.  For example:
```

#include <string.h>
#include <stdio.h>

typedef struct
{
    const char* fname;
    void (*fun)();
} LookupFunction;

void fun1() { printf("fun1 was called.\n"); }

void fun2() { printf("fun2 was called.\n"); }

void fun3() { printf("fun3 was called.\n"); }


LookupFunction functions[] = { { "fun1", fun1 },
                               { "fun2", fun2 },
                               { "fun3", fun3 },
                             };

int main(int argc, char** argv)
{
    if (argc != 2)
    {
        fprintf(stderr, "Usage: %s <fname>\n", argv[0]);
        return -1;
    }

    const size_t numFuns = sizeof(functions) / sizeof(LookupFunction);
    int n = 0;

    for (n = 0; n < numFuns; ++n)
    {
        if (strncmp(functions[n].fname, argv[1], strlen(functions[n].fname)) == 0)
        {
            (*functions[n].fun)();
            break;
        }
    }

    if (n == numFuns)
    {
        fprintf(stderr, "Function with name '%s' not found.\n", argv[1]);
    }

    return 0;
}

```

---

### Post by IAMTubby on 2013-02-09
> **Tony Flury said:**
> The name of a function is not available readily at runtime in a C program, so the best way would be to build a table that associates a string (I.e. a name) with a function pointer, and search for the name in the table.
Tony Flury, I need some time to think about the reply.
But I did a mistake here, I posted on 2 separate threads thinking that my earlier thread was not created.

Admin, if possible, please delete the thread at [http://ubuntuforums.org/showthread.php?t=2114181](http://ubuntuforums.org/showthread.php?t=2114181)

Tony Flury, I'm sorry, quoting you here, so that others get to read your reply.

---

### Post by IAMTubby on 2013-02-09
> **dwhitney67 said:**
> They can.  For example:
```

#include <string.h>
#include <stdio.h>

typedef struct
{
    const char* fname;
    void (*fun)();
} LookupFunction;

void fun1() { printf("fun1 was called.\n"); }

void fun2() { printf("fun2 was called.\n"); }

void fun3() { printf("fun3 was called.\n"); }


LookupFunction functions[] = { { "fun1", fun1 },
                               { "fun2", fun2 },
                               { "fun3", fun3 },
                             };

int main(int argc, char** argv)
{
    if (argc != 2)
    {
        fprintf(stderr, "Usage: %s <fname>\n", argv[0]);
        return -1;
    }

    const size_t numFuns = sizeof(functions) / sizeof(LookupFunction);
    int n = 0;

    for (n = 0; n < numFuns; ++n)
    {
        if (strncmp(functions[n].fname, argv[1], strlen(functions[n].fname)) == 0)
        {
            (*functions[n].fun)();
            break;
        }
    }

    if (n == numFuns)
    {
        fprintf(stderr, "Function with name '%s' not found.\n", argv[1]);
    }

    return 0;
}

```
dwhitney, thanks a lot for the reply. I tried it out and it works. But is there any way to get rid of the mapping, as in, 
"fun1" corresponds to fun1.
I mean, can we *typecast/convert(not able to find another word)* the name of the function from string to function pointer, so that we don't need a lookup table.

---

### Post by dwhitney67 on 2013-02-09
> **IAMTubby said:**
> 
I mean, can we *typecast/convert(not able to find another word)* the name of the function from string to function pointer, so that we don't need a lookup table.

No, not using C or C++.  You could do it in Java.

---

### Post by IAMTubby on 2013-02-09
> **dwhitney67 said:**
> No, not using C or C++.  You could do it in Java.
dwhitney, I'm not well-versed with java, so wouldn't be able to take it forward. But just out of curiosity, how is it done in java? Can you maybe explain the concept or give a small code snippet?

---

### Post by r-senior on 2013-02-09
It uses a feature of Java called reflection -- the ability for Java code to get information about classes, their methods and interfaces at runtime.

*Reflect.java*
```

import java.lang.reflect.Method;

public class Reflect {

	public void methodOne() {
		System.out.println("calling methodOne");
	}

	public void methodTwo() {
		System.out.println("calling methodTwo");
	}
	
	public static void main(String[] args) throws Exception {
		Reflect reflect = new Reflect();
		Method method = Reflect.class.getMethod(args[0]);
		method.invoke(reflect);
	}

}

```

Here's a test run. The parameter passed on the command line (args[0]) tells the program which method to run. When it's not found, an exception is thrown.

```

$ javac Reflect.java
$ java Reflect methodOne
calling methodOne
$ java Reflect methodTwo
calling methodTwo
$ java Reflect methodThree
Exception in thread "main" java.lang.NoSuchMethodException: Reflect.methodThree()
	at java.lang.Class.getMethod(Class.java:1622)
	at Reflect.main(Reflect.java:13)

```

Note the lack of lookup tables and function pointers. The getMethod() method effectively looks up a function pointer from a lookup table that is maintained internally by Java.

---

### Post by SledgeHammer_999 on 2013-02-09
I am not really familiar with dynamically loading shared libraries here it goes(not actual code):

1. You build the file that contains the functions into a shared library(.so or .dll)
2. You create another program which reads the text file gathers all the function names it needs. Then it dynamically loads the shared libray with dlopen(or equivalent). Then it uses the appropriate command(I forget it's name) on the lib to find the function by name which returns a pointer to said function. Then executes the function.

Of course this will only work in C, since C++ mangles symbols. But it is too much work.

---

### Post by IAMTubby on 2013-02-09
> **r-senior said:**
> It uses a feature of Java called reflection -- the ability for Java code to get information about classes, their methods and interfaces at runtime.
r-senior, thanks a lot, I tried out the code snippet you gave. Just what I was looking for :)

> 
```

$ javac Reflect.java
$ java Reflect methodOne
calling methodOne

```

I am not well-versed with java, and very thoughtful of you to give me the build steps as well. 

> 
The getMethod() method effectively looks up a function pointer from a lookup table that is maintained internally by Java.
So, the *java build environment*(not sure if that's correct usage,I mean to say, the equivalent of gcc for java) first parses the entire code, and makes a lookup table for all the functions it contains?

Shall mark the thread as solved in a while, SledgeHammer_999 has hinted about a command on the lib to find the function by name which returns a pointer to said function.

---

### Post by IAMTubby on 2013-02-09
> **SledgeHammer_999 said:**
> I am not really familiar with dynamically loading shared libraries here it goes(not actual code):

1. You build the file that contains the functions into a shared library(.so or .dll)
2. You create another program which reads the text file gathers all the function names it needs. Then it dynamically loads the shared libray with dlopen(or equivalent). Then it uses the appropriate command(I forget it's name) on the lib to find the function by name which returns a pointer to said function. Then executes the function.

SledgeHammer_999, thanks for the reply. I can do the first step and the file part of the second. I tried searching for the command you were referring to, but haven't got anything so far. Is there maybe,a keyword you remember, so I can google more precisely.

> 
Of course this will only work in C, since C++ mangles symbols. But it is too much work.
That's great, I would be happy if I can do it in C.

---

### Post by SledgeHammer_999 on 2013-02-10
[https://en.wikipedia.org/wiki/Dlopen#Loading_the_Library](https://en.wikipedia.org/wiki/Dlopen#Loading_the_Library)

dlopen() to load the library
dlsym() to search for the function(symbol) and get a pointer to it.

---

### Post by r-senior on 2013-02-10
> **IAMTubby said:**
> So, the *java build environment*(not sure if that's correct usage,I mean to say, the equivalent of gcc for java) first parses the entire code, and makes a lookup table for all the functions it contains?
Java is a programming language and a runtime environment. Then on top of that there are libraries and frameworks.

At the simplest level, when you take a Java program and compile it, you produce bytecode. This is the equivalent of compiling a C source file with gcc or another C compiler.

```
$ cat HelloWorld.java 
public class HelloWorld {

	public static void main(String[] args) {
		System.out.println("Hello World");
	}

}
$ javac HelloWorld.java
$ ls
HelloWorld.class  HelloWorld.java
```

The .class file contains bytecode, which is machine-code for a Java virtual machine. This is a computer that doesn't exist in hardware, only in software.

When you run the program, you run it on the Java virtual machine:

```
$ java HelloWorld
Hello World

```

So running 'java' runs the virtual machine and executes the program. Any platform that has a Java virtual machine can run this class file without recompiling. So I could take this class file, copy it to my Mac and run it on Mac OS.

One of the things that Java does that some other languages don't do, is keep information about the names of classes and methods when it is compiled. This allows for "reflection"; the ability for code to find out what methods a class provides and dynamically invoke them by name. This feature, which is considered an overhead by some, allows some interesting frameworks to be developed for Java.

This is what I meant by "keeps a lookup table". It's just something that Java does, not the main thing it does.
> Shall mark the thread as solved in a while, SledgeHammer_999 has hinted about a command on the lib to find the function by name which returns a pointer to said function.
We have two threads and this one is splitting a bit (apologies to SledgeHammer for mixing Java back into what looks like an interesting idea) so perhaps it would be a good idea to think about the direction you want to go and start a new one?

---

### Post by ofnuts on 2013-02-10
> **IAMTubby said:**
> SledgeHammer_999, thanks for the reply. I can do the first step and the file part of the second. I tried searching for the command you were referring to, but haven't got anything so far. Is there maybe,a keyword you remember, so I can google more precisely.


That's great, I would be happy if I can do it in C.

I find this way of going directly from the text file to the function not very safe in the long run, for at least two reasons:

[LIST=1]
[*]You have no real control on what gets called. For instance you may someday have other entry points defined in the dynamic library (experimental or deprecated stuff), and you can't prevent the text file from calling them.
[*]Unless you are using functions without parameters, you'll have to retrieve parameters, check them, maybe convert them to the proper type (text to int, for instance) and feed them to the functions. So you'll need some data structure attached to each function "name" to define the parameters, and it can as well contain a pointer to the function.
[/LIST]
The introspection in Java is a blessing in some cases, but it's so abused it has also become the programmer's bane. Problems with Introspected code will only show at run time instead of being caught at compile time. And "at runtime" often means "after waiting 10-20 minutes for that dang server to start up in debug mode" (aka "crawltime"), and this is the nice case...

---

### Post by IAMTubby on 2013-02-10
> **SledgeHammer_999 said:**
> [https://en.wikipedia.org/wiki/Dlopen#Loading_the_Library](https://en.wikipedia.org/wiki/Dlopen#Loading_the_Library)

dlopen() to load the library
dlsym() to search for the function(symbol) and get a pointer to it.
> **r-senior said:**
> 
We have two threads and this one is splitting a bit (apologies to SledgeHammer for mixing Java back into what looks like an interesting idea) so perhaps it would be a good idea to think about the direction you want to go and start a new one?
SledgeHammer_999, r-senior
I have got some material on the topics you introduced me into. But I would like to reply after I have gone through them in detail. I promise to get them working and post my learnings in some time. Thanks a lot for all the help. :)

---

### Post by Lux Perpetua on 2013-02-11
Here's a minimal example I wrote a while ago showing how this could be done: ```
/* Compile with gcc -ldl -rdynamic */

#include <stdio.h>
#include <dlfcn.h>
#include <stdlib.h>

void testit(void) {
    printf("Working!\n");
}

int main(void) {
    void *handle;
    void (*fn)(void);
    char *error;

    handle = dlopen(NULL, RTLD_LAZY);
    if (!handle) {
        fprintf(stderr, "%s\n", dlerror());
        exit(1);
    }

    dlerror();

    *(void **)(&fn) = dlsym(handle, "testit");

    if ((error = dlerror()) != NULL) {
        fprintf(stderr, "%s\n", error);
        exit(1);
    }

    fn();

    dlclose(handle);
    exit(0);
}
```Warning: you need to be absolutely sure that the symbol you load actually has the type you think it has, because no type checking is performed by the loader.  This could be pretty difficult if the name of your function literally comes from a user-supplied text file, and I would indeed advise against dlsym here.  You're better off making a table of function pointers as dwhitney67 presented in the first reply.

---

### Post by trent.josephsen on 2013-02-11
Nifty. Thanks Lux Perpetua for the interesting (albeit inadvisable) proof of concept.

If you needed to do something like this in non-toy code, you could have the Makefile generate the mapping from string to function pointer -- I don't think it would be too difficult. That would allow you to validate input within your own code, and selectively choose which files you want to generate mappings for. Just a thought.

---

### Post by IAMTubby on 2013-02-12
> **SledgeHammer_999 said:**
> [https://en.wikipedia.org/wiki/Dlopen#Loading_the_Library](https://en.wikipedia.org/wiki/Dlopen#Loading_the_Library)


> **trent.josephsen said:**
> Nifty. Thanks Lux Perpetua for the interesting (albeit inadvisable) proof of concept.


> **Lux Perpetua said:**
> Here's a minimal example I wrote a while ago showing how this could be done

Thanks Lux Perpetua for the source code. But I have a problem. 

**_I made the following modifications to your code_**
1. Tried giving 2 arguments
2. Changed the return type 
and there seems to be a problem

**_code_**
```

#include <stdio.h>
#include <dlfcn.h>
#include <stdlib.h>
char* testit(int num, char* str)
{
    printf("Working!\n");

    printf("\nnum == [%d]",num);
    printf("\nstr == [%s]",str);

    return str;/*EDIT : I had forgotten to add this line, this line is added after dwhitney67 advised me to in the following post*/
}
int main(void)
{
    void *handle;
    void (*fn)(void);
    char *error;
    char* value;
    char* ret;

    value = malloc(200 * sizeof(char));
    ret = malloc(200 * sizeof(char));
    strcpy(value,"hello world");

    handle = dlopen(NULL, RTLD_LAZY);
    if (!handle)
    {
        fprintf(stderr, "%s\n", dlerror());
        exit(1);
    }

    dlerror();

    *(void **)(&fn) = dlsym(handle, "testit");

    if ((error = dlerror()) != NULL) {
        fprintf(stderr, "%s\n", error);
        exit(1);
    }

    ret = fn(5,value);
    printf("\nthe value returned == [%s]",ret);

    dlclose(handle);
    exit(0);

```

[b]_Build steps_[b]
gcc -ldl -rdynamic -o exe main.c

**_The output is as follows_**
```

main.c: In function âmainâ:
main.c:21: warning: incompatible implicit declaration of built-in function âstrcpyâ
main.c:39: error: too many arguments to function âfnâ
main.c:39: error: void value not ignored as it ought to be

```

Thanks.
Please advise.

---

### Post by IAMTubby on 2013-02-12
> **r-senior said:**
> Java is a programming language and a runtime environment. Then on top of that there are libraries and frameworks.

r-senior, your explanation of Java was excellent and I really feel like learning java now :). Thanks a lot.

---

### Post by IAMTubby on 2013-02-12
> **ofnuts said:**
> I find this way of going directly from the text file to the function not very safe in the long run, for at least two reasons:

ofnuts, okay, I understand. But needed it for something quick.
If I can get it working with arguments, it would be great.
I shall keep your advice in the long run though. Thanks.

---

### Post by IAMTubby on 2013-02-12
> **trent.josephsen said:**
> 
If you needed to do something like this in non-toy code, you could have the Makefile generate the mapping from string to function pointer -- I don't think it would be too difficult.
trent.josephsen, it would be great if I could do that. I tried googling for it, but all pages lead me to one of the following:
1. Can be done only using a mapping as dwhitney67 suggested
2. Cannot be done in C
3. leads me to dlsym.

Would you be able to explain how I can do it ?

Thanks.

---

### Post by dwhitney67 on 2013-02-12
> **IAMTubby said:**
> 
Please advise.

Edit:  Nevermind... perhaps you are correct.  Looking at an old example I have, it appears the declarations you have are correct.

You do however need to return something from testit().

---

### Post by dwhitney67 on 2013-02-12
Btw, here's an example I played with long ago (I cannot recall where I got it from):


Util.cpp:
```

#include <stdbool.h>

extern "C"
{
  bool Max(const int val1, const int val2)
  {
    return val1 > val2;
  }
}

```
dltest.cpp:
```

#include <dlfcn.h>
#include <cstdlib>
#include <string>
#include <iostream>

typedef bool (*MaxPtr)(const int, const int);

int main()
{
  const std::string libpath = "libUtil.so";

  // open the library
  void* handle = dlopen(libpath.c_str(), RTLD_LOCAL | RTLD_LAZY);

  if (!handle)
  {
     std::cerr << "failed to open library" << std::endl;
     return 0;
  }

  // resolve the symbol 'Max'
  MaxPtr max;

  *(void**) (&max) = dlsym(handle, "Max");

  if (!max)
  {
    std::cerr << "failed to resolve symbol" << std::endl;
  }
  else
  {
    std::cout << "is 5 greater than 10... "
              << (max(5, 10) ? "yes" : "no")
              << std::endl;
  }

  dlclose(handle);
}

```
Makefile:
```

EXE     = dltest

LIBSRCS = Util.cpp
LIBOBJS = $(LIBSRCS:.cpp=.o)
LIBNAME = libUtil.so

SRCS    = dltest.cpp
OBJS    = $(SRCS:.cpp=.o)

CXXFLAGS = -Wall -ansi -pedantic
LDLIBS   = -ldl


all: $(LIBNAME) $(EXE)

run:
    @ PATH=. LD_LIBRARY_PATH=. $(EXE)

$(LIBNAME):
    $(CXX) $(CXXFLAGS) -fPIC -c $(LIBSRCS) -o $(LIBOBJS)
    $(CXX) -shared -o $@ $(LIBOBJS)

$(EXE): $(OBJS)
    $(CXX) $^ -o $@ $(LDLIBS)

clean:
    $(RM) $(EXE)
    $(RM) $(LIBOBJS) $(OBJS)
    $(RM) $(LIBNAME)

```
To test:
```

$ make
$ make run

```

---

### Post by IAMTubby on 2013-02-12
> **dwhitney67 said:**
> 
You do however need to return something from testit().
dwhitney67, just missed out on that one. I have done an EDIT to the code and added the return statement, so that people looking at it will not have any problems, when copying code.

> **dwhitney67 said:**
> Btw, here's an example I played with long ago (I cannot recall where I got it from):

I am getting the following error on that one
**Makefile:20: *** missing separator.  Stop.**
Please find attached my files.(uploading both cpp and makefiles as .txt since those file formats are not supported for upload)

_dwhitney, these are some of my queries_
1. **void* handle = dlopen(libpath.c_str(), RTLD_LOCAL | RTLD_LAZY);**. I know it's got something to do with libUtil.so, but what does ***.c_str()*** mean ?
2. Is it not possible to support multiple arguments with the code from my previous post where I modified Lex Perpetua's code?
3. Is it possible to get a C version of this ?

Thanks.

---

### Post by Lux Perpetua on 2013-02-13
> **IAMTubby said:**
> Thanks Lux Perpetua for the source code. But I have a problem. 

**_I made the following modifications to your code_**
1. Tried giving 2 arguments
2. Changed the return type 
and there seems to be a problemYour function pointer **fn** is still declared as **void (*fn)(void)**, which is a function that takes no arguments and returns no value. This is inconsistent both with the actual type of the symbol you're reading into it (exactly what I warned against in my previous post) and with the way you're calling the function pointer.  The solution here should be obvious; if not, learn about function pointers before attempting this.

---

### Post by IAMTubby on 2013-02-13
> **Lux Perpetua said:**
> Your function pointer **fn** is still declared as **void (*fn)(void)**
Lux :D, it's working after making the change you pointed me to.

> **Lux Perpetua said:**
> Warning: you need to be absolutely sure that the symbol you load actually has the type you think it has
Sorry, I should have read this more carefully earlier.

Have 1 more question
**1. *(void **)(&fn) = dlsym(handle, "testit");**
Please can you explain the *(void **) part to me? I understand pointers, but just can't visualize this one. 

2. The only change I have made is to do
**char* (*fn)(int, char*);** instead of *void (*fn)(void);*
I have not touched the ***(void **)(&fn) = dlsym(handle, "testit");** part.
Then how is my return value getting printed?

Thanks a lot.

---

### Post by Lux Perpetua on 2013-02-13
> **IAMTubby said:**
> Have 1 more question
**1. *(void **)(&fn) = dlsym(handle, "testit");**
Please can you explain the *(void **) part to me? I understand pointers, but just can't visualize this one. Sure: dlsym returns void *, but the type of fn isn't void *: it's a function pointer type.  We know (or think we know) that dlsym(handle, "testit") is actually a char *(*)(int, char*), which is the type of fn, but that's technically incompatible with void *.  So what we need to do is convince the compiler to let us store the return value of dlsym in our variable, even though the types aren't compatible in the strict sense.  This is called "type punning," and you'll encounter this occasionally in C programming.  Informally, that line of code says "pretend the address of fn is really the address of a void *, and then store dlsym(handle, "testit") there."  If you work it out carefully, you can build the exact correspondence between that informal sentence and the actual line of code.  

Sorry, I don't understand your second question.

---

### Post by IAMTubby on 2013-02-13
> **Lux Perpetua said:**
> Sure
Sir, thanks for the explanation. But I need sometime to think and get back to you. :)

---

### Post by IAMTubby on 2013-02-13
> **Lux Perpetua said:**
> Informally, that line of code says "pretend the address of fn is really the address of a void *, and then store dlsym(handle, "testit") there."

EDIT : 2 hours from this post : Lux, PLEASE DO NOT REPLY TO THIS POST. ofnuts has already clarified some of the concepts. If possible, please try and explain the questions in my next post.

Lux Perpetua, I'm a bit confused again.
First thing I'll do is to mark the thread as solved. 
dwhitney67, r-senior, SledgeHammer_999, ofnuts, trent.josephsen, Tony Flury and you of course have completely given me a solution for the original purpose of the thread.




I still have a couple of questions regarding our discussion in the previous post.
> **Lux Perpetua said:**
> We know (or think we know) that dlsym(handle, "testit") is actually a char *(*)(int, char*), which is the type of fn, but that's technically incompatible with void *.

1. Do you mean to say that what is returned as void* by dlsym is actually a char *(*)(int, char*) ?

2. Assuming that 1(above) is correct, so our next step would be to *convert*(type pun) that to a void*, cotrrect ?
3. Assuming 2 is correct, why can't we just achieve that using **(void*)fn = dlsym(handle, "testit");**? I tried it and it gives an lvalue error.(**same as 5**)
4. I also tried without any type punning **fn = dlsym(handle, "testit");** and that too works. I know this is bad, but how does it work ? Isn't is supposed to give a warning like ""
Isn't it similar to this which gives a warning and wrong value?
[b]
int main(void)
{
 float* ptr;
 int a = 5;
 ptr = &a;
}
[/b]

5. Why does this give an lvalue error ? **your answer of 3 will cover this also**
[b]
int main(void)
{
 float* ptr;
 int a = 5;
 (int*)ptr = &a;
}
[/b]


> Sorry, I don't understand your second question.
I am sure your explanation of the above questions will clear those for me.

Thanks.

PS : I'm sorry Lux Perpetua, I tried reading a lot of web pages, but the more I read, the more questions come to my mind. If you could answer to some of these, I can dig deep on the internet again.

---

### Post by ofnuts on 2013-02-13
You can't cast a "lvalue". if you want to shoehorn a pointer to int into a pointer to float, you use:
```

float *ptr;
int a;

ptr=(float *)(&a);

```But if you want to assign any type of pointer to a variable, declare that variable as "void *" (pointer to anything). You can then assign any pointer to it without casting, but you'll have to cast its value when you use the pointer:
```

void *anyptr;

float f;
int i;

anyptr=&f;
anyptr=&i;

int x=1+* (int *) anyptr;

```

---

### Post by IAMTubby on 2013-02-13
> **ofnuts said:**
> You can't cast a "lvalue". 
Thanks a lot for the explanation ofnuts. Both examples were very clear.
1. But this question of mine still remains. Why can't we do **(void*)fn = dlsym(handle, "testit");** instead of ** *(void **)(&fn) = dlsym(handle, "testit");**. I mean, in the second case, you are converting fn to &fn which means, adding (void **) in type and then finding the value there, which all ultimately comes down to fn right ? I mean ***&** negate each other. So, why can't we just do **(void*)fn = (void*)fn = dlsym(handle, "testit");** ? I understand I'm wrong, I have tried it out, but trying to find the reason.

2. What is the whole point of doing ***(void **)(&fn) = dlsym(handle, "testit");** I don't think I have understood it well.
Is it to save the void* address returned by dlsym in a pointer type(fn) which is not same as void* ? So, does that mean that irrespective of the type of function pointer(say I'm writing some other function type, with 3 arguments and float return), **still *(void **)(&fn) = dlsym(handle, "testit"); will be used the save the address in fn ?**

Thanks.

---

### Post by ofnuts on 2013-02-13
> **IAMTubby said:**
> Thanks a lot for the explanation ofnuts. Both examples were very clear.
1. But this question of mine still remains. Why can't we do **(void*)fn = dlsym(handle, "testit");** instead of ** *(void **)(&fn) = dlsym(handle, "testit");**. I mean, in the second case, you are converting fn to &fn which means, adding (void **) in type and then finding the value there, which all ultimately comes down to fn right ? I mean ***&** negate each other. So, why can't we just do **(void*)fn = (void*)fn = dlsym(handle, "testit");** ? I understand I'm wrong, I have tried it out, but trying to find the reason.

2. What is the whole point of doing ***(void **)(&fn) = dlsym(handle, "testit");** I don't think I have understood it well.
Is it to save the void* address returned by dlsym in a pointer type(fn) which is not same as void* ? So, does that mean that irrespective of the type of function pointer(say I'm writing some other function type, with 3 arguments and float return), **still *(void **)(&fn) = dlsym(handle, "testit"); will be used the save the address in fn ?**

Thanks.
1) "(void *) fn=" is casting the lvalue (telling to redeclare the variable). The convoluted workaround is not, it's casting a pointer to a variable.

2) Because in C you can't cast a "void *" to a function pointer. The behavior is undefined(*). So the indirect workaround above is used (there is [another solution](http://blog.s11n.net/?p=82)):. Its behavior is also technically undefined, but it keeps the compiler happy. It seems that GCC complains only if you are using -pedantic, though.

(*) one possible reason is that you can find system where pointers to data and pointers to code are too different animals.

---

### Post by IAMTubby on 2013-02-13
> **ofnuts said:**
> 1) "(void *) fn=" is casting the lvalue (telling to redeclare the variable).
 
I need some more clarity here, are you saying something like, *(void**) &fn, will act on the value held by the function pointer, which is what we want, whereas (void *) fn will act on the variable called fun. *can you please tell me what concepts I can google for this. It might be difficult for you to explain this to me over mail *

>  
The convoluted workaround is not, it's casting a pointer to a variable.
 
Sorry Sir, didn't get that.

>  
2) Because in C you can't cast a "void *" to a function pointer. 
I get this completely.

---


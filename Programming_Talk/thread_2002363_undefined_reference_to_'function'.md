---
title: "undefined reference to 'function'"
date: 2012-06-12
forum: Programming Talk
---

### Post by hasanalikhattak on 2012-06-12
**i want to use one program as a shared library for an other program.**

i started as follows:
i have a application which i have compiled using

```
/usr/bin/g++ -I/usr/include/libxml2  -fpermissive -ffriend-injection -Wformat -Wno-deprecated -Xlinker -zmuldefs -fPIC -c abc.cpp
```

then i have created a shared object library from the objects i get from this file using this command

```
g++ -fPIC -Xlinker -zmuldefs -shared -o libabc.so abc.o
```
after this i get the libabc.so file which i copy to the 
```
sudo cp libabc.so /usr/local/lib/libabc.so
```


now when i compile my orignal application which will use this newly created library **libabc.so** using this command
```
/usr/local/lib/libabd.so: undefined reference to `xmlXPathNewContext'
``` i get errors for all the functions i used of that included library **libxml2** in the first application and the function which has this undefined reference is actually the library i include in the first program.
so kindly anyone guide me where i need corrections

---

### Post by trent.josephsen on 2012-06-12
I don't think you're doing that right...

gcc(1)
```
       -I dir
           Add the directory dir to the list of directories to be searched for
           header files.  Directories named by -I are searched before the
           standard system include directories.  If the directory dir is a
           standard system include directory, the option is ignored to ensure
           that the default search order for system directories and the spe-
           cial treatment of system headers are not defeated .
```

Do you understand the difference between including a header file and linking to a library?

---

### Post by hasanalikhattak on 2012-06-12
> **trent.josephsen said:**
> I don't think you're doing that right...

gcc(1)
```
       -I dir
           Add the directory dir to the list of directories to be searched for
           header files.  Directories named by -I are searched before the
           standard system include directories.  If the directory dir is a
           standard system include directory, the option is ignored to ensure
           that the default search order for system directories and the spe-
           cial treatment of system headers are not defeated .
```

Do you understand the difference between including a header file and linking to a library?
yes i guess.
header files have code which needs to be used by source code while library is collection of programs, header files and/or the data which can be used to create another program.
but i think the problem is that in first application i am including header files of libxml2 in my code and then make a shared object library of it.

then i use this library in my second application but it does not find the functions which this library have due to including libxml2

---

### Post by Barrucadu on 2012-06-12
You're not linking your library against libxml2.

---

### Post by trent.josephsen on 2012-06-12
> **hasanalikhattak said:**
> yes i guess.
header files have code which needs to be used by source code while library is collection of programs, header files and/or the data which can be used to create another program.
but i think the problem is that in first application i am including header files of libxml2 in my code and then make a shared object library of it.

then i use this library in my second application but it does not find the functions which this library have due to including libxml2
Not how I would put it.

Source files contain *objects* and *function definitions*, which are the data and routines that make up your program or library. Source files are compiled into object files, which are linked into libraries or programs.

Header files contain *declarations* and *function prototypes*, which **tell you about** the source code. Header files mostly exist for the purpose of compile-time type checking, and do not exist after the compilation process. (This is an oversimplification but I think it will do for now.)

You've *included the header files* for libxml2, so your code **knows about** the data and subroutines that make up the external libxml2 API, but you haven't *linked* the objects and subroutines of the libxml2 library to your own binaries, so you **can't use them**. The library has to be linked to be used.

(Sorry if you already knew all this.)

As I understand it, you have two linking stages:

1) where you link abc.o into its own library, libabc.so
2) where you link your application with libabc.so

This is where my expertise gets a little hazy. I'm not sure whether or not you can link libxml2 during the first stage, even though your abc library might be useless without it. What you almost certainly can do is link libxml along with libabc in the final linking stage. How you do this depends on your compiling process, but you'll use the same method to link your libabc library.

---

### Post by hasanalikhattak on 2012-06-12
can you guide me how to do so. because i think i am linking it in compilation using 
```
/usr/bin/g++ -I/usr/include/libxml2 -Xlinker -zmuldefs -fPIC -c a.cpp
/usr/bin/g++ -I/usr/include/libxml2 -Xlinker -zmuldefs -fPIC -c b.cpp
/usr/bin/g++ -I/usr/include/libxml2 -Xlinker -zmuldefs -fPIC -c c.cpp
```

should i also do this while making the shared library

> **Barrucadu said:**
> You're not linking your library against libxml2.

---

### Post by Tony Flury on 2012-06-12
> **hasanalikhattak said:**
> can you guide me how to do so. because i think i am linking it in compilation using 
```
/usr/bin/g++ -I/usr/include/libxml2 -Xlinker -zmuldefs -fPIC -c a.cpp
/usr/bin/g++ -I/usr/include/libxml2 -Xlinker -zmuldefs -fPIC -c b.cpp
/usr/bin/g++ -I/usr/include/libxml2 -Xlinker -zmuldefs -fPIC -c c.cpp
```

should i also do this while making the shared library

As Baracuda has already pointed out the "-I" does not link against a library it merely includes the header files, you need to use the -l option to link against a library.

```

/usr/bin/g++ -I/usr/include/libxml2 -l/usr/lib/libxml2.so -Xlinker -zmuldefs -fPIC -c a.cpp

```

I am NOT an expert - but something like that should work - or maybe : 

```

g++ -fPIC -Xlinker -zmuldefs -l/usr/lib/libxml2.so -shared -o libabc.so abc.o

```

---

### Post by hasanalikhattak on 2012-06-12
but this location has the header files for the libxml2 library not the libxml2.so file it self.
```
-I/usr/include/libxml2
```

do you think adding ```
-lxml2
``` to the flags passed to the linker should solve the problem ?

---

### Post by Tony Flury on 2012-06-12
> **hasanalikhattak said:**
> but this location has the header files for the libxml2 library not the libxml2.so file it self.
```
-I/usr/include/libxml2
```

do you think adding ```
-lxml2
``` to the flags passed to the linker should solve the problem ?

isn't that similar to what i said ?

---

### Post by hasanalikhattak on 2012-06-12
> **Tony Flury said:**
> isn't that similar to what i said ?
:(
i was just saying that libxml2 is a folder containing the header files which i used. but you mentioned -l/usr/lib/libxml2.so

actually my application is using libxml2 and i want to use this application along with libxml2 in another application. 
i have created the object file like this
```
/usr/bin/g++ -I/usr/include/libxml2  -Xlinker -zmuldefs -fPIC -c a.cpp
/usr/bin/g++ -I/usr/include/libxml2  -Xlinker -zmuldefs -fPIC -c b.cpp
/usr/bin/g++ -I/usr/include/libxml2  -Xlinker -zmuldefs -fPIC -c c.cpp
```

then i have created the shared library using this command
```
g++ -fPIC -Xlinker -zmuldefs -shared -o libabc.so a.o b.o c.o
```

after this i get the libabc.so file which i copy to the
```
sudo cp libabc.so /usr/local/lib/libabc.so
```

now when i compile my orignal application which will use this newly created library libabc.so using it gives this error
```
/usr/local/lib/libabd.so: undefined reference to `xmlXPathNewContext'
```
i get errors for all the functions i used from the included library libxml2 in the first application and the function which has this undefined reference is actually the library i include in the first program i mean i have tested it. so kindly anyone guide me where i need corrections

---

### Post by Tony Flury on 2012-06-12
I just told you how to do it - read what i wrote !

you use : 
```

g++ -fPIC -Xlinker -zmuldefs -shared -o libabc.so a.o b.o c.o

```

to create your library try using 
```

g++ -fPIC -Xlinker -zmuldefs -shared -llibxml2 -o libabc.so a.o b.o c.o

```

to link against the libxml2 library - it should also work with "-l/usr/lib/xml2" I think - I am not an expert though.

The actual library you need is actually /usr/lib/libxml2.so - hence my suggestion. The header files are in /usr/include/libxml2 - they are very different places.

---

### Post by hasanalikhattak on 2012-06-13
well this is the library and here are its config for with cflags as well as for linker.
i hope this might be of help
[IMG]http://i.imgur.com/DdlcL.png[/IMG]

---

### Post by Tony Flury on 2012-06-13
Have you actually tried the commands i suggested for linking together your shared library. If you have what errors did you get ?

p.s. The options command you just gave tells you exactly what compiler and linker options to use - and from that it seems that the commands i have given are mostly correct. i.e.

use "-I/usr/include/xml2" on your compile line to pick up the right header files.

use "-lxml2" on your link command to link to the right library (I said -llibxml2 appologies).

Note - since in your linker command you look like you are trying to create a static libary - you might want to run 
```

xml2-config --libs --static

```
To see exactly what options you need on your linker command (as i may have missed some).

---

### Post by the_unforgiven on 2012-06-13
> **hasanalikhattak said:**
> well this is the library and here are its config for with cflags as well as for linker.
i hope this might be of help
[IMG]http://i.imgur.com/DdlcL.png[/IMG]
Your library creation step needs to change to:
```
g++ -fPIC -Xlinker -zmuldefs -shared **-lxml2** -o libabc.so a.o b.o c.o
```

Moreover, you can also find out which all libraries are being used by a binary (another shared library or an executable) by using the **ldd** util: ```
ldd /path/to/library/or/executable
```
For example, trying this command on the ls binary on my machine yields:
```
 $ ldd /bin/ls
        linux-gate.so.1 =>  (0xb77f0000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb77cc000)
        libselinux.so.1 => /lib/libselinux.so.1 (0xb77b1000)
        libacl.so.1 => /lib/libacl.so.1 (0xb77a8000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb764f000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7636000)
        /lib/ld-linux.so.2 (0xb77f1000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7632000)
        libattr.so.1 => /lib/libattr.so.1 (0xb762c000)

```
If a library is not found on your system, the right side of "=>" will say so.

---

### Post by hasanalikhattak on 2012-06-13
actually i need to have libxml2 in my generated library (from an application which i developed earlier) so i can have  my new application (which is giving errors of undefined reference ) use it.
this is a link to my make file [http://pastebin.com/RFKa5pT4](http://pastebin.com/RFKa5pT4)
and this is the output of the make file [http://pastebin.com/922BCWwS](http://pastebin.com/922BCWwS)
[LIST=1]
[*]compile
**i used this command to compile my code**
```
/usr/bin/g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.  -I/usr/include/libxml2  -fpermissive -ffriend-injection -Wformat -Wno-deprecated -Xlinker -zmuldefs -fPIC -c ClassicIndividual.cpp

```

[*]link
**and this command to link the objects**
```
/bin/bash ../libtool --mode=link /usr/bin/g++  -fpermissive -ffriend-injection -Wformat -Wno-deprecated -Xlinker -zmuldefs -fPIC  -o neoclassic  ClassicIndividual.o IndividualSet.o NeoConsApp.o RoleRestr.o MatchMake.o Concept.o Inference.o NeoEnvironment.o Rule.o neoclassic.o DebugStream.o InferenceConflict.o NeoForm.o Set.o Description.o InferenceNegativeSub.o NeoObject.o Soup.o socket.o Evaluator.o InferenceNorm.o NeoPtrObject.o StdAfx.o standComp.o Explanation.o InferencePositiveSub.o Node.o String.o temp.o InterpreterFunctions.o OneOf.o Symbol.o typdefs.o Hooks.o Kb.o Parser.o Test.o user.o HostIndIM.o MinOrMax.o Primitive.o UpdateOccurrence.o HostIndividual.o NamedObject.o Role.o gensym.o SolveCXP.o NeoXmlObjects.o TellsTranslator.o -L/usr/lib -lxml2 -lz -lm -lxml2
mkdir .libs
/usr/bin/g++ -fpermissive -ffriend-injection -Wformat -Wno-deprecated -Wl,-zmuldefs -fPIC -o neoclassic ClassicIndividual.o IndividualSet.o NeoConsApp.o RoleRestr.o MatchMake.o Concept.o Inference.o NeoEnvironment.o Rule.o neoclassic.o DebugStream.o InferenceConflict.o NeoForm.o Set.o Description.o InferenceNegativeSub.o NeoObject.o Soup.o socket.o Evaluator.o InferenceNorm.o NeoPtrObject.o StdAfx.o standComp.o Explanation.o InferencePositiveSub.o Node.o String.o temp.o InterpreterFunctions.o OneOf.o Symbol.o typdefs.o Hooks.o Kb.o Parser.o Test.o user.o HostIndIM.o MinOrMax.o Primitive.o UpdateOccurrence.o HostIndividual.o NamedObject.o Role.o gensym.o SolveCXP.o NeoXmlObjects.o TellsTranslator.o  -L/usr/lib -lz -lm /usr/lib/libxml2.so
```


[*]library generation
**this command i use for generating the library**
```
g++ -fPIC -Xlinker -zmuldefs -lxml2 -shared -o libneoclassic.so ClassicIndividual.o IndividualSet.o NeoConsApp.o RoleRestr.o MatchMake.o Concept.o Inference.o NeoEnvironment.o Rule.o neoclassic.o DebugStream.o InferenceConflict.o NeoForm.o Set.o Description.o InferenceNegativeSub.o NeoObject.o Soup.o socket.o Evaluator.o InferenceNorm.o NeoPtrObject.o StdAfx.o standComp.o Explanation.o InferencePositiveSub.o Node.o String.o temp.o InterpreterFunctions.o OneOf.o Symbol.o typdefs.o Hooks.o Kb.o Parser.o Test.o user.o HostIndIM.o MinOrMax.o Primitive.o UpdateOccurrence.o HostIndividual.o NamedObject.o Role.o gensym.o SolveCXP.o NeoXmlObjects.o TellsTranslator.o
```
[/LIST]

i used ldd to find the libraries in my library or the files in my library and it give this
```
$ ldd /usr/local/lib/lneoclassic.so 
	linux-gate.so.1 =>  (0x005ef000)
	libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0x005f0000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0x005bf000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0x00c62000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x008c3000)
	/lib/ld-linux.so.2 (0x00c11000)
```
which i think does not have libxml2 in in so my application is giving error.

---

### Post by Tony Flury on 2012-06-13
I am no expert, but i think this line might be the error : 

```
/usr/bin/g++ -fpermissive -ffriend-injection -Wformat -Wno-deprecated -Wl,-zmuldefs -fPIC -o neoclassic ClassicIndividual.o IndividualSet.o NeoConsApp.o RoleRestr.o MatchMake.o Concept.o Inference.o NeoEnvironment.o Rule.o neoclassic.o DebugStream.o InferenceConflict.o NeoForm.o Set.o Description.o InferenceNegativeSub.o NeoObject.o Soup.o socket.o Evaluator.o InferenceNorm.o NeoPtrObject.o StdAfx.o standComp.o Explanation.o InferencePositiveSub.o Node.o String.o temp.o InterpreterFunctions.o OneOf.o Symbol.o typdefs.o Hooks.o Kb.o Parser.o Test.o user.o HostIndIM.o MinOrMax.o Primitive.o UpdateOccurrence.o HostIndividual.o NamedObject.o Role.o gensym.o SolveCXP.o NeoXmlObjects.o TellsTranslator.o  -L/usr/lib -lz -lm /usr/lib/libxml2.so

```
I think you need -lxml2 (rather than /usr/lib/libxml2.so) at the end.

---

### Post by hasanalikhattak on 2012-06-13
when i compile my main application
i get this error
```
g++ -lneoclassic -lrt -o common/ptypes2tcl common/ptypes2tcl.o
/usr/local/lib/libneoclassic.so: undefined reference to 'xmlXPathNewContext'
```

so i thought to look through my libneoclassic.so using 
```
nm -D /usr/local/lib/lneoclassic.so | grep xmlXPathNewContext
```
and it returned me
> U xmlXPathNewContext
it means my library is okay
error may be in my main application not my library

i can share the make file if you can look into it
[http://pastebin.com/NZWPxKht](http://pastebin.com/NZWPxKht)

---

### Post by dwhitney67 on 2012-06-13
Could you please explain what you think that Step 2 is doing?  I'm not familiar with "libtool".

Typically when a shared-object library is created, the individual source files are compiled, using at a minimum -fPIC and -c, to generate an object file.

Then all of the object files are collected to form the shared-object library.  If your library is dependent on any external library, you can opt to specify it when building the shared-object library.

Example:
```

g++ -fPIC -c File1.cpp
g++ -fPIC -c File2.cpp
g++ -fPIC -c FileN.cpp

g++ File1.o File2.o FileN.o -shared -o libstuff.so

```

Since you are attempting to include libxml2 in your library, something like the following should suffice:
```

g++ -fPIC -c `xml2-config --cflags` File1.cpp
g++ -fPIC -c `xml2-config --cflags` File2.cpp
g++ -fPIC -c `xml2-config --cflags` FileN.cpp

g++ File1.o File2.o FileN.o -shared -o libstuff.so `xml2-config --libs`

```

P.S.  I'm not familiar with libxml2; so I have not tested the statements above.

---

### Post by hasanalikhattak on 2012-06-13
i have done that and i have checked that my library is fine using 
> nm -D /usr/local/lib/libneoclassic.so | grep xmlXPath
and it shows that the functions are present in the library
>          U xmlXPathCompiledEval
         U xmlXPathCtxtCompile
         U xmlXPathEvalExpression
         U xmlXPathFreeContext
         U xmlXPathFreeObject
         U xmlXPathNewContext
but still i get these error which i am unable to understand
```
g++ -L/usr/local/lib -lneoclassic -lrt -o common/ptypes2tcl common/ptypes2tcl.o
/usr/local/lib/libneoclassic.so: undefined reference to `xmlXPathNewContext'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlXPathFreeContext'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlFree'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlSetProp'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlReadFile'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlStrcmp'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlXPathCtxtCompile'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlDocGetRootElement'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlXPathFreeObject'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlXPathCompiledEval'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlGetProp'
/usr/local/lib/libneoclassic.so: undefined reference to `xmlXPathEvalExpression'
collect2: ld returned 1 exit status
make: *** [common/ptypes2tcl] Error 1
```
I think i need to fine tune my makefile to have these errors looked after

my make file is [http://pastebin.com/NZWPxKht](http://pastebin.com/NZWPxKht)
and here is the log file if needed [http://pastebin.com/922BCWwS](http://pastebin.com/922BCWwS)

---

### Post by dwhitney67 on 2012-06-13
Don't specify the library before the object file; do it after.
```

g++ -o common/ptypes2tcl common/ptypes2tcl.o **-L/usr/local/lib -lneoclassic -lrt**

```

Edit:

After examining your Makefile, it appears that you have the definitions for LDFLAGS and LIBS backwards.  You can link your object files using one of the following examples:
```

LDFLAGS += -L/usr/local/lib

LIBS    += -lneoclassic -lrt

$(APPNAME): $(OBJS)
        $(CXX) $(LDFLAGS) $^ $(LIBS) -o $@

or

        $(CXX) $^ $(LDFLAGS) $(LIBS) -o $@

```
Where you place the -o option is up to you.  Some like it at the beginning; others like me, prefer it at the end of the statement.

---

### Post by dwhitney67 on 2012-06-13
Follow up...

I just created a simple library that uses the XML2 library, and an application that references the library, and I could not duplicate the issue you are describing.  I suspect your project has a buggy Makefile.

Here's the Makefile I used to build the library:
```

LIBNAME  = libfoo.so

SRCS     = Foo.cpp
OBJS     = $(SRCS:.cpp=.o)

CXXFLAGS = -fPIC -c `xml2-config --cflags`

LDFLAGS  = `xml2-config --libs`

$(LIBNAME) : $(OBJS)
        $(CXX) $^ -shared -o $@ $(LDFLAGS)

clean :
        $(RM) $(LIBNAME) $(OBJS)

```

Here's the Makefile used to build the application:
```

APP      = main

SRCS     = Main.cpp
OBJS     = $(SRCS:.cpp=.o)

CXXFLAGS = -c -I../Lib

LDFLAGS  = -L../Lib -lfoo

$(APP) : $(OBJS)
        $(CXX) $^ $(LDFLAGS) -o $@

clean :
        $(RM) $(APP) $(OBJS)

```

P.S.  I've attached the mini-project so that you can see/test for yourself.

---


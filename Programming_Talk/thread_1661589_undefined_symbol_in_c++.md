---
title: "undefined symbol in c++ ???"
date: 2011-01-06
forum: Programming Talk
---

### Post by jimchen on 2011-01-06
Hi members,
I build up a c++ library of couple hpp/cpp files and they declare/define some classes. I have other projects to include this library for inheriting those perdefined classes. when building those child-projects, it always gets a message of "undefined symbol: ShmooParameter::BIST_RESOURCE".  I do declare and define the class member in my lib. I wonder the cause and solution to this message.

I simplified the original code to get people easily understand my program.
Here is my simplified-file-organiztion ,
files of dummy_library:
ShmooUtil.hpp - declare class ShmooParameter and its public member , static const string BIST_RESOURCE. It also declare/define a global var, bool pf_rslt
ShmooUtil.cpp - include ShmooUtil.hpp, define const string ShmooParameter::BIST_RESOURCE = "BIST Resource";

One of my children-project's file-organization (differnt project/directory from dummy_library):
RX_core.hpp - includes ShmooUtil.hpp; define/declare a core class,  class RX_GAIN_TEST, which access the global var, bool pf_rslt, defined in ShmooUtil.hpp.
shmoo_RX.cpp - includes RX_core.hpp; all classes of this file will inherit both classes of RX_GAIN_TEST and  ShmooParameter.

I paste my simplified codes below,
ShmooUtil.hpp:
#ifndef INCLUDE_SHMOO_UTIL_HPP
#define INCLUDE_SHMOO_UTIL_HPP

#include <cassert>
#include <string>
#include <map>
#include <utility>
#include <sys/time.h>
using namespace std;

class ShmooParameter
{
      

public:
    
  static const string BIST_RESOURCE;
 
 
 //remaining declarations
 
 
};


#ifdef MAINFILE
    #define EXTERN
#else
    #define EXTERN extern
#endif

EXTERN bool pf_rslt;


#endif

-----------------------------------------------
ShmooUtil.cpp:

#include "ShmooUtil.hpp"
#include <cmath>
#include <sstream>
using namespace std;

const string ShmooParameter::BIST_RESOURCE = "BIST Resource";

 //other definitions


-------------------------------------------------------------------------------------
 children-projects, RX_core.hpp:

#define MAINFILE
#include "ShmooUtil.hpp"

class RX_GAIN_TEST{

//declarations/definitions;
//member function accesses global var, pf_rslt

};

-------------------------------------------------------------------------------------
children-projects, shmoo_RX.cpp:

#include "RX_core.hpp"

class shmoo_RX_GAIN_TEST: public Shmoo, public RX_GAIN_TEST
{

//definitions

};



Thanks,
Jim

---

### Post by dwhitney67 on 2011-01-06
First of all, please post all source code within CODE tags.  It makes it very difficult to read anyone's code without these tags.

Second, if you are unable or unwilling to post all of your code, then at least attempt to post a smaller project that exhibits the problem you are describing.

Lastly, what would really be helpful is for you to show 1) how you built your library, 2) how you linked together your external project with this library, and 3) the complete g++ error that was generated (not just a snip).


P.S.  As I indicated before, never employ the use of a "using namespace" statement in a header file.

Also, avoid including header files which are not necessary for a particular unit to compile.  For example, I hardly doubt that <cassert> is necessary within a .hpp file.

Also, you should avoid (to be read as "should not") have global variables.  This is indicative of a poor design choice for your library.

---

### Post by dwhitney67 on 2011-01-06
For grins I have constructed a small library and external test program that uses this library.  Please examine how everything is laid out; it may assist you with determining where you went astray with your project.

The project I build is included as an attachment (silly.tar).

---

### Post by worksofcraft on 2011-01-07
Yes that should work as you are definitely defining ShmooParameter::BIST_RESOURCE in ShmooUtil.cpp.

Now my quess is that you are not linking ShmooUtil.o
The way it works with libraries is you use the archiver "ar" to put all your library object files that your programs might perhaps want to use in an archive (object library) e.g. call it libShmoo.a  and tell the compiler to look in there for unresolved symbols...

Although I didn't yet look at dwhitney67's example I do know from the quality of his work that it will be a very good example and explain a lot to you if you build it. :guitar:

---

### Post by worksofcraft on 2011-01-07
Anyway I downloaded that "silly.tar" file and decided Ima do a review on it... not from a technical POV (cuz dwhitney67 knows just possibly a tad more than I do on that score...) but instead this is from perspective of a budding programmer who wants to learn ;)

So I click "extract here" and get a "silly" folder containing lib and mytest folders.

Open the lib folder and I spot a Makefile, so I type *make* and sure enough it does something (but IDK quite what yet). Then I go to the mytest folder and do likewise that also does something, or other and has produced an exe file... oops no soz this being Linux so it's not got a suffix... but the icon suggests I can click on it to run. OTOH just in case it writes stuff to stdout/stderr I run it from command line:
```

$ ./mytest
./mytest: error while loading shared libraries: libfoo.so: cannot open shared object file: No such file or directory

```

Sigh - now you know how much stuff is out there on the web and how soon ppl surf on to the next web page when they can't get no satisfaction? ANyway that's not me... so "I'll be back" as that famous 38th governor of California is reputed to say.. and hopefully I'll have some more informative insights for you then :)

---

### Post by worksofcraft on 2011-01-07
So first of all, let's have a look at the lib folder

There is a sub-folder  "include" and a sub folder "src"...

why two separate folders you may wonder?

It's like this: You want to make a software library that the linker can incorporate into your own projects right ?
So the compiler **DOES** want to know all the definitions of what is in that library, but it doesn't need to recompile the actual object code! Thus you **WILL** want the header files that give the declarations for #including but the src that has all the definitions is just for you to do further developments and bug fixes of what is in said library.

Anyway, I have a look at that Makefile and AFI'mC it's *complete and utter gobble-de-gook with cherries on top* and you won't catch me wasting my time with that when I can write nice straight forward shell scrips that do exactly what I tell them to :)

However what I CAN see is that a thing called libfoo.so has been created. Now the .so suffix means "shared object" i.e. this ain't no static link library that gets built into your exe... oops I mean your "no-suffix" file... oh hang on apparently they are called "elf" files... whatevah it get linked when you run your program and may be shared with multiple other programs too!

The question is evidently how does the link/loader know where to find these shared libraries?


So I did a bit of Googling and there are a bunch of system folders like /usr/local/lib where they reside and you can build the "rpath" into your "elf" file... but you can also set an environment variable and so on my system judging from where the .so file is situated I did:
```

export LD_LIBRARY_PATH=/home/cjs/Desktop/examples/silly/lib
# and then run again:
$ ./mytest
Some String

```

I hope that helps but otherwise these are my recommendations:
[LIST=1]
[*]Don't use auto tools or make files: they are ill-conceived, badly designed and give unreliable results
[*]Use static link libraries for anything that hasn't been tried and tested and incorporated into dozens of apps.
[*]Do as you please and develop your own style based on your own understanding... and don't be afraid to ask for explanations ;)
[/LIST]

and fo r those of you who are veteran Crash-team racing fans:
"From CoCo with Love"
;P

---

### Post by dwhitney67 on 2011-01-07
worksofcraft, it almost seems as if you are conversing with yourself.  :?

It seems the OP has vanished from the Earth; probably dropped s/w development as a hobby, and decided to enroll in a business school?

Anyhow, I'm glad you figured out how to build the "silly" example I provided.  Running the application was not important, but it's good to know that you learned that step too.  The main point was to show the declaration of a static variable within a library, and then building an application that relied on that library.

And talking about scripts, I cannot fathom why you would use those to build an application.  Imagine if the application consisted of hundreds of files... are you going to recompile each and every file simply because one module has been updated?  The whole point of Makefiles is not only to build a project, but also to manage dependencies and also to build the minimum number of files necessary to get the project "up to date".

As for shared-object libraries, their usefulness is subject to debate.  For a mere one or two applications, it is probably not useful to build a shared-object library, but instead a static library.  However, if you have many applications sharing the same library, then the shared-object is a better approach.  In some projects, both the shared-object and the static libraries are provided.

As for getting an application to locate a shared-object library, the other option you did not mention was the use of ldconfig to augment the cache of library paths where typical libraries reside.  Typically, though, ldconfig is only used to locate libraries that will be made available to the entire system.  For personal projects, using the LD_LIBRARY_PATH is typically sufficient.  (And just for the record, I'm clueless about how to do the 'rpath' thing, but I've heard about it before.  Maybe that is something I should learn about sometime.)

P.S.  I'm surprised that your first instinct was to run an application via a Nautilus browser.  That's so Windoze-like.  Try to get more intimate with using a terminal... after all, most Linux/Unix programmers do that.

---

### Post by worksofcraft on 2011-01-07
> **dwhitney67 said:**
> worksofcraft, it almost seems as if you are conversing with yourself.  :?

It seems the OP has vanished from the Earth; probably dropped s/w development as a hobby, and decided to enroll in a business school?

Anyhow, I'm glad you figured out how to build the "silly" example I provided.  Running the application was not important, but it's good to know that you learned that step too.  The main point was to show the declaration of a static variable within a library, and then building an application that relied on that library.

And talking about scripts, I cannot fathom why you would use those to build an application.  Imagine if the application consisted of hundreds of files... are you going to recompile each and every file simply because one module has been updated?  The whole point of Makefiles is not only to build a project, but also to manage dependencies and also to build the minimum number of files necessary to get the project "up to date".

As for shared-object libraries, their usefulness is subject to debate.  For a mere one or two applications, it is probably not useful to build a shared-object library, but instead a static library.  However, if you have many applications sharing the same library, then the shared-object is a better approach.  In some projects, both the shared-object and the static libraries are provided.

As for getting an application to locate a shared-object library, the other option you did not mention was the use of ldconfig to augment the cache of library paths where typical libraries reside.  Typically, though, ldconfig is only used to locate libraries that will be made available to the entire system.  For personal projects, using the LD_LIBRARY_PATH is typically sufficient.  (And just for the record, I'm clueless about how to do the 'rpath' thing, but I've heard about it before.  Maybe that is something I should learn about sometime.)

P.S.  I'm surprised that your first instinct was to run an application via a Nautilus browser.  That's so Windoze-like.  Try to get more intimate with using a terminal... after all, most Linux/Unix programmers do that.


Lol

I don't care ^^

p.s. I studied your example for my own benefit and I wrote my summary for my own benefit, but I share my insights with this forum for the benefit of any who might choose to read it... and just in case it generates further insights and feed back.

:P

---

### Post by jimchen on 2011-01-18
> **worksofcraft said:**
> So first of all, let's have a look at the lib folder
 
There is a sub-folder "include" and a sub folder "src"...
 
why two separate folders you may wonder?
 
It's like this: You want to make a software library that the linker can incorporate into your own projects right ?
So the compiler **DOES** want to know all the definitions of what is in that library, but it doesn't need to recompile the actual object code! Thus you **WILL** want the header files that give the declarations for #including but the src that has all the definitions is just for you to do further developments and bug fixes of what is in said library.
 
Anyway, I have a look at that Makefile and AFI'mC it's *complete and utter gobble-de-gook with cherries on top* and you won't catch me wasting my time with that when I can write nice straight forward shell scrips that do exactly what I tell them to :)
 
However what I CAN see is that a thing called libfoo.so has been created. Now the .so suffix means "shared object" i.e. this ain't no static link library that gets built into your exe... oops I mean your "no-suffix" file... oh hang on apparently they are called "elf" files... whatevah it get linked when you run your program and may be shared with multiple other programs too!
 
The question is evidently how does the link/loader know where to find these shared libraries?
 
 
So I did a bit of Googling and there are a bunch of system folders like /usr/local/lib where they reside and you can build the "rpath" into your "elf" file... but you can also set an environment variable and so on my system judging from where the .so file is situated I did:
```

export LD_LIBRARY_PATH=/home/cjs/Desktop/examples/silly/lib
# and then run again:
$ ./mytest
Some String

```
 

I hope that helps but otherwise these are my recommendations:[LIST=1]
[*]Don't use auto tools or make files: they are ill-conceived, badly designed and give unreliable results
[*]Use static link libraries for anything that hasn't been tried and tested and incorporated into dozens of apps.
[*]Do as you please and develop your own style based on your own understanding... and don't be afraid to ask for explanations ;)
[/LIST]
and fo r those of you who are veteran Crash-team racing fans:
"From CoCo with Love"
;P
 
 
Hi Worksofcraft,
You really pointed at a right direction for me. It is really about linker and .so file. I modified my linkers and the program can work correctly now. I modified in the IDE environment(it is a GUI). However, I still don't have good explainations between my modifications and your descriptions above. I attatch my screenshots. Would you please help me to explore what my changes exactly affects?
 
Thanks,
Jim

---

### Post by worksofcraft on 2011-01-18
> **jimchen said:**
> Hi Worksofcraft,
You really pointed at a right direction for me. It is really about linker and .so file. I modified my linkers and the program can work correctly now. I modified in the IDE environment(it is a GUI). However, I still don't have good explainations between my modifications and your descriptions above. I attatch my screenshots. Would you please help me to explore what my changes exactly affects?
 
Thanks,
Jim
I'll try but I am not familiar with your IDE and really I was just learning from dwhitney67's example as I went...

What I see is image 4 specifies -L"..." option and this is basically telling the linker that it should look in that folder as well as in the system default ones to find library files.

Image 3 shows that you specify the library to use. What this is telling the linker is that it needs to get missing symbols from a library of that name. It isn't actually going to link it yet because that would be a static link library... with shared objects the linking happens each time you run the application. Advantage is your application is much smaller, disadvantage can be a slight delay on program start for the linking, but that may be offset by only having to load much less program into memory :)

Image 2 you define the "soname" that is the shared object name that gets built into the library itself I think. You see as far as I can tell the actual .so file name doesn't have to be the same as the name that the linker uses... in fact quite often they add on version numbers so that you can have different file versions of the same library being used by different programs even though they have the same "soname" built in.

Now I'm really not so sure about image 1 because I thought all that is done with other ones and I'm also not sure how it knows at run time where to find that library because normally you have to use a -R linker option to build a non standard library search path into the elf file...

---

### Post by worksofcraft on 2011-01-18
> **dwhitney67 said:**
> 
And talking about scripts, I cannot fathom why you would use those to build an application.  Imagine if the application consisted of hundreds of files... are you going to recompile each and every file simply because one module has been updated?  The whole point of Makefiles is not only to build a project, but also to manage dependencies and also to build the minimum number of files necessary to get the project "up to date".


IMO if the application becomes so big that it takes ages to rebuild after a change then the designers have failed to modularize properly... A good design will allow changes to be contained within separate modules.

Is this not an important aspect of using libraries in the first place? Say the "silly" library needs to changed... then the revised "silly.so"... now with added interfaces, go faster stripes and furry dice... It should not necessitate all the other libraries involved are rebuilt and with good design none of the legacy applications will have to be either :)

The advantages of using scripts is that *everyone* can see exactly what compile commands are needed and *nobody* has to try understand how esoteric macros get processed, learn some arcane language or get their recursive dependencies wrong :shock:

---

### Post by dwhitney67 on 2011-01-19
> **worksofcraft said:**
> IMO if the application becomes so big that it takes ages to rebuild after a change then the designers have failed to modularize properly... A good design will allow changes to be contained within separate modules.

Is this not an important aspect of using libraries in the first place? Say the "silly" library needs to changed... then the revised "silly.so"... now with added interfaces, go faster stripes and furry dice... It should not necessitate all the other libraries involved are rebuilt and with good design none of the legacy applications will have to be either :)

The advantages of using scripts is that *everyone* can see exactly what compile commands are needed and *nobody* has to try understand how esoteric macros get processed, learn some arcane language or get their recursive dependencies wrong :shock:

For sake of argument, say you are collaborating on a project that consists of 10 header files and 10 corresponding .cpp files, and an additional .cpp file which contains the main() function.

Your collaborator has made a change to a header file.

What is the minimum number of files that will need to be recompiled to rebuild the application?

More importantly, which files will need to be recompiled to achieve the goal of rebuilding the application?

Yes, one viable answer is that all files may need to be recompiled, but oftentimes that is not the case.

Show me a script that you would use to determine the minimum effort needed to rebuild the application.

Now, extrapolate this script to handle a project with over a 1000 files, in which you may obtain s/w updates on a daily basis.

You seem like you know it all, so I await your almighty answer.

---

### Post by worksofcraft on 2011-01-19
> **dwhitney67 said:**
> For sake of argument, say you are collaborating on a project that consists of 10 header files and 10 corresponding .cpp files, and an additional .cpp file which contains the main() function.

Your collaborator has made a change to a header file.

What is the minimum number of files that will need to be recompiled to rebuild the application?

More importantly, which files will need to be recompiled to achieve the goal of rebuilding the application?

Yes, one viable answer is that all files may need to be recompiled, but oftentimes that is not the case.

Show me a script that you would use to determine the minimum effort needed to rebuild the application.

Now, extrapolate this script to handle a project with over a 1000 files, in which you may obtain s/w updates on a daily basis.

You seem like you know it all, so I await your almighty answer.

Thanks :)

I would not presume to to be so "almighty know it all" that I would expect to get a minimum effort task for the computer remotely right.

A project of that scale would do better partitioned into separately manageable sub-projects with modules that can be individually built, managed and maintained IMHO. :popcorn:

---

### Post by dwhitney67 on 2011-01-19
> **worksofcraft said:**
> 
A project of that scale would do better partitioned into separately manageable sub-projects with modules that can be individually built, managed and maintained IMHO. :popcorn:

Not for a mere 10 modules!  Rather than dodge the questions I posed to you in my previous post, please show a little more wisdom.  Or is this all you got?

---

### Post by Vox754 on 2011-01-19
> **worksofcraft said:**
> ...A good design will allow changes to be contained within separate modules.
...

You just don't get it, do you?

"Make" allows exactly this. It allows you to recompile only the needed modules, not all of them! Hence modularity is preserved.

> 
The advantages of using scripts is that *everyone* can see exactly what compile commands are needed ...
"Everybody" is not everybody; everybody will still need to know how the compiler works, what those flags are, and the shell language (bash) used in the script. That is, you still need advance insight on how things work. And surprise, you can also write Makefiles that show exactly what compile commands are needed!

> ... and *nobody* has to try understand how esoteric macros get processed, learn some arcane language or get their recursive dependencies wrong :shock:
What esoteric macros? Arcane language?

You say this because you have not taken a few hours of your life to understand how to write a Makefile. If you had, you would realize that, surprise, it's not that difficult!

You already know how GCC works. Just grab the GNU Make manual, read through it, and in a week you will know how most things work.

Seriously, instead of complaining about everything (remember when you said that C was obsolete and insisted in compiling C code with the C++ compiler), you should try to learn a bit more about this.

We know you are not a kid  with an attitude aspiring to be a hax0r. But on the other hand, you seem like a grumpy ol' grampa with too much free time, set on doing his stuff his own way. That's okay when you are alone, but if you are in this forum, I feel bad for those beginners that follow your example, and could end confused. Think about the children!

PS. I admit that whenever dwhitney posts Makefiles, I feel they are a little bit too complicated for most beginners. Some things like a "build-dep" rule, and packaging, are not really needed when just learning about compiling and "make".

---

### Post by worksofcraft on 2011-01-19
> **dwhitney67 said:**
> Not for a mere 10 modules!  Rather than dodge the questions I posed to you in my previous post, please show a little more wisdom.  Or is this all you got?

For a "mere 10 modules" building all 10 is IMO best strategy. I doubt any extra processing it takes would be prohibitive. Plus there be no danger a dependency gets overlooked, plus build scripts would be intelligible to most programmers and they could see easily what commands are used for each.

As for your hypothetical monolithic projects with over a 1000 modules and daily updates from different sources... whatevah :P

---

### Post by Arndt on 2011-01-19
> **worksofcraft said:**
> For a "mere 10 modules" building all 10 is IMO best strategy. I doubt any extra processing it takes would be prohibitive. Plus there be no danger a dependency gets overlooked, plus build scripts would be intelligible to most programmers and they could see easily what commands are used for each.

As for your hypothetical monolithic projects with over a 1000 modules and daily updates from different sources... whatevah :P

Even assuming that the computer is so fast that it doesn't matter whether you compile 20 files or just the one you changed, one effect of compiling just the one is that any new warnings due to the change you made do not drown in the output from all the other files.

---

### Post by worksofcraft on 2011-01-20
Just as a matter of interest I happened to make a very simple program for another thread here and I sort of accidentally left in the use of an error handling class I had in a shared library somewhere...

To my surprise on attempting to run I got loads of undefined symbols from the GTK library.
The reason appears to be that my shared library that has the error handling class also contains a module that depends on GTK... Even though this simple program was using NOTHING from said module it still wanted to link in GTK :shock:

With a static link library that does not happen. It just pulls in the module it needs. However it highlights the need to split these libraries up based on their dependencies !

I'm not quite sure how yet... like should I move that one gtk dependent module out into a separate library of it's own even though it is part of the same namespace :confused:

---


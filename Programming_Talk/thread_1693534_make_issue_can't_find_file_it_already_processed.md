---
title: "make issue: can't find file it already processed?"
date: 2011-02-23
forum: Programming Talk
---

### Post by jclose on 2011-02-23
Howdy all.  I am having a slight issue with a Makefile I am trying to get working.  I relocated bits of my source files into different directories and have been trying to get 'make' to behave in these new locations.

I first had a problem where it said that it couldn't find a .h file.  So I put in a VPATH directive to the new location and that got fixed.  But now it is complaining about another file that is the that same directory as the .h file!  It says that the file doesn't exist. 

The oddest part:  using the '-d' flag on 'make' shows that it is going through many variations of the file trying to find it, and when it gets to the VPATH line it finds the file (apparently); but then a few lines later it says it doesn't exist!  Here is the output:

The file being looked for is 'rgns.c'.

```

...
Trying implicit prerequisite `s.rngs.w'.
        Trying pattern rule with stem `rngs.w'.
        Trying implicit prerequisite `SCCS/s.rngs.w'.
       Trying pattern rule with stem `rngs'.
       Rejecting impossible implicit prerequisite `rngs.w'.
       No implicit rule found for `rngs.c'.
       Finished prerequisites of target file `rngs.c'.
      No need to remake target `rngs.c'; using VPATH name `../originals/rngs.c'.
     Finished prerequisites of target file `rngs.o'.
    Must remake target `rngs.o'.
gcc -c rngs.c -g -fprofile-arcs -ftest-coverage -Wall
Putting child 0x01633360 (rngs.o) PID 3863 on the chain.
Live child 0x01633360 (rngs.o) PID 3863 
gcc: rngs.c: No such file or directory
gcc: no input files
Reaping losing child 0x01633360 PID 3863 
make: *** [rngs.o] Error 1

```


Here is the dir structure:
```

~/originals/
~/j/
~/j/obj/Debug/
~/j/obj/Debug/originals  (this is from Code::Blocks, I think)

```

~/originals/      (contains many .h and a few .c files that are common to the project I am working on, including the rngs.c file mentioned above, and the rngs.h file that was previously 'not found' but now is found with VPATH.  These files don't change.)

~/j/       (contains the rest of my code: the .c files with main(), as well as a few .h files I wrote to support all this)

~/j/obj/Debug/      (Code::Blocks created dir with output files in it)

~/j/obj/Debug/originals      (Another Code::Blocks dir, created after I made these new directory structures and re-configured the project.)


And my Makefile (which I run from ~/j):
```

CFLAGS = -fprofile-arcs -ftest-coverage -Wall
VPATH = ../originals/   #up one from current; Make should search there for pre-req files
#The VPATH should cause Makefile to look for source files in that dir too; but not quite working...

rngs.o: rngs.h rngs.c
        gcc -c rngs.c -g $(CFLAGS)

dominion.o: dominion.h cardDefs.h moreFunctions.h dominion.c rngs.o
        gcc -c dominion.c -g $(CFLAGS)

jjc:  dominion.o unitTests_jjc.c
        gcc -o jjc_tests unitTests_jjc.c -g -lm dominion.o rngs.o -fprofile-arcs -Wall

all: playdom player

clean:
        rm -f *.o playdom.exe jjc_tests playdom test.exe test player player.exe testInit testInit.exe *.gcov *.gcda *.gcno


```


My ultimate goal is to try and get Gcov to work again!  I had it going before hand, both compiling w/ make or with Code::Blocks; but now I get all the .gcda files for each source file, but I only get .gcno files for the source files that contain the main() routine.  I am most interested in a secondary .c file actually (it has the implementation, the main() file just starts it up and has the unit tests).  

Thanks for any ideas or input you might have!

--  J

---

### Post by Arndt on 2011-02-23
> **jclose said:**
> Howdy all.  I am having a slight issue with a Makefile I am trying to get working.  I relocated bits of my source files into different directories and have been trying to get 'make' to behave in these new locations.

I first had a problem where it said that it couldn't find a .h file.  So I put in a VPATH directive to the new location and that got fixed.  But now it is complaining about another file that is the that same directory as the .h file!  It says that the file doesn't exist. 

The oddest part:  using the '-d' flag on 'make' shows that it is going through many variations of the file trying to find it, and when it gets to the VPATH line it finds the file (apparently); but then a few lines later it says it doesn't exist!  Here is the output:

The file being looked for is 'rgns.c'.

```

...
Trying implicit prerequisite `s.rngs.w'.
        Trying pattern rule with stem `rngs.w'.
        Trying implicit prerequisite `SCCS/s.rngs.w'.
       Trying pattern rule with stem `rngs'.
       Rejecting impossible implicit prerequisite `rngs.w'.
       No implicit rule found for `rngs.c'.
       Finished prerequisites of target file `rngs.c'.
      No need to remake target `rngs.c'; using VPATH name `../originals/rngs.c'.
     Finished prerequisites of target file `rngs.o'.
    Must remake target `rngs.o'.
gcc -c rngs.c -g -fprofile-arcs -ftest-coverage -Wall
Putting child 0x01633360 (rngs.o) PID 3863 on the chain.
Live child 0x01633360 (rngs.o) PID 3863 
gcc: rngs.c: No such file or directory
gcc: no input files
Reaping losing child 0x01633360 PID 3863 
make: *** [rngs.o] Error 1

```


Here is the dir structure:
```

~/originals/
~/j/
~/j/obj/Debug/
~/j/obj/Debug/originals  (this is from Code::Blocks, I think)

```

~/originals/      (contains many .h and a few .c files that are common to the project I am working on, including the rngs.c file mentioned above, and the rngs.h file that was previously 'not found' but now is found with VPATH.  These files don't change.)

~/j/       (contains the rest of my code: the .c files with main(), as well as a few .h files I wrote to support all this)

~/j/obj/Debug/      (Code::Blocks created dir with output files in it)

~/j/obj/Debug/originals      (Another Code::Blocks dir, created after I made these new directory structures and re-configured the project.)


And my Makefile (which I run from ~/j):
```

CFLAGS = -fprofile-arcs -ftest-coverage -Wall
VPATH = ../originals/   #up one from current; Make should search there for pre-req files
#The VPATH should cause Makefile to look for source files in that dir too; but not quite working...

rngs.o: rngs.h rngs.c
        gcc -c rngs.c -g $(CFLAGS)

dominion.o: dominion.h cardDefs.h moreFunctions.h dominion.c rngs.o
        gcc -c dominion.c -g $(CFLAGS)

jjc:  dominion.o unitTests_jjc.c
        gcc -o jjc_tests unitTests_jjc.c -g -lm dominion.o rngs.o -fprofile-arcs -Wall

all: playdom player

clean:
        rm -f *.o playdom.exe jjc_tests playdom test.exe test player player.exe testInit testInit.exe *.gcov *.gcda *.gcno


```


My ultimate goal is to try and get Gcov to work again!  I had it going before hand, both compiling w/ make or with Code::Blocks; but now I get all the .gcda files for each source file, but I only get .gcno files for the source files that contain the main() routine.  I am most interested in a secondary .c file actually (it has the implementation, the main() file just starts it up and has the unit tests).  

Thanks for any ideas or input you might have!

--  J

It seems to me it's gcc which complains, not make. gcc tries to find rngs.c in the current directory, but it is in ../originals.

---

### Post by jclose on 2011-02-23
Yeah, but it isn't part of the make functionality to pass the files along to gcc as it finds them?  There was that header file which had the same error, before putting in VPATH, that now is working (well, not giving errors).  It is in the same directory as this .c file...

-- J

---

### Post by Arndt on 2011-02-23
> **jclose said:**
> Yeah, but it isn't part of the make functionality to pass the files along to gcc as it finds them?  There was that header file which had the same error, before putting in VPATH, that now is working (well, not giving errors).  It is in the same directory as this .c file...

-- J

If the rule says: run "gcc -c rngs.c", then that is what will be run.

This seems to discuss (and solve) exactly your problem:

[http://sunsite.ualberta.ca/Documentation/Gnu/make-3.79/html_chapter/make_4.html#SEC30](http://sunsite.ualberta.ca/Documentation/Gnu/make-3.79/html_chapter/make_4.html#SEC30)

but start reading at 4.3.1.

---

### Post by jclose on 2011-02-23
Thanks for the tip and link; yes, that did help...but revealed other problems.  I did a bunch more messing around without finding a complete solution.

I used the tips you pointed to and got one section of 'make' to work OK, but then it failed on another section.  So I did a bunch of other things to try and rectify that, but it seems like I am just playing Whack-a-mole.  Here is my newest Makefile (along with all the comments I made inside it to track what the heck I was doing).  

```

CFLAGS = -fprofile-arcs -ftest-coverage -Wall -I../originals
VPATH = ../originals/
#VPATH should cause 'make' to look for source files in that dir (up one, then down, from current);
#Not quite working well, though...  trying further things below...
#OK, added -I<path> to flags to try and fix this...didn't work.  

rngs.o: rngs.c rngs.h
        gcc -c $(CFLAGS) $< rngs.c -g 

#Trying to force rngs.c to use IMPLICIT rules for compilation, thus using the automatic 
#variables, which should include the VPATH paths.  What about flags, though?  Don't need?
#OK, that didn't work.  Giving me failure to find 'rings.h' again.
#Ah...it appears that CFLAGS applies to implicit rules, too!
#OK, new tack:  Using auto-variable $<, 'the name of the first prerequisite'
#Nope...rearranging pre-req files (.h was first, now .c is)
#Doh!  With debugging turned on I figured out that it wasn't this line causing the problems, but a line below that:  dominion.c
# '-g' is the debug flag, bTW

dominion.o: dominion.c rngs.o dominion.h cardDefs.h moreFunctions.h
        gcc -c $^ -g $(CFLAGS)
#       gcc -c dominion.c -g $(CFLAGS)

testAll: dominion.o testSuite.c
        gcc -o testSuite testSuite.c -g -lm dominion.o rngs.o $(CFLAGS)

jjc:  dominion.o unitTests_jjc.c
        gcc -o jjc_tests unitTests_jjc.c -g -lm dominion.o rngs.o -fprofile-arcs -Wall
        #Removed CFLAGS above because don't need to profile unitTests_jjc.c, just Dominion.c 
        #But will that affect the linker?

clean:
        rm -f *.o playdom.exe jjc_tests playdom test.exe test player player.exe testInit testInit.exe *.gcov *.gcda *.gcno

```

My current failure is again with rngs.h file, but it is coming from an #include statement in my .c file this time.  I thought that the "-I<path>" option passed to the compiler (via $(CFLAGS) in the makefile) was supposed to fix that.  (That's a letter 'eye', not an 'ell'.)

Here is the 'make -d' output:
```

   Finished prerequisites of target file `unitTests_jjc.c'.
  No need to remake target `unitTests_jjc.c'.
 Finished prerequisites of target file `jjc'.
Must remake target `jjc'.
gcc -o jjc_tests unitTests_jjc.c -g -lm dominion.o rngs.o -fprofile-arcs -Wall
Putting child 0x01322030 (jjc) PID 4140 on the chain.
Live child 0x01322030 (jjc) PID 4140 
unitTests_jjc.c:5: fatal error: rngs.h: No such file or directory
compilation terminated.

```

Thanks again for your help and patience.  :)

--  J

---

### Post by Vox754 on 2011-02-23
> **jclose said:**
> Thanks for the tip and link; yes, that did help...but revealed other problems.  I did a bunch more messing around without finding a complete solution.
...


I definitely think this should not be too hard to compile. Is this the entire Makefile? It doesn't seem hard.

I suggest you divide the compilation in as many steps as necessary, for example creating many rules for each source file.

For each source file:
```

rngs.o: rngs.c rngs.h
	gcc -c $(CFLAGS) rngs.c -g

```

Once you know it compiles okay each object file, you may link them together and produce the final executable.

```

final : one.o two.o final.o
	gcc -g $^ -o $@

# $^  expands to all the requisites, the three object files
# $@  expands to the name of the target, "final"

```

Use a variable to hold the full path to a file in another directory. Why not? If it's only one object file, it may be easy this way.
```

subdir := some_directory
special_c := ./$(subdir)/two.c
special_o := ./$(subdir)/two.o

$(special_o) : $(special_c)
	gcc -g $^ -o $@

final : one.o $(special_o) final.o
	gcc -g $^ -o $@

```

Another tip is that, if you have many subdirectories with source files, you may have one Makefile in each subdirectory to compile only the files in that subdirectory.

Change to the specified subdirectory and run "make" there:
```

subdir1 :
	$(MAKE) -C ~/originals/
subdir2 :
	$(MAKE) -C ~/j/

```

That should help with the complexity of the paths. It's definitely easier when starting, and it may become unnecessary once you are more experienced with compiling and Makefiles.

Another thing that bothers me about your code is that you are not using the automatic variables correctly and other things.

```

rngs.o: rngs.c rngs.h
	gcc -c $(CFLAGS) **$< rngs.c** -g 
# No need to include the implicit variable "$<"
# and the prerequisite "rngs.c"
# both in the command

```

When creating an object file, you are not actually linking, so there is no need to include other object files, in this case "rngs.o" should be removed.
```

dominion.o: dominion.c **rngs.o** dominion.h cardDefs.h moreFunctions.h
	gcc -c $^ -g $(CFLAGS)
#       gcc -c dominion.c -g $(CFLAGS)

# The automatic variable "$^" includes all prerequisites
# This is the resulting command
#       gcc -c dominion.c rngs.o dominion.h cardDefs.h moreFunctions.h -g $(CFLAGS)

# See? It includes even the headers.
# The second command is actually correct.

```

Here the command includes "rngs.o" but it is not a requisite. Why not? You want to use the newest requisite after all.
```

testAll: dominion.o testSuite.c
        gcc -o testSuite testSuite.c -g -lm dominion.o **rngs.o** $(CFLAGS)

# It is also somewhat confusing when the name of the target
# does not correspond to the actual executable name.
# What about this?

test_suite.o : test_suite.c
test_suite : dominion.o rngs.o test_suite.o
	gcc -g $(CFLAGS) -lm $^ -o $@

# It will try to make the requisite object files
# with implicit rules,
# or with the explicit rules written elsewhere in the Makefile

```

Same here:
```

jjc:  dominion.o unitTests_jjc.c
        gcc -o jjc_tests unitTests_jjc.c -g -lm dominion.o rngs.o -fprofile-arcs -Wall

unit_tests_jjc.o : unit_tests_jjc.c
unit_tests_jjc : dominion.o rngs.o unit_tests_jjc.o
	gcc -g -fprofile-arcs -Wall -lm $^ -o $@

```

See?

Use as much rules as needed. Don't worry about wordiness. Once it works, you may try cut on the size of your Makefile, and write only the strictly necessary rules using clever tricks and Makefile magic.

I could also suggest to use a linker variable, or many variables, depending on your needs:
```

CFLAGS = -fprofile-arcs -ftest-coverage -Wall
LIBS = -lm
FLAGS = -g

exe : requisites.o exe.o
	gcc $(CFLAGS) $(LIBS) $^ -o $@

```

> 
My current failure is again with rngs.h file, but it is coming from an #include statement in my .c file this time.  I thought that the "-I<path>" option passed to the compiler (via $(CFLAGS) in the makefile) was supposed to fix that.  (That's a letter 'eye', not an 'ell'.)

...

Now, it's also very important to check the source code.

The include directives could have many forms, a generic path, or even relative paths:
```

#include <rngs.h>
#include <subdir/rngs.h>
#include "../../rngs.h"
#include "../subdir/rngs.h"

```

Depending on how the include directive is written, you may need to adjust the search flag "-I<path>".

For simple headers included in the same directory as the source code, use double quotes:
```

#include "rngs.h"

# Compile with
gcc -I/my/source_dir/ /my/source_dir/rngs.c

# Or perhaps change to the directory first
cd /my/source_dir/
gcc -I. rngs.c

```

For more general headers, a separate directory may be useful.
```

#include <my_project.h>

cd /my/source_dir/
gcc -I/one/directory/that/has/headers/ rngs.c

```

Were you place source code and header files is entirely up to you. There are not hard rules on this. You, the programmer, are responsible for deciding how the code is to be organized in directories, and you are also responsible for providing the appropriate paths to the compiler, "-I" for header files (.h), and "-L" for already compiled shared libraries (.so).

---


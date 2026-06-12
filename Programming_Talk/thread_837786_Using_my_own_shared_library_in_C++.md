---
title: "Using my own shared library in C++"
date: 2008-06-22
forum: Programming Talk
---

### Post by Andruk Tatum on 2008-06-22
After dinking around a bit with C++, I took a C++ class last semester. I did a small (American English) grammar tool for my final project.  During the project (forced to use Visual Studio) I was compiling into an executable, but now I would like to make it a shared library.  I have the project in its current state thrown up to [launchpad]("http://code.launchpad.net/~andruk/+junk/libgramm/"): 
Feel free to tell me I'm doing it all wrong, as I probably am.  :-D

From what I've gathered, a few parameters to g++ should do the linking for me, but, how to I use the library within the code?  The link1.cpp file is what I will be using to test the library.  Here is an [archive]("http://www.mediafire.com/?gdgzdddgz3s") of all of the files.

Thanks in advance.

---

### Post by dwhitney67 on 2008-06-22
It looks like you need to dink some more with your code.  It does not compile.

A little advice... never use a "using namespace" in a header file.

Here's a Makefile that you can use to build your library:
```
SRCS     = functions.cpp Word.cpp Sentence.cpp
OBJS     = $(SRCS:.cpp=.o)
CXXFLAGS = -Wall -pedantic
LIB      = libgramm.a


all: $(OBJS)
        $(AR) r $(LIB) $(OBJS) 

.cpp.o:
        $(CXX) $(CXXFLAGS) -c $< -o $@
```

To build your test application:
```
SRCS     = link1.cpp
OBJS     = $(SRCS:.cpp=.o)
CXXFLAGS = -Wall -pedantic
LPATH    = -L./gramm/src
LIB      = -lgramm
EXE      = link1


$(EXE): $(OBJS)
        $(CXX) $(OBJS) $(LPATH) $(LIB) -o $@

.cpp.o:
        $(CXX) $(CXXFLAGS) -c $< -o $^
```

Another little bit of advice... refuse to use Eclipse until you fully understand how to develop a software project, associated libraries, and Makefiles by hand.  Don't rely on an IDE  to do this for you, or you will possibly end up learning zilch.

As for the Makefiles, the first part of each Makefile begins with declarations for source file(s), object file(s), compiler flags, and so forth.

Depending on the Makefile shown above, one archives the object files into a library; the other links the library with the sole main program.  In the latter case, the Library Path (LPATH) and the Library itself (LIB) were defined.

The last statement in the Makefile, provides instructions on compiling the source file into object file.

There is a lot more to Makefiles than the basics I presented, so if you are interested, I suggest you find a reference on the web to read/study.

P.S.  You can archive your library any where you choose.  In the Makefile example above, it will be created (providing your code compiles) in the gramm/src directory.

---

### Post by _sphinx_ on 2008-06-23
> **dwhitney67 said:**
> 
A little advice... never use a "using namespace" in a header file.


Why so?
Any harm is doing this thing?

---

### Post by henchman on 2008-06-23
namespaces were invented to encapsulate classes and functions in different 'units' to avoid ambiguous names of these...

if you now put all namespaces together by "using namespace" you again have one big namespace...

---

### Post by _sphinx_ on 2008-06-23
> **henchman said:**
> namespaces were invented to encapsulate classes and functions in different 'units' to avoid ambiguous names of these...

if you now put all namespaces together by "using namespace" you again have one big namespace...

So you mean that we should not use the 
> using namespace at all. Then whats the use of having the namespace. I think it has to something with the header file but I am not getting it.

---

### Post by henchman on 2008-06-23
The use is that you could for example create your own *cout* member in your own namespace called "foo::bar::veryimportantclasses"...

of course you are not very likely to do specifically this, but there may be a name already in use by a member of the ::std namespace which you might want to use one day :)

of course this doesnt mean you mustnt use "using namespace" at all... for example for small projects or a quick hack it would be okay for me.. or if you have the opinion that its okay and the above arguments are too lightweight, just use it, too

---

### Post by dwhitney67 on 2008-06-23
> **henchman said:**
> 
...
if you now put all namespaces together by "using namespace" you again have one big namespace...
This is mildy correct.

_sphinx_ -

Here's the URL for a programming guide that contains the rationale for not putting "using namespace" in a header file:  [http://nepsweb.co.uk/pgtcpp/namespace.htm](http://nepsweb.co.uk/pgtcpp/namespace.htm)

You can find other similar documents, with the same advice, by simply googling.

---

### Post by hojotoolee2 on 2008-06-23
> 
A little advice... never use a "using namespace" in a header file.

that is true, if someone else use your .h file in their project, they are forced to use the namespace you put into the .h file.

that is why you don't want to put "using namespace" in a header file

---

### Post by rnodal on 2008-06-23
I personally don't like using "using namespace" at all. I think it makes code more readable when you see the namespace before the classes or functions. I know that it can be come tedious to type but at the end it will pay off.

---

### Post by dwhitney67 on 2008-06-23
This thread is drifting off course with respect to the "using namespace" issue.  It's a minor thing compared to the original problem the OP sought assistance in solving... and that is how to create a shared library and then use it in a program.

Does anybody have any thoughts on these particular issues that could challenge or improve my original response to the matter?

---

### Post by nvteighen on 2008-06-23
dwhitney's post shows you how have to create a **static** library (.a extension). A **shared** library (.so) is a bit different, as it involves a specific object file format called PIC (Position-independent Code. See [http://en.wikipedia.org/wiki/Position-independent_code](http://en.wikipedia.org/wiki/Position-independent_code)).

You first have to compile source files (.cpp) into object files (.o), but using the -fpic flag:
```

g++ -c -fpic source.cpp -Wall

```

That will produce source.o.

Then, you tell the compiler to create the shared library by invoking the -shared flag to object files. Shared libraries use the lib**(name)**.so convention, so be sure to use the -o flag to set the output file's name. Let's call it "libmylib.so"
```

g++ -shared -o libmylib.so source.o -Wall

```

For some strange reason, output libraries will have execution permissions, which aren't needed. Do a **chmod a-x** to it.

The problem is to get the shared library actually working. You either have to copy it into /usr/lib (you need root privileges and give read permission to all users that will use the library) or start playing with the LD_LIBRARY_PATH environment variable.

To make a program use the library, use the -l(name) flag (drop the lib- part and the .so!), as using any other shared library.

For our fictional libmylib.so *EDIT: Corrected thanks to dwhitney67*:
```

g++ hello.cpp -lmylib -L<library path>

```

That are the basics, I think.

---

### Post by dwhitney67 on 2008-06-23
nvteighen -

Thanks for the correction and for the instructions on building a shared library.

In one little area I disagree with you... to get an application to link with a shared library still requires the user to specify the -L linker option.  Modifying LD_LIBRARY_PATH alone would not suffice.

Of course, one could plop their library into a system folder (e.g. /usr/lib) and afterwards, if necessary, run '/sbin/ldconfig', however both these operations require root-privileges and could lead to disaster if a user-library overwrites a system one.  In other words, I would not recommend it for run-of-the-mill projects.

Btw, if the user-library is stored in user-space, then the LD_LIBRARY_PATH needs to be specified to run the program.  Something like:
```
LD_LIBRARY_PATH=<path-to-library> app
```

---

### Post by WW on 2008-06-23
> **nvteighen said:**
> 

The problem is to get the shared library actually working. You either have to copy it into /usr/lib (you need root privileges and give read permission to all users that will use the library) or start playing with the LD_LIBRARY_PATH environment variable.

In Debian and its offspring (including Ubuntu), it is best to not put your home-grown libraries in /usr/lib; leave that directory for files that are part of packages.  Instead, put the .so (and/or .a) files in /usr/local/lib.

---

### Post by rnodal on 2008-06-23
Also I would recommend leaving the lib in a directory that the user can write modify etc. So if your app lib is not a system library I think you are better off leaving near the executable either in the same folder or in a sub folder. 

-r

---

### Post by hojotoolee2 on 2008-06-23
also add the path to your *.so to LD_LIBRARY_PATH, if your *.so shared library is not in the same path as your exe.

---

### Post by nvteighen on 2008-06-24
> **dwhitney67 said:**
> 
In one little area I disagree with you... to get an application to link with a shared library still requires the user to specify the -L linker option.  Modifying LD_LIBRARY_PATH alone would not suffice.

Yes, your right. -L is needed always except for libraries in /lib and /usr/lib. Thanks for your correction!

> Btw, if the user-library is stored in user-space, then the LD_LIBRARY_PATH needs to be specified to run the program.  Something like:
```
LD_LIBRARY_PATH=<path-to-library> app
```

The issue is that LD_LIBRARY_PATH gets reset after closing the shell, so if you don't want to set it manually each time you either have to:
1) Add "export LD_LIBRARY_PATH=<whatever>" to your .bashrc file.
2) Launch your application through a shell script that sets the environment variable before running the executable. I think how Firefox actually works to be able to launch the user-wide extensions (e.g. Flash installed through Adobe's official script not being root).

---

### Post by rnodal on 2008-06-24
Some compilers allow you to hard code the path to the library saving you from needing a script.

---

### Post by dwhitney67 on 2008-06-24
> **rnodal said:**
> Some compilers allow you to hard code the path to the library saving you from needing a script.
You are correct, but it is not a wise decision to do such a thing.

From [http://gcc.gnu.org/faq.html#rpath:](http://gcc.gnu.org/faq.html#rpath:)
[I]Dynamic linker is unable to find GCC libraries

This problem manifests itself by programs not finding shared libraries they depend on when the programs are started. Note this problem often manifests itself with failures in the libio/libstdc++ tests after configuring with --enable-shared and building GCC.

GCC does not specify a runpath so that the dynamic linker can find dynamic libraries at runtime.

The short explanation is that if you always pass a -R option to the linker, then your programs become dependent on directories which may be NFS mounted, and programs may hang unnecessarily when an NFS server goes down.

The problem is not programs that do require the directories; those programs are going to hang no matter what you do. The problem is programs that do not require the directories.

SunOS effectively always passed a -R option for every -L option; this was a bad idea, and so it was removed for Solaris. We should not recreate it.

However, if you feel you really need such an option to be passed automatically to the linker, you may add it to the GCC specs file. This file can be found in the same directory that contains cc1 (run gcc -print-prog-name=cc1 to find it). You may add linker flags such as -R or -rpath, depending on platform and linker, to the *link or *lib specs.

Another alternative is to install a wrapper script around gcc, g++ or ld that adds the appropriate directory to the environment variable LD_RUN_PATH or equivalent (again, it's platform-dependent).

Yet another option, that works on a few platforms, is to hard-code the full pathname of the library into its soname. This can only be accomplished by modifying the appropriate .ml file within libstdc++/config (and also libg++/config, if you are building libg++), so that $(libdir)/ appears just before the library name in -soname or -h options.[/I]

---

### Post by WW on 2008-06-24
Instead of LD_CONFIG_PATH, you can configure the path with the file /etc/ld.so.conf (or files in /etc/ld.so.conf.d/) and the ldconfig command.  See my post in [this thread](http://ubuntuforums.org/showthread.php?t=466808).

---

### Post by nvteighen on 2008-06-25
> **WW said:**
> Instead of LD_CONFIG_PATH, you can configure the path with the file /etc/ld.so.conf (or files in /etc/ld.so.conf.d/) and the ldconfig command.  See my post in [this thread](http://ubuntuforums.org/showthread.php?t=466808).
Really useful! It works flawlessly and it's much more senseful than changing the environment variable.

The question is, why is that necessary, if **/etc/ld.so.conf.d/libc.conf** already includes **/usr/local/lib**?

---

### Post by dwhitney67 on 2008-06-25
Running 'ldconfig' registers all libraries (including new ones) that have been added to the directories specified in ld.so.conf.d and in the .conf files contained within.  You can see this occurring if you run ldconfig with the '-v' option.

There are instances where the benefits of setting LD_CONFIG_PATH are preferable than relying on ld.so.conf.d.  The most obvious example is when the s/w developer does not have root-privileges!

---

### Post by nvteighen on 2008-06-25
> **dwhitney67 said:**
> Running 'ldconfig' registers all libraries (including new ones) that have been added to the directories specified in ld.so.conf.d and in the .conf files contained within.  You can see this occurring if you run ldconfig with the '-v' option.

I know that... What I meant is that creating the local.conf file is not needed because libc.conf already includes /usr/local/lib, at least in Hardy. So, just copying there and updating the library register is enough!

> There are instances where the benefits of setting LD_CONFIG_PATH are preferable than relying on ld.so.conf.d. The most obvious example is when the s/w developer does not have root-privileges!

Actually, not only developers... but any unprivileged user attempting to compile an application may run into that issue! 

To avoid that, maybe you could include this line in ld.so.conf?

**WARNING: Try only if you know what's this thread is about!!!**
```

$HOME/lib

```

And tell each user to create a 'lib' directory in their home?

---

### Post by dwhitney67 on 2008-06-25
Nice, but it won't work.  When you log in as root or when you use sudo to run 'ldconfig', the HOME environment variable is not the user's home directory, but the home directory of the root account.

Contrary to what is perceived concerning Ubuntu, there is indeed a root account and its home directory is in /root.  Of course, by default the root account's password is disabled (thus preventing a malicious hacker from being one step closer to compromising the system), but nevertheless the account exists.

--- Actually, take that back... apparently when running 'sudo echo $HOME', the grunt-user's home directory is returned.  So maybe your proposal could work.  Still, the grunt-user would have to have privileges to run 'ldconfig'.  Remember, 'ldconfig' builds a listing of the libraries that are added to the designated area(s).  If a new library is added, it will not be found until 'ldconfig' is run again.  Btw, 'ldconfig' is automatically invoked during the initial system startup.

---

### Post by nvteighen on 2008-06-25
Oh, yes... You still need root-privileges to "ldconfig". :p

Drop my proposal, then... or tell people to restart their box after installing, which sounds terribly similar to what another popular OS there always needs...

---

### Post by Andruk Tatum on 2008-06-26
Okay, so I create the .so, then run sudo ldconfig, and then (after putting the directory to the shared library into /etc/ld.so.conf) compile the program that will be linked to the library?

Do I have to put anything into the program (not the library) code?  Or do I just use the functions in the lib?  Do I have to include headers for the library or something?  I keep getting "undefined reference" errors.

Thanks for helping such a noob.  I appreciate it.

---

### Post by dwhitney67 on 2008-06-26
Since it appears that you are still in the middle of developing this application (and its associated library), I would highly recommend that you do not abuse your sudo-privileges!

Create the .so, place the header file(s) for the library in a known place, then compile your application, and finally link the application.

For now, create a local directory structure like:
```

~/MyProject/
            lib/
            include/
            libsrc/
            app/
```

```
$ mkdir -p ~MyProject/{lib,include,libsrc,app}
```

In libsrc, place the header file(s) and the source code of your library.  Also create a Makefile that will build the .so and that will also install the .so in 'lib'.  The Makefile should also install the header file(s) in 'include'.

In app, place your application source code there and a Makefile.  As discussed earlier, you will need to provide the -L option to specify the location of the library (which hopefully is in ~/MyProject/lib).  You will also need to use the -I option (when compiling the application) to specify where the library's header files are located at (~/MyProject/include).

If you do not understand how to create a Makefile, that is ok.  You can do all of this manually from the command line.

For the library:
```
$ cd ~/MyProject/libsrc
$ g++ -c -fpic -Wall -pedantic *.cpp
$ g++ -shared *.o -o libmylib.so
$ install -m 444 libmylib.so ../lib
$ install -m 444 *.h ../include
```

For the application:
```
$ cd ~/MyProject/app
$ g++ -c -Wall -pedantic -I~/MyProject/include *.cpp
$ g++ *.o -L~/MyProject/lib -lmylib -o myApp
```

Once you have everything working, it is up to you if you want to promote your library to the system folders.  The library would normally go in /usr/local/lib and the library header files in /usr/local/include.  After the library is copied (installed) to /usr/local/lib, then you run 'ldconfig'.

If/when you promote your library and its associated header file(s) to the /usr/local area, then your application can be built like:
```
$ cd ~/MyProject/app
$ g++ -c -Wall -pedantic -I/usr/local/include *.cpp  # actually, I am not sure if the -I<path> is needed!
$ g++ *.o -lmylib -o myApp
```

P.S.  Forgive me if there are any typos in the commands above.  Yet another reason to avoid using sudo at this time!

---

### Post by nvteighen on 2008-06-26
It seems you don't need -I/usr/local/include and -L/usr/local/lib, but using them won't hurt.

---

### Post by rnodal on 2008-06-26
> **dwhitney67 said:**
> You are correct, but it is not a wise decision to do such a thing.

From [http://gcc.gnu.org/faq.html#rpath:](http://gcc.gnu.org/faq.html#rpath:)
[I]Dynamic linker is unable to find GCC libraries

This problem manifests itself by programs not finding shared libraries they depend on when the programs are started. Note this problem often manifests itself with failures in the libio/libstdc++ tests after configuring with --enable-shared and building GCC.

GCC does not specify a runpath so that the dynamic linker can find dynamic libraries at runtime.

The short explanation is that if you always pass a -R option to the linker, then your programs become dependent on directories which may be NFS mounted, and programs may hang unnecessarily when an NFS server goes down.

The problem is not programs that do require the directories; those programs are going to hang no matter what you do. The problem is programs that do not require the directories.

SunOS effectively always passed a -R option for every -L option; this was a bad idea, and so it was removed for Solaris. We should not recreate it.

However, if you feel you really need such an option to be passed automatically to the linker, you may add it to the GCC specs file. This file can be found in the same directory that contains cc1 (run gcc -print-prog-name=cc1 to find it). You may add linker flags such as -R or -rpath, depending on platform and linker, to the *link or *lib specs.

Another alternative is to install a wrapper script around gcc, g++ or ld that adds the appropriate directory to the environment variable LD_RUN_PATH or equivalent (again, it's platform-dependent).

Yet another option, that works on a few platforms, is to hard-code the full pathname of the library into its soname. This can only be accomplished by modifying the appropriate .ml file within libstdc++/config (and also libg++/config, if you are building libg++), so that $(libdir)/ appears just before the library name in -soname or -h options.[/I]



I have used this method millions of time across systems with no problems at all. I only hard code my custom shared libraries and not the system ones. So if my program lets say depends in libxxxxyr then when you run the program it will search for that library in a sub folder called lib. 
That way if there is a new version of the library the user ca just copy and paste it there.

-r

---

### Post by Andruk Tatum on 2008-07-19
So, here's my makefile:

```
OBJS = functions.o Sentence.o Word.o

libgramm.so : $(OBJS)
	g++ -shared -Wl,-soname,libgramm.so.1 $(OBJS) -o libgramm.so
	chmod a-x libgramm.so
	cp functions.h libgramm.h

functions.o : functions.h functions.cpp
	g++ -g -c -fPIC -Wall functions.cpp
Sentence.o : Sentence.h Sentence.cpp
	g++ -g -c -fPIC -Wall Sentence.cpp
Word.o : Word.h Word.cpp
	g++ -g -c -fPIC -Wall Word.cpp

.PHONY : clean
clean : 
	rm $(OBJS) libgramm.so

```

Here is the function prototype:
```
extern "C" unsigned int lg_findSentEnd(const std::string&, const int);
```

Here is the function itself:
```
unsigned int lg_findSentEnd(const string& sentences, const int start) {
	// TODO: This can account for quotations if it has the whole sentence!
	unsigned int place = sentences.size();
	string quotes = "";
	
	for(unsigned int i = start; i < sentences.size(); i++) {
		if(quotes != "") {
			if((sentences[i] == quotes[quotes.size()-1])) {
				if(quotes[quotes.size()-1] == '\"') {
					quotes.erase(quotes.size()-2);
					continue;
				} else if(quotes[quotes.size()-1] == '\'') {
					if((i < sentences.size()-1) && ((sentences[i+1] == ' ') || (sentences[i+1] == '\"') || (sentences[i+1] == ','))) {
						continue;
					} else if(i == sentences.size()-1) {
						break;
					}
				}
			}
		} else if((sentences[i] == '\'') || (sentences[i] == '\"')) {
			quotes += sentences[i];
		} else {
			if((sentences[i] == '!') || (sentences[i] == '?')) {
				place = i;
				break;
			} else if(sentences[i] == '.') {
				string caps = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
				bool acronym = false;
				for(unsigned int j = 0; j < caps.size(); j++) {
					if(sentences[i-1] == caps[j]) {
						acronym = true;
						break;
					}
				}
				
				if(!acronym) {
					place = i;
					break;
				}
			}
		}
/*		// Check for an ending punctuation mark and double spaces
		if((sentences[i+1] == '\n') || (sentences[i+1] == '\0') || ((sentences[i+1] == ' ') && (sentences[i+2] == ' '))) {
			if((sentences[i] == '\"') || (sentences[i] == '\'') || (sentences[i] == '!') || (sentences[i] == '?') || (sentences[i] == '.')) {
				place = i;
				break;
			} else {
				continue;
			}
		}
*/	}
	
	return place;
}
```

Here is the test program that calls the shared library:
```
#include <iostream>
#include <string>
#include <dlfcn.h>
#include "/home/student/libgramm/gramm/libgramm.h"

int main() {
    using std::cout;
    using std::cerr;

    cout << "C++ dlopen demo\n\n";

    // open the library
    cout << "Opening hello.so...\n";
    void* handle = dlopen("/usr/lib/libgramm.so", RTLD_LAZY);
    
    if (!handle) {
        cerr << "Cannot open library: " << dlerror() << '\n';
        return 1;
    }
    
    // load the symbol
    cout << "Loading symbol lg_findSentEnd...\n";
    typedef void (*hello_t)();
    
    // reset errors
    dlerror();
    hello_t lg_findSentEnd = (hello_t) dlsym(handle, "lg_findSentEnd");
    const char *dlsym_error = dlerror();
    if (dlsym_error) {
        cerr << "Cannot load symbol lg_findSentEnd: " << dlsym_error << '\n';
        dlclose(handle);
        return 1;
    }
    
    // use it to do the calculation
    cout << "Calling lg_findSentEnd...\n";
    int lg_start = 1;
    unsigned int pos = lg_findSentEnd("That is a lovely cake.  This is a beautiful gate.", lg_start);
    cout << "Position: " << pos << "\n";
    
    // close the library
    cout << "Closing library...\n";
    dlclose(handle);
}


```

Here is the command I use to compile the test program:
```
g++ test.cpp -o test -lgramm
```

And finally, here is the error I have not been able to solve:
```
test.cpp: In function &#8216;int main()&#8217;:
test.cpp:38: error: too many arguments to function
test.cpp:38: error: void value not ignored as it ought to be
```

So, is there something I am missing?  I manually copy libgramm.so into /usr/lib, and chown and chgrp it to student (instead of root).

Thanks in advance.
- Andruk

---

### Post by dwhitney67 on 2008-07-19
That is go to be the first program I have ever seen go through so much effort to "import" a shared library.  I could be wrong... I have been before... but I think you are going about things the wrong way with respect to your main program and how it uses a shared library.

Your main program should look something like:
[PHP]#include "libgramm.h"
#include <iostream>

int main() {
    // use it to do the calculation
    std::cout << "Calling lg_findSentEnd...\n";
    int lg_start = 1;
    unsigned int pos = lg_findSentEnd("That is a lovely cake.  This is a beautiful gate.", lg_start);
    std::cout << "Position: " << pos << "\n";
    
    return 0;
}[/PHP]
When you compile the main program, use a statement like:
```
g++ -I/home/student/libgramm/gramm test.cpp -o test -L/home/student/libgramm/gramm -lgramm
```
The -I instructs the compiler where to locate non-system header files; the -L instructs the linker where to locate non-system library files.

In your Makefile, where you build the libgramm library, clean up the redundancies and simplify:
```
SRCS     = functions.cpp Sentence.cpp Word.cpp
OBJS     = $(SRCS:.cpp=.o)

LIB      = libgramm.so
HDR      = libgramm.h

CXXFLAGS = -g -fPIC -Wall -pedantic
LDFLAGS  = -shared -Wl,-soname,$(LIB).1


$(LIB) : $(OBJS)
	$(CXX) $(LDFLAGS) $^ -o $@
	@chmod a-x $@
#	@install -m 444 functions.h $(HDR)    <--- I don't recommend this!  Rename functions.h to libgramm.h

.cpp.o :
	$(CXX) $(CXXFLAGS) -c $< -o $@

.PHONY : clean distclean

clean : 
	$(RM) $(OBJS)

distclean : clean
	$(RM) $(LIB) $(HDR)
```
I may have other things to suggest, but let me spend some more time researching what you have done versus what I have done in the past.

P.S.  IMHO, it is very difficult to read source code that is tab-indented.  You should consider indenting 2, 3, or at most 4 spaces per block.  Also, you should consider inserting comments so that in 2 days, or perhaps 1 year, you won't forget what the code is doing.

---

### Post by dwhitney67 on 2008-07-19
Ok, rather than fix my last post, here's what I did... and mind you, I don't know what is contained in the Sentence.cpp or Word.cpp files, thus I did not compile these nor are they included in the shared library.

The first thing I did was to rename functions.h to gramm.h.  I also renamed functions.cpp to gramm.cpp.

Here's gramm.h:
[PHP]#ifndef GRAMM_H
#define GRAMM_H

#include <string>

extern "C" unsigned int lg_findSentEnd(const std::string& sentences, const int start);

#endif[/PHP]
Here's gramm.cpp:
[PHP]#include "gramm.h"

unsigned int lg_findSentEnd(const std::string& sentences, const int start) {
	// TODO: This can account for quotations if it has the whole sentence!
	unsigned int place = sentences.size();
	std::string quotes = "";
	
	for(unsigned int i = start; i < sentences.size(); i++) {
		if(quotes != "") {
			if((sentences[i] == quotes[quotes.size()-1])) {
				if(quotes[quotes.size()-1] == '\"') {
					quotes.erase(quotes.size()-2);
					continue;
				} else if(quotes[quotes.size()-1] == '\'') {
					if((i < sentences.size()-1) && ((sentences[i+1] == ' ') || (sentences[i+1] == '\"') || (sentences[i+1] == ','))) {
						continue;
					} else if(i == sentences.size()-1) {
						break;
					}
				}
			}
		} else if((sentences[i] == '\'') || (sentences[i] == '\"')) {
			quotes += sentences[i];
		} else {
			if((sentences[i] == '!') || (sentences[i] == '?')) {
				place = i;
				break;
			} else if(sentences[i] == '.') {
				std::string caps = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
				bool acronym = false;
				for(unsigned int j = 0; j < caps.size(); j++) {
					if(sentences[i-1] == caps[j]) {
						acronym = true;
						break;
					}
				}
				
				if(!acronym) {
					place = i;
					break;
				}
			}
		}
/*		// Check for an ending punctuation mark and double spaces
		if((sentences[i+1] == '\n') || (sentences[i+1] == '\0') || ((sentences[i+1] == ' ') && (sentences[i+2] == ' '))) {
			if((sentences[i] == '\"') || (sentences[i] == '\'') || (sentences[i] == '!') || (sentences[i] == '?') || (sentences[i] == '.')) {
				place = i;
				break;
			} else {
				continue;
			}
		}
*/	}
	
	return place;
}[/PHP]
Here's the Makefile to build libgramm.so:
```

SRCS     = gramm.cpp
OBJS     = $(SRCS:.cpp=.o)

LIBNAME  = libgramm.so

CXXFLAGS = -g -fPIC -Wall -pedantic
LDFLAGS  = -shared

DEP_FILE = .depend

TEST_SRC = main.cpp
TEST_OBJ = $(TEST_SRC:.cpp=.o)
LDPATH   = -L/home/userid/temp
LIBS     = -lgramm
APP      = test_gramm


# Primary Makefile entry point
#
all: depend $(LIBNAME) $(APP)


# Build shared library
#
$(LIBNAME): $(OBJS)
	@echo Linking $@
	@$(CXX) $(LDFLAGS) $^ -o $@
	@chmod a-x $@

# Build test program
#
$(APP): $(LIBNAME) $(TEST_OBJ)
	@echo Building $@
	@$(CXX) $(TEST_OBJ) $(LDPATH) $(LIBS) -o $@

# Build object files
#
.cpp.o:
	@echo Compiling $<
	@$(CXX) $(CXXFLAGS) -c $< -o $@


.PHONY: clean distclean

clean: 
	$(RM) $(OBJS)

distclean: clean
	$(RM) $(LIBNAME)
	$(RM) $(APP)
	$(RM) $(DEP_FILE)


# Build dependencies
#
depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Building dependencies in: $@
	@$(CXX) -E -MM $(SRCS)     >> $(DEP_FILE)
	@$(CXX) -E -MM $(TEST_SRC) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```
Here's the main.cpp:
[PHP]
#include "gramm.h"
#include <iostream>

int main() {
    // use it to do the calculation
    std::cout << "Calling lg_findSentEnd...\n";
    int lg_start = 1;

    unsigned int pos = lg_findSentEnd("That is a lovely cake.  This is a beautiful gate.", lg_start);
    std::cout << "Position: " << pos << "\n";

    pos = lg_findSentEnd("That is a lovely cake.  This is a beautiful gate.", pos+1);
    std::cout << "Position: " << pos << "\n";

    return 0;
}
[/PHP]
To build main.cpp, use the Makefile or to do so manually:
```
$ g++ -I/home/userid/temp -Wall -pedantic main.cpp -L/home/userid/temp -lgramm -o test_gramm
```
Here's how I ran test_gramm:
```
$ LD_LIBRARY_PATH=/home/userid/temp test_gramm
```

---


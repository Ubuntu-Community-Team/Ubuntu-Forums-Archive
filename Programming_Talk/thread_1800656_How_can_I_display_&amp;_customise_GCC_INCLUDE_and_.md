---
title: "How can I display &amp; customise GCC INCLUDE and LIB folders?"
date: 2011-07-09
forum: Programming Talk
---

### Post by vincegata on 2011-07-09
Hello, 

I used to develop with Visual Studio now I switched to Ubuntu, hence the newbie question.

What I found that PATH is stored in file \etc\environment 
If I type "export" in terminal it displays environment variables but I do not see INCLUDE or LIB. (LIBRARY_PATH CPLUS_INCLUDE_PATH)

So, how can I see environment variables that are used by GCC, especially INCLUDE and LIB?

How can I add new headers and libraries using environment variables (not through compiler options)?

How does the GCC finds the header files such as \usr\include\C++\4.5\iostream on the first place if I do not see them in the environment variables?

THX!

---

### Post by dwhitney67 on 2011-07-09
For GCC, the following options may be used to specify header file and library file paths:
```

-I <header file path>

-L <library file path>

-l <libname>

```
Note that for the libname, the "lib" and ".so" (or ".a") are dropped from the name.

When running an application, it may be necessary to tell the app the location of the libraries which it is dependent upon.  Most libraries reside in /usr/lib or /usr/lib64, however different Linux distros like to change things around.  User-developed libraries typicaly exist in /usr/local/lib or other defined location.

Linux uses a library-path cache to denote where common libraries can be found.  'ldconfig' is the app that creates this cache, and to use it, one must be root.  Library locations are defined within files located in /etc/ld.so.config.d (under Ubuntu; may be different for other distro).

For users that lack admin privileges, the environment variable LD_LIBRARY_PATH can be used.  The variable is set to the path(s) of where user-defined libraries are located.  You can define this variable for your environment, or you can define it "on the fly" when you run your app; for example:
```

LD_LIBRARY_PATH=/path/to/my/lib:/path/to/other/lib ./myexe

```
If you have additional questions, please don't hesitate to ask.


P.S.  You do _not_ need to set LD_LIBRARY_PATH to include paths that are in the 'ldconfig' library cache.  You can verify the library paths in the cache by running 'ldconfig -v'.

---

### Post by vincegata on 2011-07-09
Thanks for the reply!

I see with the libraries.

Do you know where does Ubuntu stores paths for INCLUDES?

---

### Post by dwhitney67 on 2011-07-09
> **vincegata said:**
> 
Do you know where does Ubuntu stores paths for INCLUDES?

Typically in /usr/include.  User-developed header files should *not* go in there.  Those should either be placed in /usr/local/include, or in a project folder.

---

### Post by vincegata on 2011-07-10
Besides header files in /usr/include folder (those look like C header files) there are many subfolders with other header files. 
For example, there is /usr/include/C++/4.5 and /usr/include/C++/4.52 but I do not know which one GCC is using.

How can I check/display the exhaustive list of all include folders used by GCC?

How can I add new INCLUDE path, not through compiler option?

Thanks!

---

### Post by dwhitney67 on 2011-07-10
> **vincegata said:**
> Besides header files in /usr/include folder (those look like C header files) there are many subfolders with other header files. 
For example, there is /usr/include/C++/4.5 and /usr/include/C++/4.52 but I do not know which one GCC is using.

Those particular sub-folders are for C++; you can check which version of the GCC C++ compiler you have by issuing this command:
```

g++ --version

```
> **vincegata said:**
> 
How can I check/display the exhaustive list of all include folders used by GCC?

Typically only /usr/include and /usr/include/c++/<version> are included by default.
> **vincegata said:**
> 
How can I add new INCLUDE path, not through compiler option?
Thanks!
You can hard-code the path in your C/C++ source file, but this is a very bad idea.  Alternatively, you can build your own GCC compiler (this is not trivial).

---

### Post by Mr. Picklesworth on 2011-07-10
> **vincegata said:**
> Besides header files in /usr/include folder (those look like C header files) there are many subfolders with other header files. 
For example, there is /usr/include/C++/4.5 and /usr/include/C++/4.52 but I do not know which one GCC is using.

How can I check/display the exhaustive list of all include folders used by GCC?

How can I add new INCLUDE path, not through compiler option?

Thanks!

Edit: I think I probably misunderstood what you were asking for here, but maybe this will help anyway :)

One option is the C_INCLUDE_PATH / CPLUS_INCLUDE_PATH environment variable: [http://gcc.gnu.org/onlinedocs/gcc-4.4.3/gcc/Environment-Variables.html#Environment-Variables](http://gcc.gnu.org/onlinedocs/gcc-4.4.3/gcc/Environment-Variables.html#Environment-Variables)
That one isn't usually set outside gcc, so you just set it to add more paths.

Another thing you may want to look at is pkg-config. pkg-config is a system that groups compiler and linker options you need for a particular development package under one name. So, you can run something like this:
```
gcc myprogram.cpp $(pkg-config --libs --cflags gtk+-2.0)
```
&#8230;and that will add the appropriate command line arguments to build / link with gtk+-2.0. (pkg-config just outputs the command line arguments gcc usually takes, or an error if the package's dependencies are unsatisfied).
pkg-config gets its information from /usr/lib/pkgconfig, so you can just look through there to find all the packages that are available.

---

### Post by vincegata on 2011-07-10
I want to know what are the system-wide include folders. By definition, CPLUS_INCLUDE_PATH is "colon separated list of directories to find out header files for C++ programs." I want to know what that list is.

In Windows there is Environment Variables settings option under Control Panel where I can see and set up PATH, LIB, and INCLUDE env. variables.

So, the /usr/include, /usr/unclude/C++/4.5, and /usr/local/include are hard-coded in GCC?

For example, when I create a new project in Eclipse CDT it shows seven include folders that it looks into. Besides those three, there are also /usr/local/include/backward, /usr/local/include/x86_64_linuxgnu and others. These folders are not anywhere in project settings, I think Eclipse picks them up from the system. So where are those stored, are they also hard-coded?

To add a new include folder I think I can add CPLUS_INCLUDE_PATH into /etc/environment file.

---

### Post by vincegata on 2011-07-10
When I compiled a program from the terminal I included -v (verbose) option. Here is what I got:

#include <...> search starts here:
 /usr/include/c++/4.5
 /usr/include/c++/4.5/x86_64-linux-gnu
 /usr/include/c++/4.5/backward
 /usr/local/include
 /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/include
 /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.

GNU C++ (Ubuntu/Linaro 4.5.2-8ubuntu4) version 4.5.2 (x86_64-linux-gnu)

Where are all those include folders are stored, are they all hard-coded?

My compiler is 4.52, why is it using /usr/include/c++/4.5 folder and not /usr/include/c++/4.52?

THX

---

### Post by Mr. Picklesworth on 2011-07-10
> **vincegata said:**
> When I compiled a program from the terminal I included -v (verbose) option. Here is what I got:

#include <...> search starts here:
 /usr/include/c++/4.5
 /usr/include/c++/4.5/x86_64-linux-gnu
 /usr/include/c++/4.5/backward
 /usr/local/include
 /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/include
 /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.

GNU C++ (Ubuntu/Linaro 4.5.2-8ubuntu4) version 4.5.2 (x86_64-linux-gnu)

Where are all those include folders are stored, are they all hard-coded?

My compiler is 4.52, why is it using /usr/include/c++/4.5 folder and not /usr/include/c++/4.52?

THX

4.5.2 is a symbolic link pointing at 4.5, so it doesn't make any difference in practice. It's a common thing with shared libraries as well, for example, where we have a .so file with the current version in its name and then a bunch of symlinks pointing to it with more general names. (I've never looked into what direction these usually go in, though, or if there's a convention).

I found a documentation page on gcc's include search path: [http://gcc.gnu.org/onlinedocs/cpp/Search-Path.html](http://gcc.gnu.org/onlinedocs/cpp/Search-Path.html)
Looks like you're right that these are hard coded, and specifically available to programs running under gcc.

---

### Post by vincegata on 2011-07-10
I should have also looked at preprocessor documentation.

Thanks a lot for your responses!

---


---
title: "what is the difference between a static and dynamic library"
date: 2011-06-30
forum: Programming Talk
---

### Post by jamesbon on 2011-06-30
Guys I had Googled this and I am getting definitions which are same on all the links.[Here]("http://www.google.co.in/search?hl=en&q=difference+between+static+and+dynamic+libraries&aq=0c&aqi=g-c1g-b1&aql=&oq=diffstatic+and+dynamic+libraries") is what I searched.

I want some real example of some where, where Static and dynamic library is being used.Take for example in Ubuntu where static library is being used and where dynamic library is used?

---

### Post by schauerlich on 2011-06-30
First of all, [http://en.wikipedia.org/wiki/Dynamic_library#Static_libraries](http://en.wikipedia.org/wiki/Dynamic_library#Static_libraries)

When you compile a program, one of the things it does it "link" all of the libraries that it uses. So, for instance, when you do #include <stdlib.h> at the top of a C program, all you do is tell your program that the functions in there EXIST, but you don't actually get the binary executable code for atoi, exit, malloc, etc. This code lives in a library called libc, which is linked automatically by most compilers. If you use some other library, though, you may have to link it manually using the -l option with gcc. 

Now, what does this have to do with static and dynamic? Well, with a static library, the entire library is copied from /lib (or wherever it normally resides) *inside your program*, and the entire executable is spat out, with your code and the library code. With a dynamic library, however, the library is NOT copied. A reference to the library is included in your executable, but the actual library code is not. When you call a function in that library, the C runtime will see if the library you need exists on the current system. If it does, and it's not already in RAM, it will load it up and allow you to use anything defined in it.

Dynamic libraries have several benefits:
[list][*]Smaller executable sizes
[*]Less duplication - multiple programs that depend on the same library only need one copy for the whole system
[*]Less RAM usage - the same library can be shared among different programs running at the same time[/list]

However, it also has some issues:
[list][*]It is slightly slower, as all  the linking must be done at runtime instead of compile time.
[*]It must be able to find the library at runtime if it exists on the system. If it doesn't exist or can't be found, the program can't run.[/list]

The last point is the source of all of those "foo.dll could not be found" errors you used to get on Windows. .dll stands for "dynamically linking library".

---

### Post by BkkBonanza on 2011-06-30
On Linux Dynamic libraries are called "shared" libraries or objects. Often with the extension .so - you'll find lots of them under the path /lib and other places.

---

### Post by Bachstelze on 2011-06-30
> **schauerlich said:**
> 
[*]It must be able to find the library at runtime if it exists on the system. If it doesn't exist or can't be found, the program can't run.[/list]


Also, the library on the system must be compatible with the one that was used to compile the program.  With very unstable libraries whose API often changes (libx264 comes to mind), static linking ensures that the program will still run even after the API has changed dramatically in current versions of the library.

---

### Post by tgalati4 on 2011-06-30
[http://bitnami.org](http://bitnami.org) packages up popular services using static libraries.  Some of these I have running on an old Dapper Drake (6.06) machine.  When you look at the size of each package, they are several hundred megabytes.  That's because they can't rely on any of the libraries of the OS--as they would if they were dynamically linked.

That's how you can get a modern version of WordPress to run on a 5-year-old distro.  Statically-linked libraries means all of the required libraries are bundled with the package.  There are no dependencies on the host system--other than Linux, x86 (Intel-like) architecture, and 32-bit.

---


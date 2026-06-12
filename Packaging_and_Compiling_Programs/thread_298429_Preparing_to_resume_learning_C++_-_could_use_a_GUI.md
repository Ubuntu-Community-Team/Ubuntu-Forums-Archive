---
title: "Preparing to resume learning C++ - could use a GUI"
date: 2006-11-12
forum: Packaging and Compiling Programs
---

### Post by Velotix on 2006-11-12
A simple question: where could I find an appropriate GUI for writing C++ programs? Although Kate is sufficient for Python for most people, I use IDLE as a dedicated GUI for my Python programs, and would like something in the same vein for C++. I'm pretty sure they exist, I just don't know what I'm looking for.

On a side note, what are the key differences between C and C++, etc.?

Thanks for pointing me in the right direction. ^^

---

### Post by hod139 on 2006-11-12
I have been a fan of the [codeblocks]("http://www.codeblocks.org/") IDE lately.  There is no package in the ubuntu repositories, but codeblocks provides deb files in the nightly builds section.

The key difference between C and C++ is that C++ was designed to be an object oriented language based on C (originally called C with classes).  This is why C and C++ syntactically seem so similar.  Further enhances include virtual functions, operator overloading,  templates, and exception handling ([http://en.wikipedia.org/wiki/C++](http://en.wikipedia.org/wiki/C++))

---

### Post by Velotix on 2006-11-12
Forgive the newb question, but to date I haven't installed anything manually in Linux:

I have the Nov 10 nightly build downloaded as a .deb, so now what do I do with it? Run it through aptitude or the like or is it something more like Windows installs I need to do?

---

### Post by kewldude606 on 2006-11-12
Just double click on it.

Or, do dpkg -i <deb file> from the command line.

See here:
[http://monkeyblog.org/ubuntu/installing/#deb](http://monkeyblog.org/ubuntu/installing/#deb)

---

### Post by Velotix on 2006-11-12
*sigh* Got this from command line:

```
Unpacking codeblocks (from .../CB_20061110_rev3202_Ubuntu6_10.deb) ...
[b]dpkg: dependency problems prevent configuration of codeblocks:
 codeblocks depends on libwxbase2.6-0 (>= 2.6.3.2.1.5); however:
  Package libwxbase2.6-0 is not installed.
 codeblocks depends on libwxgtk2.6-0 (>= 2.6.3.2.1.5); however:
  Package libwxgtk2.6-0 is not installed.[/b]
dpkg: error processing codeblocks (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 codeblocks
```

Tried to install these packages and got the following:

```
$ sudo aptitude install libwxbase2.6-0 libwxgtk2.6-0
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
[b]Couldn't find any package whose name or description matched "libwxbase2.6-0"
Couldn't find any package whose name or description matched "libwxgtk2.6-0"[/b]
The following packages have been automatically kept back:
  libavahi-client3 libavahi-compat-libdnssd1 libavahi-qt3-1
  linux-restricted-modules-2.6.17-10-generic
  linux-restricted-modules-common
The following packages have been kept back:
  avahi-daemon info libavahi-common-data libavahi-common3 libavahi-core4
  screen
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

I'm guessing they're in a repository I don't have activated - where would they be? (BTW, I'm specifically using the Edgy nightly build and am running K/Xubuntu* v6.10.)

*i.e. I have both *kubuntu-* and *xubuntu-desktop* installed. I'd have GNOME as well but [*ubuntu-desktop* hates me](http://www.ubuntuforums.org/showthread.php?t=297919).

---

### Post by hod139 on 2006-11-12
They are in the universe repository.  See this site for enabling extra repos: [http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

---

### Post by Velotix on 2006-11-15
A quick question now it's working properly:

CodeBlocks has defaulted to the GNU GCC Compiler and the GNU G++ Compiler isn't listed. Am I right in assuming that this compiler only compiles to C or will it not matter?

If I need to add the correct compiler manually, how do I do this?

---

### Post by hod139 on 2006-11-15
My guess is that they are using the term GCC to stand for gnu compiler collection, and will use gcc for C code and g++ for C++ code.  Seems confusing though, I agree.  If you create a new c++ project, does it work?

---

### Post by Velotix on 2006-11-15
Yes, though my compiled program won't run. Looking at the debug window suggests that the files aren't being forwarded to the compiler in the first place. All I've ever compiled before are VB6 programs and C++ programs in win32, and both of those handled the compiling themselves without any interference from me.

In other words, am I doing something wrong here? I've heard of makefiles but I'm not at all familiar with them, and I'm guessing that's the problem somehow.

---

### Post by hod139 on 2006-11-15
If you output your error messages someone can probably help you get it straightened out.

---

### Post by Velotix on 2006-11-15
Actually, there aren't any errors - it definitely is a makefile problem:

```
-------------- Build: Release in C++ Tests ---------------
Linking console executable: bin/Release/c++test
g++: **no input files**

Process terminated with status 1 (0 minutes, 0 seconds)
0 errors, 0 warnings
```

On the plus side, it's using the C++ compiler. ^^

*looks for a generic makefile if such a thing exists*

---

### Post by hod139 on 2006-11-15
After creating the project, do you add any files to it?  
Project-->Add Files

---

### Post by Velotix on 2006-11-15
D'oh. Even so, it's still not compiling.

```
-------------- Build: Debug in C++ Tests ---------------
[b]Compiling: testcode
g++: testcode: linker input file unused because linking not done[/b]

Linking console executable: bin/Debug/c++test
g++: no input files

Process terminated with status 1 (0 minutes, 0 seconds)
0 errors, 0 warnings
```

Still something I'm not doing here.

I then checked both "Compile File" and "Link File" in the menu (I see this is disabled by default so you can safely omit a file - cool.) and that had some effect, but not the desired one:

```
-------------- Build: Debug in C++ Tests ---------------
[b]Compiling: testcode
g++: testcode: linker input file unused because linking not done

Linking console executable: bin/Debug/c++test
g++: obj/Debug/testcode.o: No such file or directory
g++: no input files[/b]

Process terminated with status 1 (0 minutes, 0 seconds)
0 errors, 0 warnings
```

Under the project's properties the makefile is listed as "Makefile" - that's obviously wrong. Methinks I need to find out how to write a makefile - I bet it's a very simple script.

---

### Post by hod139 on 2006-11-15
I decided to make a new project and write down exactly what I did to get it up and running.  

First I start codeblocks, and then I create a new project

I select
Console Application

In the console application wizard:
Project Title: Test
Folder to create project in: /home/sberard/temp

select next, and on the next screen:
Compiler: GNU GCC Compiler

select next, and on the next screen:
Highlight C++

After clicking Finish, I have a new C++ console hello world application. Codeblocks created and added a main.cpp, and I can press F9 to build and run it.

Does this process not work for you?

---

### Post by Velotix on 2006-11-15
Yes, that works, so why didn't mine (which was also a Hello World test)? I started with an empty project, so what options have to be configured to get the program to correctly compile?

I could attach the duff project files if it would be easier to look at them yourself.

---

### Post by hod139 on 2006-11-15
If you create and empty project, and then add in your your source files, you still have to set up the include and linking requirements of the project.  Go to 
   project-->build options
and you can specify all the include/linking details for your project.  You don't need to touch a makefile.

---

### Post by Velotix on 2006-11-15
Thanks, but even looking at the two projects side-by-side I still can't see any difference between the two.

The only thing I can assume then is that the program has to run from a file called "main.cpp", because that's the only difference I can see.

**EDIT:** Just confirmed this. Bizarre limitation of C++, that.

Also, the .exe files the compiler creates seem to want to run via Python by default when I run them from Nautilus et al. How should I be compiling these files to get them to work properly? As .bin files?

---

### Post by hod139 on 2006-11-16
I guess I'm confused.  Why are you producing .exe files?  Are you running in Windows?

You do not need to have a file called main.cpp, you do need to have a function called main inside one of your files.

> How should I be compiling these files to get them to work properly? As .bin files?
If you are using code blocks you should simply be pressing F9, never specifying a file type.  In fact, the executables produced will have no file extension.  Where are you specifying a file type?

---

### Post by Velotix on 2006-11-16
I guess because CodeBlocks was originally built for win32 and the Linux version is only a port, it's set to .exe by default. I'm not specifying the filetype at all, it just compiles to a .exe. Should I just rename the file and chop the extension off?

**EDIT:** And now the one compiled from my empty project compiled straight to an extensionless file. Weird.

---

### Post by hod139 on 2006-11-22
I'm confused why you would ever be getting a .exe extension from codeblocks in Ubuntu.  Hopefully you have figured it out by now, because I don't think I have an answer.

---


---
title: "how do c++ libraries work under ubuntu"
date: 2008-09-29
forum: Programming Talk
---

### Post by sandro87 on 2008-09-29
i'm starting to learn c++ and i've just enabled g++ compiler under my 7.10 ubuntu. I've been wondering how do the libraries for c++ in ubuntu work (i know something about them but not much)

if there is somebody that has the time to respond to a couple of questions i would be very grateful:

- where are the libraries under ubuntu ? like in what directory, and can i access them, and modify ??
- if i want to know what libraries i already have installed on my computer how do i do it ?
- if i want to add a new library how do i do it (maybe i'm asking too much, so even a link to some good guide is ok too) ?

tnx

---

### Post by lavinog on 2008-09-29
> **sandro87 said:**
> 
- where are the libraries under ubuntu ? like in what directory, and can i access them, and modify ??

/usr/include/c++
it is possible to modify anything on your system, but you REALLY DON'T want to since the libraries are used by other programs.

> 
- if i want to know what libraries i already have installed on my computer how do i do it ?
- if i want to add a new library how do i do it (maybe i'm asking too much, so even a link to some good guide is ok too) ?

tnx
if you don't see anything in /usr/include/c++ you may want to check that build-essential is installed
```
sudo apt-get install build-essential
```
Someone might have better info for you.

---

### Post by Zugzwang on 2008-09-29
> **sandro87 said:**
> 
- where are the libraries under ubuntu ? like in what directory, and can i access them, and modify ??
- if i want to know what libraries i already have installed on my computer how do i do it ?
- if i want to add a new library how do i do it (maybe i'm asking too much, so even a link to some good guide is ok too) ?

tnx

Good questions.
[LIST]
[*]EDIT: You know that libraries come in "two parts", don't you? So there are the "include" files needed for compiling and the "library" files needed for linking and running the program. In this post, I'll talk about the latter.
[*]All the usual libraries are installed into /usr/lib or one of the sub-directories therein. These are however only compiled versions, not the source-code of them. You have to download the source code individually, if you want to modify them. However, *NEVER* copy modified versions of libraries into this directory. This will cause malfunctions of other programs or might render your operating system unusable. Also never copy you own custom libraries there. Some suggest putting them to "/usr/local/lib", however personally I would advise against this - Copy them somewhere in you home directory (or its sub-directories) and refer to them when linking.
[*] For having a look what's on your machines, start synaptic and look at all the lines starting with "lib". These are essentially the libraries installed. You can also simply look at the contents of the /usr/lib folder.
[*] Adding a new library: Here it depends on what you are actually trying to achieve. If you want to use a library without a package in the repositories, compile them somewhere local in you home directory and refer to them when linking. Static linking makes one's life easier. If you want to have your own library included in Ubuntu, make a package and follow the instructions somewhere here (search).
[*] Finally, try to install all libraries you need using the package manager. Only do it the manual way if there are no packages for the library you need. Also note that there is normally to need to actually know the path of those librarys for which there are packages provided when linking. They are either found automatically or are intended to be used with the "pkg-config" tool. For an explanations, search for some tutorial on GTK here. GTK is a windowing toolkit for which one is normally advised to use "pkg-config", so you'll see an example for its usage in such a tutorial.
[/LIST]

---

### Post by sandro87 on 2008-09-29
tnx for reply, was really helpful.

anyway, i'm still wondering about couple of things, mostly about c++.

example, if i create my own small library with a couple of classes that i want to use in some project. In which directory should i put them ? If i put them in subdirectory of my project, and then i also use some standard library like iostream how does the linking work (how does the compiler know in which directory to look for)?

can i put my small libraries in /usr/include/c++ ??

tnx

---

### Post by Zugzwang on 2008-09-29
> **sandro87 said:**
> 
can i put my small libraries in /usr/include/c++ ??


You can, but definitely shouldn't.

So, the process of building your own library would go as follows:
[LIST=1]
[*]Create your librariy in some path, e.g. /home/you/libfoo
[*]Make some include directory in that library path, e.g. /home/you/libfoo/include
[*]compile your library to, lets say /home/you/libfoo/lib/libfoo.a
[/LIST]

Then you can build your programs using that library. Of course you have to tell the compiler where to look. If you just had a single-file project "test.cpp", you would compile it somehow like this:

```
g++ test.cpp -o test -I /home/you/libfoo/include -L /home/you/libfoo/lib -lfoo
```

The "-I" directive adds some *include* paths, the "-L" some library search path and "-lfoo" finally tells the linker to link to "libfoo" found in some of the search paths.

BTW: The *linker* searches in all of the search paths for some library. Please do not mix the compiler and linker. It is somehow a pity that in the GNU tool chain, "g++" is the command for both of them since that somehow distorts the view on that issue.

---

### Post by sanket on 2008-09-29
when i run my c++ program i hav this error

cin out of scope 
cout out of scope

PS:im a amateur programmer.. well wanna be a good programmer.. assist me

---

### Post by Zugzwang on 2008-09-29
> **sanket said:**
> when i run my c++ program i hav this error

cin out of scope 
cout out of scope

PS:im a amateur programmer.. well wanna be a good programmer.. assist me

No thread hijacking, please! If you've got an unrelated question, open a new thread. Anyway, you should definitely start with some tutorial, like for example [http://www.cplusplus.com/doc/tutorial/]("http://www.cplusplus.com/doc/tutorial/") and/or buy or lend a good book. For the actual question, try looking [here]("http://www.cplusplus.com/doc/tutorial/program_structure.html") and watch out for "using". :-)

---

### Post by nvteighen on 2008-09-29
> **Zugzwang said:**
>  Some suggest putting them to "/usr/local/lib", however personally I would advise against this - Copy them somewhere in you home directory (or its sub-directories) and refer to them when linking.


Could you please elaborate on this? I don't see any inconvenient by putting your libraries at /usr/local/lib... You even avoid the hassle of setting the linker LD_LIBRARY_PATH environment variable, what I rather see as an advantage. But I may be missing a point.

---

### Post by dwhitney67 on 2008-09-29
> **nvteighen said:**
> Could you please elaborate on this? I don't see any inconvenient by putting your libraries at /usr/local/lib... You even avoid the hassle of setting the linker LD_LIBRARY_PATH environment variable, what I rather see as an advantage. But I may be missing a point.
There is no advantage or disadvantage.  In some cases developers do not have admin privileges to write to /usr/local/lib (or /usr/local/include), thus they must consider creating their libraries and headers within their project directory (-ies).

P.S.  Setting LD_LIBRARY_PATH is not a "hassle".  If you develop a large application, what is a few more keystrokes?  Just insert/define LD_LIBRARY_PATH into your ~/.bashrc file.

---

### Post by nvteighen on 2008-09-30
> **dwhitney67 said:**
> There is no advantage or disadvantage.  In some cases developers do not have admin privileges to write to /usr/local/lib (or /usr/local/include), thus they must consider creating their libraries and headers within their project directory (-ies).

Yeah, I know that. But that's why I ask Zugzwang why he thinks there's a disadvantage on placing your libraries into /usr/local/lib (supposing you have the rights to do that).

> P.S.  Setting LD_LIBRARY_PATH is not a "hassle".  If you develop a large application, what is a few more keystrokes?  Just insert/define LD_LIBRARY_PATH into your ~/.bashrc file.

I forgot that... :p

---

### Post by dribeas on 2008-09-30
> **nvteighen said:**
> Yeah, I know that. But that's why I ask Zugzwang why he thinks there's a disadvantage on placing your libraries into /usr/local/lib (supposing you have the rights to do that).

Just personal opinion. While being developed it should be in a directory outside of system dirs. Once the lib is stable and if it is of general use for others than the current project you work on, then I would move it to system wide dirs. 

I work in a couple of projects that are quite complex, they have libraries, but just as a way of ordering subsystems. Those libraries are of no use outside these two projects: I don't install them in system wide dirs.

If I work in a general use library, that is in use by other programs, I don't want changes in my code line to break external apps, and thus only stable versions of the library would be moved into system-wide dirs. Note that if you modify, say glibc and place it in /usr/local/lib, then any problem that arises will probably break most of your system.

To me the question is just the opposite: do I want/need the lib to be system wide? If I don't have a really strong yes as an answer then I use user dirs or /usr/local/my_lib_name paths, so that the applications I want to use my lib can use then with LD_LIBRARY_PATH, but the lib does not get in the way of system applications.

We even to this for external libs. Our client requires an specific version of TAO, Boost and QT. We keep those installed in their own directories in /usr/local. Our system uses -I and LD_LIBRARY_PATH to run with those specific libs while the rest of the system uses ubuntu provided versions. It takes a little more effort once (create Makefiles (cmake in our case) scripts for compilation and running scripts for the apps that reset LD_LIBRARY_PATH) but it does not get in the way afterwards.

Then again, that is my rationale and I have not really built any lib that can be used in a general context.

---

### Post by dwhitney67 on 2008-09-30
> **dribeas said:**
> Just personal opinion. While being developed it should be in a directory outside of system dirs. Once the lib is stable and if it is of general use for others than the current project you work on, then I would move it to system wide dirs. 

I work in a couple of projects that are quite complex, they have libraries, but just as a way of ordering subsystems. Those libraries are of no use outside these two projects: I don't install them in system wide dirs.

If I work in a general use library, that is in use by other programs, I don't want changes in my code line to break external apps, and thus only stable versions of the library would be moved into system-wide dirs. Note that if you modify, say glibc and place it in /usr/local/lib, then any problem that arises will probably break most of your system.

To me the question is just the opposite: do I want/need the lib to be system wide? If I don't have a really strong yes as an answer then I use user dirs or /usr/local/my_lib_name paths, so that the applications I want to use my lib can use then with LD_LIBRARY_PATH, but the lib does not get in the way of system applications.

We even to this for external libs. Our client requires an specific version of TAO, Boost and QT. We keep those installed in their own directories in /usr/local. Our system uses -I and LD_LIBRARY_PATH to run with those specific libs while the rest of the system uses ubuntu provided versions. It takes a little more effort once (create Makefiles (cmake in our case) scripts for compilation and running scripts for the apps that reset LD_LIBRARY_PATH) but it does not get in the way afterwards.

Then again, that is my rationale and I have not really built any lib that can be used in a general context.
+1

This is excellent advice.  Too bad it is buried two pages into a thread.  The next newb on the block probably won't find it.

---


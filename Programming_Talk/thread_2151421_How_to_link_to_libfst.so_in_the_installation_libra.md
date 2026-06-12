---
title: "How to link to libfst.so in the installation library directory?"
date: 2013-06-04
forum: Programming Talk
---

### Post by DreeDrunk on 2013-06-04
Hi there,

I am trying to learn to get along with openfst but I am standing at the beginning. My question is perhaps very simple but I did read a lot before posting here but didn't comprehend how that's related to my problem:

On [http://www.openfst.org/twiki/bin/view/FST/FstQuickTour#OperationExample](http://www.openfst.org/twiki/bin/view/FST/FstQuickTour#OperationExample) I do not understand the following line:
> The OpenFst library is a C++ template library. From C++, include <fst/fstlib.h> in the installation include directory and link to libfst.so in the installation library directory. (You may instead use just those include files for the classes and functions that you will need.)

I would be very glad if someone could help me out.

Greetings,
Dree

PS Because this is my first post here: I am very fond of Ubuntu and want to thank the people who contributed to this great project :D.

---

### Post by dwhitney67 on 2013-06-04
You can download the FST library source code from this page:  [http://www.openfst.org/twiki/bin/view/FST/FstDownload](http://www.openfst.org/twiki/bin/view/FST/FstDownload)

Once you have downloaded the tar.gz file (called openfst-1.3.3.tar.gz) to your favorite location (e.g. Downloads), you will need to un-compress the package and build the library.

Here's some basic instructions:

```

$ cd Downloads

$ tar xzf openfst-1.3.3.tar.gz

$ cd openfst-1.3.3

$ ./configure --prefix=/home/you/usr   # see note below

$ make

$ make install

```
Note:
If you have admin privileges on your Ubuntu system, you may wish to install OpenFST library under system folders (e.g. /usr or /usr/local).  This is not required, but it useful should you wish to allow other developers on your system to use the library.  It also will make building user applications slightly easier.  If you opt for installing OpenFST under a system folder, remove the "--prefix" statement from the "configure" command.  You will also need to run the "make install" using "sudo".

After you have installed OpenFST, you should be able to use it to compile/link your application.  Use the GCC options -I (uppercase eye) to specify the location of the header file(s), the -L option to specify the location of the OpenFST library, and -l (lowercase ell) to specify the library itself.  For example, assuming OpenFST is installed in /home/you/usr:
```

g++ -I/home/you/usr/include MyApplication.cpp -L/home/you/usr/lib -lfst -o myapp

```
If you have opted to install OpenFST within the system folders, then you may be able to get away with building your application using something similar to:
[code
g++ MyApplication.cpp -lfst -o myapp
[/code]

P.S.  I do not know anything else about OpenFST (nor do I care to).  I was able to compile, and install the package on a Kubuntu 12.04 x86-64 system, using GCC 4.6.3.

---

### Post by DreeDrunk on 2013-06-05
Thanks for your extensive help, dwhitney67!

I did install the program before. And I did it without a special prefix, so the files are located in /usr/local/... Did I get you right, that you prefer this location for the files? (I am a bit confused, because I don't have the directory /home/you/usr, you specified in your post.)

I do get the same error messages from the compiler, with or without the ```
-lfst
```. So is it possible, that this link is already made by the system? Does the GCC know, where to look for the libraries when I write something like ```
#include <fst/fstlib.h>
```. So it is globally set for GCC to look in the system files? Isn't this kind of ineffective to search every time there is such an #include-tag?

@dwhitney67: Could you please send me your testfile with which you compiled something? So I have an example to look for my mistakes. I only took an example from the openfst-site, but it is not complete I think. I did get an error like: "fst does not name a type". On sites like that one [http://stackoverflow.com/questions/3608305/class-name-does-not-name-a-type-in-c](http://stackoverflow.com/questions/3608305/class-name-does-not-name-a-type-in-c), where the same error occured, is talked about header files (which the user wrote by himself which is not the case here), but I cannot understand what my mistake is.

Thanks again!
Dree

PS I am using Ubuntu 12.04 x86-64.

Attached: Some Code I am trying to compile:
```
#include <fst/fstlib.h>
namespace fst {

// A vector FST is a general mutable FST 
StdVectorFst fst;

// Adds state 0 to the initially empty FST and make it the start state. 
fst.AddState();   // 1st state will be state 0 (returned by AddState) 
fst.SetStart(0);  // arg is state ID

// Adds two arcs exiting state 0.
// Arc constructor args: ilabel, olabel, weight, dest state ID. 
fst.AddArc(0, StdArc(1, 1, 0.5, 1));  // 1st arg is src state ID 
fst.AddArc(0, StdArc(2, 2, 1.5, 1)); 

// Adds state 1 and its arc. 
fst.AddState();
fst.AddArc(1, StdArc(3, 3, 2.5, 2));

// Adds state 2 and set its final weight. 
fst.AddState();
fst.SetFinal(2, 3.5);  // 1st arg is state ID, 2nd arg weight

}
```

---

### Post by dwhitney67 on 2013-06-05
If you have the OpenFST library installed in /usr/local, then you will need to employ the use of the GCC options -I (uppercase eye) and -L as I previously mentioned.

For example:
```

g++ -I/usr/local/include MyApplication.cpp -L/usr/local/lib -lfst -o myapp

```

P.S.  On some systems (e.g. mine), I do not need to specify the location of libraries that are in /usr/local/lib.  This is because I have included that location in my system's ldconfig cache.  If you have interest in doing the same on your system, please open a new thread specifically querying about this topic.

---


---
title: "Objective C on linux?"
date: 2009-04-27
forum: Programming Talk
---

### Post by Zargoon on 2009-04-27
Hey.  I'm about to start interning with a start-up company whos entire model is currently based off of Objective-C.  What I was wondering is if this language will run on other platforms, namely ubuntu and windows.  Thanks!

---

### Post by jespdj on 2009-04-27
[Objective-C](http://en.wikipedia.org/wiki/Objective-C) can also be compiled by gcc on Linux and Windows.

---

### Post by Zargoon on 2009-04-27
Cool.  But I'm being told that the existing platform that I'm going to be working with cannot be compiled on linux because there are "mac os calls" that won't run on linux.  Is there a way around this?

---

### Post by cabalas on 2009-04-27
If they are Mac OSX specific calls then chances are there isn't a way around this natively. It might be worth looking into [GNUStep]("http://www.gnustep.org/"). Theoretically you **could** install Mac OSX into a virtual machine and run it there - but (to the best of my knowledge) doing so is in violation of the OSX EULA which I believe states that you can only run OSX in virtual machines on a machine already running OSX (or something similar).

---

### Post by soltanis on 2009-04-28
Using Mac-specific stuff, you're going to have to be running in a Mac environment. Unless the application is compatible with GNUStep (which should be encouraged, but what kind of company listens anyway), you're out of luck, and are going to have to use a Mac to develop.

---

### Post by nvteighen on 2009-04-28
Let's see very carefully. If you want to use Objective-C, just follow this How-To [http://ubuntuforums.org/showthread.php?t=1064045](http://ubuntuforums.org/showthread.php?t=1064045) That's all you need to compile an Objective-C program.

**But,** you surely know ObjC is quite useless without the OpenStep libraries. OpenStep is an open standard and Apple NeXTStep is just one implementation (though the original which lead to the standard), just like GNUStep is. So, are you sure those "OSX calls" you mean aren't just calls to the OpenStep libraries? Ok, you won't have NeXTStep in GNU/Linux, but you can use GNUStep and it should work. For that, do:
```

sudo apt-get install gnustep-devel

```

(Or install gnustep, though that will install the whole environment not just the libraries and will clutter your GNOME menus a lot...)

The docs (/usr/share/doc/gnustep-base-doc) have enough information to compile GNUStep-based programs.

But, if your code is actually interfacing to Mac OS X's API (e.g. Cocoa), then, you are pretty much lost without a Mac OS X system... It's like trying to access Windows's API in a GNU/Linux system. Or trying to use Linux's API in a Mac... Also, the executable format will be different (OS X: Mach-O; GNU/Linux: ELF)

---

### Post by UBForty on 2009-05-01
In order to build existing Objective-C code, you need three components:

1) an Objective-C compiler
2) an Objective-C runtime
3) the class libraries which the code you want to port is using


The compiler is the easiest part. There are a number of Objective-c compilers around, all of which are cross-platform:

- the objective-c front-end in GCC

this can target any platform which is supported by CGG as a target

- Clang, a new fast compiler for C, Objective-C and C++ for LLVM

this can target any platform which is supported by LLVM as a target

- Portable Object Compiler, aka PoC

this can target any platform for which an ANSI-C compiler is available, it generates C code

- the original Stepstone compiler

this, too was a preprocessing compiler for C, I heard it can still be found, maybe google will find it for you

Note, that the compiler back-end will take care of executable formats (e.g. MachO versus ELF) for you, so that is of no concern to you whatsoever.


The runtime isn't much of an issue either. There is an open source runtime for the GCC compiler but that requires GCC to build, so on Windows you would need something like MinGW to build and use it. But of course that won't be an issue when you target Linux as the GCC toolchain is default anyway. IIRC the PoC compiler has its own runtime, too.


The class libraries, called Frameworks in Objective-C lingo, are most likely the biggest challenge when porting MacOS X code. In principle, GNUstep will provide you with all the classes provided by Cocoa and they are designed to be drop-in compatible. In practise, however, Apple has many more developers than the GNUstep team and they keep adding new classes. That means that right after a new major SDK release from Apple, GNUstep will lack the classes which Apple has just added, and it will take a little while until the GNUstep team can add those to GNUstep.

The OpenStep API, on which Cocoa and GNUstep is based was designed to be platform independent and that hasn't really changed. The frameworks hide all the platform specific details from your Objective-C code. Unfortunately though, many MacOS X applications are not written with a policy only to use the Cocoa API. Every once in a while a developer may use a system call from another API called Carbon, which is Apple's legacy API, initially provided to make it easier for developers to bring their code from the classic MacOS to MacOS X.

If the code base you want to port contains many such Carbon API calls, then you will need to replace them with Cocoa equivalents or with Posix system calls, etc etc.

There is also another slight difference between Cocoa and GNUstep. OpenStep was designed with two user layers only, the Foundation and Application layer. GNUstep follows this. However, when Apple was working on the early MacOS X, it was a big challenge to bring all the developers along who had all their code using the classic Macintosh API (called the Macintosh Toolbox). Mr. Jobs wanted to get rid of this in a clean sweep, but most of the developers were up in arms. So a compromise was found in the aforementioned Carbon API, which contains about 60 or 70% of the old Toolbox API calls. Yet, understandably and sensibly, Apple didn't want to waste development resources and so they decided to build a low level API called Core Foundation which was to form the basis for both Carbon and Foundation (the lower user layer of Cocoa, just as in OpenStep). A number of Foundation calls can be mapped 1:1 to Core Foundation calls. Apple calls this "toll-free bridged". Any CF API calls for APIs which are toll-free bridged can easily be replaced with Foundation calls.

The code you want to port might be using non-toll-free bridged Core Foundation calls, though. Those are not available in GNUstep. So, even if your colleagues say "No, we don't use Carbon here" there may still be some API calls which are not strictly OpenStep. Ask if they are using Core Foundation calls directly. If they did, check if there are any non-toll-free-bridged ones. Eeven then, there are some ways around that, too.

Apple had released an open source package called CFLite (Core Foundation Lite), it looks like it has since been abandoned but it should still be around somewhere, Core Foundation API calls don't change, so even an older copy should be alright. If I am not mistaken, Apple has since licensed Core Foundation under their APSL license, which is like a BSD license but with restrictions that you can't use Apple's brand and product names for your own stuff, in practise this will not be a problem but legally the clauses that establish this are incompatible with the GPL. This is a little silly, because the restrictions don't really limit your freedom to use and modify the software, and even with the GPL, you can't use Red Hat trademarks for example, regardless of the GPL. The difference is that in the case of the APSL, the restrictions are written into the license, in the case of the GPL, the restrictions are imposed by trademark law, which the GPL does not circumvent. The net effect is the same, but legally it makes the APSL incompatible with the GPL, although I am not a lawyer, so don't take my assessment of what the APSL means for granted, ask your legal people.

There is also an open source project called libFoundation which provides a BSD licensed API that is compatible with Foundation and IIRC this has drop in replacements for CF calls, at least some, or so I think. You may want to check out how much libFoundation will be of help to your effort.

However, don't be discouraged. There are quite a few applications which can be compiled without modifications on Linux under GNUstep and MacOS X under Cocoa and even on Windows under Cocotron (an OpenStep implementation for Windows). So, this is being done all the time and it is probably worthwhile throwing out the legacy Mac API calls anyway.

Note, that Apple is phasing out the Carbon API. They have announced that they will not make Carbon 64bit, so all the Carbon based applications will be stuck with 32 bit forever. Chance is that this is only the tip of the iceberg and once enough developers have converted there code to Cocoa, then Mr. Jobs may pull the plug on Carbon altogether. Apple has a history of dropping things more radically than most other vendors: No floppy disks when the iMac was introduced. No more ADB keyboards and mice when USB was introduced. Initially, they didn't even want to support the classic Mac API at all. In other words, if that code base contains any legacy calls, you probably want to get rid of them anyway.

Last but not least, there is a mailing list called cocoa-dev, which is a very good resource even if you want to port away from the Mac OS X. Of course there is also the GNUstep-developer mailing list, which is a good resource too, but fewer subscribers. I recommend you subscribe to both lists.

good luck

---

### Post by Marco A on 2009-05-01
.

---

### Post by UBForty on 2009-05-01
> **Marco A said:**
> Some questions from your post.

If building Objective-C code requires the Objective-C runtime, I think this means no to statically compiles.

Static compilation, is it possible?

Is it a runtime environment like Java has? a virtual machine?

The short answers are No and No.

But maybe that isn't entirely satisfactory because not knowing how Objective-C does its thing, it may seem a little confusing without further explanation.

It helps to remember that Objective-C is a hybrid between Smalltalk (dynamic typing and late binding) and C (static typing and binding). Because of this, Objective-C is both static and dynamic and both statically bound and late bound. This may sound confusing too, and it probably requires some further explanation too.

Objective-C is a strict superset of ANSI-C, so any vanilla ANSI-C program is also a correct Objective-C program (without any #ifdef __cpluplus {" wrappers and such). Such a vanilla C program is compiled and linked just like any other C program. You can do whatever you can do when you use vanilla C, you can link statically, you can link dynamically etc etc.

When you use the Objective-C language extensions in your program, then still, all your vanilla C code which doesn't use the language extensions will follow the same rules and be subject to the same constraints as your vanilla C only program.

Where you have used the Objective-C language extensions in your program, things get a little more interesting. Important to note in this regard is that the extensions are all related to creating and using Objective-C classes. So anything you do in an Objective-C program which isn't vanilla C will either declare or define a class and/or add methods to one, or it will call a method of a class (in Objective-C lingo this is called sending a message).

The declaration and definition of classes and the sending of messages to them in Objective-C follows different rules. The classes live inside the Objective-C runtime, but the runtime is not a virtual machine. The runtime is simply a library which manages Objective-C classes and method calls. This is needed because the object model of Objective-C (following Smalltalk) is reflective and late bound (dynamic message dispatch).

For instance, you can add methods to an existing class (or override them) *at runtime* without subclassing the class and without even having the source code. The Objective-C runtime is what keeps track of classes and their methods and accepts calls to add new classes and new methods while the program is running. Unlike the Java VM, it does *not* provide a virtual CPU on which to execute the code. All Objective-C code is always compiled into the machine code of the target architecture, it is not interpreted. The runtime is needed to manage the dynamic features which would otherwise have been lost by the fact that the code had been compiled into machine code.

Therefore, yes, you can link your code statically or dynamically, but that will not have any effect on the the object oriented parts in your code, because they will nevertheless be registered with the Objective-C runtime *at runtime* and the method calls will be dynamically *dispatched* even if the code that implements them had been statically linked.

Think of it like an embedded dynamic scripting language, say Python, inside an old fashioned programming language, say C, where the Python functions aren't interpreted by the Python VM but compiled by the C compiler into machine code. The calling and replacing of your Python commands still happens in a dynamic fashion, but the code that is being executed has all the characteristics of C code because it had been compiled. Most Lisp implementations provide an environment where code can be both interpreted or compiled as chosen by the programmer, Objective-C just so happens to always compile code but *invoke* some of it like it would be invoked with an interpreter/VM.

---

### Post by nvteighen on 2009-05-01
There's actually no "Objective-C runtime", as it compiles to native binary... what you have to do is to link to the ObjC Library (libobjc.so in GNU/Linux) plus the C Standard Library (libc.so). This is not because the binary code produced by the compiler is not native and has to be interpreted (e.g. Java), but because the Objective-C calls, when compiled, are translated into regular C function calls that are available at the libobjc.so library.

I guess you can static link libobjc by using gcc's -static flag... Though I don't know if its advisable or if there even is a static version of this library available (libobjc.a)

---

### Post by jimi_hendrix on 2009-05-01
> **cabalas said:**
> Theoretically you **could** install Mac OSX into a virtual machine and run it there - but (to the best of my knowledge) doing so is in violation of the OSX EULA which I believe states that you can only run OSX in virtual machines on a machine already running OSX (or something similar).

yeay for stupidity!

that EULA is mean

---

### Post by UBForty on 2009-05-01
> **nvteighen said:**
> There's actually no "Objective-C runtime", as it compiles to native binary... what you have to do is to link to the ObjC Library

It's a library, yes, but it *is* called Objective-C runtime in all the literature and always has been. Also, the use of the term runtime meaning a runtime library *predates* virtual machines by at least a decade if not more. It is therefore incorrect to assume that runtime==vm and to say that there is no runtime because its not a virtual machine.

---

### Post by nvteighen on 2009-05-01
> **UBForty said:**
> It's a library, yes, but it *is* called Objective-C runtime in all the literature and always has been. Also, the use of the term runtime meaning a runtime library *predates* virtual machines by at least a decade if not more. It is therefore incorrect to assume that runtime==vm and to say that there is no runtime because its not a virtual machine.
Ok, thanks for the correction!

---

### Post by skullmunky on 2009-05-01
UB40, just wanted to say thanks for that terrific explanation - so many things make a lot more sense to me now.  Now I also get why objective-c is important and cool!

---

### Post by msdark on 2009-06-16
someone have installed?

i have a lot of problems compiling CoreFoundation in my Ubuntu 9.04.

I was trying to install pyobjc to build iphone/ipod touch applications with pure python in my Linux machine, but i need to install Core Foundation (or CF-Lite) first but i have a lot of errors when i try to compile...

Somebody have this running?

(Sorry for my english)

---

### Post by ullazusman on 2009-08-30
> **msdark said:**
> someone have installed?

i have a lot of problems compiling CoreFoundation in my Ubuntu 9.04.

I was trying to install pyobjc to build iphone/ipod touch applications with pure python in my Linux machine, but i need to install Core Foundation (or CF-Lite) first but i have a lot of errors when i try to compile...

Somebody have this running?

(Sorry for my english)

Hiya, follow the steps on this page: [http://gnustep.made-it.com/BuildGuide/#THE.GNUSTEP.SOURCES](http://gnustep.made-it.com/BuildGuide/#THE.GNUSTEP.SOURCES) and you most likely won't have any problems. Also try and install the dependencies on the webpage: [http://gnustep.blogspot.com/2005/12/gnustep-on-ubuntuppc.html](http://gnustep.blogspot.com/2005/12/gnustep-on-ubuntuppc.html) it will surely help.

A quick question, don't you need an iPhone SDK to be able to write iPhone apps?

Cheers!

---


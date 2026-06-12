---
title: "what are bindings?"
date: 2007-09-13
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2007-09-13
I am novice in programming so try to understand me!!!(I think I know some basic stuff and how C++ works)

What are bindings? 

If a project(like gstreamer) doesn't have bindings for C++, does this mean that I can't write in C++(to use gstreamer)?

thank you for your time.

---

### Post by pmasiar on 2007-09-13
we were just talking in the other thread how easy is answer any question by searching wikipedia:

[http://en.wikipedia.org/wiki/Binding_%28computer_science%29](http://en.wikipedia.org/wiki/Binding_%28computer_science%29)

---

### Post by Awalton on 2007-09-13
Bindings are a way of using one library written in one language (usually C or some other low level language) in another (usually a higher level language like Python or C++ or the like). Some language require bindings in order to use them (Python), others don't (C++).

You can use Gstreamer from a C++ project rather easily, C and C++ work together really well, and there are C++ bindings available:
[http://gstreamer.freedesktop.org/bindings/cplusplus.html](http://gstreamer.freedesktop.org/bindings/cplusplus.html)

Hope that helps.

---

### Post by SledgeHammer_999 on 2007-09-13
@pmasiar I'll take a look into that

@Awalton you say that C++ doesn't require bindings, but gstreamer has bindings for it. Also, the site says that these bindings are under development, that's why I asked if needed bindings for gstreamer and C++.

---

### Post by aks44 on 2007-09-13
> **SledgeHammer_999 said:**
> you say that C++ doesn't require bindings, but gstreamer has bindings for it.

C++ doesn't *require* bindings to C libraries (aka "wrappers" in the C vs C++ context), as it can use those libraries *as is*.

However, C++ paradigms don't mix really well with C ones, so such bindings are rather a matter of comfort (and code safety as well), in this case their goal is to shield the C++ programmer from the C concepts, and present him a true C++ library.

---

### Post by Awalton on 2007-09-13
> you say that C++ doesn't require bindings, but gstreamer has bindings for it

Well, there's a difference between "need" and "want"; with bindings you can do neat things like Gstreamer::Object.Method(var1, var2), without them you have to do gstreamer_object_method_name(var1, var2).

Some bindings will do a lot of setup work in the background that will make it a lot easier for you to use them; in the example above, if you threw in "using namespace Gstreamer;", you could just do Object.Method().

The biggest problem with most bindings is that Gstreamer and glib and gtk+ use a different object model (gobject) that doesn't really mesh well with C++, so you still end up having to do a lot of verbose commands in a lot of cases, but in the end having bindings in C++ usually makes life easier. If you're familiar at all with C#, you might want to look into Vala, which is like C# implemented using the gobject  model.

And of course, if you write valid C, your C++ compiler will compile it, so if you don't want to use the C++ GStreamer bindings, you can just code it in straight C, just don't expect GStreamer to play nice with C++ objects (you lose a lot of the greatness of C++ by doing it that way).

---

### Post by SledgeHammer_999 on 2007-09-13
ok thank you I think I understand why C++ bindings are good.

But I don't quite understand what bindings are. And the wikipedia article isn't helping.
In my mind this is how I understand bindings so far(I'm a noob, remember? ):
let's say that Gstreamer gives me 3 functions for accomplishing 1 specific task. But I need to call all these 3 functions in my code in order to accomplish the task.So I make a fourth function which handles the other 3 functions.So now I only call function number 4. To my mind function number 4 is the "binding".
Am I close?

---

### Post by aks44 on 2007-09-13
> **SledgeHammer_999 said:**
> let's say that Gstreamer gives me 3 functions for accomplishing 1 specific task. But I need to call all these 3 functions in my code in order to accomplish the task.So I make a fourth function which handles the other 3 functions.So now I only call function number 4. To my mind function number 4 is the "binding".
Am I close?

Almost. ;) Although I'd rather call that a "wrapper".

A binding would rather be some kind of "bridge" allowing you to call from language X a function which was written in another (incompatible) language Y.

Some bindings are just plain equivalents to the original library (ie. a one-to-one mapping), but most are also wrappers that make the original library "fit better" in the destination language's concepts.

Back to the C vs C++ thing, in my POV C++ bindings for C libraries simply don't exist, since C++ can natively call C functions. However there *is* a need for wrappers, to "translate" C concepts to C++ ones (mainly, resource management and exception safety).


Hope I was not too confusing. :)

---

### Post by SledgeHammer_999 on 2007-09-13
> **aks44 said:**
> 
A binding would rather be some kind of "bridge" allowing you to call from language X a function which was written in another (incompatible) language Y.

Well, that "bridge" in what language will be written? In X or Y or Z?

---

### Post by aks44 on 2007-09-13
> **SledgeHammer_999 said:**
> Well, that "bridge" in what language will be written? In X or Y or Z?

It depends on the features & architecture of the languages involved.

As an example, Python itself is written in C, so a Python binding for a C library could be written in C too.

If you wanted to write a Python binding for a pure C++ library, the task would be harder. Since C can't call C++ code as is, first off you'd have to write a C++ to C binding (using C++), then write a C to Python binding in C (note: I know this seems to contradict my previous post, but I really meant "C++ can call C code natively", while the reverse is not true).

Depending on the languages involved, you may have to go as far as resorting to assembly (eg. to convert between different call conventions).


(Someone please correct me if I'm talking BS about Python internals, I don't really know it under the hood. But anyway even if I messed up some details about Python internals, the reasoning is correct so you get the basic idea.)

---

### Post by SledgeHammer_999 on 2007-09-13
oh I see. Do you care do go further? Are these functions, which need "bindings", considered API?

---

### Post by aks44 on 2007-09-13
> **SledgeHammer_999 said:**
> oh I see. Do you care do go further? Are these functions, which need "bindings", considered API?

There's another thread currently going on about what APIs are exactly: [http://ubuntuforums.org/showthread.php?t=548495](http://ubuntuforums.org/showthread.php?t=548495)

I didn't fully read it but from what I've seen it is quite informative.

And I'm gonna sleep, gotta work in 8h30... ;)

---

### Post by SledgeHammer_999 on 2007-09-13
ok no problem. I thank very very much for your help and your time!!!!

---

### Post by the_unforgiven on 2007-09-14
I'll try to pitch in for aks44... ;)

As aks44 said, language bindings are required for two incompatible languages - because each language has its own ways of defining and implementing programming concepts like variable definitions, functions, calling conventions (i.e. how functions are to be called - the way parameters are passed to the function, the way the values are returned from the function), the way the compiler generates symbols in the binaries etc.

Lanugage bindings provide a mechanism for mapping such implementation details of one language (source language) to another language (target language).

For example, python allows runtime type association whereas C/C++ doesn't. So, we need to provide a way to map python types to C/C++ types - especially, higher level types like lists, dictionaries etc.

Most of the low-level stuff (libraries etc.) is written in C/C++ for performance reasons - but to make life easier for application development on top of these libraries, we need to be able to use those libraries with other languages too. This is where the bindings come in.

Say, you've written an MPEG decoder in C/C++ (for performance reasons); now, you want to call it from a python app (PyGtk/PyQt are very easy toolkits to write GUI apps). So, in this case you'd need to generate the python bindings for your MPEG decoder library so that it can be called from the python app - because the constructs you define in your python code need to be passed onto C/C++ code (and vice versa).

Also, python can be implemented in different languages - the one we normally use and which is officially supported by python.org is CPython. But there are implementations written in Java (Jython) as well.

I have used python as an example - the same things apply to other languages too - like perl, PHP, Java (using JNI) etc.

Hope this clarifies some of your doubts. ;)

PS: The C binding for C++ code (C++ code being called from C) is simple **extern "C"** prefix - so to speak ;). This is because of C++ [name mangling]("http://en.wikipedia.org/wiki/Name_mangling").

---


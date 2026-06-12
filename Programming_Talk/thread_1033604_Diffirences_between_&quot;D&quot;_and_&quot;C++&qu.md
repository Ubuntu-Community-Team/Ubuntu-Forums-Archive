---
title: "Diffirences between &quot;D&quot; and &quot;C++&quot;"
date: 2009-01-07
forum: Programming Talk
---

### Post by Kilon on 2009-01-07
First some questions

1) Can C++ Libraries used by D as they are with no wrappers

2) Can Python work well with D instead of C/C++

3) what are the disadvantages and what the advantages

I have recently discovered this porgramming language and it stimulated my curiosity.

I also discovered PyD which answers partly my question No 2 but I still need personal experiences on the matter. Things could look good on paper , but on practice things differ. 

[http://www.digitalmars.com/d/2.0/comparison.html](http://www.digitalmars.com/d/2.0/comparison.html)

[http://pyd.dsource.org/](http://pyd.dsource.org/)

---

### Post by snova on 2009-01-07
Glad to find another programmer interested in D. I think it's a very nice language, if only it had a bit more library wise...

I haven't used it much, though. (Should come up with a small project and try to write it with D)

1. No, not to my knowledge.

2. Yes. The Python API is in C, so you can do it the same way you would in C.

3. I'm not going to try to compare languages... D has a number of niceties, and I can't think of any disadvantages offhand.

---

### Post by marcelkoopman on 2009-01-07
Try to find a progamming language that has better support and tooling.
I dont think you can find many frameworks and utilities for D.
Why not consider Java? It has many frameworks you can use and tools for profiling, unit testing, bug finding, etc.

---

### Post by Kilon on 2009-01-07
> **marcelkoopman said:**
> Try to find a progamming language that has better support and tooling.
I dont think you can find many frameworks and utilities for D.
Why not consider Java? It has many frameworks you can use and tools for profiling, unit testing, bug finding, etc.

LOL ... actually I am already using JAVA through python with Jython. And Also use JAVA solely sometimes. 

But because I like what I am seeing in python I was thinking of a good way to use C++ Libraries in Python and that make me wonder if It is a good idea to use C++ libraries with Python through D. 

I took a deep look in the website and it seems that are much fewer differences between C++ and D that there are between C++ and Python/Java. Even rewriting the code from C++ to D seems pretty straightforward cause underneath all the polished surface D is C++. 


D has a garbage collector which makes things alot easier. The only thing that make me hesitate is that there is Windows Compiler and Linux , but no MACOS compiler.


And with PyD wrapping D for Python is pretty much automatic. That is why it seems to me , so far,  like a very good middle ground to access C++ libraries from Python. 

So I do not care for D libraries, only C++ libraries interest me , I just want to avoid using/coding C++.

---

### Post by marcelkoopman on 2009-01-07
What I dont understand is why you want to switch languages.
Dont you think that writing test-driven applications are more important?

---

### Post by Kilon on 2009-01-07
> **marcelkoopman said:**
> What I dont understand is why you want to switch languages.
Dont you think that writing test-driven applications are more important?

I repeat and clarify , "I do not intent to use D alone".

For now jython is my preferred choice (largely because I love python syntax and JAVA behaves perfectly in MACOSX [the perfect combination , so far] ) but If I decide to use at some point Python , then I would like to avoid the use of C++ for extending python and importing C++ libraries. 

That is why I would like people with experience in D to share their opinions.  

I do not understand what is so difficult for you to understand.

---

### Post by snova on 2009-01-07
> **Kilon said:**
> D has a garbage collector which makes things alot easier. The only thing that make me hesitate is that there is Windows Compiler and Linux , but no MACOS compiler.

Hmm, are you sure? GCC runs on just about every platform there is (I can only assume whatever Mac runs on is included), and supports D through GDC.

> And with PyD wrapping D for Python is pretty much automatic. That is why it seems to me like a very good middle ground to access C++ libraries from Python.

I'll have to look into that! Python with PyQt4, and D to be the backbone of the work, sounds like a beautiful combination.

---

### Post by Kilon on 2009-01-07
> Hmm, are you sure? GCC runs on just about every platform there is (I can only assume whatever Mac runs on is included), and supports D through GDC.

Yes I am sure , but offers other options too. Take a look here for clarification. 

[http://www.digitalmars.com/d/2.0/memory.html](http://www.digitalmars.com/d/2.0/memory.html)

EDIT: OUPS!!! I thought you were talking about the garbage collector. Scrap that. Well I have not found any mention of MACOS anywhere, so I assumed that it was not really supported. Do you know something that you could share it with me ? 

I will keep searching for a MACOS version , maybe I am missing something.  


> 
I'll have to look into that! Python with PyQt4, and D to be the backbone of the work, sounds like a beautiful combination.

What impressed me in PyD is that the whole process is alot more automatic than it is in Python.Boost and several libraries that help implement C++ libraries and since coding in D is to a very large extend exactly the same as C++ but without the headaches ,well it is a temptation that is hard to resist.... isn't it ?

[http://pyd.dsource.org/](http://pyd.dsource.org/)


As always waiting for your opinion.

---

### Post by Kilon on 2009-01-07
Ok I was EXTREMELY WRONG

There is D for MACOS through GDC as you suggested. 

[http://gdcmac.sourceforge.net/](http://gdcmac.sourceforge.net/)

Quoting from the website

> The GCC D Compiler (GDC) is based on the GNU Compiler Collection (GCC)

GDC by David Friedman, see [http://dgcc.sourceforge.net/](http://dgcc.sourceforge.net/)

**You can run programs created with GDC on any Mac OS X machine (no special run-time libraries required) _It is also possible to link with programs created by the usual Apple versions of the GCC C Compiler (gcc) and the GCC C++ Compiler (g++)_**. 

Nice ... it seems that D really interests me. Time to explore it a bit further. 

I already know C++ , so learning D should be a piece of cake.

---

### Post by Arylon on 2009-01-07
> **Kilon said:**
>  Well I have not found any mention of MACOS anywhere, so I assumed that it was not really supported. Do you know something that you could share it with me ? 

I will keep searching for a MACOS version , maybe I am missing something.  

I don't know about MACOS, but Xcode for Mac OS X uses a modified GCC, and you can get GDC for Mac here. ;)
[http://sourceforge.net/projects/gdcmac](http://sourceforge.net/projects/gdcmac)

I found the above link here...
[http://www.digitalmars.com/d/download.html](http://www.digitalmars.com/d/download.html)

EDIT: I guess you found it yourself a minute before I did.

---

### Post by Kilon on 2009-01-07
Yes I did , but you still deserve a "thank you" ;)

Are you a fellow MACOS developer?

---

### Post by Arylon on 2009-01-07
Used to be, on the old classic Mac OS. I never really go into programming for Mac OS X, just dabbled a bit. I haven't even had a OS X capable computer in the house for the past five years!

---


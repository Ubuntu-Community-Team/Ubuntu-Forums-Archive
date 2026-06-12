---
title: "Learning Python..."
date: 2010-04-24
forum: Programming Talk
---

### Post by KdotJ on 2010-04-24
I'm sorry to post this thread as I know there are so many threads about "which language shall I learn?" or "Which is the best language" blah blah blah...
However, I just want your opinions on my question...

I have been programming for a bout 2 years or so, I learnt some very simple Visual Basic and then went on to get more involved in C#.
I started university last September and there they used Java, so I translated my skills from C# to Java as the syntax is not too dissimilar to that of C# and of course they are both Object-Oriented. On the side of this, I'm slowly doing now bits and pieces in C++, but right now my stongest language is Java by far.

Since starting to use Linux/Ubuntu I see a very large usage of Python. 

I just wanted to know, is it worth me learning this? or at least having a basic stab at it? Or would you guys just suggest I continue with Java and the C++?

What is the advantages of Python in a Linux environment over languages such as Java and C++?


Thanks in advance for any input and opinions.

---

### Post by MCVenom on 2010-04-24
I can't tell you why exactly it's so widespread in use on Linux, but it's a great language and **definitely** one you should learn. It's great for almost anything in general applications programming. Its one drawback is that it doesn't perform as well as C# or Java. 

As for C#, Java and C++; all of those languages are good to know too (well I'm not sure about Java :p), you can use MonoDevelop for C#, and I'm sure someone here can suggest and IDE for C++ if you don't already have one. I'd suggest Eclipse for Java.

---

### Post by phrostbyte on 2010-04-24
IMO Python is growing in popularity at a rapid rate, and it's not just in the Ubuntu/Linux world. Django is becoming pretty popular as a MVC web framework thanks in part to some endorsements by Google.

I suppose an advantage of Python is it doesn't force a paradigm. You could potentially make useful 1-2 liner scripts in Python, without requiring stuff like functions or classes. In that way it is similar to Perl (or Bash/shell scripting). But unlike ordinary scripting it also has a large standard library (arguably on par with .NET or Java), and many many many useful libraries. Arguably some of the best scientific computing libraries are Python libraries, if you are in to that kind of stuff.

I also really enjoy its syntax, it's refreshing after language after language of code brackets. Python most resembles the kind of pseudo-code you might find in an algorithms textbook.

---

### Post by takisan on 2010-04-24
Python is an Interpretive shell that's avalible for All OSes (of course you already knew that.) I use it more for calculator stuff, but in a way it's like BATCH or BASH. I'm a lot more fluent in BATCH, but have done a bit with Python. Batch is just slightly easier on my mind (I grew up in the 95 era and only recently started using Linux.)

---

### Post by CptPicard on 2010-04-24
Java, C# and C++ are conceptually quite similar -- static-typed languages heavy on the (very explicit) object-orientation. Python is something different, and worth learning because of that... you even get some functional-style constructs. Plus it gives you a really nice scripting language for all kinds of task automation/data mangling where using something like Java would be cumbersome.

---

### Post by MCVenom on 2010-04-24
> **takisan said:**
> Python is an Interpretive shell that's avalible for All OSes (of course you already knew that.) I use it more for calculator stuff, but in a way it's like BATCH or BASH. I'm a lot more fluent in BATCH, but have done a bit with Python. Batch is just slightly easier on my mind (I grew up in the 95 era and only recently started using Linux.)
I'd tend to say that Python is a bit more than just a 'command shell' type thing, it's really a fully-featured programming language in most respects. :p
Honestly, if it were faster, I'd probably want to use it for everything. :D

---

### Post by CptPicard on 2010-04-24
> **BlackOtaku said:**
> 
Honestly, if it were faster, I'd probably want to use it for everything. :D

Learn the extension API and use C for the slow bits. It doesn't solve the speed issue 100% but at least quite a bit of it.

---

### Post by MCVenom on 2010-04-24
> **CptPicard said:**
> Learn the extension API and use C for the slow bits. It doesn't solve the speed issue 100% but at least quite a bit of it.
I'll look into that, thanks. :)

---

### Post by phrostbyte on 2010-04-24
> **CptPicard said:**
> Learn the extension API and use C for the slow bits. It doesn't solve the speed issue 100% but at least quite a bit of it.

You don't even necessarily have to learn the C extension API (although it's pretty simple, and arguably worth using).

Thanks to ctypes in Python 2.5 or greater, you can call exported C functions directly. :D

ctypes is a bit slower then outright writing a C module, but all the overhead is in setting up the C call, and it could probably be measured in nanoseconds without using too many digits. :)

I suppose one advantages of ctypes though your C code doesn't have to be aware of Python, and could easily be called from other languages as well. A functional disadvantage over the Python API is the inability to work with native Python types.

---

### Post by CptPicard on 2010-04-24
True, but I like the extension API because it allows you to actually write actual Python-side classes/objects in C. This lets you give a far richer interface to your C code (which can mostly still reside in a non-Python-aware library). As you know, Python is cool because of the niceties of the language's design, and having to just abstract everything as mere function calls is relatively lame...

---

### Post by phrostbyte on 2010-04-24
> **CptPicard said:**
> True, but I like the extension API because it allows you to actually write actual Python-side classes/objects in C. This lets you give a far richer interface to your C code (which can mostly still reside in a non-Python-aware library). As you know, Python is cool because of the niceties of the language's design, and having to just abstract everything as mere function calls is relatively lame...

What I would do is write a nice Python module around a C library. Some people do this with C modules anyway, you can see some examples of this in the Python standard library (interestingly enough, the ctypes module itself is a hybrid C / Python module).

The thing you lose if you go with C modules though is (simple) compatibility with other languages. This is of course not a problem if all you are interested in is Python.

---

### Post by CptPicard on 2010-04-24
It all depends on the structure of your library really. The performance can again take a hit if the Python-side higher-level constructs are heavily used and then there's the additional impact of shuffling data over ctypes...

---

### Post by KdotJ on 2010-04-24
People say its easy to learn but it seems a long task to take on a new structure of a language that is so different from java/c++ for example. I just feel by not learning it I'm missing out lol.

I'll give it a shot, new challenges are always fun

---

### Post by phrostbyte on 2010-04-24
> **CptPicard said:**
> It all depends on the structure of your library really. The performance can again take a hit if the Python-side higher-level constructs are heavily used and then there's the additional impact of shuffling data over ctypes...

We are not in disagreement. :)

---

### Post by MCVenom on 2010-04-24
> **KdotJ said:**
> People say its easy to learn but it seems a long task to take on a new structure of a language that is so different from java/c++ for example. I just feel by not learning it I'm missing out lol.

I'll give it a shot, new challenges are always fun
That's the spirit! (Tip: Learn with the latest Python3 release. The Py3 series is incompatible with Py2, which will no longer be in active development after this summer. To avoid having to relearn everything when the rest of the world finally makes the switch, I'd be looking at Python 3. You can find it in the Software Center, get Python 3.1.) :)

---

### Post by KdotJ on 2010-04-24
> **BlackOtaku said:**
> That's the spirit! (Tip: Learn with the latest Python3 release. The Py3 series is incompatible with Py2, which will no longer be in active development after this summer. To avoid having to relearn everything when the rest of the world finally makes the switch, I'd be looking at Python 3. You can find it in the Software Center, get Python 3.1.) :)

Thanks for the tip! from little bits I have done so far it's so much simpler than Java lol.

---

### Post by The Thunder Chimp on 2010-04-24
This thread should be moved to Recurring Discussions, that's what that Category is for. This Category is for questions about programming (as far as I know).

---

### Post by Bachstelze on 2010-04-24
> **The Thunder Chimp said:**
> This thread should be moved to Recurring Discussions, that's what that Category is for. This Category is for questions about programming (as far as I know).

I think a question about programming languages is about programming.

---

### Post by jm2 on 2010-04-24
Please correct If I am wrong.

Python in order to give someone else to run the code on there machine, they would have to have python installed.

If you write a program in c. you have an executable object. Therefore, you just run the exe on another computer. You don't need to have c installed.

---

### Post by phrostbyte on 2010-04-24
> **jm2 said:**
> Please correct If I am wrong.

Python in order to give someone else to run the code on there machine, they would have to have python installed.

If you write a program in c. you have an executable object. Therefore, you just run the exe on another computer. You don't need to have c installed.

You 99% of the time need the "C Standard Library" or "C Standard Runtime" installed. It's just that almost every OS (incl. Windows) includes it. Plus there may be shared library dependencies (eg: a GTK+ app depends on GTK+).

---

### Post by MCVenom on 2010-04-24
> **jm2 said:**
> Please correct If I am wrong.

Python in order to give someone else to run the code on there machine, they would have to have python installed.

If you write a program in c. you have an executable object. Therefore, you just run the exe on another computer. You don't need to have c installed.
You can compile a python program as an *.exe, I've done it before :p

---

### Post by KdotJ on 2010-04-25
Thanks guys for all the input. My plan now is to learn it on the side, as I'm truly a fan of the object-oriented paradigm. And the next year of my uni course involves a software engineering project, which they require us to write in java. 

I really do love the simplicity of Python though, the way I can condense a simple 20 line java program into just 6 lines in python

---


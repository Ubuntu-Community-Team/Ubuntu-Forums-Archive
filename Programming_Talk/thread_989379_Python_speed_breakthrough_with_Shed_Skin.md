---
title: "Python speed breakthrough with Shed Skin"
date: 2008-11-21
forum: Programming Talk
---

### Post by pmasiar on 2008-11-21
[ShedSkin compiles Python ](http://blog.showmedo.com/2008/11/20/making-python-math-196-faster-with-shedskin/) making it **much** faster - one example is ~200 times faster, just 7 times slower than hand-coded C++, which is amazing.

[http://code.google.com/p/shedskin/](http://code.google.com/p/shedskin/) - "Shed Skin is an experimental compiler, that can translate pure, but implicitly statically typed Python programs into optimized C++. "

That's one worthy project to contribute to for someone with time.

Shed Skin is looking for new developers and accepts code which does not compile (aka bug reports).

---

### Post by CptPicard on 2008-11-21
So Python is 1400 times slower than hand-coded C++? :shock:

---

### Post by kripkenstein on 2008-11-21
> **pmasiar said:**
> [ShedSkin compiles Python ](http://blog.showmedo.com/2008/11/20/making-python-math-196-faster-with-shedskin/) making it **much** faster - one example is ~200 times faster, just 7 times slower than hand-coded C++, which is amazing.

[http://code.google.com/p/shedskin/](http://code.google.com/p/shedskin/) - "Shed Skin is an experimental compiler, that can translate pure, but implicitly statically typed Python programs into optimized C++. "

That's one worthy project to contribute to for someone with time.

Shed Skin is looking for new developers and accepts code which does not compile (aka bug reports).

It's an interesting project, but I'm more hopeful for [PyPy]("http://codespeak.net/pypy/dist/pypy/doc/home.html").

ShedSkin will work on a subset of Python, which can be compiled into statically-typed code. PyPy does that as well, formally defining the subset as RPython, and furthermore by writing the Python interpreter/VM from scratch in RPython, they hope to design much more efficient just-in-time compilation, which should speed up normal Python.

---

### Post by Greyed on 2008-11-22
> **CptPicard said:**
> So Python is 1400 times slower than hand-coded C++? :shock:

Probably an extreme case.  I think the one cited was neural-net mathematics?  Something of that nature.

Gotta admit, though, for the Python approach to bottlenecks this holds promise.  Right now it is write in pure Python, identify the slow parts, optimize those parts by using standard Python tricks (local variables for function calls et al) or drop down to C and hand code the inner loops to be called by Python.  For those of us (*cough* like me) who are C deficient having the notion of writing slightly altered Python and auto-generating C++ for the inner loops is an absolute godsend.

---

### Post by slavik on 2008-11-22
I am actually wondering what is so slow in Python for the purpose they are using it for ... like which piece of code exactly. This could lead to improvments for CPython.

---

### Post by ssam on 2008-11-22
nice to see all these projects. I have used Cython before.

---

### Post by jespdj on 2008-11-22
> **pmasiar said:**
> [http://code.google.com/p/shedskin/](http://code.google.com/p/shedskin/) - "Shed Skin is an experimental compiler, that can translate pure, but implicitly statically typed Python programs into optimized C++. "
So, does this compile Python into C++ source code, that you'd then have to compile with for example g++?

There's also an implementation of Python on the Java VM - [Jython](http://www.jython.org/Project/). I don't know much about it, but it also has the potential for great performance, when it makes use of the JVM's JIT (just-in-time) compiler to compile bytecode to native machine code. (JRuby is already faster than standard Ruby because of this).

---

### Post by wmcbrine on 2008-11-22
Python is slow, no doubt about it. It's a feature. Python is slow, so that you, the programmer, can be faster.

99% of the time, it's still fast enough.

---

### Post by Zootropo on 2008-11-22
Interesting.

It would be cool if someone could write a benchmark between Shed Skin, Jython, Cython, IronPython, Psyco, ...

---

### Post by kripkenstein on 2008-11-22
> **Zootropo said:**
> Interesting.

It would be cool if someone could write a benchmark between Shed Skin, Jython, Cython, IronPython, Psyco, ...

Well, it's hard to compare since they do different things. ShedSkin doesn't work on arbitrary Python code, so standard benchmarks might not even run. Likewise, subtler differences exist in other implementations (for example, IronPython can't run Django, last I heard).

But I presume once they are more mature we will see such benchmarks.

---

### Post by pmasiar on 2008-11-22
> **slavik said:**
> I am actually wondering what is so slow in Python for the purpose they are using it for ... like which piece of code exactly. This could lead to improvments for CPython.

Python (as you know, but just for the moment did not considered consequences) is dynamically typed. So only at runtime can be resolved what code does ie '+' between two operands. C++ can do that at compile time.

Limits on Python for Shed Skin is that names do not change type, once assigned.

@ CptPicard: Possibly not 1400 times slower, but 300 times, range was (1.5..7 times ) times 200. It of course depends on the problem being solved, that one likely used a lot of dynamic tricks which could be compiled away. Benchmarks  are **always** ballpark figures (and often misleading), there is no replacement to making your own benchmark using your own data and approach.

More interesting is, Shed Skin project is looking for bug reports (and of course developers, that's true for every project). That could be quite fun for people knowing both C++ and Python.

---

### Post by pmasiar on 2008-11-22
> **kripkenstein said:**
> Well, it's hard to compare since they do different things. ShedSkin doesn't work on arbitrary Python code, so standard benchmarks might not even run. 

If you know any code which does not run or with bugs, please report it to Shed Skin. If you are just afraid it might not, relax: someone is working on fixing it... 8-)

> Likewise, subtler differences exist in other implementations (for example, IronPython can't run Django, last I heard).

It's in libraries/utilities. IronPython is based on .NET, so some parts of "standard" C/GNU environment is not  available. My gut feeling would be networking.

> But I presume once they are more mature we will see such benchmarks.

Yes, Django runs on Jython!

---


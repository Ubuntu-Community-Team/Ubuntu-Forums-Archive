---
title: "Java and Python"
date: 2009-10-04
forum: Programming Talk
---

### Post by jamesnormanedwards on 2009-10-04
I was looking at the Google app engine and noticed they utilize Java and Python for app development. Why does anybody use Java when Python is just as capable. Also, in my experience, python requires less typing.

---

### Post by -grubby on 2009-10-04
Because some people prefer Java. I don't see what the problem is here.

---

### Post by NovaAesa on 2009-10-04
> **jamesnormanedwards said:**
> I was looking at the Google app engine and noticed they utilize Java and Python for app development. Why does anybody use Java when Python is just as capable. Also, in my experience, python requires less typing.

Lots of reasons use Java. Mainly it is personal preference. For object orriented programming,  I find that I am more comfortable using languages that have explicit typing rules that are statically applied. Java provides this (so does C++, which I use when it is called for). Python on the other hand uses implicit and dynamic typing. Neither of these I like all that much. Sure they are great if you are writing a script or small imperative program, but for any largish program using OOP, I don't find them very fun. And just so you know, I was using Python long before I even typed a line of Java :P

> Why does anybody use Java when Python is just as capableWhy not write your programs using John Conway's Game of Life. It's just as capable after all! In regards to Turing Completeness at least.

---

### Post by wmcbrine on 2009-10-05
I wouldn't use Java when I could use Python, but I can think of a few reasons someone might:

1. Knowledge. More people have experience with Java than with Python, alas.

2. Code base. You might want to use some specific library that's only available for Java... and, again, I think Java has more available for it (although I've yet to miss out on something I was looking for in Python).

3. Speed. This is the surprising one, since Java has long had a reputation for slowness. But -- apart from its startup time, which is atrocious -- Java is still faster than Python.

---

### Post by NovaAesa on 2009-10-05
> **wmcbrine said:**
> 
3. Speed. This is the surprising one, since Java has long had a reputation for slowness. But -- apart from its startup time, which is atrocious -- Java is still faster than Python.
Java hasn't really been slow since at least 5 years ago. It's *almost* comparable to C++ now. Java's JIT compilation processes makes sure that things on Java run (almost) lightning fast. Python, being interpreted from source, can only go so fast.

With slowness, I think Java suffers from what I call "Internet Explorer Syndrome". It used to be bloody horrid, but these days it is much better. But as with IE, people still shun it as "that terrible thing! I will never use it!".

---

### Post by nvteighen on 2009-10-05
> **NovaAesa said:**
> Java hasn't really been slow since at least 5 years ago. It's *almost* comparable to C++ now. Java's JIT compilation processes makes sure that things on Java run (almost) lightning fast. Python, being interpreted from source, can only go so fast.


Er... Python is also JIT compiled... The issue is much simpler: Java's compiler is much more efficient because Java is statically typed. The Python compiler is unable to do type optimizations...

Another issue that objectively puts Java on top of Python is that the JVM is an incredible piece of software, while the CPython VM is still too slow and still considered more like a shell than a programming platform... In some sense, because it is also a shell. Funny, because nobody says SBCL is a shell, but anybody agrees it's a Lisp VM, and it essentially works the same as CPython VM.

There's a lot of a perception issue, IMO. People still perceive Java as a serious enterprise programming language and Python as a kid scripting language. That's a mistake... as Google is showing to the world. Of course Java has a niche and is the best choice for a lot of tasks; but Python is also getting its "serious" place in the programming world.

Sometimes you need a dynamic language; sometimes you need a static one. That's the way it works.

---

### Post by froggyswamp on 2009-10-05
> **nvteighen said:**
> 
There's a lot of a perception issue, IMO. People still perceive Java as a serious enterprise programming language and Python as a kid scripting language. That's a mistake... as Google is showing to the world. Of course Java has a niche and is the best choice for a lot of tasks; but Python is also getting its "serious" place in the programming world.
Java is enterprise oriented while Python is not, which means exactly that - Python can't replace Java (without help from C/C++ native libs) it also doesn't scale as much as Java.
Python is ideal for scripting (fast startup & slower VM) while Java is the opposite (slower startup & fast VM).
So whoever wonders why A doesn't replace B, it's both a matter of image and merits.

In my personal Desktop experience, not that it's Python's fault rather programmer's fault, I replaced both Glipper and Deluge (both written partially in Python) because of crashing and being unreliable for Percellite and Azureus (written in C & Java) respectively for being more reliable (neither has once crashed for me yet).

---

### Post by NovaAesa on 2009-10-05
> **nvteighen said:**
> Er... Python is also JIT compiled...You have me there, you learn something new each day!

---

### Post by nvteighen on 2009-10-05
> **NovaAesa said:**
> You have me there, you learn something new each day!

Ok, let's refine it a bit.

If you run a .py file, what happens is that it gets compiled in the background first and then it's executed, but the compiled version is lost when exiting the program. Only when importing a module for the first time you get the .pyc file so it gets imported more quickly in next imports.

You can of course run a .pyc... and if you used the shebang in the source code, just put execution permissions to the .pyc file and you can run the compiled version directly.

---

### Post by nvteighen on 2009-10-05
> **froggyswamp said:**
> Java is enterprise oriented while Python is not, which means exactly that - Python can't replace Java (without help from C/C++ native libs) it also doesn't scale as much as Java.
Python is ideal for scripting (fast startup & slower VM) while Java is the opposite (slower startup & fast VM).
So whoever wonders why A doesn't replace B, it's both a matter of image and merits.

In my personal Desktop experience, not that it's Python's fault rather programmer's fault, I replaced both Glipper and Deluge (both written partially in Python) because of crashing and being unreliable for Percellite and Azureus (written in C & Java) respectively for being more reliable (neither has once crashed for me yet).

I agree... Isn't that the same I'm saying? The thing is that there seems to be an overlap in Python's and Java's niches that might make both compete eachother in a very near future... and there, the one proven as best will prevail!

---

### Post by engla on 2009-10-05
> **nvteighen said:**
> Ok, let's refine it a bit.

If you run a .py file, what happens is that it gets compiled in the background first and then it's executed, but the compiled version is lost when exiting the program. Only when importing a module for the first time you get the .pyc file so it gets imported more quickly in next imports.

You can of course run a .pyc... and if you used the shebang in the source code, just put execution permissions to the .pyc file and you can run the compiled version directly.

Python is *not* JIT compiled, it is only compiled to Python interpreter byte code. The only optimization is the peephole optimizer, optimizing smaller things on the Python level. Python does not do anything close to JIT (which I interpret as compiling-down to a specialized code representation, either using type information, architechture-specific code etc.). Python .pyc are de facto compatible across platforms.

PyPy is experimenting with JIT for Python (PyPy is awesome coolness, they aren't writing a JIT for Python, they are writing a Python implementation in Python, and a JIT **generator** that can generate a JIT compiler for an arbitrary interpreter!)

---

### Post by nvteighen on 2009-10-05
> **engla said:**
> Python is *not* JIT compiled, it is only compiled to Python interpreter byte code. The only optimization is the peephole optimizer, optimizing smaller things on the Python level. Python does not do anything close to JIT (which I interpret as compiling-down to a specialized code representation, either using type information, architechture-specific code etc.). Python .pyc are de facto compatible across platforms.

PyPy is experimenting with JIT for Python (PyPy is awesome coolness, they aren't writing a JIT for Python, they are writing a Python implementation in Python, and a JIT **generator** that can generate a JIT compiler for an arbitrary interpreter!)

Hm... seems you're right... (sorry, NovaAesa for misleading you...). I've been interpreting JIT as "prior-to-execution compilation at runtime" :p

---

### Post by engla on 2009-10-05
> **nvteighen said:**
> Hm... seems you're right... (sorry, NovaAesa for misleading you...). I've been interpreting JIT as "prior-to-execution compilation at runtime" :p

Well, all is not lost. I forgot there is Psycho for Python on x86; this is mostly like a typical JIT compiler; it selects only the oft-used functions to compile, can compile different versions of the same function depending on the types of the passed arguments. Using such information, it can speed up Python code dramatically. Now I can't use it on this rusty mac, but Psycho should be like an external module that you can just import and activate in your program. I don't know any major programs that use Psycho.

---

### Post by engla on 2009-10-06
...and this is just in from the PyPy status log.

You know I think the PyPy JIT compiler generator is really one of the most exciting things you can follow on the web :-)

But it's interesting since they in the bechmarks compare Plain Python, Python + Psycho, Python + PyPy's generated JIT, and Java's **JVM**, and they come out in that order, with JVM fastest.

[PyPy's JIT now supports floats]("http://morepypy.blogspot.com/2009/10/pypys-jit-now-supports-floats.html")

---


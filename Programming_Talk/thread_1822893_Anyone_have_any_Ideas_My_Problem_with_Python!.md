---
title: "Anyone have any Ideas? My Problem with Python!"
date: 2011-08-11
forum: Programming Talk
---

### Post by x-D on 2011-08-11
Just to post here, that I love Python and I use it a lot in terms of my programming. I have 1 main problem with Python. There is no option inside of the Compiler to make straight executables, that do not require the end-user to have Python installed. I know in Windows you can use Py2exe and Cx_Freeze in Linux, but they result in massive file sizes, and furthermore I haven't a clue as to how you would go about using Cx_Freeze in the first place.

Any suggestions...

x-D :guitar:

---

### Post by ssam on 2011-08-11
there is an early attempt a using GCC to compile python.
[http://gcc.gnu.org/wiki/PythonFrontEnd](http://gcc.gnu.org/wiki/PythonFrontEnd)

there is also cython that translates python to c and then compiles it. though it is aimed at making fast libraries that can be called from normal python.

is the any particular reason you want this? pretty much every linux distro has python installed (and the main ones use python for a lot of basic tasks). If someone has linux without python then they must have some specialist reason, for example very low memory, in which case they probably wont want to run your python app.

---

### Post by x-D on 2011-08-11
> **ssam said:**
> there is an early attempt a using GCC to compile python.
[http://gcc.gnu.org/wiki/PythonFrontEnd](http://gcc.gnu.org/wiki/PythonFrontEnd)

there is also cython that translates python to c and then compiles it. though it is aimed at making fast libraries that can be called from normal python.

is the any particular reason you want this? pretty much every linux distro has python installed (and the main ones use python for a lot of basic tasks). If someone has linux without python then they must have some specialist reason, for example very low memory, in which case they probably wont want to run your python app.

I've heard that there are some distros that do not come pre-installed with Python, and I'm thinking about trying to make a Cross-Platform project, using .py for Linux, and then .exe for Windows.

Thanks for the Reply, really helped. :)

---

### Post by x-D on 2011-08-11
> **ssam said:**
> there is an early attempt a using GCC to compile python.
[http://gcc.gnu.org/wiki/PythonFrontEnd](http://gcc.gnu.org/wiki/PythonFrontEnd)

there is also cython that translates python to c and then compiles it. though it is aimed at making fast libraries that can be called from normal python.

is the any particular reason you want this? pretty much every linux distro has python installed (and the main ones use python for a lot of basic tasks). If someone has linux without python then they must have some specialist reason, for example very low memory, in which case they probably wont want to run your python app.

Another question, inside Windows, using IronPython on the .NET Framework. Does this allow for the creation of standard .exe files, with a smaller filesize than that of say py2exe?

And does IronPython have the exact same syntax as regular Python?

---

### Post by billdougan on 2011-08-11
I've heard good things about this:

[http://www.py2exe.org](http://www.py2exe.org)

Haven't tried it however, as I don't do much in Windows these days.

---

### Post by x-D on 2011-08-11
> **billdougan said:**
> I've heard good things about this:

[http://www.py2exe.org](http://www.py2exe.org)

Haven't tried it however, as I don't do much in Windows these days.

Yeah, that seems to be the way forward in Windows, but I'm looking for something that 'actually' compiles it, instead of converting it into C or C++ and then adding an interpretor for the modules you've imported, as this is slow and has a very large file size :)

x-D :guitar:

---

### Post by ofnuts on 2011-08-11
> **x-D said:**
> Just to post here, that I love Python and I use it a lot in terms of my programming. I have 1 main problem with Python. There is no option inside of the Compiler to make straight executables, that do not require the end-user to have Python installed. I know in Windows you can use Py2exe and Cx_Freeze in Linux, but they result in massive file sizes, and furthermore I haven't a clue as to how you would go about using Cx_Freeze in the first place.

There is no silver bullet. Either the stand-alone code you generate includes the equivalent of the whole interpreter(the best you can dream of is a DLL/SO to avoid duplicating it across your modules) or you can generate executables of reasonable size but you have to forget many of the niceties of the language that come from its dynamic execution (the eval()-type instruction are the first to go, usually). So it all depends on how much of Python you use in your code (but if you don't use much of Python, rewriting in another language shouldn't be difficult).

---

### Post by cgroza on 2011-08-11
Unfortunately, the nature of dynamically typed languages makes compiling them to machine code before run-time very difficult.

Because Python is not statically typed (the references are untyped, only the objects they point to are) makes it very difficult to know the types at compile time and generate machine code for them. Only at runtime, the types are revealed and the interpreter generates the machine code and runs it.

What py2exe does, is takes your code, the libraries it uses and embeds the interpreter into the .exe. That should explain the big file sizes.

---

### Post by ssam on 2011-08-11
you might find this series of posts interesting
[http://en.wordpress.com/tag/pythons-innards/](http://en.wordpress.com/tag/pythons-innards/)

it shows what actually happens when you run a piece of python code.

---

### Post by x-D on 2011-08-11
> **ssam said:**
> you might find this series of posts interesting
[http://en.wordpress.com/tag/pythons-innards/](http://en.wordpress.com/tag/pythons-innards/)

it shows what actually happens when you run a piece of python code.

Thanks for the info everyone, :) I'll look at those posts in a minute. I think they could add in say once you have created and saved your program, run it debugged it etc, a function that would enable you to build it into an exe file. Seeing as how once it's all saved it's basically static isn't it? The code is there, so surely it can be seen and then converted to .exe?

When it's being compiled it could just link and list all the references?

I know this would mean you would need to go through a few more stages to compile it, but it would give Windows users rapid dev cycles.

Doesn't Iron Python manage to combat this though, using Python Syntax inside the .NET framework, meaning I would in theory be able to make standalone .exe's?

---

### Post by Tony Flury on 2011-08-12
> **x-D said:**
> Thanks for the info everyone, :) I'll look at those posts in a minute. I think they could add in say once you have created and saved your program, run it debugged it etc, a function that would enable you to build it into an exe file. Seeing as how once it's all saved it's basically static isn't it? The code is there, so surely it can be seen and then converted to .exe?


I think maybe you have a misconception about the meaning of the word Static - it doesn't mean that the source code is not changing. Static and Dynamic (is this context) is about what you can tell about your data just by looking at the source code.

I could write a function in python that operates on two integers (maybe multiplies them together) : 
```

def mult(a,b):
    return a*b

```
There is nothing in this code that says that a or b are integers, in fact my programm could call the same function with floating point numbers, complex numbers, matrices etc, and so long as that data type has the "*" operator defined, the code would work. So if you tried to compile that function - you would have to include libraries to do all of the above (floating point, complex numbers etc) - there is no way for the compiler to know that they are not needed. This is called Dynamic typing - it is what Python does.

Contrast that with a C function 
```

int mult( int a, int b)
{
    return a * b ;
}

```
In this example the C compiler would know that my function will only ever take integers and return an integer - and therefore there is no need for it ever to worry about having to multiply floating points, Complex numbers, matrices etc - this function will NEVER do that. This is called Static typing and because of the extra type information it is far easier to compile into Machine code.

---

### Post by ofnuts on 2011-08-12
> **Tony Flury said:**
> I think maybe you have a misconception about the meaning of the word Static - it doesn't mean that the source code is not changing. Static and Dynamic (is this context) is about what you can tell about your data just by looking at the source code.

I could write a function in python that operates on two integers (maybe multiplies them together) : 
```

def mult(a,b):
    return a*b

```There is nothing in this code that says that a or b are integers, in fact my programm could call the same function with floating point numbers, complex numbers, matrices etc, and so long as that data type has the "*" operator defined, the code would work. So if you tried to compile that function - you would have to include libraries to do all of the above (floating point, complex numbers etc) - there is no way for the compiler to know that they are not needed. This is called Dynamic typing - it is what Python does.

Contrast that with a C function 
```

int mult( int a, int b)
{
    return a * b ;
}

```In this example the C compiler would know that my function will only ever take integers and return an integer - and therefore there is no need for it ever to worry about having to multiply floating points, Complex numbers, matrices etc - this function will NEVER do that. This is called Static typing and because of the extra type information it is far easier to compile into Machine code.

Even simpler, consider the difference between:
print '1' + '2'
and
print 1 + 2

---

### Post by x-D on 2011-08-20
> **ofnuts said:**
> Even simpler, consider the difference between:
print '1' + '2'
and
print 1 + 2

Ah I see, I got a bit confused with that, seeing as originally when I first started learning, this dynamic language stuff didn't exist*.

Thanks for the help!

*well it did exist, just not like today.

---


---
title: "Python on ide on ubuntu"
date: 2008-10-07
forum: Programming Talk
---

### Post by hoboy on 2008-10-07
I have just made a decision to learn python, I have read that python ide is already installed on ubuntu, how do I launch it, I have looked at synaptic I can se that python is installed but I can se where to launch it.

---

### Post by LaRoza on 2008-10-07
You don't need an IDE, Gedit has everything you need and more.

Some recommend IDLE, but I find it inferior to Gedit.

See my site and the stickies for more. (Gedit is the "Text Editor")

---

### Post by artir on 2008-10-07
sudo apt-get install idle

---

### Post by Canis familiaris on 2008-10-07
> **LaRoza said:**
> You don't need an IDE, Gedit has everything you need and more.

Some recommend IDLE, but I find it inferior to Gedit.

See my site and the stickies for more. (Gedit is the "Text Editor")

+1

gedit's in built interpreter and syntax highlighting is excellent.

@OP: To execute python script:
```
python filename.py
```

Making the file executable
```

chmod +x filename.py
./filename.py

```
Though in the latter case you must have #!/usr/bin/python in the beginning of your code

---

### Post by hoboy on 2008-10-07
gedit's  ???? is it sudo gedit ? it opens a text editor is it this texeditor you are talking about ?

---

### Post by Canis familiaris on 2008-10-07
> **hoboy said:**
> gedit's  ???? is it sudo gedit ? it opens a text editor is it this texeditor you are talking about ?
Yes Applications->Accessories->Text Editor
Yes it's the text editor and you DO NOT NEED root permission :)

Enable the Python Plugin

In gedit:
Go to Edit->Preferences, choose the plugins tab and enable the python console plugin.
Now you can view the python console by View->Bottom Pane.

You can always save your python code as a text file with extension .py and execute it with the commands I gave above.

A good Python Resource is [http://learnpython.pbwiki.com/](http://learnpython.pbwiki.com/).

I just like you am a beginner in python.

---

### Post by gomputor on 2008-10-07
[[COLOR="Red"]Geany[/COLOR]]("http://www.geany.org/Main/HomePage") is also a good alternative. You can run your scripts directly from it too.

You can install it directly with:
```
sudo apt-get install geany
```

---

### Post by Canis familiaris on 2008-10-07
> **gomputor said:**
> [[COLOR="Red"]Geany[/COLOR]]("http://www.geany.org/Main/HomePage") is also a good alternative. You can run your scripts directly from it too.

You can install it directly with:
```
sudo apt-get install geany
```

Thanks. I didn't know about this.

---

### Post by snova on 2008-10-07
Oh dear, another beginner. Ah well, I love explaining things. Somebody will probably beat me to it. Edit: wow, *three* people beat me.

First of all, Python is an interpreted language. That means that the programs you write don't "run" directly. Instead, you use another program (the "interpreter") that runs your program line by line. The interpreter for Python is named "python". So if you type

```
python myscript.py
```

Then the file named myscript.py will be run.

Alternatively, if you mark your script as executable, you can just run it like this:

```
./myscript.py
```

To mark a program as something that can be run, use this command:

```
chmod a+x myscript.py
```

You can also use your file manager. Look for the checkbox for "executable" and see that it's checked.

Now, gedit is simply a text editor. Use it to open your program and edit it.

"sudo" is used to run programs as the administrator, and you should be careful when using it. Do not run gedit with sudo, or anything else, unless you know why. Usually this is to perform various administrative tasks, like installing packages or changing system files. *Don't use it lightly or with ignorance.*

An "IDE" is just a text editor with some other tools built in. There are many such programs. IDLE is well known as a Python-only IDE, but there are plenty of alternatives. Eric is another one for Python, and I couldn't list all of the ones that support Python in addition to many others.

IDE's are nice for some things, but all you really need in the end is a text editor. I do it both ways. But the advantage of an IDE is that you don't need to use the command line as much. For example, you can usually run your program by pressing a button somewhere.

---

### Post by hoboy on 2008-10-07
Thanks to all of you, who have used their times to help.
Today I have written to this forum,about witch language i should start to learn, weather I should lean php or python, I got many very qualified inputs, then I decided to start with python. 
I am a Newb on it, thanks for puting me on track, great forum
I have installed IDLE, Greany

---

### Post by skeeterbug on 2008-10-07
Eclipse + PyDev plugin is a nice setup.

[http://pydev.sourceforge.net/features.html](http://pydev.sourceforge.net/features.html)

---

### Post by LaRoza on 2008-10-07
Since the Python question has been answered, this thread is closed, as promised:

[http://ubuntuforums.org/showthread.php?t=752224](http://ubuntuforums.org/showthread.php?t=752224)

---

### Post by pmasiar on 2008-10-07
> **snova said:**
> First of all, Python is an interpreted language. That means that the programs you write don't "run" directly. Instead, you use another program (the "interpreter") that runs your program line by line. 

Wrong, wrong, and wrong.

Python is not interpreted (in sense like you describe: "run line by line" - it was BASIC 25 years ago. Python is compiled into intermediate structure ("byte code") which is abstract machine like P-code or JVM. This code can be compiled further, but usualy is just executed by Python runtime.

Compiled code is in .pyc files, you can distribute them instead of sources - but source can be easily restored from them (sans comments of course)

I still recommend IDLE (the Python IDE): not as editor (which is just so-so, and Linux has plenty of competent editors, imne preferred is SciTE), but as shell.

Compared to other languages, shell allows you to try language one line and one construct at a time, and see results immediatelly, instead of having to write small half-page programs just to try single feature, like you have to do in ie Java. And IDLE shell has syntax highlighting, which helps beginner a lot.

See wiki in my sig for links, including IDLE demo.

---

### Post by snova on 2008-10-07
I'm aware of that, but need technicalities be exposed to somebody who is only starting the language? By the looks of it, this person is only *starting* to program. I deemed it an unnecessary detail.

I didn't mean to convey the literal meaning of that sentence, rather I intended to clarify that it was an interpreted language, and thus is executed by another program.

Sometimes I wish Python had an option to switch into this mode though, so that you could do shell-script like things with it like appending binary data; just as long as you exit() before it chokes.

---

### Post by LaRoza on 2008-10-07
> **snova said:**
> I'm aware of that, but need technicalities be exposed to somebody who is only starting the language? By the looks of it, this person is only *starting* to program. I deemed it an unnecessary detail.


No, that is how wrong information is spread about ;)

You should tell when you are over simplifying it.

So many times on this forum did we have to set someone straight because they were told something incorrect by someone else and had preconceptions that were false.

---

### Post by pmasiar on 2008-10-07
> **snova said:**
> I'm aware of that, but need technicalities be exposed to somebody who is only starting the language? By the looks of it, this person is only *starting* to program. I deemed it an unnecessary detail.

If you cannot explain it trutffully, don't mention it, or say "this is gross oversimplification". Beginner wants to know  how to run your program, technical details are irrelevant. Compiler, interpreter, why beginner should care? And develop biases one way or the other?

---

### Post by Canis familiaris on 2008-10-08
> **pmasiar said:**
> Wrong, wrong, and wrong.

Python is not interpreted (in sense like you describe: "run line by line" - it was BASIC 25 years ago. Python is compiled into intermediate structure ("byte code") which is abstract machine like P-code or JVM. This code can be compiled further, but usualy is just executed by Python runtime.

Compiled code is in .pyc files, you can distribute them instead of sources - but source can be easily restored from them (sans comments of course)

I still recommend IDLE (the Python IDE): not as editor (which is just so-so, and Linux has plenty of competent editors, imne preferred is SciTE), but as shell.

Compared to other languages, shell allows you to try language one line and one construct at a time, and see results immediatelly, instead of having to write small half-page programs just to try single feature, like you have to do in ie Java. And IDLE shell has syntax highlighting, which helps beginner a lot.

See wiki in my sig for links, including IDLE demo.

Thanks. I didn't know that.

---

### Post by snova on 2008-10-08
If this disagreement is about whether 'line by line' is technically incorrect, it is, or whether I shouldn't have said that, I admit it would have been better had I worded it differently. But the meaning behind it is still clear- that Python is an interpreted language run by another program. I had no intentions of misinformation, though I agree that intentions are not everything.

As to whether it was oversimplification, I remain convinced that it wasn't, and when this person comes to the point where they will learn more about the particulars of the interpreter, the additional information should not conflict with what I have provided. At the very least, the adjective "gross" is a little too powerful.

I also think that this is a moot point by now, and its further discussion would probably not benefit much (including this post itself). I was wrong to word it so, but as a *figurative* expression it worked well enough.

At the risk of being told to take my own advice, let us drop it.

But the criticism was well taken, my choice of grammar improved, and I even learned a little more about the history of programming languages.

---

### Post by pmasiar on 2008-10-08
> **snova said:**
> Python is an interpreted language run by another program.

Of course I agree with you 99%, but the fun (and learning opportunity) is in talking about the fine details, right?

So I am not sure what is your definition of "interpreted".

We agree that Python source is fully parsed, and from parse tree abstract code (.pyc file) is generated, which is saved and can be distributed instead of sources. Bytecode is executable using runtime libraries, similar to JVM of Java or DLL of .NET, instead of statically linking libraries, but so what? Difference might be that the generated bytecode is currently for abstract virtual machine, not concrete CPU architecture like with C. But that is just minor implementation detail: of course free software project like Python had different focus (and resources) as commercial company with hundreds of dollar of revenue. 

Currently, there are couple of projects working to bridge the last step, using most promising approach: just-in-time compilation of the most-inner loops (using profiling) instead of static compilation of the full sources. And also this last step is not relevant to Python's success: bytecode machine is written in C, fast enough for most applications (because most of the time bottleneck is web, I/O or database access, not the time needed to execute Python code itself).

So I strongly objected against your classification of Python as somewhat inferior "interpreted" language: it is definitely not "interpreted line by line", as you can see if you make any syntax error. 

Also, interpreted compared to what? Java is also interpreted, even if differently (JVM uses compiled "class" to reconstitute source, then compile it to architecture-relevant binaries. Exact code to be executed  by C++ subclass has to be resolved at runtime too. Does it mean C++ is interpreted? If not, why not? In OOP language, whole point is to have the flexibility?

---

### Post by snova on 2008-10-08
Details are interesting and worth learning most of the time, but since the process of bytecode compilation is transparent, and not even observable until one starts working with modules, I decided that this particular detail could be deferred. And besides, who needs all that background in language design when you've only just begun? It's beneficial to understand the mechanics of your platform, certainly, but less so during early stages.

As far as I care, if it's run as native code, it's a "compiled" language, and everything else is "interpreted". Java and .NET are a little weird and I'm actually not certain how those should be classified; I haven't thought about them much.

Perhaps the line should be drawn at recoverability: if you can get the original source (or a close approximation of it) from the compiled form, it counts as interpreted. Python is supposed to be easily decompiled (I think this doesn't work as well with recent versions, though), but I don't think Java and .NET would, along with JIT languages.

Though the "line-by-line" thing was technically incorrect, I didn't expect anybody to take it literally. And assuming the reader comprehended it in this manner, no confusion would have arisen when the details *were* exposed, since my comment should have been ignored as mere emphasis.

I suspect the key words there are "assuming" and "should have", but it didn't seem like something one would take literally when I wrote it.

---

### Post by indecisive on 2008-10-08
What true binary compilers are there for python?

---

### Post by LaRoza on 2008-10-08
> **indecisive said:**
> What true binary compilers are there for python?

[http://ubuntuforums.org/showthread.php?t=927962](http://ubuntuforums.org/showthread.php?t=927962)

---


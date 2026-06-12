---
title: "Programming With Python (IRC Scripts)"
date: 2009-06-13
forum: Programming Talk
---

### Post by miniCruzer on 2009-06-13
Hi,
I am a new Ubuntu user, and love that it comes with Python on it.
Long story short, I am using Gutsy Gibbon, which has reached the end of its life. My DVD burner writes too fast, and does not have a slow enough setting to burn Hardy or later. So I've ordered copies. In the mean time. Is there a way to get to Python to write some IRC scripts while I wait for my Jaunty to arrive?

According to Add/Remove Programs and Synaptic, its installed, but I can't figure out how to open it...

---

### Post by soltanis on 2009-06-13
Open up a terminal and type 'python' to get a REPL.

Save your scripts with the .py extension, and then (in the shell again) type 'python x.py' (replacing x.py with the name of your script) to execute the script.

See the stickies in this forum to get started with Python programming itself.

---

### Post by miniCruzer on 2009-06-13
```

Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

Okay, now what?

---

### Post by simeon87 on 2009-06-13
Well, that's where you can type Python and run it right away. For example, type

```
[ i for i in range(10) ]
```

to display a list of numbers. Just follow some Python tutorials to learn the language itself.

If you want to run Python code from a file, you need to give a filename as well when you start the Python interpreter (so type: python filename.py, where filename.py contains your Python code).

---

### Post by Can+~ on 2009-06-13
> **miniCruzer said:**
> ```

Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

Okay, now what?

Learn it?
[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

Sample:
```
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> a = "this is a string"
>>> b = ["a list!", 3, 1.15, a]
>>> for thing in b:
...     print thing
... 
a list!
3
1.15
this is a string

>>> print "Hello world is just a one-liner!"
```

---

### Post by OnlyOneOfUsWalksAway on 2009-06-13
Firstly, create your python file. Do that by going to Applications->Accessories->Text Editor and writing your code. For example :
[PHP]
#!/usr/bin
print "hello world"
[/PHP]
Secondly, save it as x.py, open the terminal (Applications->Accessories->Terminal) and type the following : python x.py

That's all.

Note : make sure you've saved x.py in your home directory, which is /home/<your_username>.

---

### Post by simeon87 on 2009-06-13
> **OnlyOneOfUsWalksAway said:**
> Firstly, create your python file. Do that by going to Applications->Accessories->Text Editor and writing your code. For example :
[PHP]
#!/usr/bin
print "hello world"
[/PHP]
Secondly, save it as x.py, open the terminal (Applications->Accessories->Terminal) and type the following : python x.py

That's all.

Note : make sure you've saved x.py in your home directory, which is /home/<your_username>.

When you execute it like that, you don't need to #!/usr/.. line at the top.

Also, that line is now malformed as it doesn't indicate with which executable the code should be executed. An example of what the line could be is: #!/usr/bin/env python

---

### Post by miniCruzer on 2009-06-13
Wow, thanks you guys...

I thought Python would open as a separate program (must still be the Windows in me)

Thanks for helping the newbie!

---

### Post by Sinkingships7 on 2009-06-13
> **miniCruzer said:**
> Wow, thanks you guys...

I thought Python would open as a separate program (must still be the Windows in me)

Thanks for helping the newbie!

Python comes standard on many Linux distributions, because a lot of programs depend on its runtime. Happy hacking!

---

### Post by miniCruzer on 2009-06-13
> **Sinkingships7 said:**
> Python comes standard on many Linux distributions, because a lot of programs depend on its runtime. Happy hacking!

I noticed that after taking a visit to System Monitor and seeing that it's "sleeping" :):):):)

---

### Post by soltanis on 2009-06-13
Python is another program; its an interpreter (a program that interprets code for programs). It just launched inside a shell. There are plenty of GUI python shells to (with syntax highlighting and stuff), search around the forums for them (an example is IDLE, but that one isn't so good on Linux for some odd reason).

The next step is as others said, learn the language.

---

### Post by insanecrazy4 on 2009-06-13
judging by your topic your also wanting to learn how to make irc scripts for python. once you get the hang of it check out this link for a nice irc library for python which can make your scripts much easier.
[http://python-irclib.sourceforge.net/](http://python-irclib.sourceforge.net/)

also here is some basic documentation for it as well

[http://www.devshed.com/c/a/Python/IRC-on-a-Higher-Level/](http://www.devshed.com/c/a/Python/IRC-on-a-Higher-Level/)
[http://www.devshed.com/c/a/Python/IRC-on-a-Higher-Level-Concluded/](http://www.devshed.com/c/a/Python/IRC-on-a-Higher-Level-Concluded/)

---

### Post by miniCruzer on 2009-06-13
> **insanecrazy4 said:**
> judging by your topic your also wanting to learn how to make irc scripts for python. once you get the hang of it check out this link for a nice irc library for python which can make your scripts much easier.
[http://python-irclib.sourceforge.net/](http://python-irclib.sourceforge.net/)

also here is some basic documentation for it as well

[http://www.devshed.com/c/a/Python/IRC-on-a-Higher-Level/](http://www.devshed.com/c/a/Python/IRC-on-a-Higher-Level/)
[http://www.devshed.com/c/a/Python/IRC-on-a-Higher-Level-Concluded/](http://www.devshed.com/c/a/Python/IRC-on-a-Higher-Level-Concluded/)

Ooo those are some good links. I appreciate it ;-)

Q: Can I get the scripts on a network through Python, or do I need to use a client, like xChat,for example?

---


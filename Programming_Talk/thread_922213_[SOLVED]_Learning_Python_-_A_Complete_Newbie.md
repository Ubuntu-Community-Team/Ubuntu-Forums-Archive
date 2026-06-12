---
title: "[SOLVED] Learning Python - A Complete Newbie"
date: 2008-09-17
forum: Programming Talk
---

### Post by jrsc109 on 2008-09-17
Hi all

This may seem like a weird post, but I have a weird problem.

I am trying to teach myself Python (and have no programming experience at all).

On Ubuntu,I have installed Komodo Edit 4.4 and when I run a sample program, I get the correct response.

However (and here's the rub) when I run the usual:
[COLOR="SandyBrown"]print [/COLOR]'hello world' 
and double-click the command button, nothing happens.

I created a new file; called Hello-World.py, and I know the command button I created works, because the sample file works.

So, what could it be.  I may not have know-how, but I consider myself fairly intelligent, and this has me stumped.

Sorry for the rambling.  Hope someone can shed some light on this.

Thanks

---

### Post by LaRoza on 2008-09-17
You can't double click such a file. It would have to be run in the terminal because its output goes there. It won't open a terminal by itself.

---

### Post by jrsc109 on 2008-09-17
I ran it the same way that the sample file was run - the code was in the top window, and the response appeared in the output window.

I would have expected the 'hello world' script to work the same.  The program looks like it attempted to run it, but nothing happens.

---

### Post by LaRoza on 2008-09-17
> **jrsc109 said:**
> I ran it the same way that the sample file was run - the code was in the top window, and the response appeared in the output window.

I would have expected the 'hello world' script to work the same.  The program looks like it attempted to run it, but nothing happens.

I don't understand...

What is this "top window" and "output window"? It sounds like an IDE.

This is why I don't like IDE's and never recommend them. People are lost without them because they don't see what they are doing.

```

~/p$cat p.py
#!/usr/bin/env python
print "Hello world"
~/p$chmod +x p.py
~/p$./p.py
Hello world
~/p$

```

---

### Post by SeanHodges on 2008-09-17
I think I understand your problem, you're having problems using Komodo Edit (and not Python itself). The way I understand it (I may be wrong, I've never used Komodo), you need to set-up the Run button before it can do anything useful to your new program:

[http://morlockhq.blogspot.com/2008/01/launching-python-shell-and-running-code.html](http://morlockhq.blogspot.com/2008/01/launching-python-shell-and-running-code.html)


Having said that, I agree with LaRoza, if you're starting out in programming you should really consider using a simple text editor (like Gedit) and the command line to start with. You can run your program using:

```
python ./Hello-World.py
```

Until you learn how to make programs self-executable. For Python, there are some good tutorials for all this: [http://docs.python.org/tut/](http://docs.python.org/tut/)

If you start off using an IDE like Komodo, you'll find yourself depending on it later on (because there is no "command button" in other IDE's for example - other people simply won't know what you're talking about).

---

### Post by jrsc109 on 2008-09-17
Thanks for your input.  I'll look at gedit and see how I progess with that.

Oh, the trials and tribulations of a newbie...

---

### Post by ad_267 on 2008-09-17
If you're just learning python then you should try going to applications - accessories - terminal and enter "python". Then you can enter any python commands and see the result immediately. Then when you get the hang of that you can start writing scripts.

---

### Post by nvteighen on 2008-09-17
> **ad_267 said:**
> If you're just learning python then you should try going to applications - accessories - terminal and enter "python". Then you can enter any python commands and see the result immediately. Then when you get the hang of that you can start writing scripts.

+1

Or use the nice and usually under-estimated Gedit. It has a Python plugin.

Forget about IDEs. Build your own using an extensible text editor like the mentioned Gedit, vim, emacs, whatever.

---

### Post by pmasiar on 2008-09-17
Komodo has plenty of advanced features you have no use for as beginner, will just stumble on your way. If you want IDE, use the simple one, like IDLE. Or simple text editor with syntax highlighting, like SciTE, and terminal.

---


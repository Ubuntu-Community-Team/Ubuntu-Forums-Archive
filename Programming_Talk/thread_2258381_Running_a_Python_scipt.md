---
title: "Running a Python scipt"
date: 2014-12-27
forum: Programming Talk
---

### Post by pyth0n2 on 2014-12-27
Hi there Ubuntuforums community.

I have a random beginner question in regards to running python scripts.

I guess some quick context is in order. I've been doing the Codecademy and Computer Science Circles courses online. So no need for an editor so far.
However today I decided to read some other articles aswell. When I tried to follow one of these articles lessons that involved creating and running a simple script, it all fell apart.

You know when you open up IDLE, and it greets you with the text:

Python 3.4.0 (default, Apr 11 2014, 13:05:11) 
[GCC 4.8.2] on linux
Type "copyright", "credits" or "license()" for more information.



Well, when I make a simple script containing only:
```
Print ("Hello World")
```

and then save it to my Desktop as script.py and run it. I receive the following error:


```

  File "script.py", line 1
    Python 3.4.0 (default, Apr 11 2014, 13:05:11) 
             ^
SyntaxError: invalid syntax
```



Its saving the copyright information as part of the script and then running it!
I have tried googling this issue, and searching the forums, however I am at a loss as to how to put this into into keywords for a search, so Ive turned up nothing.


Can anyone shed some light on the (probably embarrasingly simple) mistake I am making?

Thanks in advance guys.

P.S. If this is worded too poorly let me know and i'll attempt to rephrase it. I've done my best though.

---

### Post by steeldriver on 2014-12-27
The IDLE IDE is kind of funny - when you go to the 'File --> Save as...' menu, it saves a **transcript of the interactive python session**, rather than saving your command(s) as actual python code.

To save an actual script, first go to 'File --> New' which opens a script file editor window, type your commands there, and then save **that**.

Alternatively you can just use any regular text editor - I use IDLE on Windows, but TBH I rarely bother with it on *nix systems

---

### Post by The Cog on 2014-12-27
Could I suggest using geany as your editor? It's in the repositories. I think it's at least worth a try-out.

---

### Post by flaymond on 2014-12-27
I'm using Vim as Python script editor (I use Terminal when I'm learning because I can learn the identation and spaces)

I think it's better for you to try regular text editor instead IDLE(It'll help you so much on the beginning, automatic in beginning is not very good for me)

I try your code in IDLE, and found the same error. The reason is, the greetings is included into the script.py. Like in steeldriver comment, it save the whole session in the shell rather only the code you type.

You can edit the script.py file and do like this, just add hash/# or simply delete the greetings -

```
 
# Python 3.4.0 (default, Apr 11 2014, 13:05:11) 
# [GCC 4.8.2] on linux
# Type "copyright", "credits" or "license()" for more information.

print ("Hello World!")
```

The # symbol will make the greetings as a comment, so the interpreter will ignore the greetings and skip to print Hello World.

but, if you really still wanna use an IDLE, try open new file instead of save as on the IDLE...This will open a blank file and the function is same like text editor

I totally prefer a regular text editor to make Python Scripts....It help you to learn the identation and spaces rules in Python.

Thanks.

---

### Post by pyth0n2 on 2014-12-28
Thanks heaps for all the replies guys.

They definitely answered my question as well as provided additional good tips. I appreciate it.

Time to start really getting into writing python scripts! :smile:

P.S. I've asked two questions on these forums so far, and both have been answered promptly and nicely.
       You guys definitely seem to have a good community going here.

---


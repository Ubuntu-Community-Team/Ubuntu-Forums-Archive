---
title: "Python"
date: 2008-03-25
forum: Programming Talk
---

### Post by Zelphien on 2008-03-25
yeah so I have Ubuntu 7.10 Gusty Gibbon and I miss our Programming Folder.

Of course I know I have Python 2.5.2 on my computer.

But where is the default? How can I find it? I need to use it too.


Anyone can help please that would be lovely


All I am asking is too where Python is located on Gusty Gibbon...

---

### Post by ruy_lopez on 2008-03-25
> **Zelphien said:**
> 
Of course I know I have Python 2.5.2 on my computer.
But where is the default? How can I find it? I need to use it too.
Anyone can help please that would be lovely
All I am asking is too where Python is located on Gusty Gibbon...

Try:
```

which python

```

---

### Post by earobinson on 2008-03-25
earobinson@MinusOne:~$ which python
/usr/bin/python

but i dont thing thats what your looking for, what exactly are you trying to figure out?

---

### Post by CptPicard on 2008-03-25
```

eneva@manticore:~$ which python
/usr/bin/python

```

---

### Post by Zelphien on 2008-03-25
well not exactly what i need now


Okay, I need to figure out how to use/get in python

I want to start making programs with python

I have it from my Add/Remove Programs feature on Ubuntu Gusty Gibbon but, I can't find the place to access it anywhere. I remember Ubuntu 7.04 had a Programming Folder for programs like this...

---

### Post by Wybiral on 2008-03-25
Interactive terminal:
```

python

```

Run source file:
```

python source.py

```

---

### Post by ruy_lopez on 2008-03-25
I use ~/bin as a programming folder. The path should be setup already. All you have to do is create ~/bin

---

### Post by LaRoza on 2008-03-25
See the sticky, specifically the section on scripting languages.

---

### Post by Lord Illidan on 2008-03-25
I think he's referring to the Python interactive shell under the Programming submenu under the Applications menu. Just type : python in a terminal to get it.

---

### Post by Zelphien on 2008-03-25
still having problems....the code you gave me

" python source.py "


didn't work

---

### Post by Lord Illidan on 2008-03-25
It was an example. Obviously, source.py must be an existing source file containing python code.

Try putting this line into an empty file :

```
print "hello world"
```

save it as example.py

and then run it as```
python example.py
```

---

### Post by Wybiral on 2008-03-25
> **Zelphien said:**
> still having problems....the code you gave me

" python source.py "


didn't work

You're going to have to be more descriptive :)

What do you mean by "didn't work"? What happened?

---

### Post by CptPicard on 2008-03-25
Probably:

```

python: can't open file 'source.py': [Errno 2] No such file or directory

```

:)

---

### Post by LaRoza on 2008-03-25
> **Zelphien said:**
> still having problems....the code you gave me

" python source.py "


didn't work

Did you read the sticky, and the section on scripting languages? It has step by step instructions. If they do not work, post the errors here.

---

### Post by Zelphien on 2008-03-25
no i just want to use python, i can find the real program anywhere on my computer, but i know i have it

---

### Post by CptPicard on 2008-03-25
The real program ... as opposed to the *unreal* python at /usr/bin/python? :)

---

### Post by Wybiral on 2008-03-25
> **Zelphien said:**
> no i just want to use python, i can find the real program anywhere on my computer, but i know i have it

Open a terminal, type "python", hit enter... You're using Python. What else do you want?

---

### Post by LaRoza on 2008-03-25
> **Zelphien said:**
> no i just want to use python, i can find the real program anywhere on my computer, but i know i have it

You didn't read the sticky that has the answer to your question and step by step instructions?

---

### Post by pmasiar on 2008-03-25
Read sticky FAQ, and especially "how to ask questions" part :-)

---

### Post by WW on 2008-03-25
> **Wybiral said:**
> Open a terminal...
Zelphien, do you know what that means?  If not, say so.  Everyone here is assuming that you do.

---

### Post by Can+~ on 2008-03-25
I know what's going on here. Most people coming from windows and many new programmers install an IDE and associate the IDE with the language they are using.

Answering your questions
-python is a programming language, it's not an "application", although you can enter the interactive mode, and the compil... but let's just ignore that for now.

-a programming language it's a way of building applications, as it would be too difficult to type 0's and 1's with a magnetized needle (god, I love xkcd), languages try to be as close to human language as possible.

-to run something on python, write an empty file with .py and start coding there, check the [ for python on the documentation](http://docs.python.org/tut/tutorial). Enter the terminal, navigate to the proper folder and write "python myfile.py".

-If you want to make it easier, install **geany** (it's on add/remove), which is an IDE that has an "execute" button, so you won't have to use the shell (although, it's good to know how to use the shell)

---

### Post by LaRoza on 2008-03-25
Oh, use IDLE then.

See [http://ubuntuprogramming.wikidot.com/Idle](http://ubuntuprogramming.wikidot.com/Idle)

---

### Post by Wybiral on 2008-03-25
> **LaRoza said:**
> Oh, use IDLE then.

See [http://ubuntuprogramming.wikidot.com/Idle](http://ubuntuprogramming.wikidot.com/Idle)

Or... Eclipse with the PyDev addon is also good.

Or... Gedit with the visible whitespace + embedded terminal + Python console is my personal preference (I personally don't feel like Python is one of those languages that requires a specific IDE, you just need to be able to see the whitespace and have syntax highlighting)

---

### Post by LaRoza on 2008-03-25
> **Wybiral said:**
> Or... Eclipse with the PyDev addon is also good.

Or... Gedit with the visible whitespace + embedded terminal + Python console is my personal preference (I personally don't feel like Python is one of those languages that requires a specific IDE, you just need to be able to see the whitespace and have syntax highlighting)

I have knocked IDLE in the past, and prefer Gedit and Vim, but it seems like for this user a highly specific tool is in order.

(I mean, if the posts so far didn't help...)

---


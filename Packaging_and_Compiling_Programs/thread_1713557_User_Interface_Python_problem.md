---
title: "User Interface Python problem"
date: 2011-03-24
forum: Packaging and Compiling Programs
---

### Post by WlaadDyaab on 2011-03-24
Hi

Currently I'm worked up after seeing this Magazine Lol for beginners: [http://fullcirclemagazine.org/python-special-edition-1/](http://fullcirclemagazine.org/python-special-edition-1/) (to download the PDF format just click on the snake's picture)

It's the first edition for User Interface programming in Python. It's meant to be for beginners...etc

Here's what I done for the first exercise:

On the PDF format it say "Type the following 4 lines."

> #!/usr/bin/env python

print 'Hello. I am a python program.'

name = raw_input("What is your name? ")

print "Hello there, " + name + "!"

What I understood was that I had to type the following in Terminal:

> python
This happened in Terminal: > rex@rex-HP-ProBook-4510s:~$ python
Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

(Nicely done! And I'm happy about it Lol)

Then I put this: > >>> #!/usr/bin/env python

Pressed the return key and got that: > ... 


I never understood what it meant so I pressed the return key, then this came up: > >>> 


Anyway I continued with the tutorial: > >>> print 'Hello. I am a python program.'
 Then I pressed the return key and got this: > Hello. I am a python program.
>>> 


Then I put this: > >>> name = raw_input("What is your name? ")

Pressed the return key: > What is your name?

I typed > Rex
Pressed return key: > >>> 


I typed this: > >>> print "Hello there, " + name + "!"

Pressed return key: > Hello there, Rex!
>>> 


Then I got stuck

How am I meant to save this?

(Please don't direct me to links. Just tell me what to type. Thanks)

---

### Post by andrew1992 on 2011-03-24
What do you mean by save? You're using the interactive interpreter right now, if you mean you want to save your program, you have to write it in a text editor and save the file. Then you can run the program with the command "python [filename]".

---

### Post by WlaadDyaab on 2011-03-25
> **andrew1992 said:**
> What do you mean by save? You're using the interactive interpreter right now, if you mean you want to save your program, you have to write it in a text editor and save the file. Then you can run the program with the command "python [filename]".

Where do I get the text editor? Is it a command?

Sorry I'm new to programming and I've had problem even with choosing what programming language is suitable for me

Again, could you please just tell me the code or command that I need to put, and not direct me to links. I don't understand what to do when viewing links because they already expect me to know something about programming but I never studied programming in college or uni...etc

---

### Post by andrew1992 on 2011-03-25
Alright, sounds like you're a new programmer.  What you're seeing and working with right now is Python's **interactive interpreter**.  Essentially, this is a handy tool to use to test little pieces of code to see if they work, before incorporating them into a real program.  Most Python teaching resources start with examples from the interactive interpreter, but you're absolutely right, they don't make it clear enough to new programmers that it isn't used for real programming.

In real programs, you would write all the code using a text editor (or an IDE, but save this for when you work on larger projects).  If you are running Ubuntu, you already have gedit (the text editor you can find in the Applications menu).  Gedit is nice because it has syntax highlighting for many languages, including Python. So you would write all of your code in gedit and save it just like any other document, and then you can run it from the command line.  For example, to write a program that prints "Welcome to Python!" to the screen, first, you would open a text editor like gedit (and select Python for syntax highlighting), and then type in the print statement:

```
print "Welcome to Python!"
```

Then, save the file (you can use a .py extension for it to work in windows as well).  Then, if you use your terminal to get into the directory where it was saved, you can **run** the program with the command:

```
python [insert filename]
```

So if we called our little program "hello.py", we can run it with

```
python hello.py
```

Does this make sense to you?

---

### Post by WlaadDyaab on 2011-03-25
> **andrew1992 said:**
> Alright, sounds like you're a new programmer.  What you're seeing and working with right now is Python's **interactive interpreter**.  Essentially, this is a handy tool to use to test little pieces of code to see if they work, before incorporating them into a real program.  Most Python teaching resources start with examples from the interactive interpreter, but you're absolutely right, they don't make it clear enough to new programmers that it isn't used for real programming.

In real programs, you would write all the code using a text editor (or an IDE, but save this for when you work on larger projects).  If you are running Ubuntu, you already have gedit (the text editor you can find in the Applications menu).  Gedit is nice because it has syntax highlighting for many languages, including Python. So you would write all of your code in gedit and save it just like any other document, and then you can run it from the command line.  For example, to write a program that prints "Welcome to Python!" to the screen, first, you would open a text editor like gedit (and select Python for syntax highlighting), and then type in the print statement:

```
print "Welcome to Python!"
```

Then, save the file (you can use a .py extension for it to work in windows as well).  Then, if you use your terminal to get into the directory where it was saved, you can **run** the program with the command:

```
python [insert filename]
```

So if we called our little program "hello.py", we can run it with

```
python hello.py
```

Does this make sense to you?

[SOLVED]

Thanks a million! That just made my week Lol not just my day

Thank you very much andrew1992

Here's what I done (for other people to benefit from) to get my first User Interface Python Interactive Interpreter program using Terminal:

Note: I don't know if that makes any difference but I'm using Ubuntu 10.10

- Applications > Accessories > Text Editor (a.k.a Gedit)
- In "Untitled Document 1 - gedit" windows > Type the following as an example exercise: print "Welcome to Python!"
- File > Save As... > In "Name" type "hello.py"
- Save

Notice how "print" became brown and ""Welcome to Python!"" became pink and how the Python IDLE logo is before where it says "hello.py"

Now to open Terminal:

- Applications > Accessories > Terminal (short cut: ctrl + alt + T)
- Type "python hello.py"
- Press "Enter" or "the return key"

That's what I got: > rex@rex-HP-ProBook-4510s:~$ python hello.py
Welcome to Python!
rex@rex-HP-ProBook-4510s:~$ 


Again thanks to andrew1992. I think this should help newbies in the future to understand how to program in User Interface

And yes indeed, no one made that simple for me to understand up until now, and thanks again andrew1992

Finally

To find where you saved you hello.py file:

Places > Home folder > hello.py (it should be somewhere over there)

---

### Post by andrew1992 on 2011-03-25
You're welcome! Glad to see you've figured it all out.

---

### Post by cgroza on 2011-03-25
That interactive interpreter is just to test some quick code.

---


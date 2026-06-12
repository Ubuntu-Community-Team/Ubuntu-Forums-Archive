---
title: "Python 3.5 problem"
date: 2016-05-17
forum: Packaging and Compiling Programs
---

### Post by hall-johnanthony on 2016-05-17
ok I HAVE looked to see if this has been asked and it hasn't 'quite'.

Firstly hello and thank you for taking the time to look at this.

ok I'm hoping to learn Python 3.5 (I'm completely new to programming btw) so I write the traditional 'Hello World' in Kate and save it to Documents/Progs as 'helloworld.py' - in ths file which I created for my Pythin 3.5 programs. I cd to this directory from the terminal and for the life of me I can't get this to open or run. I either get a 'file not found' error or I get 'syntax error'.

Now I think whats happening is that the terminal defaults to 2.7 which would explain the syntax error. If I open the terminal and type 'Pythin3.5' to begin with I get the usual '>>>' and can write in Python 3.5 BUT I can't then save the file. 

So I need the thing to recognise the syntax of 3.5 programs written in Kate because I'm never going to write in 2.7. 

So the questions are:

1. How do I get the terminal (Konsole) to recognise P3.5 files that I write in Kate and save in the said directory?
2. Can I write in P3.5 in the terminal and save it from there - and if so will I still have the same prob?

I realise that the 'helloworld.py' file is very basic but I simply cannot move on without knowing how to open my saved programs with 3.5.

If someone could do the Touron Rah for me, I would appreciate it :)

Thanks for reading.

Kubuntu 16.04 - which I believe to be the most advanced OS on earth. Genius pure and simple :)

---

### Post by spjackson on 2016-05-17
Does this help you with your issues with running your script?
```

$ pwd
/home/spj/Documents/Progs
$ ls -l
total 4
-rw-rw-r-- 1 spj spj 24 May 17 13:06 helloworld.py
$ cat helloworld.py

print("Hello, World!")
##### Run the script in the current directory by invoking python3
$ python3 helloworld.py
Hello, World!
##### Just Run the script as a commend - Fail
$ helloworld.py
helloworld.py: command not found
##### Specify where to find the script - Fail
$ ./helloworld.py
bash: ./helloworld.py: Permission denied
##### Allow everyone to execute the script.
$ chmod a+x ./helloworld.py
chmod a+x ./helloworld.py
$ ls -l
total 4
-rwxrwxr-x 1 spj spj 24 May 17 13:06 helloworld.py
$ ./helloworld.py
./helloworld.py: line 2: syntax error near unexpected token `"Hello, World!"'
./helloworld.py: line 2: `print("Hello, World!")'
##### Edit helloworld.py to use shebang magic
$ cat helloworld.py
#!/usr/bin/python3

print("Hello, World!")
$ ./helloworld.py
Hello, World!
$ cd ~
##### Run the script (with shebang) by giving the full path to it.
$ ~/Documents/Progs/helloworld.py
Hello, World!
##### Allow all scripts in the directory to be found as commands.
spj@ubuntu-16-04-i386:~$ PATH=$PATH:$HOME/Documents/Progs
spj@ubuntu-16-04-i386:~$ helloworld.py
Hello, World!


```
> 
1. How do I get the terminal (Konsole) to recognise P3.5 files that I write in Kate and save in the said directory?

I don't use Kate and I don't know how to do that, but I expect that "File->Save As" ought to let you save it where you want.

---

### Post by hall-johnanthony on 2016-05-17
Hi there,

Thanks for this but I honestly don't understand all that Im looking at. Do I have to type in all that just to get this one tiny script to run?

Ant.

---

### Post by $yl9pAR%t on 2016-05-17
```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```

Did you start your file created in Kate with these two lines above?

EDIT:

Regardless of your problem:

1. Good starting point to learn Python

[https://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_3](https://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_3)

2. Perhaps instead of Kate editor start using Geany?

---

### Post by spjackson on 2016-05-18
> **hall-johnanthony said:**
> 
Thanks for this but I honestly don't understand all that Im looking at. Do I have to type in all that just to get this one tiny script to run?

There are many ways to do it. My post was meant to demonstrate several ways and to show some of the solutions to typical errors that arise. I'm sorry that you found it confusing. It is sufficient simply to do:
```

cd ~/Documents/Progs
python3 helloworld.py

```

---

### Post by hall-johnanthony on 2016-05-18
Thanks for this. No I didn't use this - the book I bought seems to be 'windows centric' I added the two lines but it made no difference. I think I have figured out the problem. Python 3 is slightly different to pytyhon 3.5 in its syntax. The difference is this:

Python3: print ("Hello world") #This works and can be run in the terminal by cd to directory and typing Python3 helloworld.py

Pythin 3.5: >>> print ("hello world 2") # This works if I write it in the terminal and if I first type python3.5 BUT if I write it in geany OR Kate I get a syntax error as follows:

anthony@anthony-HP-255-G3-Notebook-PC:~/Documents/Progs$ python3 helloworld.py
  File "helloworld.py", line 1
    >>> print ("Hello world")
     ^
SyntaxError: invalid syntax
anthony@anthony-HP-255-G3-Notebook-PC:~/Documents/Progs$ 

On the other hand if I write the thing in konsole by first invoking Python 3.5 I get:
anthony@anthony-HP-255-G3-Notebook-PC:~/Documents/Progs$ python3.5
Python 3.5.1+ (default, Mar 30 2016, 22:46:26) 
[GCC 5.3.1 20160330] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print ("hello world")
hello world
>>> 

So the problem seems to be getting the terminal to recognise the syntax of 3.5 when written outside the terminal.

Lastly: Geany doesn't automatically add the three >>> whereas Kate does. I have to learn 3.5 for a project I am working on with others and I need the 3.5 syntax to work. The webpage you offered is for 3 and does not mention these >>> which are used in 3.5.

I really am confused!

---

### Post by oldfred on 2016-05-18
> start using Geany
+1 on mefisto888's suggestion

Edit preferences.
Just change editor to use spaces in place of tabs or you get into issues.
Change file save to use spaces not tabs.

Edit build commands to use python3, default still seems to be python2.7
[http://stackoverflow.com/questions/29105941/how-do-i-make-python3-the-default-python-in-geany](http://stackoverflow.com/questions/29105941/how-do-i-make-python3-the-default-python-in-geany)

---

### Post by steeldriver on 2016-05-18
It sounds like you are including the >>> in your file - DON'T

It's just a "prompt" that is used in the interactive shell

---

### Post by $yl9pAR%t on 2016-05-18
Just to clarify, in Ubuntu 16.04 by default:

1. Invoking Python interpreter in terminal by typing **python**, makes you are working with Python 2.7.11+

2. Invoking Python interpreter in terminal by typing **python3**, makes you are working with Python 3.5.1+

Let us know if you are not using 16.04

Use shebang lines at the beginning of your python scripts. As I said before, for python 3:


```
#!/usr/bin/env python3
```

And now you can run this scripts in terminal just typing:

```
./name_of_your_script
```

---

### Post by hall-johnanthony on 2016-05-18
It worked! Well sort of... The spaces idea didn't work but writing it in geany minus spaces worked a treat. For clarity I wrote the following in Geany:

print ("This is using Geany without spaces and without tabs")
print ("Here's hoping!")   
print ("Why do all the texts for learning Python 3.5 insist on tabs?")

The terminal worked as follows:

anthony@anthony-HP-255-G3-Notebook-PC:~$ cd Documents/Progs
anthony@anthony-HP-255-G3-Notebook-PC:~/Documents/Progs$ python3 Geanyspaces.py
This is using Geany without spaces and without tabs
Here's hoping!
Why do all the texts for learning Python 3.5 insist on tabs?
anthony@anthony-HP-255-G3-Notebook-PC:~/Documents/Progs$ 

So now I know what NOT to do and how to open any future programs in th Terminal.

I am extremely grateful to you all for your time and patience and it is my hope to be able to lend assistance to someone else in turn -when I can.

print ("Thanks guys")

Ant.

---

### Post by oldfred on 2016-05-19
You still use tabs to indent, which is python.

But Geany will convert to spaces, if editor set that way.

---


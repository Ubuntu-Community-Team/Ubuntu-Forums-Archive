---
title: "Super basic python problem (I'm very new and trying to learn python)"
date: 2008-07-12
forum: Programming Talk
---

### Post by s3a on 2008-07-12
I'm reading diveintopython and it says:

[B]Now run this program and see what happens.
In the ActivePython IDE on Windows, you can run the Python program you're editing by choosing File&#8722;>Run...
(Ctrl&#8722;R). Output is displayed in the interactive window.
In the Python IDE on Mac OS, you can run a Python program with Python&#8722;>Run window... (Cmd&#8722;R), but there is
an important option you must set first. Open the .py file in the IDE, pop up the options menu by clicking the black
triangle in the upper&#8722;right corner of the window, and make sure the Run as __main__ option is checked. This is a
per&#8722;file setting, but you'll only need to do it once per file.
On UNIX&#8722;compatible systems (including Mac OS X), you can run a Python program from the command line:
python odbchelper.py
The output of odbchelper.py will look like this:
server=mpilgrim;uid=sa;database=master;pwd=secret[/B]

However, when I type "odbchelper.py" into the terminal I get:
[B]
deniz@deniz-desktop:~$ odbchelper.py
bash: odbchelper.py: command not found
deniz@deniz-desktop:~$[/B]

What am I doing wrong??

*Edit: I type "python odbchelper.py" into the terminal and get:

[B]deniz@deniz-desktop:~$ python odbchelper.py
python: can't open file 'odbchelper.py': [Errno 2] No such file or directory
deniz@deniz-desktop:~$[/B]*

---

### Post by -grubby on 2008-07-12
Just type in "python" and you should be all set

EDIT: Wait, I misread. Do you have this file saved in your home (/home/user) directory?

---

### Post by shifty2 on 2008-07-12
You need to be in the same directory as obdchelper.py in order to run it using the command python obdchelper.py.

For example:
```

$ python /path/to/obchelper.py

```
or
```

$ cd /directory/with/obchelper/in
$ python obchelper.py

```

---

### Post by s3a on 2008-07-12
I don't know the directory though, I would cd if I did, all I know is the free book diveintopython says to do it. Sorry for being an idiot :(, I am just trying to learn python to help myself as well as the community.

---

### Post by s3a on 2008-07-12
So wait...I don't think this is an important part of the book, it just wants to show me a certain output right? So, basically, if I knew the directory and **cd**ed to it then entered "python obchelper.py", I would get the output that the book shows?

---

### Post by -grubby on 2008-07-12
> **s3a said:**
> So wait...I don't think this is an important part of the book, it just wants to show me a certain output right? So, basically, if I knew the directory and **cd**ed to it then entered "python obchelper.py", I would get the output that the book shows?

Yes

---

### Post by s3a on 2008-07-12
Thanks!

---

### Post by s3a on 2008-07-12
Is:

[B]def buildConnectionString(params):

"""Build a connection string from a dictionary of parameters.

Returns string."""[/B]

actual python commands or are they just examples for you to learn? I'm trying to execute things as I read on but none of the commands seem to work...even after I type python followed by those commands. What am I doing wrong? Or can I simply not execute those?

---

### Post by Gilabuugs on 2008-07-12
Try starting off with a much lighter book than dive into python, the FAQs at the top have a few links for beginners, 

here is a more friendly book:

[http://www.swaroopch.com/byteofpython/](http://www.swaroopch.com/byteofpython/)

How to think like a CS with python is good as well:

[http://www.greenteapress.com/thinkpython/thinkCSpy/](http://www.greenteapress.com/thinkpython/thinkCSpy/)

---

### Post by red_Marvin on 2008-07-12
> **s3a said:**
> Is:

[B]def buildConnectionString(params):

"""Build a connection string from a dictionary of parameters.

Returns string."""[/B]

actual python commands or are they just examples for you to learn? I'm trying to execute things as I read on but none of the commands seem to work...even after I type python followed by those commands. What am I doing wrong? Or can I simply not execute those?

As far as I can see it is a function (called buildConnectionString) definion with a doc string (stuff between triple quotes), right now the function won't do anything, since it's only contents are said doc string.

---

### Post by s3a on 2008-07-12
> **Gilabuugs said:**
> Try starting off with a much lighter book than dive into python, the FAQs at the top have a few links for beginners, 

here is a more friendly book:

[http://www.swaroopch.com/byteofpython/](http://www.swaroopch.com/byteofpython/)

How to think like a CS with python is good as well:

[http://www.greenteapress.com/thinkpython/thinkCSpy/](http://www.greenteapress.com/thinkpython/thinkCSpy/)

Thanks! I'm reading byteofpython now!

---

### Post by pmasiar on 2008-07-12
Dive into Python is not for beginner programmers - author assumes experience in other language, and just dives in.

Check wiki in my sig for good links (also linked from sticky FAQ)

---

### Post by s3a on 2008-07-12
I dont understand the following from byteofpython:

[B]You are now able to run the program as long as you know the exact path of the program - but what if
you wanted to be able to run the program from anywhere? You can do this by storing the program in one
of the directories listed in the PATH environment variable. Whenever you run any program, the system
looks for that program in each of the directories listed in the PATH environment variable and then runs
that program. We can make this program available everywhere by simply copying this source file to one
of the directories listed in PATH.
$ echo $PATH
/opt/mono/bin:/usr/local/bin:/usr/bin:/bin:/usr/X11R6/bin:/home/swaroop/bin
$ cp helloworld.py /home/swaroop/bin/helloworld
$ helloworld
Hello World[/B]

Can someone explain it to me in further detail please?

---

### Post by ghostdog74 on 2008-07-12
that's the problem of not getting familiar with your shell and shell environments before plunging into Python. Explanation [here]("http://www.gnu.org/software/bash/manual/bashref.html#Bourne-Shell-Variables")

---

### Post by LaRoza on 2008-07-13
> **s3a said:**
> 
Can someone explain it to me in further detail please?

It doesn't matter what it means; you shouldn't be altering your $PATH without knowledge of it. Just run your programs using absolute paths (or the "." for the CWD)

---

### Post by s3a on 2008-07-13
Well, I guess it is trying to show me how to run my programs regardless of where they are but, **cd**ing to directory alone should do it for me [atleast for now], right?

---

### Post by LaRoza on 2008-07-13
> **s3a said:**
> Well, I guess it is trying to show me how to run my programs regardless of where they are but, **cd**ing to directory alone should do it for me [atleast for now], right?

Right.

---

### Post by -grubby on 2008-07-13
> **s3a said:**
> Well, I guess it is trying to show me how to run my programs regardless of where they are but, **cd**ing to directory alone should do it for me [atleast for now], right?

I don't get why that wouldn't do it for you every time. If you wanted to run your programs from the command line with one word I assume you'd have to make an sh file in /usr/bin/

---

### Post by s3a on 2008-07-14
_Another thing I am not really getting:_

Note for Regular Expression Users
Always use raw strings when dealing with regular expressions. Otherwise, a lot of backwhack-
ing may be required. For example, backreferences can be referred to as **'\\1' or r'\1'.**

I bolded what I don't get. for the first one, I keep thinking the \ makes the first ' diseappear and I am getting confused. Can someone clarify this for me please?

---

### Post by LaRoza on 2008-07-14
> **s3a said:**
> _Another thing I am not really getting:_

Note for Regular Expression Users
Always use raw strings when dealing with regular expressions. Otherwise, a lot of backwhack-
ing may be required. For example, backreferences can be referred to as **'\\1' or r'\1'.**


There are several ways of writing strings. A "raw" string is just that, a raw string. Nothing is interpreted.
```

x = "this\nis\nx\n\n"
y = r"this\nis\nx\n\n"

print x
print y

```

---

### Post by s3a on 2008-07-14
Ya but why is there two **\\**'s in the first one and not one?

---

### Post by LaRoza on 2008-07-14
> **s3a said:**
> Ya but why is there two **\\**'s in the first one and not one?

Because for a regex, "\" has meaning. In Python, it is an escape character, so to print a "\", you have to use "\\". To use a regex with a "\", you have to use three.

---

### Post by s3a on 2008-07-14
Ok, I got almost all of what you said. The last part: "To use a regex with a "\", you have to use three." confused me.

_Last question before I can move on:_ Why do I need to use ***_three_*** "\\\" in order to make one "\" in a regular expression?

---

### Post by LaRoza on 2008-07-14
> **s3a said:**
> Ok, I got almost all of what you said. The last part: "To use a regex with a "\", you have to use three." confused me.

_Last question before I can move on:_ Why do I need to use ***_three_*** "\\\" in order to make one "\" in a regular expression?

You don't; you just have to do it in a non raw string.

Why? Because you need two to do one, and regex requires one extra. Add them together.

---

### Post by s3a on 2008-07-14
Ok so back to the beggining; _'\\1' or r'\1'_ the first one is a regular expression and the second one is a raw expression and in a regular expression you need two \\s to make one \ while using the raw mode there (r), it allows you to not waste time adding extra \s as escape sequences, am I right?

---

### Post by pmasiar on 2008-07-14
Did you tried to read docs?

raw strings are 'as is', while in normal plain strings you can use special characters like '\n' and '\t' - and then obviously you need '\\' as a way to express r'\'.

---

### Post by LinuX-M@n1@k on 2008-07-14
Sorry, I have a question:
Why
```
#!/usr/bin/env python
```and not```
#!/usr/bin/python
```
And what is the difference?

Sorry again for asking this question in your thread :).

---

### Post by nanotube on 2008-07-14
> **LinuX-M@n1@k said:**
> Sorry, I have a question:
Why
```
#!/usr/bin/env python
```and not```
#!/usr/bin/python
```
And what is the difference?

Sorry again for asking this question in your thread :).

this [rather long] discussion thread will give you a [very] thorough explanation:
[http://mail.python.org/pipermail/python-list/2008-May/thread.html#489190](http://mail.python.org/pipermail/python-list/2008-May/thread.html#489190)

---

### Post by pmasiar on 2008-07-14
> **nanotube said:**
> this [rather long] discussion thread will give you a [very] thorough explanation:
[http://mail.python.org/pipermail/python-list/2008-May/thread.html#489190](http://mail.python.org/pipermail/python-list/2008-May/thread.html#489190)

... where relevant bit is:

> 
The "env" method allows python to be installed in an alternate location
(i.e. /usr/local/bin).  "env" in this case is being used to launch python
from whatever location python is installed to.


"#!/usr/bin/python" hardwires python location, program will not work if some distro will place python elsewhere

---

### Post by s3a on 2008-07-14
[B]% Modulo Returns the remainder of 8%3   gives  2.   -
         the division             25.5%2.25 gives 1.5
                                  .[/B]

I don't get that at all!

---

### Post by nanotube on 2008-07-14
> **s3a said:**
> [B]% Modulo Returns the remainder of 8%3   gives  2.   -
         the division             25.5%2.25 gives 1.5
                                  .[/B]

I don't get that at all!

2*3 + 2 = 8

and also 25.5%2.25 should be 0.75, not 1.5

see here for a general explanation of remainders:
[http://en.wikipedia.org/wiki/Remainder](http://en.wikipedia.org/wiki/Remainder)

---

### Post by thornmastr on 2008-07-14
> **nanotube said:**
> 2*3 + 2 = 8

and also 25.5%2.25 should be 0.75, not 1.5

see here for a general explanation of remainders:
[http://en.wikipedia.org/wiki/Remainder](http://en.wikipedia.org/wiki/Remainder)

Using the python shell 2.52

>>> 25.5%2.25
0.75
>>> 

Robert

---

### Post by s3a on 2008-07-14
So the book is wrong there then? Since it is 0.75 instead of 1.5? And I am trying to understand these mathematic looking things. So, is there a mathematical way of remembering this? I am going to grade 11 once my summer is over, is this something in math that I am going to see in the future or is this a programming only thing? Like what I really want to know, is how can I understand what the % does?

---

### Post by nanotube on 2008-07-15
> **s3a said:**
> So the book is wrong there then? Since it is 0.75 instead of 1.5? And I am trying to understand these mathematic looking things. So, is there a mathematical way of remembering this? I am going to grade 11 once my summer is over, is this something in math that I am going to see in the future or is this a programming only thing? Like what I really want to know, is how can I understand what the % does?

read the wikipedia article about the remainder. that's what the % does - it gives you the remainder from a division. it is not some fancy math concept - you must have learned it back in elementary school, when you first learned about division.

and yes, if the book said 25.5%2.25 = 1.5, then it is wrong (as you can confirm for yourself by entering that in a python shell). errors happen everywhere, including python books. :)

---

### Post by s3a on 2008-07-15
Ok, the left and right shift I have more confusion for than any previous python thing I've encountered.

[B]<< Left Shift  Shifts the bits of the      2 << 2 gives 8. - 2 is
               number to the left by the   represented by 10 in
               number of bits specified.   bits. Left shifting by 2
               (Each number is repres-     bits gives 1000 which
               ented in memory by bits     represents the decimal 8.
               or binary digits i.e. 0 and
               1)
>> Right Shift Shifts the bits of the      11 >> 1 gives 5 - 11
               number to the right by      is represented in bits by
               the number of bits spe-     1011 which when right
               cified.                     shifted by 1 bit gives
                                           101 which is nothing
                                           but decimal 5.
[/B]

---

### Post by s3a on 2008-07-15
How do you know which numbers represent a certain amount of bits? Is there an **easy** way to find out?

---

### Post by nanotube on 2008-07-15
it looks like you need to learn about the binary number system:
[http://en.wikipedia.org/wiki/Binary_numeral_system](http://en.wikipedia.org/wiki/Binary_numeral_system)

---

### Post by s3a on 2008-07-15
Is the binary number system important for python programming?

---

### Post by LaRoza on 2008-07-15
> **s3a said:**
> Is the binary number system important for python programming?

No. It isn't important for any language really. It is important for language independent algorithms though, but that is really not important at the moment.

The binary number system is easy. Instead of ones, tens, hundreds, you have ones, twos, fours, eights, sixteens, etc.

---

### Post by ghostdog74 on 2008-07-15
its not important for any language, but one who meddles with the computer in any way should at least know what are bits and bytes. They are the basic foundations.

---

### Post by pmasiar on 2008-07-15
> **s3a said:**
> Is the binary number system important for python programming?

No, if you are happy with normal decimal numbers.

yes, if you want to understand what shifting bits means. 

But it is so simple that I do not see reason not to read the wikipedia article. If you cannot understand such simple concept, how you handle more abstract ones? It is training exercise for your brain.

---

### Post by LaRoza on 2008-07-15
> **pmasiar said:**
> 
It is training exercise for your brain.

My clock is a true binary clock. I can read binary dots (simple led rows) without much thought. Much more interesting than a typical digital clock.

---

### Post by nanotube on 2008-07-15
> **LaRoza said:**
> My clock is a true binary clock. I can read binary dots (simple led rows) without much thought. Much more interesting than a typical digital clock.

i saw that on thinkgeek at some point - looks very cool. :)

---

### Post by LaRoza on 2008-07-15
> **nanotube said:**
> i saw that on thinkgeek at some point - looks very cool. :)

I have the red led one, with it in true binary (the one on the pages are in binary encoded decimal, very newbish)

---

### Post by nanotube on 2008-07-16
> **LaRoza said:**
> I have the red led one, with it in true binary (the one on the pages are in binary encoded decimal, very newbish)

linky? :)

---

### Post by LaRoza on 2008-07-16
> **nanotube said:**
> linky? :)

[http://img88.imageshack.us/my.php?image=cimg0030in9.jpg](http://img88.imageshack.us/my.php?image=cimg0030in9.jpg)

---


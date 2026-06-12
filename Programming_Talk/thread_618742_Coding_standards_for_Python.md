---
title: "Coding standards for Python"
date: 2007-11-20
forum: Programming Talk
---

### Post by NovaAesa on 2007-11-20
Does anyone know what are the standard coding conventions for Python. Specifically I mean things like how to choose names for variables/functions etc. 

The reason that I'm asking is that I've recently jumped into Python (just finished my final high school exams and have 3 months to kill before university) but I want to make sure I get things right from the start as to avoid creating bad habits for myself.

My only previous programming experience is with Visual Basic. I know that in VB is was a convention to start variable names with a prefix for the data type and then use camel case for the rest of the name. I get the impression from what I've read so far about Python is that typing (talking about data types here) works very differently compared to most other languages.

So could someone shed some light on any preexisting coding conventions? And if someone could explain how typing works in Python that would be great too.

Thanks

---

### Post by tyoc on 2007-11-20
[http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/) ???

also in  python prompt 
> import thishehe

---

### Post by LaRoza on 2007-11-20
> **NovaAesa said:**
> And if someone could explain how typing works in Python that would be great too.

[http://rgruet.free.fr/PQR25/PQR2.5.html](http://rgruet.free.fr/PQR25/PQR2.5.html)

Python is dynamic, it will assign types automatically, however, it will enforce them, unlike other languages. This won't work:

[php]
string = "2"
integer = 2

print string + integer
[/php]

You can use the + operator on strings (to concatenate  them) or to add numbers, however, you can not mix data types. Data types can be converted:

int() to integer
float() to decimal
str() to string
ord() to ascii (one charcter)
hex() to hex

---

### Post by pmasiar on 2007-11-20
Beyond PEP008, you might be interested in Python idioms.

Some are linked in my wiki: [http://learnpython.pbwiki.com/PythonTricks](http://learnpython.pbwiki.com/PythonTricks) some I bookmarked but not added :-( , you might find them via Google, 'python idioms"

My wiki has also links to training tasks for Python learner, should keep you busy for couple months at least. Make sure you check PythonChallenge website.

---

### Post by NovaAesa on 2007-11-22
Thanks guys, that's really helped!

> My wiki has also links to training tasks for Python learner, should keep you busy for couple months at least. Make sure you check PythonChallenge website
I'll have a look through this when I finish reading the book I got on Python ("Beginning Python")

---

### Post by NovaAesa on 2007-11-23
Hi, I have another question. This may seem kind of silly, but I've been trying to work it out all arvo and can't get it to work. How on earth are you meant to make your own functions in Python? I keep getting an error when I try to call the function, for example:

> Traceback (most recent call last):
  File "/home/ps/Python Programming/Python Challenge/3.py", line 6, in <module>
    if IsSequence(Counter, String):
NameError: name 'IsSequence' is not defined

I'm working through the Python Challenge website at the moment (and finding it a very entertaining way to learn a language), but I'm stuck on 3 (please don't tell me what the answer is!). I want to use a function in the program I've written to solve it, but alas it won't work. Here's the code, could anyone work out why my functions cause an error when they are called?

[PHP]String = open("3.txt").read()

Counter = -1
while Counter < len(String):
    Counter =+ 1
    if IsSequence(Counter, String):
        print String[Counter + 3]

def Upper(Chr):
    if ord(Chr) >= 65 and ord(Chr) <= 90:
        return True
    else:
        return False
    
def Lower(Chr):
    if ord(Chr) >= 97 and ord(Chr) <= 122:
        return True
    else:
        return False   

def NextThreeUpper(Start, Text):
    Flag = True
    if Upper(Text[Start]) == False or Text[Start] == "\n":
        Flag = False
    if Upper(Text[Start + 1]) == False or Text[Start + 1] == "\n":
        Flag = False    
    if Upper(Text[Start + 2]) == False or Text[Start + 2] == "\n":
        Flag = False
    return Flag

def IsSequence(Start, Text):
    Flag = True
    if NextThreeUpper(Start, Text) == False:
        return False
    if Lower(Text[Start + 3]) == False:
        return False
    if NextThreeUpper(Start + 4, Text) == False:
        return False
    return True[/PHP]

---

### Post by LaRoza on 2007-11-23
[php]
def Upper(Chr):
    if ord(Chr) >= 65 and ord(Chr) <= 90:
        return True
    else:
        return False
    
def Lower(Chr):
    if ord(Chr) >= 97 and ord(Chr) <= 122:
        return True
    else:
        return False   

def NextThreeUpper(Start, Text):
    Flag = True
    if Upper(Text[Start]) == False or Text[Start] == "\n":
        Flag = False
    if Upper(Text[Start + 1]) == False or Text[Start + 1] == "\n":
        Flag = False    
    if Upper(Text[Start + 2]) == False or Text[Start + 2] == "\n":
        Flag = False
    return Flag

def IsSequence(Start, Text):
    Flag = True
    if NextThreeUpper(Start, Text) == False:
        return False
    if Lower(Text[Start + 3]) == False:
        return False
    if NextThreeUpper(Start + 4, Text) == False:
        return False
    return True

String = open("3.txt").read()

Counter = -1
while Counter < len(String):
    Counter =+ 1
    if IsSequence(Counter, String):
        print String[Counter + 3]
[/PHP]

---

### Post by NovaAesa on 2007-11-23
Oh I get it now. I feel silly :S

---

### Post by NovaAesa on 2008-01-01
Ok, I know my thread is old by now, but I have another question that's on the same topic so I thought I would be better to continute this one rather than starting a new thread :)

So here a quote from the PEP 8 Style Guide for Python, but I can't understand what it really means:
>     In addition, the following special forms using leading or trailing
    underscores are recognized (these can generally be combined with any case
    convention):

    - _single_leading_underscore: weak "internal use" indicator.  E.g. "from M
      import *" does not import objects whose name starts with an underscore.

    - single_trailing_underscore_: used by convention to avoid conflicts with
      Python keyword, e.g.

      Tkinter.Toplevel(master, class_='ClassName')

    - __double_leading_underscore: when naming a class attribute, invokes name
      mangling (inside class FooBar, __boo becomes _FooBar__boo; see below).

    - __double_leading_and_trailing_underscore__: "magic" objects or
      attributes that live in user-controlled namespaces.  E.g. __init__,
      __import__ or __file__.  Never invent such names; only use them
      as documented.

What I'm wondering about is what I should name methods and variables in a class that I don't want the person using the class to access. I'm thinking I should either be using either a leading underscore or a double leading underscore. I don't really understand what it means by "invokes mangling" either.

I'm feeling slightly confused :confused:

---

### Post by NovaAesa on 2008-01-01
Woops, my bad I should have read the rest of PEP 8!

It answers my question a few pages down:

>  Method Names and Instance Variables

      Use the function naming rules: lowercase with words separated by
      underscores as necessary to improve readability.

      [B]Use one leading underscore only for non-public methods and instance
      variables.[/B]

      To avoid name clashes with subclasses, use two leading underscores to
      invoke Python's name mangling rules.

      Python mangles these names with the class name: if class Foo has an
      attribute named __a, it cannot be accessed by Foo.__a.  (An insistent
      user could still gain access by calling Foo._Foo__a.)  Generally, double
      leading underscores should be used only to avoid name conflicts with
      attributes in classes designed to be subclassed.

      Note: there is some controversy about the use of __names (see below).

---

### Post by ghostdog74 on 2008-01-01
> **NovaAesa said:**
> 
The reason that I'm asking is that I've recently jumped into Python (just finished my final high school exams and have 3 months to kill before university) but I want to make sure I get things right from the start as to avoid creating bad habits for myself.

If you want to make things right , read the [Python docs]("http://www.python.org/doc/") and understand them. Take the tutorial, then after that, read the library references. That's the best path to take for every beginner to Python. No use jumping into it without a clue of what Python really is. Forget about the challenges. those are for people who understand what's going on. It may sound a bit harsh, but that's the best advice there is.

---

### Post by pmasiar on 2008-01-02
> **NovaAesa said:**
> what I should name methods and variables in a class that I don't want the person using the class to access. 

Leading underscore is not "real" security, it is just suggestion ("don't do it because I asked you so, not because I have a shotgun"), so if person needs to, can use "private" methods and variables, but was warned that you may change them later.

---

### Post by NovaAesa on 2008-01-02
> **pmasiar said:**
> Leading underscore is not "real" security, it is just suggestion ("don't do it because I asked you so, not because I have a shotgun"), so if person needs to, can use "private" methods and variables, but was warned that you may change them later.

So is there any way of making private methods unable to be used?

---

### Post by pmasiar on 2008-01-03
> So is there any way of making private methods unable to be used?

not really. Why you need that? What do you want to accomplish?

AFAIK there is no "rock-solid" method in any language: if the other coder has access to sources, any of those methods can be circumvented by preprocessing the sources.

No program is safe from really determined and skilled crackers, as you can see in [slides about cracking Skype](http://www.secdev.org/conf/skype_BHEU06.handout.pdf) from blackhat conference. Even obfuscation, runtime code modification and partial checksums to protect from disassembling can and will be cracked by determined masters of the dark arts  - and tools to do that are in public (and were written in Python :-)  )

---

### Post by NovaAesa on 2008-01-03
> **pmasiar said:**
> not really. Why you need that? What do you want to accomplish?


I was just wondering because I wanted to make my classes as robust as possible. And also, if there's a better way of doing something I like to find out what it is. That's just my nature - I like to ask lots of questions :)

---

### Post by pmasiar on 2008-01-04
Whole philosophy of the security in Python is different than in ie Java.

Python is not intended to write ie nuclear plant management system, where layers of paranoid restrictions apply. Instead, programmers are considered "consenting adults" who  behave responsibly and do not try to break each other code with malicious intent. You are not supposed to use "private" metods, but if you do, and I'll change them later, you knew it from begining your code will break and **you** will have to fix it.

Like car drivers on a highway: people just drive in own line, and two cars can safely pass in opposite directions each going 100 km/h = 60mph, just 1 m=1yard from each other. Full security would require either to build private roads, or concrete barrier, and if not possible, blow up incoming cars or swerve to the side just to be safe than some suicidal maniac will not swerve to your line. "Consenting adults" way is **a lot** more practical, eh? :-)

---

### Post by gnuman on 2008-01-04
> **pmasiar said:**
> Whole philosophy of the security in Python is different than in ie Java.

Python is not intended to write ie nuclear plant management system, where layers of paranoid restrictions apply. Instead, programmers are considered "consenting adults" who  behave responsibly and do not try to break each other code with malicious intent. You are not supposed to use "private" metods, but if you do, and I'll change them later, you knew it from begining your code will break and **you** will have to fix it....

Well put.  

I'm getting ready to teach an AP Comp Sci class next year and my biggest challenge is learning how Java objects are handled compared to Python objects. 

It's even stranger for my most Pythonic students....:)

---

### Post by NovaAesa on 2008-01-05
> **pmasiar said:**
> 
Like car drivers on a highway: people just drive in own line, and two cars can safely pass in opposite directions each going 100 km/h = 60mph, just 1 m=1yard from each other. Full security would require either to build private roads, or concrete barrier, and if not possible, blow up incoming cars or swerve to the side just to be safe than some suicidal maniac will not swerve to your line. "Consenting adults" way is **a lot** more practical, eh? :-)

I love than analogy :) And it make sense - if someone is dumb enough to use my private methods (even if that someone would be me) then they can fix whatever problem occurs because of it.

---


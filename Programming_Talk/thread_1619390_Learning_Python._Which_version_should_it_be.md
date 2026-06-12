---
title: "Learning Python. Which version should it be?"
date: 2010-11-11
forum: Programming Talk
---

### Post by jakupl on 2010-11-11
I want to learn python, but I am facing a rather difficult choice. Should I dive into version 2, or 3?

I am from the [Faroe Islands]("http://en.wikipedia.org/wiki/Faroe_Islands"), where we use letters like ð,á,ú,ó,í etc. so version 3 having a more intuitive unicode handling is quite attractive to me. I altso suspect that learning a "dying" version of python is silly, one should rather look ahead.

However I'm concerned that it will be harder to find help, when most people still use 2.x. And it probably might take a long time before version 3 is implemented.

What should I do???

Fyi, I think I will start by digging into ["A Byte of Python."]("http://www.swaroopch.com/notes/Python")

---

### Post by robbiemacg on 2010-11-11
Hi [jakupl]("http://ubuntuforums.org/member.php?u=528101"),
I think there are sound arguments on both sides of this debate, many have been explored here in past. 
I'm just starting out with Python myself, and have chosen version 3. I'm finding things fairly intuitive, and have been able to translate some of what I've learned and use it in real-world situations at work.
I'm working my way through the exercises here:
 [http://inventwithpython.com](http://inventwithpython.com) 
(all the exercises are written for version 3 by default. that was part of what helped me make my decision.)

Good luck!

---

### Post by TVTrukChik on 2010-11-11
Thank you both for the links.  Just started playing with Python myself day before yesterday.  I've figured out most of what I'm trying to do so far, but Python 3 doesn't seem to see that I've got the dbus interface installed.  So I converted my code back to 2.6 instead.  

I'd prefer to use the newer version, but I just don't know enough yet to make it all work.  There are a **lot** of differences between the two versions.  I'm quite surprised at all the changes.

---

### Post by nvteighen on 2010-11-12
The issue with Py3.x is mainly that many important modules still have to be ported, so it's still not a language suited for production code.

I guess it doesn't hurt to learn both, use Py2.x for production code and Py3.x for experimenting (or contributing to port the modules that are needed... :P)

---

### Post by jakupl on 2010-11-12
So how long would it take until it's usefull for production code?

---

### Post by spjackson on 2010-11-12
> **jakupl said:**
> So how long would it take until it's usefull for production code?
The official position is covered here [http://wiki.python.org/moin/Python2orPython3](http://wiki.python.org/moin/Python2orPython3) . I'd summarise this as: Python 3 is ready as a language but many of the libraries available for 2.x are not yet ready for 2.x. So it could be regarded as useful for production now, provided that you don't need the things that don't yet work with it.

As for predicting the future, programmers are notoriously bad at this. My gut feeling is that Python 3 won't be mainstream for the next 12 months.

---

### Post by raydeen on 2010-11-12
At this point, you'll most likely be learning both as most books and tutorials will show examples of both. The two biggest differences starting out are the changes to print and input. In 2.x, print is a method and input can be used in two different ways, input (for numbers) and raw_input (for characters). 

```

### 2.x
name = raw_input('What is your name? ')
age = input('What is your age? ')
print 'Hello',name

```

In 3.x print is a function and requires '()' around the info to be printed and raw_input has been replaced with just input(). To get numerical input you would use eval(input()) to change the string to a number.

```

### 3.x
name = input('What is your name? ')
name = eval(input('What is your age? '))
print ('Hello',name)

```

I'm pretty sure that's accurate. The gurus can correct me if I'm wrong.

---

### Post by schauerlich on 2010-11-12
> **raydeen said:**
> raw_input has been replaced with just input(). To get numerical input you would use eval(input()) to change the string to a number.

in 2.x, input() is the equivalent of eval(raw_input()) - meaning the interpreter will evaluate ANY expression that it's passed. Needless to say, this is a huge security hole. If you want to take in a number in 2.x, you should be using int(raw_input()). It also has the advantage of failing gracefully if the user doesn't pass in a number.

Also, print is now a function as opposed to a statement, with keyword arguments and such. It's a much bigger difference than just adding parentheses.

There's also important differences in semantics, such as old vs new classes.

[http://docs.python.org/release/3.1.2/whatsnew/3.0.html](http://docs.python.org/release/3.1.2/whatsnew/3.0.html)

---

### Post by raydeen on 2010-11-12
Good to know about the int(raw_input()). I honestly don't think I've ever seen that used in any of the material I've read. I'm still learning and soaking up as much info as I can.

---

### Post by MattBD on 2010-11-12
Depends what you want to do. A lot of the most popular libraries (including Twisted and Django) are still using Python 2, so if you want to use one of them I'd stick with Python 2.

---

### Post by TVTrukChik on 2010-11-12
> **nvteighen said:**
> The issue with Py3.x is mainly that many important modules still have to be ported, so it's still not a language suited for production code.

I guess it doesn't hurt to learn both, use Py2.x for production code and Py3.x for experimenting (or contributing to port the modules that are needed... :P)

Thank you for that info.  Now I won't be beating my head against the wall trying to figure out some of the stuff in version 3 just yet!

---


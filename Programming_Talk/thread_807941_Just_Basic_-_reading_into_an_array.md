---
title: "Just Basic - reading into an array"
date: 2008-05-26
forum: Programming Talk
---

### Post by Tenderfoot on 2008-05-26
Query about Just Basic.
I am a complete beginner with Just Basic and am trying to code using the help topics.

I have a comma separated file with 250 records (rows). Each record (row) has 2 numeric fields (columns) of up to 3 digits which are integers.

I am trying to read the contents of this file into a 2 dimensional array without success.

My code is as follows:-

dim array(250,2)
total = 1
open "c:\tranche3lo.csv" for input as #gapslo
input #gapslo, array(total)
total=total+1
close #gapslo
print array

If anyone out there can help, I will be most grateful.

Tenderfoot

---

### Post by Joeb454 on 2008-05-26
You may have more luck with this in the Programming Talk forum (I've requested it to be moved).

And this isn't homework by any chance is it?

---

### Post by Tenderfoot on 2008-05-26
> **Joeb454 said:**
> You may have more luck with this in the Programming Talk forum (I've requested it to be moved).

And this isn't homework by any chance is it?
Not homework I assure you - I am 63 years of age!!

---

### Post by LaRoza on 2008-05-26
> **Joeb454 said:**
> You may have more luck with this in the Programming Talk forum (I've requested it to be moved).

And this isn't homework by any chance is it?

Moved to PT.

@OP What operating system are you using?

---

### Post by Tenderfoot on 2008-05-26
> **LaRoza said:**
> Moved to PT.

@OP What operating system are you using?
Microsoft Windows

---

### Post by LaRoza on 2008-05-26
> **Tenderfoot said:**
> Microsoft Windows

Hopefully someone here will have access to this language (or knowledge of it).

---

### Post by moma on 2008-05-26
Does "Just Basic" run on Linux? I thought it was Windows only software?
I recommend you to try Gambas Basic.
[http://gambas.sourceforge.net](http://gambas.sourceforge.net)
Start Synaptic Package Manager and search for "gambas". Install and run it. Your program should be easy to complete with Gambas basic.

Your age is just fine :-)

---

### Post by LaRoza on 2008-05-26
> **moma said:**
> Does "Just Basic" run on Linux? I thought it was Windows only software?
I recommend you to try Gambas Basic.
[http://gambas.sourceforge.net](http://gambas.sourceforge.net)
Start Synaptic Package Manager and search for "gambas". Install and run it. Your program should be easy to complete with Gambas basic.

Your age is just fine :-)

Red Alert: The OP is using Windows ;)

---

### Post by Joeb454 on 2008-05-26
> **Tenderfoot said:**
> Not homework I assure you - I am 63 years of age!!

Sorry :) Had to check though ;)

---

### Post by pmasiar on 2008-05-26
> **Tenderfoot said:**
> ....

I have no idea about Basic, but if you take look at Python, you will find much more and more friendly support for it. You can install it for free from ActiveState.

> My code is as follows:-

use [ code ] tags for code - or php for colored syntax

```

from pprint import pprint # for pretty-printing

array = {}
total = 1

for line in open("c:\tranche3lo.csv"):
   parts = line.split(',') # assuming numbers separated by comma
   for column in len(parts):
        array[total, column] = int(parts[column])
   total += 1

pprint(array)

```

---

### Post by unutbu on 2008-05-26
I don't know Just Basic, so this is just a guess:
```
dim array(250,2)
open "c:\tranche3lo.csv" for input as #gapslo
FOR total = 1 TO 250
    input #gapslo, array(total)
NEXT total
close #gapslo
print array

```
 
You can find some information about Just Basic looping here:
[http://justbasic.conforums.com/index.cgi?board=tutorial&action=display&num=1110757646](http://justbasic.conforums.com/index.cgi?board=tutorial&action=display&num=1110757646)

---

### Post by cmay on 2008-05-26
here is a tutorial on arrays. 
i know just basic since it was the first language i tried to learn
but i found that free basic was more powerfull and it comes for dos linux and
windows as well. its just two years ago i played around whit it as a stepping stone to pascal and then to c but thats anhoter story. i dont renember any of basic . hope that could help.
[http://www.freebasic.net/wiki/wikka.php?wakka=TutIntroArrays](http://www.freebasic.net/wiki/wikka.php?wakka=TutIntroArrays)

---

### Post by Can+~ on 2008-05-26
And what leaded you to just basic in the first place? Seriously, that language sounds like an scam to me, check the site:

[http://www.justbasic.com/learnmore.html](http://www.justbasic.com/learnmore.html)

It calls itself a "Free language", but it asks for $49.95 to really start with the "Extended commands and functions". I mean, what the hell; I've never seen a language asking you for money to "upgrade". I've seen IDEs or other stuff, but not the code itself.

Really, just any other thing will do, [python](http://www.python.org/download/), [ruby](http://www.ruby-lang.org/), [java](http://java.sun.com/), C, you name it.

---

### Post by Lau_of_DK on 2008-05-27
> **Can+~ said:**
> 
[http://www.justbasic.com/learnmore.html](http://www.justbasic.com/learnmore.html)

It calls itself a "Free language", but it asks for $49.95 to really start with the "Extended commands and functions". I mean, what the hell; I've never seen a language asking you for money to "upgrade". I've seen IDEs or other stuff, but not the code itself.


I dont think its a scam, I just think its an incredibly bad product. Firstly, they classify this as a "cool game": [Screenshot]("http://www.justbasic.com/learnm8.jpg") 
And secondly - Who does a product-screenshot with an overpopulated Desktop and both Word and MSN running? To me it just looks like amateur hour.

To the OP, I dont know exactly why you're posting Windows questions on a Linux forum, but pmasiar actually gave you some good advice: Use Python instead, its easy, its as readable as Basic and you can get help from both worlds, ie. both Linux and Windows. Oh, and its free :)

/Lau

---

### Post by WW on 2008-05-27
> **Lau_of_DK said:**
> 
To the OP, I dont know exactly why you're posting Windows questions on a Linux forum, [...]
/Lau
Lau, reread the text just below the "Programming Talk" heading:
> 
This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any programming language is allowed.

While this is not necessarily the best forum for such questions, there is nothing wrong with asking Windows programming questions here.

---


---
title: "Python 2 vs Python 3 for a Beginner"
date: 2010-08-29
forum: Programming Talk
---

### Post by cj.surrusco on 2010-08-29
I'm a beginner and I have never programmed before, and I am interested in learning a language. I've looked up comparisons of all of the different languages and have decided that I would like to go with Python.

I noticed that they came out with Python 3 recently, but is it better to learn that or Python 2? I've read that Python 2 scripts are not completely compatible with Python 3.

So, I have two questions:

1. If I learn Python 3, will I know enough to edit Python 2 code?

2. Would code that I write in Python 3 be that useful since most people still use Python 2?

Thanks in advance for any answers or input,

cj.surrusco

---

### Post by Dies on 2010-08-29
1.) I would think so. It's not like it's a completely different language or anything.

2.) It would definitely be more "future-proof". Though you can expect Python 2 to be around for a long, long time.

---

### Post by worksofcraft on 2010-08-29
I too am learning Python and I am glad I choose to learn Python 2 because practically all the tutorials on the web are written in Python 2. Also many really cool packages like gstreamer are not yet available in Python 3 flavour.

No doubt one day you will want to switch and by then you will know enough Python to find it easy, specially since there is an automatic tool to convert Python 2 code to 3 code... but none to go back :shock:

---

### Post by Carpentr on 2010-08-29
I've just started to learn Python. I decided to go with Python 3 since it was newer. I figure eventually more and more people will wind up using it. As Python 3 gets older more documentation will become available.

I'm finding Python 3 to be an enjoyable language to learn programming with.

Right now I'm using the book _Programming in Python 3: A Complete Introduction to the Python Language_, by Mark Summerfield. For one book it has a lot of information and is easy to understand. I bought it a while ago but haven't really touched it up until now. I have the first edition, but I believe there is already a second edition as well. Either way it's said that either edition works with Python 3 and 3.1.

I'm sure there are many other books to help you with Python as well!

Hope this helped!

---

### Post by juancarlospaco on 2010-08-30
2to3 and problem solved...

---

### Post by DanielWaterworth on 2010-08-30
> **worksofcraft said:**
> since there is an automatic tool to convert Python 2 code to 3 code... but none to go back :shock:

I beg to differ there's 3to2 [http://pypi.python.org/pypi/3to2](http://pypi.python.org/pypi/3to2)

---

### Post by cj.surrusco on 2010-08-30
Thanks for all the input, everybody. 

I think I'm going to go with Python 2 for the moment, and then learn the differences in Python 3 when it is more widely used.

---

### Post by Crash Overdrive on 2010-08-30
I am as well, I also have never programmed before and am deciding to start with Python 2

---

### Post by worksofcraft on 2010-08-30
The BDFL of the Python language works for Google and they invest a lot in developing the language and it's support. Personally I even hope they include Python script interpreter to Google Chrome so we can use it on our web pages and forget about Javascript. Either way I think Python will prove to be a good choice :)

---

### Post by DanielWaterworth on 2010-08-31
> **worksofcraft said:**
> The BDFL of the Python language works for Google and they invest a lot in developing the language and it's support. Personally I even hope they include Python script interpreter to Google Chrome so we can use it on our web pages and forget about Javascript. Either way I think Python will prove to be a good choice :)

On the surface, this sounds like a great idea, python in the browser. However, I'm not so sure, the thing about web standards is there are always being updated and some browsers implement newer standards than others. Python doesn't pass errors silently, so imagine having to write code where you have to check every attribute of a class before using it and putting every import statement in a try block. Javascript wasn't designed to be a bad language, it was designed to be a web-language, it just turns out that one implies the other.

---

### Post by worksofcraft on 2010-08-31
> **DanielWaterworth said:**
> On the surface, this sounds like a great idea, python in the browser. However, I'm not so sure, the thing about web standards is there are always being updated and some browsers implement newer standards than others. Python doesn't pass errors silently, so imagine having to write code where you have to check every attribute of a class before using it and putting every import statement in a try block. Javascript wasn't designed to be a bad language, it was designed to be a web-language, it just turns out that one implies the other.

If Microsoft can put VB in IE then Google should be able to put Python in Chrome... if it were my choice I would have chosen Prolog because the way it searches for solutions is very suited to internet activity and could probably handle all the SQL requirements as well.

In what way do you think Javascript is designed to be a "web language"? I don't see it as having any merits or redeeming features what-so-ever TBH :shock:

---

### Post by matmatmat on 2010-08-31
> **danielwaterworth said:**
> javascript wasn't designed to be a bad language, it was designed to be a web-language, it just turns out that one implies the other.
:d

---

### Post by DanielWaterworth on 2010-08-31
> **worksofcraft said:**
> If Microsoft can put VB in IE then Google should be able to put Python in Chrome... if it were my choice I would have chosen Prolog because the way it searches for solutions is very suited to internet activity and could probably handle all the SQL requirements as well.

In what way do you think Javascript is designed to be a "web language"? I don't see it as having any merits or redeeming features what-so-ever TBH :shock:

I'm not saying that's it's not possible, but did vb on the web take off? Prolog would also be a poor choice, despite it being a better language.

Javascript does not have merits, but features that make it a good language for the web are weak-typing and giving undefined for none existent attributes rather than raising an exception. These aren't good language features, but they do make it easier to do web-programming. In regular programming, handling exceptions explicitly is essential, but on the web if it's not implicit then the web would constantly crash. If you interested in this subject, lookup native-client.

---

### Post by juancarlospaco on 2010-08-31
*But you cant write web with Python too*

---

### Post by worksofcraft on 2010-08-31
> **DanielWaterworth said:**
> I'm not saying that's it's not possible, but did vb on the web take off? Prolog would also be a poor choice, despite it being a better language.

Javascript does not have merits, but features that make it a good language for the web are weak-typing and giving undefined for none existent attributes rather than raising an exception. These aren't good language features, but they do make it easier to do web-programming. In regular programming, handling exceptions explicitly is essential, but on the web if it's not implicit then the web would constantly crash. If you interested in this subject, lookup native-client.

No Prolog would have been an awesome choice because it doesn't need exceptions and is quite happy to work with undefined quantities... in fact probably even finding all the possible valid solutions for you.

OTOH throwing exceptions is hardly an issue because you could choose to catch them and ignore them, or do undefined things with them if that is really what you think is needed. :confused: Personally I think Javascript only got in there because Java was seen as the cool new flavor of the month programming language at the time.

---

### Post by DanielWaterworth on 2010-09-01
> **worksofcraft said:**
> No Prolog would have been an awesome choice because it doesn't need exceptions and is quite happy to work with undefined quantities... in fact probably even finding all the possible valid solutions for you.

OTOH throwing exceptions is hardly an issue because you could choose to catch them and ignore them, or do undefined things with them if that is really what you think is needed. :confused: Personally I think Javascript only got in there because Java was seen as the cool new flavor of the month programming language at the time.

Nobody uses prolog for anything. That's not because it's not better as a language or because it's difficult to use or even because nobody's heard of it. It's because prolog is different and people don't like to change the language that they use, let along the paradigm they use.

Also, the thing that prolog excels in is making exponential time programs. It takes someone with skill to make a program that runs faster than this and the one thing that is lacking on the web is developers with skill.

And that neatly brings me to my next point. Just because it's possible to add a try-catch block around code, doesn't mean that inexperienced developers would. A good web-language is one that children could use and believe me when I say that they will.

If native-client makes it's way onto the internet at large, you will be able to make web-pages in prolog or bf or any other language that you like, the future is bright for marginal languages.

---

### Post by Dies on 2010-09-01
> **DanielWaterworth said:**
> ...
Python doesn't pass errors silently, so imagine having to write code where you have to check every attribute of a class before using it and putting every import statement in a try block.
...

Sorry, I may not be thinking as far ahead as you are, but how is this any different from using Python in any other context?

For example, why would you need to use a "try" block around imports? 

If this was implemented then you should be able to assume that the standard libraries are always available. Usage of other libraries would require you to ensure that they are available somehow or make them optional but this is always the case. I also don't see why you wouldn't be able to serve anything else you needed.

---

### Post by DanielWaterworth on 2010-09-01
> **Dies said:**
> Sorry, I may not be thinking as far ahead as you are, but how is this any different from using Python in any other context?

For example, why would you need to use a "try" block around imports? 

If this was implemented then you should be able to assume that the standard libraries are always available. Usage of other libraries would require you to ensure that they are available somehow or make them optional but this is always the case. I also don't see why you wouldn't be able to serve anything else you needed.

simply because the web is accessed by many browsers on many platforms and python code is designed to be run, generally, using one implementation.

Imagine running python code in internet explorer using an implementation that microsoft designed and made. I rest my case.

---

### Post by worksofcraft on 2010-09-01
> **DanielWaterworth said:**
> 
Imagine running python code in internet explorer using an implementation that microsoft designed and made. I rest my case.

I heard that you can run Java applets in internet explorer using an implementation that Microsoft designed and made and that they also have PhP. MySQL, and even support HTML and CSS. I don't see how it is any different.

From time to time we do see code that tests for what browser and what version and what platform. Personally I just code to the W3C standard and people who wanna use non compliant tools well that's their problem :S

Until a standard is set it would be Chrome only and expeimental. Until it is implemented and in demand, a standard probably won't be set. Doesn't mean it would have  no merit.

---


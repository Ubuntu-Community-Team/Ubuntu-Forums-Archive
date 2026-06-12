---
title: "The Most Suitable Language To Build a Search Engine"
date: 2012-01-02
forum: Programming Talk
---

### Post by multisystem on 2012-01-02
I'm begging a startup soon. It's a search engine that searches for some stuff over social networks and do some statistics on it. I need some advice from you guys for picking the most suitable environment for my startup.

1- Is the language considered the bottleneck in such case, or I can pick any language of my choice and it doesn't matter ?

2- What criteria should I consider in selecting a programming language? Should I prefer performance or productivity. In other words, I've heard that Python minimizes the coding time a lot, but It lacks performance. However, Java is a good choice but it may takes hours to do something that could be done in minutes in Python.

Thanks very much guys

---

### Post by CoffeeRain on 2012-01-03
I find that python is great for most things. What you would need is two functions. One that uses urllib to open a page and uses re to search for keywords or certain text in a certain div, and one that looks for all the links on a page and stores them in a list. Then you would loop through the list and perform these functions on them. What you would do is something like this...

```

import urllib
import re

def GetLinks(webpage)
  try:
    f = urllib.URLopener().open(webpage)
    content = f.read()

#find links and store them in a list

linklist.append(link)

  except IOError:
    pass



def GetContent(webpage):
  try:
    f = urllib.URLopener().open(webpage)
    content = f.read()
    
    #use re to find what you want in the variable content

  except IOError:
    pass


GetLinks(page)
GetContent(page)
for item in linklist:
  GetLinks(item)
  Get Content(item)

#You can define global vars in the functions and act on those.
#You could write them to files or whatever you want.

```

---

### Post by DangerOnTheRanger on 2012-01-03
I say use Cython. It's a superset of Python (meaning that all valid Python code is valid Cython code, but the reverse isn't true), and Cython code can be run through the Cython compiler to be compiled to straight C. So you get the flexibility of Python, and the speed of C :)

> **CoffeeRain said:**
> I find that python is great for most things. What you would need is two functions. One that uses urllib to open a page and uses re to search for keywords or certain text in a certain div, and one that looks for all the links on a page and stores them in a list. Then you would loop through the list and perform these functions on them. What you would do is something like this...

```

import urllib
import re

def GetLinks(webpage)
  try:
    f = urllib.URLopener().open(webpage)
    content = f.read()

#find links and store them in a list

linklist.append(link)

  except IOError:
    pass



def GetContent(webpage):
  try:
    f = urllib.URLopener().open(webpage)
    content = f.read()
    
    #use re to find what you want in the variable content

  except IOError:
    pass


GetLinks(page)
GetContent(page)
for item in linklist:
  GetLinks(item)
  Get Content(item)

#You can define global vars in the functions and act on those.
#You could write them to files or whatever you want.

```

That advice is *way* too low-level with respect to what the OP was asking, IHMO.

---

### Post by CoffeeRain on 2012-01-03
> **DangerOnTheRanger said:**
> That advice is *way* too low-level with respect to what the OP was asking, IHMO.

What do you mean? I thought that Python would be great for finding information and getting statistics from it. Could you explain some more?

---

### Post by CptPicard on 2012-01-03
Sorry, but if you've got your own money on the line in this startup, I must say this just to protect your finances...

You really just demonstrate that you don't have the competence to even begin with to build what you're seeking to build. You do not understand much about your problem, or about how it relates in any sense to any potential implementations. And we're not going to be able to answer you enough so that you'd be getting the competence to gain the better judgement.

It's not a matter of programming language choice; it's a matter of the structure of your problem and its relationship to your chosen architecture. After that, you may start choosing platforms and languages. This stuff is very secondary. The construction of a search engine begins on a higher level of abstraction, and the languages are just tools.

That said, people with exposure to certain kinds of programming will be more likely to recognize the problems inherent in what you're trying to accomplish, and will be able to choose the appropriate tools.

---

### Post by DangerOnTheRanger on 2012-01-03
> **CoffeeRain said:**
> What do you mean? I thought that Python would be great for finding information and getting statistics from it. Could you explain some more?

That example code you gave is what I was talking about. It served no real purpose, not to mention the two-function design you gave isn't flexible enough for what this guy is trying to do.

---

### Post by simeon87 on 2012-01-03
+1 to what CptPicard said.

Additionally, I expect a great search engine to be written in multiple languages. You'll need to develop the web-based site, the crawlers, you need to do computations related to the search index and analysis, et cetera and you're not going to do that in one language (for performance and suitability reasons). A language that is fast may not be suitable to write a website in and vice versa.

---

### Post by CoffeeRain on 2012-01-03
If the OP is just using this on their own, wouldn't they be able to just get the information, store it, and then request it with a different program?

---

### Post by squenson on 2012-01-03
You may need different environment for different purposes:

1. For the fetching of data, you need a programming language able to connect to the social networks. Most probably, the bottleneck will be the speed of your network and the volume of data you can retrieve, so the pure performance of the programming language is secondary. I also recommend Python which is reasonably fast and which allows fast developments. What is important is also to choose a good database engine where you can store all the information. If you plan to store more than texts (like pictures, etc.) you will need to think whether you store this information in the database or as separate files which are referenced in the database. MySQL is a good choice and can handle quite large volumes but other database engines may be more fit for your purpose.

2. For the display of data (what you will offer to your customers), you need a different environment. One of the most used is LAMP (Linux, Apache, MySQL and PHP). You can buy such hosted environment for a few dollars per month and when the revenues are good enough, you can always increase your capacity.

Finally, my recommendation is go and do it! Whatever you use for the first release of your product/service, you will anyway redo it once you have more experience and more revenues which will allow you to use more sophisticated and performing environment.

Good luck!

---

### Post by ofnuts on 2012-01-03
> **squenson said:**
> Most probably, the bottleneck will be the speed of your network and the volume of data you can retrieve!

The bottleneck will be the willingness of the site to share its data... These sites  are made for the money you can get from the data they hold. They won't let Joe Programmer pillage their cash cow without taking counter-measures.

PS: +1 with CdtPicard.

---

### Post by nvteighen on 2012-01-04
Apart from the technical and financial issues, there's the legal issue too.

Users of social networks have agreed to share their personal data with the social network to the degrees established on their (abusive) TOS. Anyway, what is quite clear though is that there has been no agreement between you and the people whose data you're retrieving even if automatically... even if you don't publish anything but very general statistics. 

This could cost you a lot of trouble.

---


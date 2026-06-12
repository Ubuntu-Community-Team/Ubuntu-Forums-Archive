---
title: "why use java over python?"
date: 2008-06-30
forum: Recurring Discussions
---

### Post by buckets on 2008-06-30
i guess i am having a difficult time understanding the reasons why anyone would use java over python aside from the popularity of java in the business world.

lets say for example you wanted to develop a cross platform desktop application with a gui frontend.  

would it be easier on java because most users have java installed already?  is that the only reason?

---

### Post by LaRoza on 2008-06-30
> **buckets said:**
> i guess i am having a difficult time understanding the reasons why anyone would use java over python aside from the popularity of java in the business world.

lets say for example you wanted to develop a cross platform desktop application with a gui frontend.  

would it be easier on java because most users have java installed already?  is that the only reason?

Java is a popular platform, and it is possible to use Python on it.

---

### Post by JudgeFudge on 2008-06-30
Java isn't exactly the language of choice for GUI oriented desktop apps either. Most of the time people and companies choose a language based on the language they know. Not ideal perhaps but the  way it works.

And I am a professional java programmer so not one of the forum's java-haters.

---

### Post by tinny on 2008-06-30
(Big breath in)

JavaFX + JVM = SOLID

> would it be easier on java because most users have java installed already? is that the only reason? 

If they browse the internet they probably will have the JVM, so yes. Although im not sure how most people get the Python runtime??? I don't have it on my Windows machine...

I recently wrote this desktop application:

[http://getsmarte.com/]("http://getsmarte.com/")

It uses Swing [Substance]("https://substance.dev.java.net/"), Hibernate and Apache Derby. It runs on Linux (although they dont want to promote this fact), Windows and Mac with no mods to the standard code base. The tools and extendible technologies are great.

It took 4 months to develop.

And it just works. It was very easy to find developers for the project as well, they grow Java developers on Trees nowadays (security in your investment).

---

### Post by antler on 2008-06-30
When considering both of these languages in their raw form - Java is faster thanks to JIT compilation.

---

### Post by tinny on 2008-06-30
> **LaRoza said:**
> Java is a popular platform, and it is possible to use Python on it.

This technology is supported by say 20 > committed developers (not tyre kickers)? It doesn't make sense to me to develop a product in a reasonably fragile technology when Java will do just fine. :)

---

### Post by LaRoza on 2008-06-30
> **tinny said:**
> (Big breath in)

JavaFX + JVM = SOLID

Python + Python = SOLID
Ruby + Ruby = SOLID
C + native binary = SOLID

What is all that supposed to mean ;)

> 
If they browse the internet they probably will have the JVM, so yes. Although im not sure how most people get the Python runtime??? I don't have it on my Windows machine...

How many Linux distros come with Java? How about Python? Python is a winner here...

HP and Compaqs come with Python and Python has the ability to compiled to a native app (so to speak).

> 
It took 4 months to develop.

I would bet it would be less if using another language.

> 
And it just works. It was very easy to find developers for the project as well, they grow Java developers on Trees nowadays (security in your investment).
As opposed to all the Python programs that don't work?!

Yes, Java programmers are easily replaced.

---

### Post by tinny on 2008-06-30
Java

> 
Python + Python = SOLID
Ruby + Ruby = SOLID
C + native binary = SOLID

What is all that supposed to mean 


SUPPORT!!!

> How many Linux distros come with Java? How about Python? Python is a winner here...

X Platform. (Got any metrics of JRE downloads compared to Python downloads?)

...> lets say for example you wanted to develop a cross platform desktop application with a gui frontend.

> I would bet it would be less if using another language.

No, because I would have had to train the developers in my area.

> As opposed to all the Python programs that don't work?!

The whole process just works. Rightly or wrongly Id never have to explain my decision for choosing Java.

> Yes, Java programmers are easily replaced. 

:twisted::twisted::twisted::twisted::twisted::twisted::twisted::twisted:

---

### Post by LaRoza on 2008-06-30
> **tinny said:**
> Java

SUPPORT!!!

What do you mean? Support from Sun? Support from docs?

> 
X Platform. (Got any metrics of JRE downloads compared to Python downloads?)

No, because I would have had to train the developers in my area.


Python downloads are higher probably. Most distros have Python, Python has several installers, and Python is often bundled with the apps that use it.

> The whole process just works. Rightly or wrongly Id never have to explain my decision for choosing Java.
Then why do you insist on others to explain their choice?


> 
:twisted::twisted::twisted::twisted::twisted::twisted::twisted::twisted:
it is the truth. As you said, Java programmers are easier to get. Higher supply == lower demand. Google is a great place to work. They hired the creator of Python. His shoes must be very happy :-)

---

### Post by tinny on 2008-06-30
> What do you mean? Support from Sun? Support from docs?

Community, the same reason I choose Ubuntu over Debian.

> 
Python downloads are higher probably. Most distros have Python, Python has several installers, and Python is often bundled with the apps that use it.


Dont most Windows machines have Java? Even if only 20% did then the number would still be greater than the Linux count. :(

> 
Then why do you insist on others to explain their choice?


??? Dont know why really given that I am always likely to get taken out to the car park for a slap on this forum. :D

Just keen to learn.

> 
it is the truth. As you said, Java programmers are easier to get. Higher supply == lower demand. Google is a great place to work. They hired the creator of Python. His shoes must be very happy 


Lower demand??? ummm not sure maybe. That isn't to say you will ever have any problems finding a Java project to work on.

Google write < 1% of the software in the world?

---

### Post by LaRoza on 2008-06-30
> **tinny said:**
> 
Dont most Windows machines have Java? Even if only 20% did then the number would still be greater than the Linux count. :(

If you know the numbers, why did you ask? If you don't know the numbers, don't give them ;)



> 
Lower demand??? ummm not sure maybe. That isn't to say you will ever have any problems finding a Java project to work on.
Yeah, a lower demand. If I had two projects going, one in Lisp and another in Java, which programmer team would be more valuable? 

> 
Google write < 1% of the software in the world?

Google write the most used software in the world ;)

---

### Post by tinny on 2008-06-30
> If you know the numbers, why did you ask? If you don't know the numbers, don't give them 

Just giving a very safe estimation, hopefully I might even mislead some student into quoting it in some sa they are doing. Believe everything you read on the internet!

> 
Yeah, a lower demand. If I had two projects going, one in Lisp and another in Java, which programmer team would be more valuable?


Commercial projects?

(Generalising here)

When programmers become familiar with a product they are more valuable right? There is far more to it than just syntax. Though I do believe you have a good point there LaRoza.

I do know that in general C programmers are more valuable than Java ones in my area (not sure about Lisp). But there are also more $100,000+ plus jobs in Java here than in C so it sort of balances out.

> Google write the most used software in the world 

Windows??? :(

---

### Post by LaRoza on 2008-06-30
> **tinny said:**
> 
Windows??? :(

google...

---

### Post by rlameiro on 2008-06-30
> **tinny said:**
> 
Windows??? :(

DUHHH!
> **LaRoza said:**
> google...
Google of course :) do you have any doubt?

---

### Post by tinny on 2008-06-30
> **rlameiro said:**
> DUHHH!

Google of course :) do you have any doubt?

Im not sure?

Microsoft is what I think (sorry)

Windows*
Exchange (probably a big count for who "uses" it)

However what about Nokia? 110.2 million units per year!

[http://blogs.guardian.co.uk/technology/2007/11/27/nokia_increases_market_share_in_mobile_phone_business.html]("http://blogs.guardian.co.uk/technology/2007/11/27/nokia_increases_market_share_in_mobile_phone_business.html")

---

### Post by rlameiro on 2008-06-30
tinny, almost everyone do web search with google, even in nokia cellphones, maybe you don't consider that google search is not an app??

---

### Post by Mateo on 2008-06-30
The ridiculous tabbing rules are reason enough to not use python.

---

### Post by LaRoza on 2008-06-30
> **Mateo said:**
> The ridiculous tabbing rules are reason enough to not use python.

What tabbing rules?

You will find that the average c style coder gets used to Python syntax in about 15 minutes of use. It is nothing new and is easier in some ways.

---

### Post by CostaRica on 2008-07-01
Tabbing rules mean readability.  Programming languages evolve, and anyone who understands python definitely notices the superiority of it over Java.  I do not hate java, it is just that people tend to stick with what they already know, and progress is about evolving...

---


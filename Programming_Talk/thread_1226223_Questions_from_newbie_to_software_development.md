---
title: "Questions from newbie to software development"
date: 2009-07-29
forum: Programming Talk
---

### Post by shankhs on 2009-07-29
hi 
I am learning software engineering.
My problem is to find good UML tool for ubuntu and corresponding tutorial on how to use the tool.
Please if you know do tell me.

Also if you have any advices or books please tell me.I am at present learning from net which is an unorganised learning.

Thankyou

---

### Post by schmendrick on 2009-07-29
I am no fan of UML and doing all that boring stuff, it regard it very rarely necessary to write myself more than a sheet of paper. But ok, sometimes you are ordered to do so, so here my advice.



Enterprise Architect is a good tool. Though not free software and purely windows.... so maybe out of reach for a student. but its the only one i use  ;)  plus there are good explanations for the newbie.
==>  [www.sparxsystems.com.au/products/ea/index.html](www.sparxsystems.com.au/products/ea/index.html) 


As for the book:
If you really need a book you can take a look at the book "Applying UML and Patterns" by Craig Larman, its ok. 
But I highly recommend you getting used to learn from the net. if you are digging into software engineering you will need to be able to do it.

---

### Post by .Maleficus. on 2009-07-29
I don't do UML either so I can't comment on tools, but as for books, [Head First Object Oriented Analysis and Design]("http://www.amazon.com/Head-First-Object-Oriented-Analysis-Design/dp/0596008678") seems like a good book.  I've read a couple other Head First books and they are easy to follow and not as dry as other programming books are.

---

### Post by Copernicus1234 on 2009-07-29
Eclipse has a UML component these days and its free.

Check the download page at Eclipse.

And yes, the book mentioned above is good and has a very original and interesting way of describing the process in a easy way.

---

### Post by shankhs on 2009-07-29
> **schmendrick said:**
> 
Enterprise Architect is a good tool. Though not free software and purely windows.... so maybe out of reach for a student. but its the only one i use  ;)  plus there are good explanations for the newbie.
==>  [www.sparxsystems.com.au/products/ea/index.html](www.sparxsystems.com.au/products/ea/index.html) 

The tool is costly and out of my reach anyways thank you for your valuable suggestion.
Thanks guys.

Can you please tell me why devs don't like UML.
My college professors explain everyday why we should UMLs,actors , use cases and other stuffs.

As far as the book is concerned I am really going to look at Head First one.
Any more help would be highly appreciated.
Thank you once again.

---

### Post by shankhs on 2009-07-30
hey
I figured out why UML is hated by most of the devs.
I stumbled a nice blog which explained why everybody hates UML.

---

### Post by hyperAura on 2009-07-30
dia is an open source software which can be used for UML.. also there is a basic tutorial on it [http://projects.gnome.org/dia/umltut/index.html](http://projects.gnome.org/dia/umltut/index.html).. hope u like it  since its easy and simple..

---

### Post by shankhs on 2009-08-02
> **hyperAura said:**
> dia is an open source software which can be used for UML.. also there is a basic tutorial on it [http://projects.gnome.org/dia/umltut/index.html](http://projects.gnome.org/dia/umltut/index.html).. hope u like it  since its easy and simple..

Thanks hyperAura I was exactly looking for this 
than you very much.

---

### Post by Greyed on 2009-08-02
> **shankhs said:**
> Can you please tell me why devs don't like UML.

No battle plan survives contact with the enemy?  ;)

---

### Post by baizon on 2009-08-02
I recommend Visual Paradigm.
URL: [http://www.visual-paradigm.com/product/vpuml/]("http://www.visual-paradigm.com/product/vpuml/")

For UML: [http://www.visual-paradigm.com/product/vpuml/demos/umlsupport/]("http://www.visual-paradigm.com/product/vpuml/demos/umlsupport/")
You can create: Class diagrams, Use case diagrams, State machine diagram, and many more.
...and it's really easy to use :)

---

### Post by shankhs on 2009-08-02
> **Greyed said:**
> No battle plan survives contact with the enemy?  ;)

Thats interesting observation by Greyed .
It will be interesting to listen to your side please explain your side.
It will help a lot for beginners.

---

### Post by shankhs on 2009-08-02
> **baizon said:**
> I recommend Visual Paradigm.
URL: [http://www.visual-paradigm.com/product/vpuml/]("http://www.visual-paradigm.com/product/vpuml/")

For UML: [http://www.visual-paradigm.com/product/vpuml/demos/umlsupport/]("http://www.visual-paradigm.com/product/vpuml/demos/umlsupport/")
You can create: Class diagrams, Use case diagrams, State machine diagram, and many more.
...and it's really easy to use :)

Thanks for your help but the software is costly.I can't afford it.

---

### Post by Greyed on 2009-08-02
> **shankhs said:**
> Thats interesting observation by Greyed .
It will be interesting to listen to your side please explain your side.

Software in academia pushes two separate phases of coding.  Design and coding.  While this is good when programming or compilation time are expensive.  However as languages progress programming time and compilation time become cheaper.  At some point the design and coding phases can be combined since once can iterate through design choices rather rapidly.  

The main thrust of my point though is that as much planning as one puts into the code at some point you actually have to code and often times during the coding process problems arise which foil the best of plans.  Having a good general overview of where you want to go ahead of time is good.  But being flexible and scrapping the plan when it is clear while coding the plan doesn't work is better.  So at some point one has to accept that planning gets you only so far and just code.

With the cost of programming and compilation time dropping the point where one stops planning and starts coding shifts more and more to planning less and coding more and more.

---

### Post by shankhs on 2009-08-03
AH!
Better your plans lesser pain you will have during coding.Its truth that during coding things go little awry but sticking to the plan will help the code development in long run.In open source projects guys generally dont care about such stuffs so understanding them is a lot difficult. There are some bugs which are 7 years older or even older than that,these bugs are due to the structure of the software , nobody tries to change the structure as this will mean a huge understanding of the software.Had there been proper model or diagram to understand the software it would have been a lot easier.

---

### Post by mihnea.radulescu on 2009-08-03
In the university, they demanded a lot of UML from us, both at the software engineering exams and in most of our software project. They wanted us to use UML class and sequence diagrams to generate almost complete code, which is absolutely idiotic. Most of us students actually generated our UML diagrams through reverse engineering. :guitar:

While I agree that UML may prove useful in some contexts, the only UML diagram type that I really needed for my projects was the class diagram, and even then I preferred the pen-and-paper method, rather than a CASE tool.

And to think some of my professors are actually believing in a future of almost full code and test cases automatic generation from UML diagrams and the OCL specification language. I asked one of them, well, what about network connectivity code, or concurrency management, just to name a few, how do you generate them from UML? He said that extensions to UML need to be developed to tackle these issues. :lolflag: :popcorn:](*,)

---


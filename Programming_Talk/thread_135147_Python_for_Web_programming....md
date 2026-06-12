---
title: "Python for Web programming..."
date: 2006-02-23
forum: Programming Talk
---

### Post by j-a-p on 2006-02-23
I've recently started to use Python, which I like.  I'd like to go on further with it and use it to create web applications.   Since looking around I've become ovewrwhelmed with the amount of options available and currently I'm unable to find the equivalent of a de-facto Python web app tool, so therefore I can't choose.  Maybe there is something up and coming I should get into?  Is there such a thing or should I use an alternative such as PHP, or Ruby-on-rails.  I really would like to continue to use Python, as it is capable of doing everything else and could be the tool for all jobs.

I'm no Python (or programming in general) expert so I'd rather not have to learn an additional language for web application. Please give me guidance.  I'm confused.:???:

---

### Post by sapo on 2006-02-23
Take a look here:

[http://www.djangoproject.com/](http://www.djangoproject.com/)

But i dont like using python to make web stuff, i think php is better for that purpose.

---

### Post by ow50 on 2006-02-23
Even Guido is confused
[http://www.artima.com/weblogs/viewpost.jsp?thread=146149](http://www.artima.com/weblogs/viewpost.jsp?thread=146149)
[http://www.artima.com/weblogs/viewpost.jsp?thread=146503](http://www.artima.com/weblogs/viewpost.jsp?thread=146503)

---

### Post by j-a-p on 2006-02-23
That didn't help in relieving my confusion!  I'm still at a loss.  If Guido can't make his mind up then I've got no chance.

---

### Post by LordHunter317 on 2006-02-23
There is no standard python web framework, nor will there ever be.  Pick which one suits you the most.

Understand that python wasn't designed with scalably in mind, and won't work well for highly scalable web-applications.

---

### Post by GazaM on 2006-02-23
[QUOTE=LordHunter317]Understand that python wasn't designed with scalably in mind, and won't work well for highly scalable web-applications.[/QUOTE]

Not sure where you got your info from, but Python is extremely scalable... I recommend going to python.org or beta.python.org (work in progress redesign of python.org) and check out the various testimonials... one of the main reasons for people using Python within their projects is that it's so scalable.

---

### Post by LordHunter317 on 2006-02-23
[QUOTE=GazaM]Not sure where you got your info from, but Python is extremely scalable...[/quote]No, it isn't.  Python can only run one thread at a time, which is a serious scalability limitation for anything that's doing anything more than just shoving pages as quickly as you can.

TBF, a huge number of web projects do exactly that.  But if you have complicated processing to do, in parallel, it's less than ideal.

> one of the main reasons for people using Python within their projects is that it's so scalable.They're being mislead, or having radically different ideals about 'scalable'.

There are ways around it, but a pure python solution will have a lower upper-limit to how far it will scale before other solutions will.

---

### Post by sapo on 2006-02-23
[QUOTE=LordHunter317]No, it isn't.  Python can only run one thread at a time, which is a serious scalability limitation for anything that's doing anything more than just shoving pages as quickly as you can.

TBF, a huge number of web projects do exactly that.  But if you have complicated processing to do, in parallel, it's less than ideal.

They're being mislead, or having radically different ideals about 'scalable'.

There are ways around it, but a pure python solution will have a lower upper-limit to how far it will scale before other solutions will.[/QUOTE]
O RLY?

[http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/](http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/)

---

### Post by LordHunter317 on 2006-02-23
[QUOTE=sapo]O RLY?[/quote]Yes, really.  **Did you even read the article?**  The GIL prevents multiple execution of threads.  Period.  This is a serious scalablity limitation for certain types of applications, and eventually a limitation for any parallel I/O application, though likely you may be constrained by other things first.

---

### Post by sapo on 2006-02-23
I did not read that, anyway.. you seen do dislike python a lot.. why is it?

---

### Post by LordHunter317 on 2006-02-23
[QUOTE=sapo]I did not read that,[/quote]It's on the first page.

>  anyway.. you seen do dislike python a lot.. why is it?I don't, I'm mearly stating the facts.  You have to consider the lack of a thread-safe interpreter when designing your application.

I don't prefer python because I abhor it's syntax, it's almost totally unreadable to me.  

OTOH, most of my real complains come from bad decisions made in the language implementation, not the language itself.  

Ruby has similar flaws: complete and utter lack of any Unicode support, for example.  This isn't a problem when your target audience is Latin-1.  It is a major problem when they're not.

---

### Post by j-a-p on 2006-02-23
[quote=LordHunter317]Yes, really.  **Did you even read the article?** The GIL prevents multiple execution of threads. Period. This is a serious scalablity limitation for certain types of applications, and eventually a limitation for any parallel I/O application, though likely you may be constrained by other things first.[/quote]

Maybe you want to calm yourself down pal.  I only asked a simple question about suggestions for developing web apps with Python.  You seem to have gotten a right strop on and want to impress others with your superior knowledge, good on you, but, take a pill geezer.  You could always have a private agument (with yourself perhaps).

As a side note to these rants, I'm still none the wiser about this topic.

---

### Post by LordHunter317 on 2006-02-23
[QUOTE=j-a-p]Maybe you want to calm yourself down pal. [/quote]I am perfectly calm.  The point is, he shouldn't have even posted that since it supports what I said, so it's clear that he didn't read it.  That's rather worthless, isn't it?

> I only asked a simple question about suggestions for developing web apps with Python.And you got a simple answer.

> You seem to have gotten a right strop on and want to impress others with your superior knowledge,No, I don't like people attempting to correct me without even making a good-faith argument.  That's simply childish on the other person's behalf.

> You could always have a private agument (with yourself perhaps).:rolleyes: You could not bite the hand that's feeding you.

> As a side note to these rants, I'm still none the wiser about this topic.As I said, try a few and use the one you like the most or are most comfortable with.  They all have some positives and some negatives too them, much like any other framework decision on the planet.

---

### Post by j-a-p on 2006-02-24
Let's put the nastiness aside, I do appreciate your input here and was only trying to make light of the argument going on.  You obviously are far more versed in these matters than myself, but as I said I am just starting out.

To be fair though, I am still at square one.  I initiated this thread in the hope that I wouldn't have to go experimenting with all kinds of methods and perhaps get a "'this is definately what you want" answer.  This is the problem I have had with Python from day one - which was not that long ago - there is too much choice.  

Without, as you say, trying some, you won't know what you like.  But this only compounds my problem: being new to Python, and programming in general, I don't want to stray from Python to learn something else on top of it.  This is what I am starting to dislike about Python already, making a choice as to which tool to use has been harder than learning the language.  This in my book is enough to put off any prospective Pythoner.

As much as I am pleased to have moved away from MS and am really into Linux, there was only one choice with MS with regard to all kinds development - Visual Studio.  Linux need an equivalent. Something that is all encompassing and everyone is using to keep things simple.

Where to now?  I'm getting fed up with it all to be honest.

---

### Post by GazaM on 2006-02-24
j-a-p, it's understandable that too much choice can be pretty confusing, especially in situations like this. It's pretty hard to point you to a web framework to use, as they are really variable in their aims and what they are capable of and it depends on what you want to use it for. django looks very interesting to me, but you may be looking for a more CMS style solution? Try to explain what features you need in it and how you want to put them to use, that would make it far easier for us to recommend something to you.

---

### Post by j-a-p on 2006-02-24
...

---

### Post by Van_Gogh on 2006-02-25
[QUOTE=LordHunter317]
Ruby has similar flaws: complete and utter lack of any Unicode support, for example.  This isn't a problem when your target audience is Latin-1.  It is a major problem when they're not.[/QUOTE]

Just for the record, Python does have excellent unicode support, so Python and Ruby are not not similar in that respect. Anyway, Seeing that J-A-P is just starting out at programming, my guess is that scalability is not on the top of his list of priorities, but having an easy and intuitve programming language/web framework is important. Different tradeoffs for different needs and all that. Now, whether Python offers what he seeks seems to be the question...

I'm thinking about trying out Django myself to publish some stuff I got around, anyone who can recommend some cheap hosting? Paying 10-15$ a month for a very traffic-light site seems a bit much for a cheapskate such as myself...

---

### Post by LordHunter317 on 2006-02-25
[QUOTE=Van_Gogh]Just for the record, Python does have excellent unicode support, so Python and Ruby are not not similar in that respect.[/quote]That wasn't my point.  My point was that Ruby also has flaws (different ones) that can make it a no-go for a web application in certain situations, that's all.

---

### Post by majikstreet on 2006-02-25
I've seen some other python web framework thingys:
turbo gears [http://www.turbogears.org/](http://www.turbogears.org/)
cherrypy [http://www.cherrypy.org/](http://www.cherrypy.org/)

majik

---

### Post by j-a-p on 2006-02-25
Thanks for all your input people, I'm keeping my eye in the thread and presently django seems to be the most regular mention.  Perhaps I'll bite the bullet soon and give it a go.

All input is gratefully received.

---

### Post by veraction on 2006-02-27
Haven't messed with it too much. 

If you're just messing around & learning, you could use CGI. Install apache2 and put this file in /usr/lib/cgi-bin: ```
#!/usr/bin/python

# Required header that tells the browser how to render the text.
print "Content-Type: text/plain\n\n"

# Print a simple message to the display window.
print "Hello, World!\n"
``` Then navigate to localhost/cgi-bin/file.py and there you are.

However, a big limitation is that for every web request, it creates a new python process (as I understand it..) -- so in order to combat that, you can use Apache2's mod_python module (it is in apt-get) -- which makes it a bit more complicated, but it is better in long run/overall I think

---


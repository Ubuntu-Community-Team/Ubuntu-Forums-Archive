---
title: "Ruby On Rails. Is It Any good???"
date: 2006-12-12
forum: Programming Talk
---

### Post by gh0st on 2006-12-12
Hi folks,

I'm a .NET web developer who's trying to reform :-) I have been looking at Ruby On Rails and I've tried PHP and JSP before a couple of years ago. What I wanted to know really is what do people think of Ruby On Rails as a development platform??

Is it as good as all the hype? I've watched the tutorial videos on their website and they look inmpressive but is it really that easy?

I learnt Java at university and I know it can do the same things ASP.NET but it doesn't seem as quick or easy. I really want to be able to seperate my logic code from the design of the page like you do in ASP.NET, I also like the prebuilt web controls you have at your disposal. Can Ruby replace all this for me?? I hope so. Where should I start? I could just get a Ruby book and read it I suppose but I just thought I'd see what people thought of it first.

Anyway, thanks in advance for your help. I think thats enough questions for one post :)

Dan

---

### Post by nephish on 2006-12-12
Yes, Ruby on Rails is an excellent platform to develop with. No, it is not as easy as the videos if you want to do anything more complicated than a blog. The learning curve is not as steep as it is with other frameworks i believe. I have taken the last two months to both learn Ruby,  RoR and re-write the web application that our company depends on for everything. It took me 6 months to write it the first time while i was learning php. I would recommend it because so much stuff is taken care of. Lots of trivial code does not have to be written over and over and over because of all the helpers out there for it. The community is strong and very helpful. I recommend two books, the *Agile Web Development with Rails*, by Thomas ( 2nd ed is due out this month ) and the *Programming Ruby 2nd ed* ( what they call the pickaxe book).
For me, learning Rails has been proving just a different way to think about how an app on the web works as a big picture. Once you get into it, it seems rather straightforward, and if i do say so myself, a lot of fun.

hth

---

### Post by gh0st on 2006-12-12
Thats great, thanks for the advice I'll definately check those books out. Looks like I'd better start learning another new language then. I've heard the syntax is similar to Java or C++ so hopefully it won't take too long.

---

### Post by nephish on 2006-12-12
hey there, good luck and God speed with your projects, can't compare ruby with Java or C++ ( clueless to both ) but it is somewhat similar to python, which is where i came from ( and still use more than anything. )

---

### Post by gh0st on 2006-12-12
Thanks. I'm clueless to Python but I'm starting to see it's pretty essential on Linux better get a book on that as well :-)

---

### Post by pmasiar on 2006-12-12
After shackles of C++ and java, both python and ruby will be for you as a breath of fresh air: No type police! create your collections on the fly, and if object have proper methods, everything just works. Exception are dynamic, and you can ignore them for prototype: it will crash, and show you stacktrace - but so what - handle the important ones now, rest for production.

There is couple differences between ruby and python: 

[LIST]
[*]python was designed with goal to be **readable by humans** and easy to use for beginners - yet scale up for experts. Ruby comes from perl tradition of having very powerful tricks, even if it hampers readability and confuses beginners.
[*]python is older, and comes with substantially more libraries
[*]python has longer experience with optimization (== is faster)
[*]Google uses python a lot :-)
[/LIST]

Python was behind the ruby in web app space, now it is catching up with Django and TurboGears frameworks. But you can use python for many other things beyond web frameworks: wxPython for GUI, command-line utilities, etc. Python (and not ruby) is standard language for Ubuntu development, IIUC.

---

### Post by Burgresso on 2006-12-12
I'm a .net developer too - my concerns with RoR is the automagic layer of doing things. For most people this is good; for others, scary, but  for me, I'm to much of a perfectionist and would rather optimize my app myself.

And python really is awesome. I love it since I've started dabbling in it.

---

### Post by skeeterbug on 2006-12-12
> **gh0st said:**
> Hi folks,

I'm a .NET web developer who's trying to reform :-) I have been looking at Ruby On Rails and I've tried PHP and JSP before a couple of years ago. What I wanted to know really is what do people think of Ruby On Rails as a development platform??

Is it as good as all the hype? I've watched the tutorial videos on their website and they look inmpressive but is it really that easy?

I learnt Java at university and I know it can do the same things ASP.NET but it doesn't seem as quick or easy. I really want to be able to seperate my logic code from the design of the page like you do in ASP.NET, I also like the prebuilt web controls you have at your disposal. Can Ruby replace all this for me?? I hope so. Where should I start? I could just get a Ruby book and read it I suppose but I just thought I'd see what people thought of it first.

Anyway, thanks in advance for your help. I think thats enough questions for one post :)

Dan

It really depends how you define easy ](*,). What I like about working with RoR, is that it does what it was designed to do VERY well. If you want to do development in .NET, you will find yourself going out to get other libraries to get the job done. 

Example: 
We use LLBLGen O/R Mapper for .NET. This is a nice third party tool to do DB work with. RoR has ActiveRecord to do this baked right in, and is very easy to use and work with.

In my opinion, use the best tool for the job. Windows form work is being done here using .NET Windows.Forms 2.0, and is connected to Ruby on Rails webservices. This allows me to take advantage of ActiveRecord (RoR), and the rapid GUI development that .NET offers.

Hope that helped. :-k

---

### Post by pmasiar on 2006-12-12
> **Burgresso said:**
> I'm a .net developer ... And python really is awesome. I love it since I've started dabbling in it.

You may be interested in IronPython for .NET. Same python shell to play with objects, but implemented on top of .NET (most of standard python libraries - some are missing for now). Agile scripting language with dynamic types on top of .NET, fully integrated, released by MS. And they say it's faster than CPython - because of .NET CLI optimizer is really good.

---

### Post by gh0st on 2006-12-13
Wow thanks for all the info everyone, much appreciated. I am definately going to look into Python and see what it can do. Does anyone have any good book suggestions for Python?? 

I have pretty good expirience as a programmer in Java/C# and VB.Net so I want something that will guide me through Python without being too basic.

Thanks again,

Dan

---

### Post by daz4126 on 2006-12-13
Ruby for Rails by David Black is an excellent book.

DAZ

---

### Post by pmasiar on 2006-12-13
> **gh0st said:**
> Does anyone have any good book suggestions for Python?? 

[Wipikedia on python]("http://en.wikipedia.org/wiki/Python_%28programming_language%29") mentions couple online books. As a non-beginner programmer, maybe "Dive into python" is the good one. I have good experience with O'Reilly books, "Learning Python" is good one too. Even if you decide to learn python from online books only, for sure buy "Python Pocket Reference". Best $10 spent on any book. :-) Official python website has also a page for you: [http://www.python.org/about/gettingstarted/](http://www.python.org/about/gettingstarted/)

Because python free online books are so good, TIOBE and othrer publishers rate Ruby as more popular (because Ruby sells more books). Don't get fooled by that statistics.

---

### Post by asimon on 2006-12-13
> **pmasiar said:**
> Because python free online books are so good, TIOBE and othrer publishers rate Ruby as more popular (because Ruby sells more books). Don't get fooled by that statistics.
Yes, don't get fooled. So time to get that right. What you write sounds as if TIOBE just counts number of book sells. Let's see: *The ratings are based on the world-wide availability of skilled engineers, courses and third party vendors. The popular search engines Google, MSN, and Yahoo! are used to calculate the ratings. Observe that the TIOBE index is not about the best programming language or the language in which most lines of code have been written.*

TIOBE doesn't even have access to the book selling statistics of publishers. The interested can read on their web page the exact definition of their index numbers.
Another thing: In the TIOBE index Python is reated higher than Ruby.


Regarding web development, coding with Rails is much more fun for me then using Django or TurboGears, but that's my opinion. All three frameworks are very good. I am more productive with Rails then the two Python frameworks I mentioned, but that's mostly because of my preference and better understanding of Ruby than Python.

For anyone planing some non-trivial projects I recommend to try out a couple of frameworks and find the one you like best. There is no point to just use Python because it's more popular in the Ubuntu community.

---


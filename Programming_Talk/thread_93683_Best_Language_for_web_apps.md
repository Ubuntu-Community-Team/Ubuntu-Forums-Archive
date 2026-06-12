---
title: "Best Language for web apps?"
date: 2005-11-22
forum: Programming Talk
---

### Post by zootreeves on 2005-11-22
I know php pretty well and can get it to do most things I want in it. But I want to learn a more powerful language for a new program I am going to work on (I have buillt a large portion of it in php already). But I need a language that can be multi threaded (I need to be able to execute more than one mysql query at once). 

Is there another way to do this with php? I have done some python in the past, does it support multithreading? could you give me an example? Also I have seen the PIP (Python in php) project has anyone tried this?

---

### Post by gord on 2005-11-22
python has fine threading support as long as your os supports it. 

if your looking for doing web stuff with python check out [django]("http://www.djangoproject.com/"), its encredible. quite similar to ruby on rails but for python, django was started (behind closed doors) before ruby on rails was started so they have some diffirences. 

i messed about with it a short while ago and fell in love with it, no more doeseverything.php or a .php for every little thing. everywhere has its own place and its much easyer for people navigating the site that don't know about or care about .php's all over the place to work with :)

---

### Post by zootreeves on 2005-11-22
thanks for the info gord, I will look into django. Well my OS is ubuntu so I presume it will work with multi threading...

Can anyone post an example on how to do multi threading with python, as I cannot seem to find much info. I found the following code to use with stackless python, but this will not work on a default ubunut install right?

def sayHello():
    print 'Hello, world'

import uthread
uthread.new(sayHello)
uthread.new(sayHello)
uthread.run()

---

### Post by gord on 2005-11-22
im not quite sure how you meen 'multi threading', but...  [http://docs.python.org/lib/module-threading.html]("http://docs.python.org/lib/module-threading.html") [http://docs.python.org/lib/module-thread.html]("http://docs.python.org/lib/module-thread.html")

its been quite a while since i have worked with threading but if i remeber rightly the base webserver that comes with python uses threading to handle requests, might be an idea to look at that.

---

### Post by Corvillus on 2005-11-22
Also, if you want to continue working with PHP, it does have it's own implementation of multithreading with the pcntl_fork() function, which works identical to the fork() function in C. More info here: [http://www.php.net/manual/en/function.pcntl-fork.php](http://www.php.net/manual/en/function.pcntl-fork.php)

---

### Post by cactus on 2005-11-22
I just love ruby on rails myself. But then..I love ruby, so I am biased. ;)

---

### Post by LorenzoD on 2005-11-23
[QUOTE=cactus]I just love ruby on rails myself. But then..I love ruby, so I am biased. ;)[/QUOTE]

Agreed. Ruby is true love, on rails or off..

---

### Post by baronKarza on 2005-11-23
Why don't u try Java/JSP/Struts... ?
It's not trivial, but u can get very good results conforming to the best practice of sw engeneering. 
The learning curve is not so short but the technology is very reliable, scalable and the OO paradigm guarantees the reusability of code.
I'm using it on a quite big project (more than 500.000 lines of code) and it works  perfectly. In my view, it's the most professional solution available today...:razz: (I don't want to start a war of religion...)

---

### Post by nemik on 2005-11-26
my favourite is still PHP/MySQL all manually (no frameworks) which was my first serious endevour with programming and my favourite still.

i code in J2EE/JSP and will get into struts eventually at my work/internship. i don't like it as much as i like PHP but i use it because i have to and that is what we have so far.

i tried ruby on rails over the summer after all the hype about it and it drove me crazy. i was not (and still am not) used to ruby syntax and somehow just cannot get myself to use a framework, it just feels so constrained to me. perhaps i should have given it more time and patience but i was and still am very busy so i doubt i'll be coming back to RoR world anytime soon.

haven't tried yet anything with python but would like to get into it a bit for developing gnome GUI apps.

but i am 100% in love with PHP.

---

### Post by Jun-Dai on 2005-12-06
I would skip struts and go straight to learning Spring.  If you can't abide by a framework, I'd recommend getting out of web programming over the next few years.  PHP is probably going to move to a framework, MS has moved, Struts _is_ a framework, and I think J2EE shops will embrace frameworks more (heck, J2EE is itself a framework: think of web.xml and WEB-INF).  Doing development outside of a framework is going to become increasingly marginal, even if it is the norm for small projects now.  The problem with *not* using a framework is that your code is that much more opaque to someone familiar with the technology but unfamiliar with your project, making it much less manageable as they have to make changes before having time to learn fully how your project is organized (my project is large enough that after 2 years, I only have a "fairly good" grasp of how it's organized).  For a small project that only you have to look at and will never have to revisit after a time, that won't ever be a problem.

But RoR is about as clean and easy to learn a framework as I can imagine at this point.  Once you are familiar with even just the basics of it, you can dive into any open source project's source code and feel comfortable with the way it's arranged.  That's pretty amazing to me.

Spring does an amazing job of doing something similar to RoR in Java.  If you _have_ to work in Java, or if you need something more mature, stable, and scalable than RoR (at least current versions of RoR--who knows what the future holds?), then Spring is a godsend.

---

### Post by Ubuntu Warrior on 2006-01-08
Can only support Jun-Dai in his comments on Spring. I have a small development team that manage legacy in-house code and code released from our outsource partners and Spring makes this a breeze. Tried Struts initially but turned out to be somewhat more complex to handle than Spring without much benefit.

Frameworks, open ones that is, are most definitely the way forward for web development and will facilitate much faster development cycles and easier managed code.

---

### Post by LordHunter317 on 2006-01-08
[QUOTE=zootreeves]But I need a language that can be multi threaded (I need to be able to execute more than one mysql query at once).[/quote]You shouldn't generally need to do this in a web application, per-request.  You may need to be able to serve a single-query per request, but you can do that already in PHP.

IOW, needing to have multiple parallel queries per-request is not a common (but not unheard of) requirement.  

> Is there another way to do this with php? I have done some python in the past, does it support multithreading?It does, but it has some limitations.  Among other things, you won't be building high-performance I/O systems in python, due to the way the interpreter works.  You can only have one thread running at once.

[quote=baronKarza]
Why don't u try Java/JSP/Struts... ?
It's not trivial, but u can get very good results conforming to the best practice of sw engeneering. [/quote]Anything using Struts won't be a "best of".  It'l likely be a "worse of" however.  Struts is easily the worse web programming framework on the planet.

> and the OO paradigm guarantees the reusability of code.Not really.  Especially with struts.  You end up having to write (and they insist by convention) not one, but two objects for every little thing.  Even when they are almost identical.

> In my view, it's the most professional solution available today... (I don't want to start a war of religion...)There are a million better solutions for Java available.  Wicket, for starters.  JSF, if you want something Sun-backed.

Ignore the people saying go to spring.  It's just really struts rehashed, and doesn't bring anything to the table, and it's an inferior paradigm compared to ASP.NET.

---

### Post by nuggien on 2006-05-22
[QUOTE=LordHunter317]
It does, but it has some limitations.  Among other things, you won't be building high-performance I/O systems in python, due to the way the interpreter works.  You can only have one thread running at once.
[/QUOTE]

a little late with the response, but unless you have more than one cpu, wouldn't you be limited to a **single** thread running at once anyways?  OS context switches threads in and out and no true parallelism is possible with one cpu.

---


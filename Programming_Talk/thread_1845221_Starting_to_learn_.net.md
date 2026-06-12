---
title: "Starting to learn .net"
date: 2011-09-16
forum: Programming Talk
---

### Post by overtone on 2011-09-16
Hi there,

This is a tricky one and I need an experienced opinion. 

I'm a 4th year cs student and were starting to learn .net in our software development module. The course will be broken into learning basic .net and c# then moving to asp.net and finally android development. I've been using Linux more and more lately and would really not like to go back to windows for my development environment.

So.... 

Mono seems like a natural choice but I'd like some opinion of it first.
How does it compare to using windows?

Will using mono to develop .net applications shoot me in the foot or is it worth my time begrudgingly going back to windows for the sake of the course.

Kind regards,

Overtone!

---

### Post by Off Shore on 2011-09-16
We are usually quite prescriptive in education. Surely your course dictates which development environment to use for each module?

On a more general  level I believe MONO is somewhat behind the current .NET Framework.

I believe it may be thereabouts with .NET v3. ... possibly still at v 2. Maybe some one can correct me if Im wrong. However, .NET by contrast is currently up and running with version 4.

The problem you will run into, when you move to ASP.Net with mono, relates to the very limited availability of server side controls. You can, of course, hand roll your own if you have lots and lots of time.

For me its a very easy choice. Visual Studio and Expression Design for developing ASP.Net each and every time. But thats just me.

Jolly good luck anyhow with your degree and Im sure you will make the right choice.

---

### Post by directhex on 2011-09-17
> **Off Shore said:**
> I believe it may be thereabouts with .NET v3. ... possibly still at v 2. Maybe some one can correct me if Im wrong.

You're wrong. Mono 2.8 introduced .NET 4.0 support. Oneiric will ship with 2.10.5, Natty has 2.6.7 (which is .NET 3.5)

> The problem you will run into, when you move to ASP.Net with mono, relates to the very limited availability of server side controls. You can, of course, hand roll your own if you have lots and lots of time.

You should be using MVC in 2011.

And Microsoft ASP.NET MVC is open-source software which runs on Mono.

---

### Post by Off Shore on 2011-09-17
> **directhex said:**
> You're wrong. Mono 2.8 introduced .NET 4.0 support. Oneiric will ship with 2.10.5, Natty has 2.6.7 (which is .NET 3.5) 

Well you are almost correct. I'm sure you know as well as I do there is no support for WPF.
You may think otherwise but I regard that as a rather significant subset of the .Net Framework. 
(you can find it in System.Windows Namespace) 
Otherwise, many thanks are due for the update. 


> **directhex said:**
> 
You should be using MVC in 2011.


I really do think it isn't quite the ticket for you or anyone else to dictate what people "should" be using.
MVC is an alternative to Web Form based ASP.Net applications. You can get a rather well written appraisal of the various approaches here [http://www.asp.net/mvc/tutorials/asp-net-mvc-overview-cs](http://www.asp.net/mvc/tutorials/asp-net-mvc-overview-cs)

The OP specifically mentioned moving on, in the context of his course, to study ASP.Net. My reply was, as you may imagine, framed inside that context. 

It remains the case that generally Educational establishments are quite prescriptive when it comes to development environments and, anyhow, Mono is not 100% compatible with the .Net Framework.

The best course of action for the OP is to follow the guidance provided by the Educational establishment when choosing his development environment.
I suspect he would receive a jolly frosty reception indeed if he adopted your stance and told his tutor, " You should be using MVC in 2011" when confronted with a Web Form based assignment.!

---

### Post by PaulM1985 on 2011-09-17
I would say, for your course, stick with windows. If you find there are issues in mono's implementation you could start having a stressful time, especially near to deadlines. However, do not let this put you off using mono for you own personal development projects now, or in the future.

Good luck

Paul

---


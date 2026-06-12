---
title: "C#+ASP.NET+AJAX Development"
date: 2007-06-29
forum: Programming Talk
---

### Post by Majorix on 2007-06-29
A friend of mine (a non-tech-person [if such a word existed he would get that title for sure]) just bought me a set of 3 books on C#, ASP.NET using C#, and AJAX with ASP.NET.

Of course he didn't know there is no VS on Ubuntu. Like I said he isn't that good with computers.

And the problem is, I don't know how I can use these languages under Ubuntu as well.

Perhaps this is a newbie question if I have to admit, but I am in desperate need.

If anyone can help with any point, I would be glad. Program names (if any exist) and/or links to sites would be great.

PS: Yeah I know of Mono but does it support ASP or AJAX too?

Thanks in advance,
Maj-

---

### Post by LaRoza on 2007-06-29
Ajax is run in the browser, it works on any OS.

C# is Microsoft's version of Java, learn Java instead, it is more useful and not limited.
ASP.NET is a server side technology that uses a Microsoft server.

If you want to program, I suggest checking out my wiki, in my sig. It is new, but it should help.

-edit For server side scripting use PHP.

---

### Post by Majorix on 2007-06-29
Yeah I know a bit about what C# is and what it is not, I worked with it on Windows computers in a job recently. I also know a little about ASP.NET, though haven't necessarily done that much web-programming. And I heard it could be run on Apache somehow too, not only on Windows... Maybe someone here knows. AJAX is totally new to me though, thanks for clarifying me on that one.

I would pretty much love the way of Java, JSP or PHP etc, but the problem is I will study C# in school next year. In computer programming schools, they just assume you use Windows. I looked around for Java-related computer programming courses, but there aren't any in the vicinity I live. So I WILL HAVE TO work with C#.

These books I got from my friend are a big help, and I want to make the most out of them.

Any thoughts?

---

### Post by Majorix on 2007-07-01
Any one?

---

### Post by aquiles_caigo on 2007-07-01
pheraps you can try using Mono!
where you can program using microsoft .Net framework but in Linux!

---

### Post by Smygis on 2007-07-01
Django!
[http://www.djangoproject.com/](http://www.djangoproject.com/)

Whips php, Java and anything else realy hard.
Ofcource you have to learn Python. But Python is realy easy to learn.
[http://www.python.org](http://www.python.org)


And yes, Mono supports ASP.NET, C#, VB.NET and so on.
Monodevelop is an IDE.

---

### Post by emperon on 2007-08-05
yes it supports ajax with the anthem.net and gaia ajax frameworks . Google them for more info

---

### Post by Note360 on 2007-08-05
Wow ok...

C# works very well in Mono.
ASP.Net can be run in Apache I did it before. Get the Mono-XSP2 set up apache (install apache2) and install hte apache2 plugin for xsp or mono. Then it should work. It is really very straight forward. Use Synaptic to find the stuff.

Good luck and if you want to learn C# go ahead dont let these guys stop you. Python is cool to though. java is nice to, but for some reason I get a kick out of running .exe files

---

### Post by pmasiar on 2007-08-05
> **Majorix said:**
> I would pretty much love the way of Java, JSP or PHP etc, 

JSP/PHP are easy to start but is is easy to create messy hard to maintain code. Right way to do web apps is [MVC](http://en.wikipedia.org/wiki/Model_view_controller)

---

### Post by Majorix on 2007-08-05
> **emperon said:**
> yes it supports ajax with the anthem.net and gaia ajax frameworks . Google them for more info

They don't seem to be available through the repos. Are there ones that are available in  the repos too?

> **Note360 said:**
> Wow ok...

C# works very well in Mono.
ASP.Net can be run in Apache I did it before. Get the Mono-XSP2 set up apache (install apache2) and install hte apache2 plugin for xsp or mono. Then it should work. It is really very straight forward. Use Synaptic to find the stuff.

Good luck and if you want to learn C# go ahead dont let these guys stop you. Python is cool to though. java is nice to, but for some reason I get a kick out of running .exe files

Ok I installed the said plugins. I will look at them closer soon.

---

### Post by Note360 on 2007-08-05
> **Majorix said:**
> They don't seem to be available through the repos. Are there ones that are available in  the repos too?



Ok I installed the said plugins. I will look at them closer soon.

yeah jsut make a file (index.aspx) with the asp code in it navigat to localhost/index.aspx and it should work. Im not sure though.

---

### Post by emperon on 2007-08-10
they are .net assemblies. usually copying the dll's to your application's bin folder is enough.You don'T have to use synaptic to install every dll's. Just google them. And if you're stuck I'll help you on ajax.

---


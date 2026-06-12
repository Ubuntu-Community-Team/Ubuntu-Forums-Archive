---
title: "I'm having Linux Problem."
date: 2008-10-24
forum: Programming Talk
---

### Post by nullQube on 2008-10-24
I am a developer in windows for about 9 years (Vc++). and unfortunatly I have been tool depended ( to lovely Visual Studio, and it's the only thing that i like about windows. )
now it's been a while that i come to linux I had tried eclipse and Gedit(:D) and EMacs(what a greate invent) and they are nice IDEs but it's good for console apps and X11 ( that i did some ), but i want GUI app (visual).
I like GNOME over KDE , it's much pretty and faster.
I cann't get anjuta&glade to work  I even can't add a single button with click signal ( I found some doc and they say push the Add button, I can't even find the f***ing button, probably different version ).

any way   I like linux a lot I did some basic thing,
and even I became bash lover ... .
I have some plan to do for linux world but I'm having begginers problem.

I also need some link to refrences.

help me guys.

by the way. I have some good news:
I working on a site something like codeproject.com but for linux world, hope you like it and I'm glad to have some help from you guys.

linux is good. it's fast ,secure , customizable, ..... ==> linux > windows.
windows have a lot of tools that linux doesn't have that much but it's not a big problem anymore and gladly they(maybe you) working on it.  linux ~ windows.
but the biggest point of windows is a lot of documentation and tutorials and ...... (specially MSDN) and site like codeproject, codeguru and ............   i this case linux < windows
and hopefully I'll do some good job in this part.
see ya

p.s.
it's not an article ,  anwser me.

---

### Post by gnusci on 2008-10-24
Did you hear about mono?

[http://www.mono-project.com/](http://www.mono-project.com/)

---

### Post by nullQube on 2008-10-24
yes I know it and I did somthings with it too.
.Net is Microsoft thing that probably would work best at theirs windows
and even in windows it can't fully use computer and windows potentials so in linux with all these lovely feature it wont be a point. but as I'm doing it for living, I can say .Net is one of the best thing for enterprise project that I (my tiny company(team)) do for our customers.
I choosed linux for my own projects.

---

### Post by cszikszoy on 2008-10-24
> **nullQube said:**
> yes I know it and I did somthings with it too.
.Net is Microsoft thing that probably would work best at theirs windows
and even in windows it can't fully use computer and windows potentials so in linux with all these lovely feature it wont be a point. but as I'm doing it for living, I can say .Net is one of the best thing for enterprise project that I (my tiny company(team)) do for our customers.
I choosed linux for my own projects.

You should look a bit further into Mono.  I don't think you fully understand what Mono is about.  It isn't JUST .NET.  The mono framework also includes many libraries for integration with unix.  Check out there's the Mono.Unix API that specifically provides access to many parts of a unix system, and also gnome and mozilla libraries.  The Gnome library provides an API for integration with the gnome desktop (GConf, GTK, etc) and the Mozilla library.. well, provides integration with Mozilla apps.

Also, if you like Visual Studio, try out Mono Develop, it's about the closest IDE you'll get to VS on Linux.

---


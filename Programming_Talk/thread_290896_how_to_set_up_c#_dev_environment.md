---
title: "how to set up c# dev environment?"
date: 2006-11-01
forum: Programming Talk
---

### Post by Choad on 2006-11-01
i am being taught c# for my uni programming module, so i need to set up a dev environment

what packages should i install, and whats the best ide? all i really need is a text editor with c# syntax highlighting

cheers

---

### Post by Engnome on 2006-11-01
gEdit supports c# :D (plus another gazillion texteditors)

Isn't monodevelop made for this? Maybe go check it out?

Edit: oh and you'll need mono (instead of .NET, [http://en.wikipedia.org/wiki/Mono_(software)](http://en.wikipedia.org/wiki/Mono_(software))) to run c#

---

### Post by bsussman on 2006-11-01
quanta has c# highlighting and it is a good editing environment - I use it for xhtml/css/php

---

### Post by Choad on 2006-11-01
ok cool, but which packages do i need to apt-get?

i dont really want to add any bloat if its possible

also, will console apps be able to be ported verbatim form MS visual studio 2005?

---

### Post by yabbadabbadont on 2006-11-01
Monodevelop.  Look at it's dependencies in Synaptic to decide if it is too much.

The mono project website, with lots of useful information, is here:

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by Choad on 2006-11-02
> **yabbadabbadont said:**
> Monodevelop.  Look at it's dependencies in Synaptic to decide if it is too much.

The mono project website, with lots of useful information, is here:

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)
ok, monodevelop ROCKS

it is pretty much a free version of visual studio 2005 lol

not quite as good at sensing what you want to type.... VS2k5 got me typing lowercase and relying on it to uppercase stuff, and that doesnt work here.

question: where is a good tutorial on gtk# programming? cant seem to find one

---

### Post by crumja on 2006-11-02
Mono website has documentations on this and examples.

[http://www.mono-project.com/GtkSharp](http://www.mono-project.com/GtkSharp)

---

### Post by Choad on 2006-11-02
> **crumja said:**
> Mono website has documentations on this and examples.

[http://www.mono-project.com/GtkSharp](http://www.mono-project.com/GtkSharp)
hmmm pretty good

monodevelop is not very mature yet is it? it crashes if you dont use it "correctly"

not so good for learning on coz i tell it to do stupid thiongs all the time

---

### Post by cunawarit on 2006-11-02
I've been playing around with MonoDevelop and it is great! If you do have a Windows machine you can give Visual Studio Express a go, in conjunction with SQL Server 2005 Express it is a great free (as in beer) home dev environment ( [http://msdn.microsoft.com/vstudio/express/](http://msdn.microsoft.com/vstudio/express/) ). Hard to believe MS gives it away...

> [http://www.mono-project.com/GtkSharp](http://www.mono-project.com/GtkSharp)

THANK YOU!!! THANK YOU!!! THANK YOU!!! I've been strugling with Gtk#

---

### Post by cunawarit on 2006-11-02
> **Choad said:**
> monodevelop is not very mature yet is it? it crashes if you dont use it "correctly"

not so good for learning on coz i tell it to do stupid thiongs all the time

I haven't had it crash, yet. But admitedly I haven't been using it heavily. 

However, if you are being taught using Visual Studio 2005, then I would reckomend that you get Visual Studio 2005 Express... It is always going to be easier to use the same IDE you are being taught with. 

I even use Visual Studio 2005 Express for work when doing .NET 2 stuff... It really is very nice!

---

### Post by chedabob on 2006-11-03
^^

Ive found that mono-devlop isnt that great for C# if you learn it in a windows environment. If you learn with Visual Studio, run it in a virtual machine. I ended up doing that anyway cos it fucks up windows no end.

---

### Post by skeeterbug on 2006-11-03
> **chedabob said:**
> ^^

Ive found that mono-devlop isnt that great for C# if you learn it in a windows environment. If you learn with Visual Studio, run it in a virtual machine. I ended up doing that anyway cos it fucks up windows no end.

Thats because mono-develop doesn't have all the features we use in VS2005. As an experiences C# dev, I still think it's damn cool I can write apps in linux. Glade/Gtk# stuff is pretty good too. Nothing like the forms designer VS has, but that doesn't make for the portable code either. Give a little, take a little I suppose! :)

---


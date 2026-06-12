---
title: "Visual Studios to Mono??"
date: 2011-01-09
forum: Programming Talk
---

### Post by brobo on 2011-01-09
Hello! I'm new here, so I'm terribly sorry if I put this in the wrong spot or if someone has already posted something like this.

I'm interested in building some programs for Linux oses. The only problem is that these programs were made in Visual Studios on my Windows computer! Does anyone know if there is a way to either build the projects in Visual Studios so they can be installed onto Ubuntu (without the use of wine- like make some .deb files) or convert the solutions so I can use them in Mono?

Thanks in advance! :D

---

### Post by pbpersson on 2011-01-09
Have you looked for any articles on the web concerning this yet?

I thought [this one]("http://ondotnet.com/pub/a/dotnet/2005/06/13/vs2mono.html") looked very interesting

---

### Post by brobo on 2011-01-09
Thanks for the quick reply. I have looked around a bit but didn't see that page.

I'm using Visual Basic, and my main problem is the gui. The UI is fairly complicated and I don't know if I will be able to convert it gtk... will I be able to just copy+paste and make a few adjustments?

I'll continue to read the article you gave me.

---

### Post by directhex on 2011-01-09
Mono can open Visual Studio.NET projects (up to 2008, I think)

Or you could just run your assemblies on Ubuntu, assuming they're built for .NET 1->3.5 (not 4.0)

---

### Post by pbpersson on 2011-01-09
Here are two more articles that looked interesting, notice the second one is from Novell:

[http://tirania.org/blog/archive/2006/May-19.html]("http://tirania.org/blog/archive/2006/May-19.html")
[http://www.novell.com/coolsolutions/appnote/1673.html]("http://www.novell.com/coolsolutions/appnote/1673.html")

From what I have been told, Mono does not support VB.NET as thoroughly as it does C#.NET.

The most recent of these three articles is over four years old.  I would think there would be tons of articles on this.  I am somewhat surprised!

---

### Post by brobo on 2011-01-09
Just to test it out, I created a very very simple program in Visual Studios 2010 Express... it just copied the value of one text box to another when a button was clicked, but the point was to see if I could open it in Mono. I **was** able to open, build, and run it without problems!

I don't know how much stuff is supported, but I suppose I'll find out as I keep messing around with Mono. Thanks for your help!

I too am surprised at how few articles there are on this subject... surely I can not be the only one who has wanted to do this within the last four years.

---

### Post by pbpersson on 2011-01-09
I had a 3300-line application written in VB.NET, I re-wrote it in Java to bring it to the Linux world.

I did not have a warm fuzzy feeling as to the maturity of Mono and there was some talk of Microsoft having their hands in Mono and perhaps someday claiming they "own" some of the libraries inside Mono and should therefore control its future.

Call me paranoid.  ;)

---

### Post by fallenshadow on 2011-01-10
I think you are paranoid! :D

---

### Post by directhex on 2011-01-11
> **pbpersson said:**
> Call me paranoid.  ;)

You're paranoid.

---


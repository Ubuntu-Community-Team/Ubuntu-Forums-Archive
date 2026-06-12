---
title: "why mono ?"
date: 2009-10-19
forum: Programming Talk
---

### Post by diffuser78 on 2009-10-19
Can someone with experience in mono list out why it is good for development ? I read that we can develop cross platform apps etc.

I want to get some opinion from folks who are actually using it and can help a newbie.

Thanks.

---

### Post by SunSpyda on 2009-10-19
Search for the other billion similar threads out there on this forum to get a answer.

A few reasons for Mono/C# (Because it's the language that Mono pretty much uses) -

1) Runtime portable across platforms.
2) Standard library (same point as above really).
3) Can do lowish-level pointer stuff without killing portability.
4) Clean syntax.
5) Has access to non-standard libraries like GTK#, which are apparently very good. GTK# is actually 'standard' with Mono I suppose.
6) Easy to use compared to C or C++.
7) Good OO support.
8) Pretty fast considering its capabilities.
9) Easy access to C libraries.
10) Preinstalled on all modern Windows, & many Linux distros are now packaging it by default.
11) Open standard for C#.
12) Multiple languages supported, in case C# isn't your thing.
13) Many people are trained using .NET on Windows, so its a easy migration path to Linux.

That's all I can think of right now. There are also many concerns about Mono, which there is a specific thread for. Choose yourself whether to believe them or not.

---

### Post by mmix on 2009-10-19
If you want develop .net application, just use vs.net from MS.
you can develop various type of application like wpf,c#,etc..

mfc/c++ is not a bad choice in win32/64.

---

### Post by directhex on 2009-10-19
> **mmix said:**
> If you want develop .net application, just use vs.net from MS.
you can develop various type of application like wpf,c#,etc..

mfc/c++ is not a bad choice in win32/64.

Did you notice the orange-and-yellow-and-red logo at the top-left of the page?

---

### Post by fevans on 2009-10-21
> **diffuser78 said:**
> I want to get some opinion from folks who are actually using it and can help a newbie.
Thanks.

I've been using mono for about a 18 months now. A lot of good answers have already been provided, but for me I needed a language which worked in both a web and thick-app context. I was maintaining a web interface in php, and desktop apps in C++.

For the record, I don't believe C# is better than php for web apps, nor is it better than C++ for back end performance. However its pretty good at both. More to the point, its pretty good at most things. If mono were an animal it would be a raccoon; a good general purpose omnivore.

In terms of cross platform compatibility I'm very satisfied. I develop in Visual Studio, and redirect my project output to a share which is accessible from both Windows and Linux.

---


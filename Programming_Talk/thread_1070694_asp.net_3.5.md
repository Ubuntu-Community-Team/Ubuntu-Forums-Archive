---
title: "asp.net 3.5"
date: 2009-02-15
forum: Programming Talk
---

### Post by qbox on 2009-02-15
Hi
I have one page written in asp.net 3.5
I need to run on linux server.
I use this guide 
[http://www.howtogeek.com/howto/ubuntu/run-aspnet-applications-on-ubuntu-for-developers/](http://www.howtogeek.com/howto/ubuntu/run-aspnet-applications-on-ubuntu-for-developers/)
But this is for ASP.NET 2.0
How to install 3.5 version and to run.
Thx

---

### Post by bruce89 on 2009-02-15
You can't.

---

### Post by Rich78 on 2009-02-16
Do you actually use any of the 3.5 libary components or can you just recompile it to 2.0?

Mono currently supports up to .net 2.0

I think you'll be in for a bit of a wait for 3.5 support.

---

### Post by directhex on 2009-02-16
There are actually only two versions of .NET - 1.0 and 2.0. 3.0 and 3.5 are add-ons for 2.0

So unless you're using 3.5-only methods, then your app is really 2.0

---

### Post by Rich78 on 2009-02-16
3.5 uses 2.0 as a base framework but the compiler is different and so you would still have to recompile as a .Net 2.0 app.

---

### Post by directhex on 2009-02-16
> **Rich78 said:**
> 3.5 uses 2.0 as a base framework but the compiler is different and so you would still have to recompile as a .Net 2.0 app.

Mono's C# compiler has features from .NET 4.0 and beyond. It certainly includes lambda functions from C# 3

---

### Post by cl333r on 2009-02-16
> **qbox said:**
> Hi
I have one page written in asp.net 3.5
I need to run on linux server.
I use this guide 
[http://www.howtogeek.com/howto/ubuntu/run-aspnet-applications-on-ubuntu-for-developers/](http://www.howtogeek.com/howto/ubuntu/run-aspnet-applications-on-ubuntu-for-developers/)
But this is for ASP.NET 2.0
How to install 3.5 version and to run.
Thx

Short advice: if you use 3.5 features - stay on windows.

<anti ms propaganda>
If you're going to care about Linux, Solaris, BSD and anything else besides windows, you should read more on Microsoft's history and how it likes to support cross-platform solutions.
Those who write ASP Net apps end up in 99.9% putting them on windows and they *think* their apps can also run on other platforms with minor tweaks, but when they actually start moving they start realizing the discrepancy between Microsoft's "promise" and the reality.
</anti ms propaganda>

---


---
title: "ASP and Apache"
date: 2007-03-22
forum: Programming Talk
---

### Post by rodgewilco on 2007-03-22
Hi Folkz,

I have to develope dynamicaly web-pages for my study, but I don't want to use Microsoft products. The requirement is to use ASP. Is there an opportunity to do this on Ubuntu 6.10?

Thanks for your help
rodgerwilco

---

### Post by Windslip on 2007-03-23
ASP is microsoft only. You could write the pages on Ubuntu, but you would have to upload it to a IIS server to test it.

---

### Post by pmasiar on 2007-03-23
> **rodgewilco said:**
>  The requirement is to use ASP.

[Mono](http://en.wikipedia.org/wiki/Mono_%28software%29) is free implementation of .NET Maybe .ASP is part of it, but... It might not be 100% and many developers consider whole .NET too risky to contribute (MS patent issues... nothing concrete yet, but why even bother?)

Maybe you can talk to them "tell me what you want to do, and let me decide how to do it, which technology has best value for your needs". But if they are MS shop inside and standardized on ASP, there is nothing you can do.

Take it as many other developers - MS tools during day job, free software in my own time! :-)

---

### Post by AndrewBarber on 2007-03-23
I have this issue too. I write the scripts at home then upload them to the college server to check.

---

### Post by mikalh on 2007-03-29
Assuming you mean ASP.NET rather than classic ASP, Mono supports it fine, though it may take a bit of effort to set up properly. The Mono website explains how to set up Mono_mono for Apache. 

For the latest and greatest versions of everything you'll probably have to build it. I suggest using Mono 1.2.3.1 and the XSP web server, with MonoDevelop 0.13.1 and the ASP.NET development AddIn.

---


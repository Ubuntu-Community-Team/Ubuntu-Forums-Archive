---
title: "mono programming."
date: 2009-08-09
forum: Programming Talk
---

### Post by frustphil on 2009-08-09
If I make a mono app, should I code it in C#? Are all mono-based apps coded in C#? I am bit confused about mono. I've searched about mono tutorial, but I couldn't find any. Maybe it's because I was expecting it as a language. And I found out that mono is not a language but a binding? Could someone enlighten me about this please...

---

### Post by credobyte on 2009-08-09
Mono is a platform for C# and ASP.NET projects ( C# for desktop app & ASP.NET for web app development ).

---

### Post by frustphil on 2009-08-09
> **credobyte said:**
> Mono is a platform for C# and ASP.NET projects ( C# for desktop app & ASP.NET for web app development ).

for Linux (and probably Mac)? and .NET is for Windows right?

---

### Post by .Maleficus. on 2009-08-09
[quote=Mono FAQ]The Mono Project is an open development initiative sponsored by Novell to develop an open source, UNIX version of the Microsoft .NET development platform. Its objective is to enable UNIX developers to build and deploy cross-platform .NET Applications. The project implements various technologies developed by Microsoft that have now been submitted to the ECMA for standardization.[/quote]
Mono is not only for C#, but VB as well (and I believe the ASP projects can be written in either C# or VB, but I don't remember).  And yes, it is for Mac as well.

---

### Post by frustphil on 2009-08-09
Thank you..
I was about to compile my first code but, sadly, a [bug ]("http://ubuntuforums.org/Cannot%20open%20assembly%20%27/usr/lib/mono/1.0/mcs.exe%27")that struck me. Any workaround for this?

---

### Post by directhex on 2009-08-09
> **frustphil said:**
> Thank you..
I was about to compile my first code but, sadly, a [bug ]("http://ubuntuforums.org/Cannot%20open%20assembly%20%27/usr/lib/mono/1.0/mcs.exe%27")that struck me. Any workaround for this?

It's not a bug. Install mono-devel.

However, 1.0 is no longer supported in Jaunty+

Use the 2.0 profile (gmcs command) to compile .NET 2.0 apps

---

### Post by directhex on 2009-08-09
Thinking about it, mono-devel only Suggests: mono-1.0-devel, so if you're absolutely wedded to using 1.0, then install mono-1.0-devel

---


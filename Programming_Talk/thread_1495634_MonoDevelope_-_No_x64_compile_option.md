---
title: "MonoDevelope - No x64 compile option"
date: 2010-05-28
forum: Programming Talk
---

### Post by BrokenKingpin on 2010-05-28
I am running Ubuntu 10.04 x64 and I have installed MonoDevelope from the official Ubuntu repository. After writing a small C# console app I noticed in the top toolbar it said Debug|x86. When I go into the build properties I only have the option to compile for the x86 platform; I do not see an option for x64. This makes no sense because I am on an 64-bit system.

I also installed the MonoDevelope database, debug, and nunit packages, if that has any relevance.

---

### Post by soltanis on 2010-05-28
I was under the impression that Mono uses .NET, which is (supposedly) platform independent. However, a possible explanation is that you installed the 32-bit version of the compiler (which would still work on a 64-bit system, with some limitations, if you had the compatibility libraries installed), though obviously I have no idea what I'm talking about.

---

### Post by BrokenKingpin on 2011-06-24
The latest version has this resolved.

---


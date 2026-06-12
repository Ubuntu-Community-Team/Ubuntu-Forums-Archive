---
title: "How To Check C# Version In Ubuntu?"
date: 2011-05-05
forum: Programming Talk
---

### Post by etdsbastar on 2011-05-05
Hello there,

I have installed mono 10.05 in Natty. Now I want to check which C# version I am using. If older then how can I update the same?

Please help

---

### Post by directhex on 2011-05-05
There's no such version of Mono - the latest upstream is 2.10.2, and the latest Ubuntu package is 2.6.7

The C# version is defined by the compiler you use, which is part of Mono. The "gmcs" compiler does C# 3 (up to .NET 3.5), the "dmcs" compiler does C# 4 (from .NET 4). In Mono 2.6.7, "mcs" does C# 1 (.NET 1.1) - in versions 2.8 and higher the "mcs" command does the same as "gmcs"

---


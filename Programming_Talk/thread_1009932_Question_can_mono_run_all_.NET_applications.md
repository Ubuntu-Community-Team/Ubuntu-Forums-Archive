---
title: "Question: can mono run all .NET applications?"
date: 2008-12-13
forum: Programming Talk
---

### Post by thinhhoangdinh95 on 2008-12-13
Hi, I'm new to Mono and I'd like to ask you whether Mono can run all .NET applications. "All" here means Console applications and Winforms applications. I've been searching through the Internet but I couldn't find the answer. Thank you for helping me out.

---

### Post by directhex on 2008-12-13
"It depends" is the cop-out answer you didn't want to hear.

First factor: Is the app purely CLI? "Pure" in this case means "only uses .NET libraries", as opposed to using P/Invoke to call methods in platform-specific C libraries. An app which is pure CLI is likely to work, an app which P/Invokes things in c:\windows\system32\ is rather less likely to work (unless you can reverse-engineer a 100% compatible replacement .so file)

Second factor: Is the app badly written? One of the main examples here is stuff like reading values from the Registry (and crashing if they don't exist), or using file paths (e.g. if someone uses code like 'path1 + "\" + path2' instead of 'System.IO.Path.Combine( path1, path2 );'). You can usually work around this kind of cock-up, but it;s highly irritating

Third factor: Does the app use closed, Microsoft-only libraries which don't make sense outside Windows? Or things from .NET 3.5? These have no Mono equivalents, and might never

The thing to remember is that Mono wasn't actually written with the ability to run Windows apps as a design goal - it's a nice secondary goal. but Mono was written to facilitate writing apps on *nix. Oh, and the most recent Mono you can get ahold of is always more likely to work than an old one.

---

### Post by Delever on 2008-12-13
Yes, 

Basic rules (in my knowledge): 

If library or application uses native libraries directly or indirectly, it won't work (what directhex said). One call to windows API is enough to make it fail on mono, for example, drawing splash screen in fancy way, or checking if same instance of program is already running.

Some part of API is still not implemented in mono, like some overloaded methods of Socket class (saw that half a year ago).

---

### Post by thinhhoangdinh95 on 2008-12-13
Thank you for your help. But one more question I'd like to ask: how can I develop an application for Ubuntu? I love Ubuntu, but I've been working on C# for 6 years and I don't want to leave it.

---

### Post by Tomosaur on 2008-12-13
> **thinhhoangdinh95 said:**
> Thank you for your help. But one more question I'd like to ask: how can I develop an application for Ubuntu? I love Ubuntu, but I've been working on C# for 6 years and I don't want to leave it.

Look into [Monodevelop](http://monodevelop.com/Main_Page), it's a C# IDE for developing applications using Mono.

There are probably C# / Mono plugins for Eclipse too (possibly the most popular of the open-source IDEs).

---

### Post by directhex on 2008-12-14
A plus point for MonoDevelop is it has an integrated GUI designer, for making GTK# apps

---

### Post by thinhhoangdinh95 on 2008-12-15
That sounds interested. I'll give MonoDevelop a try. Thanks.

---


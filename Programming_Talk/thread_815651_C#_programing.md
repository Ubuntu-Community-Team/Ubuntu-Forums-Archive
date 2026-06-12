---
title: "C# programing ?"
date: 2008-06-01
forum: Programming Talk
---

### Post by Browser_ice on 2008-06-01
Can I do C# programming in Ubuntu 7.10 ?

What do I need to manage/modify source code and compile it ?


[added comments]
Humm, that is odd. When I tried a forum search on 'c#' it found nothing. But when I do it with google+c#+ubuntu, I am finding  Ubuntu forum threads. Looking at them now ...

---

### Post by LaRoza on 2008-06-01
You need mono and mcs.

```

~$cat p.cs
class Hello
{
    static void Main()
    {
        System.Console.Write("Hello world\n\a"); 
    }
}
~$mcs p.cs
~$mono p.exe
Hello world
~$

```

---

### Post by Browser_ice on 2008-06-01
I have mono installed since I need it to start OpenSim. But mcs.... don't think so.

I read something about monodevelop.  Does it have a C# source editor ? If not, where can I find one for Ubuntu 7.10 ?

---

### Post by LaRoza on 2008-06-01
> **Browser_ice said:**
> I have mono installed since I need it to start OpenSim. But mcs.... don't think so.

I read something about monodevelop.  Does it have a C# source editor ? If not, where can I find one for Ubuntu 7.10 ?
```

~$search mcs | grep "compiler"
mono-gmcs - Mono C# 2.0 and C# 3.0 compiler for CLI 2.0
mono-mcs - Mono C# compiler for CLI 1.1
mono-smcs - Mono C# 3.0 compiler for CLI 2.1 (Moonlight / Silverlight)
~$

```

(Don't mind my alias for apt-cache search)

Run:

```

sudo apt-get update && sudo aptitude install mcs

```

And run as I showed above to test it out. 

Monodevelop is a big IDE: [http://www.monodevelop.com/Main_Page](http://www.monodevelop.com/Main_Page)

It may be something you are interested in, I don't use IDE's like that. I used Vim to write that code.

(All of this is in the repos)

---

### Post by Majorix on 2008-06-02
MonoDevelop is what you might be looking for. You can develop C# (and VB) on it, in a graphical environment, for a graphical environment.

---

### Post by LaRoza on 2008-06-02
> **Majorix said:**
> MonoDevelop is what you might be looking for. You can develop C# (and VB) on it, in a graphical environment, for a graphical environment.

It might be, but it isn't what the question was about. 

I think that is a problem with the VS crowd, they mistake tools for each other.

---

### Post by emarti on 2008-07-08
According to me, MonoDevelop is the best IDE for C# programming on Linux.

---

### Post by Sukarn on 2008-07-09
Well, monodevelop could have been better. I don't like the fact that single .cs files can't be set to run in an external terminal.

I like the ability to compile with a hotkey (F7) and the ability to quickly jump to an enum, struct, namespace, etc. to check or change something.

The upcoming version 2.0 will have code-collapsing, something that I think I would like. I liked this feature in Dev-C++ when I was programming on Windows. This is what originally got me into an IDE. Well, that and the chance of getting away from Turbo-C++.

As much as Turbo-C++ is supposed to be (although very old) an IDE, I hate it completely.

My school used to force us to use Turbo-C++ (ugh), but that was because Turbo-C++ was in our education board's computer science course.

I think I'm getting slightly offtopic, so I'll stop here.

---


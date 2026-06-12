---
title: "Learning VB .NET at school, Mono questions"
date: 2010-08-31
forum: Programming Talk
---

### Post by jerome1232 on 2010-08-31
I'm currently learning VB .NET at school, using Visual Studio 2003 in a virtual machine for the class. We just started haven't jumped into the guts of it yet.

The only other programing experience I have is limited Python and cobol, and of course basic I learned in high school.

I was just wondering if I could follow along writing programs in mono as well, how much modification would it take to make gtk apps in mono as something to learn on the side?

---

### Post by mendhak on 2010-08-31
Depends on what areas you'll be exploring.  If it's basic concepts (you know, looping, data structures, etc), then you should be OK.  If it's windows forms/GUI or ASP.NET, then I'd suggest you use the VM with VS 2003 as there will be gotchas related to winforms and webforms that make the course go a certain way.  Once you're familiar with those concepts, transitioning to Mono won't be so tough.

Also, there may be a versioning problem - Mono is currently near .NET 2.0/3.5, which is very different to 1.1 (VS 2003), you're missing Linq and Generics.

---

### Post by jerome1232 on 2010-09-02
In the class we will be developing gui desktop apps, using winforms, so I was planning on using visual studio for the class, I was more or less wondering if it would be alot of extra work to "port" the programs I make for class over to mono just to learn a bit about gtk and mono on my own.

I think from what you said it would be a bit difficult for someone who is just learning the language (going between versions and etc...)

---

### Post by phrostbyte on 2010-09-02
VB.NET support in Mono is pretty poor. The focus is on C#.

---


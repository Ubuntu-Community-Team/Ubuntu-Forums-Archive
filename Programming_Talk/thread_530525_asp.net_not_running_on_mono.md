---
title: "asp.net not running on mono"
date: 2007-08-20
forum: Programming Talk
---

### Post by rapolas on 2007-08-20
So I open a monodevelop, creating a new asp.net web app and without touching any source file I try to run, and I'm getting and error. Does anybody knows how to run it? I tried both with c# and vb, the same. I believe somebody gonna tell me to use java or php ar ruby, but that stuff I need to learn for my job.. And I hate running windows on virtual pc..

---

### Post by pmasiar on 2007-08-20
No, I am going to tell you: if you **absolutely have to** develop for ASP.NET, the smartest way to do it exactly like all other ASP.NET developers do it: under windows. So you are not standing alone when facing obscure bug.

Unless, of course, you have drive, time and skills to become expert on running ASP.NET  under non-traditional cicrumstances, and maybe write a book about it.

Or try to find another project/job, where you can use open-source technologies in their native environment.  Look at IronPython, for example - it is open-source project released by Microsoft.

---

### Post by skeeterbug on 2007-08-20
> **rapolas said:**
> So I open a monodevelop, creating a new asp.net web app and without touching any source file I try to run, and I'm getting and error. Does anybody knows how to run it? I tried both with c# and vb, the same. I believe somebody gonna tell me to use java or php ar ruby, but that stuff I need to learn for my job.. And I hate running windows on virtual pc..

Your job should supply you with Visual Studio and a computer than runs Windows if that is what you are going to be targeting. We have multiple products here that run on C#, ASP.NET 2.0. I would never ever think about trying to write it under monodevelop, especially considering we work collaboratively via SVN. Use a VM, or dual boot. It will only get worse as you start adding in third party libraries you need to include.

---

### Post by rapolas on 2007-08-21
> **skeeterbug said:**
> Your job should supply you with Visual Studio and a computer than runs Windows if that is what you are going to be targeting.
My job does that, but I want to learn better and wanna try something at home.. anyway, thanks for the answers:) Probably I will use virtual pc for that..:)

---

### Post by Dragonbite on 2007-08-28
Are you using Apache or XSP for the server-side?  I haven't done much with ASP.NET in Monodevelop so I'm uncertain how it works.

[[COLOR="Blue"]Visual Studio Express[/COLOR]]("http://msdn2.microsoft.com/en-us/express/default.aspx") is a free version of Visual Studio. Not sure what language the Web Developer component uses or if you have a choice.

---

### Post by emperon on 2007-08-30
It works fully. I am doing large ASP.NET applications on mono.

---

### Post by kiv on 2007-08-30
> **emperon said:**
> It works fully. I am doing large ASP.NET applications on mono.

im going to uni in a month to study computing - we will be using C# in visual studio.

Is it possible to do windows object orientated programming using mono?

I dnt really want to get rid of ubuntu or dualboot or even bother with a virtual machine. This is because as much as I love ubuntu I don't see the logic in running ubuntu and windows when im oging to be using windows everyday.

---

### Post by emperon on 2007-08-31
I don't know what do you mean by windows object oriented programming.
All I can say C# 2.0 is 100% percent implemented. C# 3.0 is implemented except LINQ. Windows Forms 1.1 is 100% percent implemented. Windows Forms 2.0 is mostly implemented.

So using mono is a safe bet. You can also use windows applications directly on linux without recompiling or vice versa.

---

### Post by skeeterbug on 2007-08-31
> **emperon said:**
> I don't know what do you mean by windows object oriented programming.
All I can say C# 2.0 is 100% percent implemented. C# 3.0 is implemented except LINQ. Windows Forms 1.1 is 100% percent implemented. Windows Forms 2.0 is mostly implemented.

So using mono is a safe bet. You can also use windows applications directly on linux without recompiling or vice versa.

Not to be rude or anything, but it doesn't work out so well with larger applications. Have you tried configuring mono stuff on a Mac? Yuck. We were going to port our winforms application to mono here. It turned out the time investment wasn't worth it. No, it didn't just "run" on linux without re-compiling, sadly.

It seems like a great platform to play around with on the weekends. Honestly though, I can't  see many development shops willing to spend the extra time and effort to build applications on it.

---

### Post by rapolas on 2007-09-01
I have no idea how it's working on yours computers, but on mine, simple hello world, that comes with new project, doesn't compile.. I didn't make any change to whats come when you create a new project, and it's not compiling. With windows gui programs, everything fine, but not with asp.net web page..

---

### Post by emperon on 2007-09-01
> **skeeterbug said:**
> Not to be rude or anything, but it doesn't work out so well with larger applications. Have you tried configuring mono stuff on a Mac?
.
No I tried not. I care not. This is a linux form and I know it works fine on linux and windows.

> 
 Yuck. We were going to port our winforms application to mono here. It turned out the time investment wasn't worth it. No, it didn't just "run" on linux without re-compiling, sadly.


Winforms 2.0 support is not  complete. But other than that everything else is working smoothly and with a true cross platform manner.

Examples: ?

NHibernate, db4o, nunit (both with winforms gui), Castle Windsor, log4net, Rhino Mocks, Reflector (with painting glitches)

Those applications/frameworks are very complex and designed only for Ms.net and yet it works

---

### Post by emperon on 2007-09-01
> **rapolas said:**
> I have no idea how it's working on yours computers, but on mine, simple hello world, that comes with new project, doesn't compile.. I didn't make any change to whats come when you create a new project, and it's not compiling. With windows gui programs, everything fine, but not with asp.net web page..

Dude it works. I think you are talking about MonoDevelop's generated code. MonoDevelop is still 0.15th version. So do not rely on the code it generates.
As long as you type valid ASP.NET it WILL work.
[http://ajaxtoolkit.tophostingteam.de/]("http://ajaxtoolkit.tophostingteam.de/")

The above site runs on mono/linux. As you can see it can even run Ajax control tool kit. (Not 100% functional)

But asp.net is there 100% except web parts

---


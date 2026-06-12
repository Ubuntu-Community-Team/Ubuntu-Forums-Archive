---
title: "Looking for an IDE to view VB Code"
date: 2010-01-19
forum: Programming Talk
---

### Post by PatrickD-52761 on 2010-01-19
Hi everyone,

    I know this has been asked sort of before.  Here's my situation.  I'm moving over to Kubuntu (starting out for a week and maybe longer).  One issue that I have is that I tutor at my local college, and one of the courses they teach is Visual Basic.

    I shouldn't have to compile anything, but I do need an IDE that will allow me to look at their code and help find bugs.  If worse comes to worse, I could fire up a VM that has Windows XP installed in it...  But, for this first week, I'm trying to go completely Open Source and Microsoft free.  It's more for a test than anything else.

    So, any ideas for how I can solve this will be greatly appreciated.  As far as my college courses go, they're using Java, so I can deal with that already.

Thanks for any input, and have a great day:)
Patrick.

---

### Post by wmcbrine on 2010-01-19
Well, you don't need an IDE just to view code. It's plain text.

---

### Post by tinny on 2010-01-19
I think MonoDevelop supports VB syntax.

[http://monodevelop.com/]("http://monodevelop.com/")

---

### Post by WitchCraft on 2010-01-19
> **tinny said:**
> I think MonoDevelop supports VB syntax.

[http://monodevelop.com/]("http://monodevelop.com/")

For VB.net there's monodevelop. By default, monodevelop comes only with C# runtime&compiler. You need to install the vbnc yourself with apt-get. Not a problem, though.

As for VB 6, it's more difficult. I think kbasic is the best i've seen there. [http://www.kbasic.de/](http://www.kbasic.de/)

You need to be aware that while mono is quite good, there are some incompatibilities (bugs), especially with XML reading/writing.

---

### Post by PatrickD-52761 on 2010-01-19
Thank you WitchCraft and tinny for the monodevelop information.  I checked it out, and it looks promising.  They're learning on either Visual Basic 2005 or 2008-- I'm not entirely sure right now.

Either way, this definitely increases the chances that I'll stay on Kubuntu longer than a week. :D

Have a great day:)
Patrick.

---

### Post by WitchCraft on 2010-01-23
> **PatrickD-52761 said:**
> Thank you WitchCraft and tinny for the monodevelop information.  I checked it out, and it looks promising.  They're learning on either Visual Basic 2005 or 2008-- I'm not entirely sure right now.

Either way, this definitely increases the chances that I'll stay on Kubuntu longer than a week. :D

Have a great day:)
Patrick.

I caution you: While mono can run most VB project (sometimes you need to make some/minor corrections), developing with monodevelop is another thing. I've just looked more closely into monodevelop, since I saw on my arch linux that I can develop MVC applications, and C# asp.net, on ubuntu you can't. That's because arch has a more up to date version of mono+monodevelop.

And you can't really develop WinForms projects with monodevelop. As long as you do ASP.net, everything is fine, but having to change a WinForms application might get you into trouble.

Also, it's slow, so if I was you, I'd prepare that visual studio in VirtualBox. 

PS: Visual Studio 2010 Ultimate beta and .net framework 4.0 is out.
Grab it while you can, it's free !!!
 (mono runs on the 2.0 framework, 3.5 in the working)

(expect some bugs,though).

---


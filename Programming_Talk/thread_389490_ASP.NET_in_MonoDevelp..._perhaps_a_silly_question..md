---
title: "ASP.NET in MonoDevelp... perhaps a silly question."
date: 2007-03-20
forum: Programming Talk
---

### Post by cunawarit on 2007-03-20
I'm running Xubuntu 6.10 with MonoDevelop 0.12.

Where is the ASP.NET/Website project type in MonoDevelop?

---

### Post by cunawarit on 2007-03-21
Sorry to bump this... I&#8217;ve used MonoDevelop 0.13 before on a different machine and I think the ASP.NET project type is under C#, after clicking the little drop down arrow. It isn&#8217;t there on MonoDevelop 1.2 under Xubuntu 6.10.

SharpDevelop (on Windows and where MonoDevelop forked from if I am not mistaken) has it in the same place&#8230;

Is it an add in? Has it been removed? Am I missing something obvious? Is it not there in 0.12? I thought it was!

Sorry to be a pest.

---

### Post by cunawarit on 2007-03-21
Sorry to answer myself again, but just for future reference in case anyone is interested&#8230;

Feisty fawn does come with a version of monodevelop 1.2 that has ASP.NET support. 
[http://packages.ubuntu.com/feisty/devel/monodevelop](http://packages.ubuntu.com/feisty/devel/monodevelop)

Edgy comes with monodevelop 0.12 as well, but without ASP.NET support. 
[http://packages.ubuntu.com/edgy/devel/monodevelop](http://packages.ubuntu.com/edgy/devel/monodevelop)

PS: If anyone knows why this is, please do let me know...

---

### Post by JoxBG on 2007-03-22
Thanks for the info. Now i have to install Feisty...

---

### Post by mikalh on 2007-03-29
MonoDevelop 0.12 was the first release with ASP.NET support, but it's an optional AddIn, so it's up to the packagers whether it's built or not. MonoDevelop's ASP.NET support is completely independent from #D BTW, but the ASP.NET project type should appear as a child category of C# and any other supported .NET language.

MonoDevelop 0.13 has more stable ASP.NET support, except for one breaking bug, which is fixed in 0.13.1. The ASP.NET Visual Designer is almost stable in SVN, though nowhere near feature-complete.

---

### Post by cunawarit on 2007-03-29
Thanks for the reply mikalh :) That's very useful!

---

### Post by gh0st on 2007-03-29
I am still using Visual Studio on VMWare for my ASP.NET apps at the moment but I am definately going to look into using MonoDevelop as it's the only thing I still need Windows for :( 

That information is really useful thanks, I was just wondering how MonoDevelop compares to Visual Studio for VB.Net development? What do people think of it? I'm not expecting it to be a direct replacement for Visual Studio I know they are different products.

Does anyone have any tips for a VB.NET developer who's learn't all his bad habits from Visual Studio? :) ;) 

Thanks folks. I did think of starting a new thread for this but it seemed this question was relevent enough to post here.

---

### Post by pmasiar on 2007-03-29
> **gh0st said:**
> Does anyone have any tips for a VB.NET developer who's learn't all his bad habits from Visual Studio? .

What about this one: switch to different language? :-)

You knew that one is coming right :-)

---

### Post by gh0st on 2007-03-29
> **pmasiar said:**
> What about this one: switch to different language? :-)

You knew that one is coming right :-)

Yeah I should have realized someone was gonna say that :) 

Good news I already did that anyway. I develop in loads of different languages. I started out in Java at University, then worked for a hospital which was a Microsoft partner and got pushed into the .NET framework, I actually really enjoyed ASP.NET though I found it very powerful and quite nice to use. Nowadays it's mostly Python for me, I am building some stuff in Django at the moment and thats really cool as a web platform.

Problem is I got old ASP.NET apps that I have to maintain and there's no way I can justify rewriting them just to change the language. I don't touch them very often but every now and then I get a call to change something trivial and have to fire up VMWare to get into Visual Studio. I know I could edit the source files with a plain text editor if needed but I'm not that crazy :) 

I just wondered if I could use MonoDevelop to perform these tasks and save booting a Windows VM. I know you're a Python enthusiast pmasiar and I'm right with you on that. Just gotta keep my previous work in order, you know how it is.

I was wondering what people thought of MonoDevelop in comparison to Visual Studio really? Thats all :-k

---

### Post by pmasiar on 2007-03-29
You earned double brownie point for using Python instead of VBasic :-) At recent task I needed to fix something quickly in ASP.NET and VB, and I was astonished how many reserved words VB.NET has. It was couple of pages, couple hundreds of them! Ridiculous. Anyway...

If you know your ways around VS, and do not plan to use MonoDevelop for anything else, I would be reluctant spending time to learning another big tricky IDE (monodevelop) if you know VS. 

My approach is to use simple tools if possible, and select carefully if forced to use complicated tools - it may take long time to know how to use them profficiently. IMHO is better to know couple tools (hopefully complementary to each other) and be reasonably profficient with them, than to be at beginner level in many overlapping tools.

---

### Post by gh0st on 2007-03-29
Yeah I suppose you're right. I think the language is more important than the tools. I found when I started using VB.NET that it was really easy to do stuff in Visual Studio quickly but then when it came to working out how it worked I was lost, I needed to learn the language. You find that with a lot of big IDE packages, the first one I ever used was JBuilder and I didn't have a clue what it was doing most of the time :) 

Using a big IDE is fine and sometimes saves time but it helps if you understand what it's doing behind the scenes I think. I might still install MonoDevelop and have a play with it though, I just like tinkering with new things. Jack of all trades master of none as they say :) 

When it comes to Python I use gedit mostly, it does the job quite nicely. Since you can do a lot with a small amount of code in Python it's no hardship to work on it in a basic text editor. Thats down to the design of the language I think. Even IDLE has enough features to get most tasks done. I do occasionally use SPE as well and I find that quite good.

I suppose I'll stick to VS for editing my old .NET apps for now then. Thanks for the advice :-)

---

### Post by mardawi on 2007-04-03
> **gh0st said:**
> 
I was wondering what people thought of MonoDevelop in comparison to Visual Studio really? Thats all :-k

MonoDevelop is way behind Visual Studio!

---

### Post by gh0st on 2007-04-03
Thanks for the reply. I know MonoDevelop is still in relatively early stages of it's evolution. I will try my best to support it though because I like the philosophy behind it. I remember reading when the .NET framework was first released that it would be a cross platform development environment like Java eventually, a few years ago I went on an official Microsoft training course and was told the same thing by our trainer, how I laughed ;) As if Microsoft wants people developing .NET apps on anything but Windows. It's good to see that Mono is now a real option and I hope it will continue to grow in strength.

I'll have to keep checking out MonoDevelop with each release until I feel comfortable switching completely. What a great day that will be :)

---


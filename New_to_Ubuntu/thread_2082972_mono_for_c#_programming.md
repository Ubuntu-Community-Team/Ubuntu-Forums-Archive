---
title: "mono for c# programming"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by fr33c0untry on 2012-11-11
i've heard about the software mono being able to access the .net framework to allow linux users to compile c# programs.is it any different from visual studio?and is learning c# useful for open source programmers in the long run.

---

### Post by newb85 on 2012-11-11
I'm not really a programmer, so I'm a bit out of my realm, but here are the thoughts your questions provoked.
[list]
[*]Visual Studio is an Integrated Development Environment.  I don't think Mono is.
[*][s]C# is a proprietary language.  For an open-source programmer, there are probably more useful languages to learn.[/s]
[/list]

---

### Post by directhex on 2012-11-11
> **newb85 said:**
> [list][*]C# is a proprietary language.
[/list]

I'm not sure you know what that word means. C# is a standardized language - both an ISO and ECMA specification

---

### Post by directhex on 2012-11-11
> **fr33c0untry said:**
> i've heard about the software mono being able to access the .net framework to allow linux users to compile c# programs.is it any different from visual studio?and is learning c# useful for open source programmers in the long run.

Mono is just the framework - compiler, class library, and runtime.

MonoDevelop provides an IDE similar to SharpDevelop on Windows.

---

### Post by newb85 on 2012-11-11
> **directhex said:**
> I'm not sure you know what that word means. C# is a standardized language - both an ISO and ECMA specification

Proprietary?  Yes, I do know what it means.  However, it seems I was misinformed about the current state of the language.  It was designed by Microsoft.  Apparently, that doesn't make a language proprietary.

As I said, I'm a little out of my realm.  Sorry.

---

### Post by lukew on 2012-11-16
The parts which make up C# & .NET ( CLS, CTS & CLR ) are all open standards. MS have openly ask for other languages and platforms to implement to these standards to diversify the spread of .NET right from the start. The standards ave been submitted and accepted by [Ecma]("http://en.wikipedia.org/wiki/Ecma").  The list of languages which can implement .NET is incredible: [http://en.wikipedia.org/wiki/List_of_CLI_languages]("http://en.wikipedia.org/wiki/List_of_CLI_languages")

It is true that .NET is not FOSS but to say it is a propriety language when mono and DotGNU exist are proof that the standards submitted to Ecma are in place to encourage open adoption of .NET.

Mono is the .net compiler (using CLS), the CTS, CLR and base libraries which any .net code needs to compile and run. Monodevelop is a IDE or Integrated Development Environment. You could use a simple text editor though an IDE provides not only intellisense, syntax highlighting but also other tools like database integration, refractoring tools, unit testing functionality, code analytic and many many more.

Over the last 7 or 8 years I have on and off tried monodevelop and codign in c#. I have even taken some of that code into production environments but this was a long time ago and also was a get started exercise before vinishing off in windows and VS. Having downloaded monodevelop and mono recently i was amazed at how far it has come.

Mono & Monodevelop now support .NET runtimes up to and including .net 4.5. It supports C#5, MVC3, I think Razor viewengine. Though I have only been testing the water I have not had any issues so far. The most noticable were a few MVC HTML helper extension methods missing. This includes throwing as much generics and Linq at it as I can and also Entity is also now supported. 

The extensability of .net under linux is huge. MySQL, Oracle & Sqllite all have ADO.NET Data providers allowing agnostic access database access. I have used ninject, and rhinomocks .net dlls without any hitch proving that .net is pretty much a system agnostic development and runtime and environment.

I understand that people under Linux are scared of MS though if you look at the MS acceptance of how bad ASP.NET Web Forms was as a technology, how right Ruby was and how now they have embraced MVC developing an fully open source and extensible ASP.NET MVC framework MS are clearly making steps in the right direction.

I have a blog about my .NET exploits under Linux which you might like to read. These are not for newbie programmers but .net developers who want to progress their development skills in a linux environment.  BTW I use solely MS at work and solely Linux at home. The closest i come to Linux at home is XP on Virtual box and that is only because remoting into work on a Java client is too painful. Hard fact to learn in life now matter what your choices are you need to work where the jobs. I don't know many Linux fans who openly refuse to work in any companies which use MS products.

You can read my blog here [http://lukewickstead.wordpress.com](http://lukewickstead.wordpress.com)

Ohh and no I don't work for MS nor do I want code in their platforms however I have to on a daily basis. Mono and Monodevelop allow me to progress the skills I need in my job inside Linux which makes me happy and to me above all the reason why I use and love Linux the main one is that it is right for me and makes me happy.

---

### Post by idoitprone on 2012-11-16
I am not a C# developer so i cannot give a better answer than the poster above

Here is the website for compatibility status

[http://www.mono-project.com/Compatibility](http://www.mono-project.com/Compatibility)

I not sure of the status for mono, but crazy richard stallmen always called the head developer a microsoft apologist
[http://www.osnews.com/story/22225/RMS_De_Icaza_Traitor_to_Free_Software_Community/](http://www.osnews.com/story/22225/RMS_De_Icaza_Traitor_to_Free_Software_Community/)
[http://en.wikipedia.org/wiki/Miguel_de_Icaza](http://en.wikipedia.org/wiki/Miguel_de_Icaza)
[http://www.tirania.org/blog/](http://www.tirania.org/blog/)

---

### Post by lukew on 2012-11-17
> **idoitprone said:**
> I am not a C# developer so i cannot give a better answer than the poster above

Here is the website for compatibility status

[http://www.mono-project.com/Compatibility](http://www.mono-project.com/Compatibility)

I not sure of the status for mono, but crazy richard stallmen always called the head developer a microsoft apologist
[http://www.osnews.com/story/22225/RMS_De_Icaza_Traitor_to_Free_Software_Community/](http://www.osnews.com/story/22225/RMS_De_Icaza_Traitor_to_Free_Software_Community/)
[http://en.wikipedia.org/wiki/Miguel_de_Icaza](http://en.wikipedia.org/wiki/Miguel_de_Icaza)
[http://www.tirania.org/blog/](http://www.tirania.org/blog/)

:D thanks for the links, the mono compatibility one is very useful.

Just to put things into perspective. I am not saying everyone should rush out, download and start coding Linux in .net. I am just saying there is a good career path to be made with .net due to the volume of jobs especially in ASP.NET, MVC & WCF and you can learn these skills and potentially write production code in these technologies on Linux. 

However if you are a newbie programmer then starting off in Python or Perl could also be a good starting point. Every language has the basic constructs and API call. All skills you learn in one language would be useful in all others.

---

### Post by idoitprone on 2012-11-17
> **lukew said:**
> :D thanks for the links, the mono compatibility one is very useful.

Just to put things into perspective. I am not saying everyone should rush out, download and start coding Linux in .net. I am just saying there is a good career path to be made with .net due to the volume of jobs especially in ASP.NET, MVC & WCF and you can learn these skills and potentially write production code in these technologies on Linux. 

However if you are a newbie programmer then starting off in Python or Perl could also be a good starting point. Every language has the basic constructs and API call. All skills you learn in one language would be useful in all others.
Many distro have .net installed since programs such as banshee i believe uses c#

---

### Post by newb85 on 2012-11-17
> **idoitprone said:**
> ...since programs such as banshee i believe uses c#

Indeed, banshee uses mono.  I recall hearing that was one of the reasons Canonical dropped banshee for rhythmbox, but then, I didn't specifically hear that reason from Canonical, and I know there were a few more practical reasons for dropping it.  So, mono may have had nothing to do with that decision.

---


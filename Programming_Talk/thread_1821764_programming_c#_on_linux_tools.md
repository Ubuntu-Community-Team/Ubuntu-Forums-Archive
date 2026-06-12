---
title: "programming c# on linux tools"
date: 2011-08-09
forum: Programming Talk
---

### Post by Drenriza on 2011-08-09
Hi all.
What tools are available on Linux for programming c# asp.net with some debugging tools, e.c.t. At the moment i am using Microsoft visual studio but dual booting is a pain in the butt. So if anyone know something i can use, i am all ears :p

Kind regards.

---

### Post by karlson on 2011-08-09
> **Drenriza said:**
> Hi all.
What tools are available on Linux for programming c# asp.net with some debugging tools, e.c.t. At the moment i am using Microsoft visual studio but dual booting is a pain in the butt. So if anyone know something i can use, i am all ears :p

Kind regards.

Have you tried Mono?

---

### Post by cgroza on 2011-08-09
Monodevelop is a good IDE for this language.

---

### Post by etdsbastar on 2011-08-09
I completely suggest MonoDevelop which is available through repositories.

---

### Post by ve4cib on 2011-08-09
MonoDevelop is about the only choice for doing C# on Linux.  Unfortunately Mono is not 100% compatible with the latest version of .NET (it's usually 1-2 versions behind in my experience), and I'm not sure how much work has been done on MonoDevelop's debugger yet.  Last time I used it the debugger had not been implemented at all yet.  But that was several months ago, so I imagine things have gotten better since then.  But barring those two drawbacks (one of which may not be an issue for you, and the other which may have been resolved by this point), it's a very nice IDE to use.

---

### Post by directhex on 2011-08-09
> **Drenriza said:**
> Hi all.
What tools are available on Linux for programming c# asp.net with some debugging tools, e.c.t. At the moment i am using Microsoft visual studio but dual booting is a pain in the butt. So if anyone know something i can use, i am all ears :p

Kind regards.

MonoDevelop is the main Free Software IDE for C#, but the ASP.NET addin is a little basic. On the bright side, we ship ASP.NET MVC and MVC 2 in Ubuntu, if that helps.

---

### Post by migren_teh on 2011-08-22
[SIZE=2]I can find toolbox in monodevelop but I can't find "[COLOR=Red]design mode[/COLOR]" to drag a button or a textbox or something like that on it. it drives me crazy. can anybody help me? please... :((
[/SIZE]

---

### Post by directhex on 2011-08-22
> **migren_teh said:**
> [SIZE=2]I can find toolbox in monodevelop but I can't find "[COLOR=Red]design mode[/COLOR]" to drag a button or a textbox or something like that on it. it drives me crazy. can anybody help me? please... :((
[/SIZE]

There is only a designer for C# GTK# apps - nobody has contributed a designer for other types of app.

---


---
title: "Run asp and .net on Ubuntu Guide"
date: 2007-06-11
forum: Programming Talk
---

### Post by warcriminal on 2007-06-11
Here is a tutorial with screenshots on how to get asp and .net applications running on your ubuntu install.

[http://www.goitexpert.com/entry.cfm?entry=Run-ASP-and-NET-in-UBUNTU--and-Debian-LINUX](http://www.goitexpert.com/entry.cfm?entry=Run-ASP-and-NET-in-UBUNTU--and-Debian-LINUX)

---

### Post by cunawarit on 2007-06-11
Cool :) 

XSP is a neat little asp.net server that simply just works, very useful for development. It is the open source equivalent of Microsoft's "ASP.NET Development Server" that comes with Visual Studio 2005. 

I have never used it, but you can host asp.net apps in Apache with mod_mono... 

As for MonoDevelop, you can do ASP.NET (Why not ASP.MONO?) projects on it now too, I personally think Visual Web Developer 2005 Express is a better bet if you have a Windows machine and need a gratis IDE. But there's no denying that MonoDevelop is impresively capable considering it is only on version 0.13.1. I can't wait till version 1!!!

---

### Post by RipHamilton on 2008-03-21
Hi,
Ive been reading some comments in this forum and somewhere else, but Ive figured out that too many people make the confusion between ASP and ASP.NET. An ASP file has ".asp" as extension, but an ASP.NET file has ".aspx" as extension, just to name one difference. Im trying to create some ASP Web pages using SXP/XSP2, but it doesnt work. Though, it works perfectly with ASPX files. Please, let me know whether there is any way to work with ASP files on Ubuntu. Thanks in advance.

Kind Regards,

---

### Post by psylo on 2008-03-21
definitely been having some problems getting mod_mono to run with apache - though XSP works fine on its own.

RipHamilton > Use ChilliASP under Apache and you can run most of the standard ASP stuff.

Cheers
AndrewF

---

### Post by roan_br on 2008-04-25
ChilliSoft works under Ubuntu?

---

### Post by clasificado on 2008-04-25
> **roan_br said:**
> ChilliSoft works under Ubuntu?

Well... yes. 

But classic Asp programmers relies a lot of Activex and compiled COM dlls and, afaik, Chillisoft version desnt support activex.

clasificado

---

### Post by martinopresnik on 2011-08-01
I had a lot problems with this & all i did wrong was that I didn't know how to use XSP (stupid me). All you have to do after installation is Change Directory where you have .aspx app and enter xsp2/xsp command.

---


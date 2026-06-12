---
title: "Visual Basic Alternative"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by dharmvir tiwari on 2012-09-30
Is there any alternative for VIsual Basic in Ubuntu or can we run VB in Ubuntu as well:KS

---

### Post by rai4shu2 on 2012-09-30
I think you can do some VB stuff in Mono.

---

### Post by Lars Noodén on 2012-09-30
You've got perl, python and javascript instead.  

If you're looking to write macros for LibreOffice / OpenOffice, you can use [python](http://wiki.openoffice.org/wiki/Python_as_a_macro_language) or javascript.

---

### Post by HermanAB on 2012-09-30
Perl with Glade are my favourites.

---

### Post by The Cog on 2012-09-30
I've never looked at it, but I have read that gambas is rather like vb.

---

### Post by dharmvir tiwari on 2012-09-30
> **rai4shu2 said:**
> I think you can do some VB stuff in Mono.
Does Mono provides it?

---

### Post by Lars Noodén on 2012-09-30
I would avoid mono and work with the standard material instead.

---

### Post by dude123dude on 2012-09-30
1. Avoid MONO at all costs. 
Reason 1: Its incomplete Microsoft .NET clone, missing many proprietary "features". 
Reason 2: Its unofficial.
Reason 3: Microsoft still holds whole patent portfolio. One word from MS and all stack is affected.
Reason 4: .NET is the technology, which is used by Microsoft to "[infect]("http://en.wikipedia.org/wiki/Embrace,_extend_and_extinguish")" platforms such as Android and ARM. By using MONO you directly helping widespread its usage.
Reason 5: There are plenty of good tools that do the job better, are patent-free, are complete, and are not owned by company which set its goal to stop linux or sue everyone who use it to pay "microsoft tax".

2. You are looking at GAMBAS, DarkBasic(proprietary) or (very advanced, but not VB) Lazarus. More advanced alternatives will be Guile or QT-Creator paared with Cpp.

3. You can run VB in Ubuntu, however it is not native. By using Wine(free implementation of Winapi) with VB Runtimes preinstalled (using Winetricks or PlayOnLinux).
This method is however the most cumbersome (after setting separate VM, ofc), however it is legal and MS-"stuff" is held in a separate "box".

---

### Post by directhex on 2012-09-30
> **dharmvir tiwari said:**
> Does Mono provides it?

Mono includes a VB.NET compiler, in the [mono-vbnc](apt:mono-vbnc) package. There is no sophisticated IDE integration, however, e.g. MonoDevelop does not include a GUI designer for VB.NET projects (only for C# projects).

Gambas is an environment which is very VB6-like, although may have differences since it isn't *actually* VB. Chances are it's the most comfortable fit for an experienced VB6 developer.

---

### Post by rai4shu2 on 2012-09-30
Suffice it to say that there are compelling reasons for a developer who makes a living on their coding to avoid Mono (unless you happen to work at Microsoft or EA, of course), but just be aware that Microsoft has been very busy spreading FUD about BASIC, and doing their best to discourage developers from using VB.

---

### Post by DaGeek247 on 2012-09-30
I used to use VB6 on windows XP, then I found linux and wanted it to develop my project there. It didn't work out. I know dude123dude said the VB works in wine using winetricks, and while its been awhile, I know that VB6 did not work with wine. And even if you got vb running in wine, the programs made in it would only be compatible with windows.

Also, what version of VB? I know vb.net is REALLY different from VB6.

Lastly, while gambas is a good and similar program to VB6, I don't recommend it. Don't get me wrong, it's a great program and IDE, but it only can compile for linux and there are no converters from VB6 to gambas, so you would have to rewrite any code you wanted ported. I used it for awhile in linux and I liked it, but if you are starting over and needing to learn a different BASIC language, go with Java as it has multiplatform support.

---

### Post by hwyckoff on 2012-09-30
I am curious about the outcome you are trying to reach by asking for a Linux equivalent or alternative to Visual Basic.

[LIST]
[*]Are you looking for a Visual Basic analogue for Linux because you're already comfortable and don't want to learn a new language if possible?
[*]Do you have a bucketload of programs you don't want to convert? 
[*]Is there something that you can only do in Microsoft Microsoft Visual Basic?
[/LIST]

Or, by "alternative" are you looking for an IDE that has a visual "style" in which you can program in Basic, but it doesn't have to be an exact match?

---


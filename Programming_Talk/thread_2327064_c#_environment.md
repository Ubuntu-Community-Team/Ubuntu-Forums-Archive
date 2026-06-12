---
title: "c# environment"
date: 2016-06-07
forum: Programming Talk
---

### Post by joe203 on 2016-06-07
I am new to Ubuntu, but know c#. From what I have read, Mono will provide c# on Ubuntu.

Questions:
1) Is Mono both an IDE and a compiler?
2) What is MonoDevelop - just an IDE?
3) With Mono, will I have access to many of the .Net 4.X classes?

Leading to the last question: What apps do I need to install to in order to come close to replicating Visual Studio 20XX for c#?

TIA, Joe

---

### Post by T.J. on 2016-06-08
> **joe203 said:**
> 
1) Is Mono both an IDE and a compiler?


No.  Mono is just the compiler.

> 
2) What is MonoDevelop - just an IDE?


MonoDevelop is an IDE sponsored by Xamarin (now part of Microsoft).  It is generally used for Mono coding.  I've mucked about with it a bit. It's decent for C#.

> 
3) With Mono, will I have access to many of the .Net 4.X classes?


Some perhaps, but not all.  C# is not an open language.  Version 2 was released under an ISO standard, but newer releases were not. Even in the released standards, Microsoft deliberately left a number of C# language classes out of the versions it allowed to be used under its patent promises. Everything may change now with Microsoft opening Project Roslyn as FOSS ([https://github.com/dotnet/roslyn](https://github.com/dotnet/roslyn)), but I would not expect any improvement for at least a while.  Most programmers on Linux prefer other languages covered by FOSS licenses or ISO standards, so I would not expect a rush to see new features added to Mono. 

Many of the "missing" C# classes have been replaced with equivalents.  Windows Forms are not usable under Linux last I heard, but GTK# is available on Windows, Linux or Mac.

> 
Leading to the last question: What apps do I need to install to in order to come close to replicating Visual Studio 20XX for c#?


Personally, I've found Visual Studio to be the worst IDE I have ever used, because Intellisense tries to "fix" as you type, and its debugging leaves much to be desired. However, everyone has their own tastes.  Try Visual Studio Code for Linux.  It's as close as you can get, and it is made by Microsoft.

---

### Post by joe203 on 2016-06-09
T.J. -- thanks for the reply. I will install Mono & MonoDevelop as a starting point and keep an eye on Project Roslyn.

---

### Post by T.J. on 2016-06-09
[FONT=arial][SIZE=2]Just an update, after posting I checked around, and there is a version of Windows Forms, but I do not know if it was ever added to the release. 

 You will have to experiment a bit.  I'm sorry my knowledge of the Mono situation is somewhat out of date.  I personally prefer not to use C# whenever possible.  My reasoning is that since C# does not have a current ISO standard for the existing versions, there are no cross-platform or patent guarantees as there are with C/C++.  ISO standardization basically makes it next to impossible to sue, because in order to be standardized, the same RAND terms must be offered to everyone, and everything has to be stated upfront. (I included a definition below).
[COLOR=#222222]
Ever since [/COLOR]*Oracle versus Google,*[COLOR=#222222]  started slugging it out over Java (which has no ISO specification, but is GPL), [/COLOR]I have great reservations about using languages that are not covered by ISO standards.  Corporate sponsors and their promises aside; Microsoft, like Oracle has a reputation for turning on people and being litigious. Since API's are now considered copyrightable,  FOSS licenses will no longer entirely protect you in the United States, so I would not depend on them without a RAND grant.

[/SIZE]I'm not saying I Mono/Roslyn is bad, merely that if you are going to do any form of commercial work, I'd make sure you follow Microsoft's terms to the absolute letter, because now they can bypass the license and sue for damages.
[SIZE=2]
[COLOR=#000000]"RAND, an abbreviation for *reasonable and nondiscriminatory* , is a phrase that [ISO]("http://searchdatacenter.techtarget.com/definition/ISO") , the international standards group, and other groups use to describe terms to which a patent contributor to a standard must adhere. If a technology that is part of the standard is to be licensed for a fee, the terms must be nonexorbitant, published, and the same for all implementors (rather than subject to individual negotiation).  An approach that standards users prefer is *royalty-free* implementation."[/COLOR]
[COLOR=#000000]-- [http://whatis.techtarget.com/definition/RAND-reasonable-and-nondiscriminatory](http://whatis.techtarget.com/definition/RAND-reasonable-and-nondiscriminatory)[/COLOR][/SIZE][/FONT]

---


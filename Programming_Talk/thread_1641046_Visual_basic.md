---
title: "Visual basic"
date: 2010-12-08
forum: Programming Talk
---

### Post by Vauxchen on 2010-12-08
I know that this question has been asked before, but it has been 2 years since the last topic (That I could find) had been posted and I wondered if there were any updates.

I'm learning to program using Visual basic for my college AS project and I regularly take my laptop in so that I have all my documents with me. I would like to know if there's any Visual Basic 10 versions that can be used under Ubuntu 10.10 so that I can code at home and at college on the same machine without having to worry about USB sticks, and making sure that I've copied all the files I need across and so forth.

Thanks in advance
And sorry if this is in the wrong area

---

### Post by C1RiON on 2010-12-08
Hi man.

Installing Visual Basic 2010 under Ubuntu is going to be a though one.
I went through WineHQ's App Database, but according to [this link]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19993") Wine doesn't support Visual Basic 2010 very well at this moment.
I think the main reason behind this is because Visual Basic is focused on developing applications for Windows. This means it requires the .NET 4 Framework.
As far as I know Ubuntu nor Wine supports the .NET 4 Framework (yet).

I think you best bet is to either install a version of Windows aside Ubuntu as Dual-Boot, or install a Version of Windows in VirtualBox, just to work with Visual Basic.

Other search results gave me a program called "Gambas" which you can find [ here ]("http://gambas.sourceforge.net/en/main.html)
Looking through their side it isn't quite Visual Basic, but the language and building of applications feels the same as Visual Basic. 
I don't think it will be handy if you need to write Windows specific applications, but it might help in your learning process to understand the "BASIC" language.

I hope you can sort this out ;)

---

### Post by DaithiF on 2010-12-08
Mono (a cross-platform implementation of the .net framework) seems to support visual basic, see [http://www.mono-project.com/VisualBasic.NET_support](http://www.mono-project.com/VisualBasic.NET_support)

---

### Post by directhex on 2010-12-09
Just to be crystal clear, there is no version of the Visual Basic language beyond VB 6. Subsequently, there was a language called Visual Basic.NET, which is similar but explicitly NOT the same thing (you can't just compile VB6 apps with VB.NET, for example). And to be super helpful, Microsoft officially called VB.NET 8 and above "Visual Basic", even though it's a different language. Hooray!

Ubuntu contains a compiler and runtime for Visual Basic.NET 8 (Visual Studio 2005), via the mono-vbnc package and monodevelop IDE. There's no GUI designer, but you can write GUI apps directly in code.

---


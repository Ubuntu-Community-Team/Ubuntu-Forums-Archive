---
title: "How do i program with visual basic.net in ubuntu"
date: 2008-12-25
forum: Packaging and Compiling Programs
---

### Post by linux_lover69 on 2008-12-25
I want to know of any programs that I can use to program using the visual basic.net language. I'v tried Mono and Gambas, help on using them would be wonderful if I can program using visual basic.net. And I don't want posts saying that i should learn another computer language like C# or C++. Help is greatly appreciated.

---

### Post by tuxxy on 2008-12-25
If all else fails you could boot a virtual XP drive in virtualbox

---

### Post by linux_lover69 on 2008-12-25
I'm duel booting Ubuntu and Windows right now and i want to get rid of windows, But yeah if there's no other choice I'll continue to duel boot.

---

### Post by MaindotC on 2008-12-25
I run Visual Studio in Wine and it works perfectly fine.  Have you tried using Wine?

---

### Post by linux_lover69 on 2008-12-25
No I havn't. What version did you install that worked?

---

### Post by directhex on 2008-12-26
Sigh.

mono-vbnc package. The compiler is called "vbnc". Monodevelop should support vbnc for compiling, assuming you want an IDE.

---

### Post by MaindotC on 2008-12-26
> **linux_lover69 said:**
> No I havn't. What version did you install that worked?

I installed Visual Studio 2008.  Ever since Wine 1.0 I've had little if any difficulty running windoze programs that my university uses like phpDesigner, dreamweaver, or visual studio.  However, it may be wise to use a native application like Mono that directhex suggested.  You can check out Mono at [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page).  I haven't used Mono yet nor have I allocated time to read the docs.

---

### Post by noerrorsfound on 2008-12-26
> **linux_lover69 said:**
> And I don't want posts saying that i should learn another computer language like C# or C++.
I hope you don't mind if I recommend [REALbasic]("http://www.realsoftware.com/realbasic/"). It's not only available for Windows, Mac, and Linux, but you can compile for a different OS than you're currently running (compiling a Windows version on Linux, for example). [REALbasic versus Visual Basic (PDF)]("http://tech-publishing.com/Downloads/RB2.pdf") says:
> Programmers with a background based on Visual Basic .NET will also find the transition to REALbasic relatively smooth and will be able to bring over most of their Visual Basic programming experience, less any .NET specific features.

---

### Post by directhex on 2008-12-26
An awful lot of these solutions are ignoring the actual original question.

```
directhex@mortos:/tmp$ lsb_release -d
Description:	Ubuntu 8.10
directhex@mortos:/tmp$ cat hello.vb 
Imports System
 Module Module1
     Sub Main()
         Console.WriteLine ("Hello World")
     End Sub
 End Module
directhex@mortos:/tmp$ vbnc hello.vb 
 version  (Mono 2.0 - r)



Assembly 'hello, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' saved successfully to '/tmp/hello.exe'.
Compilation successful
Compilation took 00:00:02.5077040
directhex@mortos:/tmp$ mono hello.exe 
Hello World
directhex@mortos:/tmp$
```

The mono-vbnc and libmono-microsoft-visualbasic8.0-cil packages are available only in Jaunty or newer, but they ought to install cleanly in Intrepid

---

### Post by linux_lover69 on 2008-12-27
Thanks, I guess I'll try to figure out mono.

---


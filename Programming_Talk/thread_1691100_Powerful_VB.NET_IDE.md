---
title: "Powerful VB.NET IDE ?"
date: 2011-02-19
forum: Programming Talk
---

### Post by etdsbastar on 2011-02-19
Hello there,

Can anyone suggest me a beautiful and powerful IDE for VB.NET with code-completion feature for Ubuntu Marverick.

Thanks.

---

### Post by Apapousek on 2011-02-19
Take a look at Mono:
[ http://www.mono-project.com/VisualBasic.NET_support]("http://www.mono-project.com/VisualBasic.NET_support")

You could probably use it in Eclipse, and do vb.net from there.
On a side note, why not just use C, C++, Java, or Python?

---

### Post by etdsbastar on 2011-02-19
> **Apapousek said:**
> Take a look at Mono:
[ http://www.mono-project.com/VisualBasic.NET_support]("http://www.mono-project.com/VisualBasic.NET_support")

You could probably use it in Eclipse, and do vb.net from there.
On a side note, why not just use C, C++, Java, or Python?

Dear,

I had already used mono, its not so compatible and doesn't comply completely with C# and VB.NET standards. Secondly, I want IDE for VB.NET with complete features. Please suggest one.

I had used Eclipse, It's good for C and CPP.

Netbeans for Java...

---

### Post by Phoenixie on 2011-02-19
> **etdsbastar said:**
> Secondly, I want IDE for VB.NET with complete features. Please suggest one.

Mono is the best you could get on Linux.

---

### Post by etdsbastar on 2011-02-19
Ok I understood now...

Thanks for ur support all of you...

---

### Post by forrestcupp on 2011-02-19
> **etdsbastar said:**
> 
I had already used mono, its not so compatible and doesn't comply completely with C# and VB.NET standards. Secondly, I want IDE for VB.NET with complete features. Please suggest one.

I had used Eclipse, It's good for C and CPP.

Netbeans for Java...

Then you'll just have to use Visual Studio or Visual Basic Express in Windows. If you want to program in a Microsoft language, you might as well use their OS and software to do it. If you don't, don't expect 100% compliance.

And I personally like Eclipse better than Netbeans for Java. But that's my opinion. ;)

---

### Post by etdsbastar on 2011-02-19
> **forrestcupp said:**
> Then you'll just have to use Visual Studio or Visual Basic Express in Windows. If you want to program in a Microsoft language, you might as well use their OS and software to do it. If you don't, don't expect 100% compliance.

And I personally like Eclipse better than Netbeans for Java. But that's my opinion. ;)

I know that Microsoft and Linux are completely different platforms, As per your suggestion, I will give Eclipse a try. I am using Geany at present.

---

### Post by forrestcupp on 2011-02-20
> **etdsbastar said:**
> I know that Microsoft and Linux are completely different platforms
I know. I wasn't trying to be a jerk. I was just saying that Mono is the closest thing you can get to VB in Linux. If it's for Linux, then you shouldn't need anything more. If you need more than that, then you just need to use the real thing.

---

### Post by directhex on 2011-02-21
> **etdsbastar said:**
> Hello there,

Can anyone suggest me a beautiful and powerful IDE for VB.NET with code-completion feature for Ubuntu Marverick.

Thanks.

MonoDevelop has support for Visual Basic.NET, but it's a second-class citizen compared to C# - e.g. there's no GUI designer for VB.NET

---

### Post by etdsbastar on 2011-02-21
> **directhex said:**
> MonoDevelop has support for Visual Basic.NET, but it's a second-class citizen compared to C# - e.g. there's no GUI designer for VB.NET

Dear,

What do you mean by second-class citizen compared to C#.

Please explain clearly...

---

### Post by directhex on 2011-02-21
> **etdsbastar said:**
> Dear,

What do you mean by second-class citizen compared to C#.

Please explain clearly...

Well, for example, there's no GUI designer for VB.NET

Any feature which generates code needs specific support for every language it can target. The GUI designer is an example - your GUI in MonoDevelop is converted to C# source, and they'd need to write an output converter for every language beyond that. So far, nobody has bothered.

---


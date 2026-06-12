---
title: "Want to Deploy Program in LINUX"
date: 2009-02-22
forum: Programming Talk
---

### Post by trendyabinash on 2009-02-22
Sir,

 I want to write a program which can run in Linux environment. I know visual basic and am a beginner of C#. I use to write progem for my personal use. For data keeping of my business.

So, can you please suggest me a language, which is visual and best suits me being a C# programmer. I keep my data in a database, SO i MANAGE DATABASE FROM THE PROGRAM.

Any help is welcomed. Please help me.

I shifted from windows because of virus problems.
It was getting into my nerves.

Please help me.

---

### Post by Tomosaur on 2009-02-22
> **trendyabinash said:**
> Sir,

 I want to write a program which can run in Linux environment. I know visual basic and am a beginner of C#. I use to write progem for my personal use. For data keeping of my business.

So, can you please suggest me a language, which is visual and best suits me being a C# programmer. I keep my data in a database, SO i MANAGE DATABASE FROM THE PROGRAM.

Any help is welcomed. Please help me.

I shifted from windows because of virus problems.
It was getting into my nerves.

Please help me.

Why not just use C#?

[Mono Project - .Net for Linux]("http://www.mono-project.com/Main_Page")
[MonoDevelop - IDE for Mono](http://monodevelop.com/Main_Page)

MonoDevelop also a plugin / add-on for drag and drop GUI development, just like Visual Studio.

---

### Post by trendyabinash on 2009-02-22
and how can I use softwares deploy for windows to work on linux????

as I use a program build in VB6 and wine doesn't accept the vb runtimes to be installed

or is there a way and I am going some where wrong

---

### Post by Tomosaur on 2009-02-22
> **trendyabinash said:**
> and how can I use softwares deploy for windows to work on linux????

as I use a program build in VB6 and wine doesn't accept the vb runtimes to be installed

or is there a way and I am going some where wrong

Well, there is never likely to be 100% compatibility between Windows and Linux software if you want to use Microsoft languages. If that is what you **really** want, then you are better off switching to something more platform independent such as Java.

If you have a C# project developed on Windows, then rather than trying to use the same executable in Linux, just load the project in Monodevelop and compile it with that. 

As for VB, I'm not too knowledgeable in that area, but I don't think there is all that much support for Visual Basic in general on Linux.

With Mono and Monodevelop, you do not need to use Wine. You may have to forget about the Visual Basic stuff, but somebody else will know more about that than me.

---

### Post by directhex on 2009-02-22
VB6 is a proprietary language for Windows - compatibility with it is a case of luck more than anything else

C# however is an international standard, and a C# app compiled on Windows (as long as your code isn't crap) will run out of the box on Linux with Mono

---

### Post by trendyabinash on 2009-02-22
Java is actually not for me as I am really confused as to how it works.
Either I need a good teacher for java which I couldn't or shall teach my self how it works


Neways thanks for the support for now I would like to learn MONO.

---

### Post by slavik on 2009-02-23
you're at ease with C# but are confused by Java? You, sir, are weird ...

---

### Post by era86 on 2009-02-23
> **slavik said:**
> you're at ease with C# but are confused by Java? You, sir, are weird ...

My thoughts exactly... are they not "almost" the same thing?

As for deploying programs from Windows to Linux, I've tried this with very little success...

---

### Post by directhex on 2009-02-23
> **slavik said:**
> you're at ease with C# but are confused by Java? You, sir, are weird ...

Not THAT weird - C# is the end result of frustration with the thing Java is terrible at doing, such as JNI

I spent three years earning a degree on a Java-centric course, and would always use C# for preference these days

---

### Post by trendyabinash on 2009-02-24
Guys I have never tried JAVA myself.

Ok One question, can I handle database with JAVA?
Or is it possible via C# only?

---

### Post by trendyabinash on 2009-02-24
And Yes I have been reading some ebooks related to JAVA and C# and JAVA are very similar.
But Microsoft C# gives a graphical interface which makes the work much easier and faster.

---

### Post by Can+~ on 2009-02-24
> **trendyabinash said:**
> And Yes I have been reading some ebooks related to JAVA and C# and JAVA are very similar.
But Microsoft C# gives a graphical interface which makes the work much easier and faster.

[Eclipse]("http://www.eclipse.org/downloads/")

Although, if it's a language just to interact with a database, anything will do. Unless you're looking to create GUIs.

---

### Post by directhex on 2009-02-25
> **trendyabinash said:**
> Guys I have never tried JAVA myself.

Ok One question, can I handle database with JAVA?
Or is it possible via C# only?

Java is fine with databases - its equivalent of ADO.NET is JDBC

It's also fine with GUIs, as long as you don't mind them looking like crap and there being no drag-and-drop GUI designers worth using

---

### Post by trendyabinash on 2009-02-25
I want to make GUI.

If java can not handle GUIs then why the hell it is so popular?
Yes I am getting a little hold of java, via book and with the help of you guys.

But it will be a complete waste of time to learn a language then ultimately find that it doesn't fulfill your requirements.

Neways as java is platform independent so it has won, for me. May be I will make an console application for my staffs.

Is there any other which is platform independent,
having the facility to support GUIs?

---

### Post by Zugzwang on 2009-02-25
> **trendyabinash said:**
> If java can not handle GUIs then why the hell it is so popular?
Yes I am getting a little hold of java, via book and with the help of you guys.


This was only the opinion of someone who tried it. Java *is* capable of GUI stuff, but GUI builders are a little bit different here. 

It is true that there's no nice point-and-click GUI maker for java - but - for example the netbeans GUI builder is absolutely usable if you only use the so-called "GridBagLayout" and totally forget about the rest. You'll end up with professional layouts that also scale well. 

There's the official Sun tutorial on GUI making for Java, if you are interested. Use google/whatever to find it.

---

### Post by Gordon Bennett on 2009-02-25
You can use a cross-platform GUI library such as GTK or QT - and they have point-and-click design apps.

---

### Post by ajackson on 2009-02-25
Java has the nice advantage of being able to more or less use the same code on various platforms. The GUIs look a bit ugly by default but I've also seen some nice looking Java GUIs so I guess if you spend a bit of time on them you can get rid of the uglyness.

Python has the tkinter widgets that are platform neutral (they map to the native systems GUI widgets via the python interpreter) and the design work for that is so simple you don't really need an actual GUI builder (as with all things a GUI builder does help speed up GUI design).

The mono installer for Windows sticks GTK on the system so C# is another potential cross platform using either GTK or even the Windows forms (though I've never played around with them on Linux so don't know how good/bad they are).

---

### Post by soltanis on 2009-02-25
I strongly suggest you consider Python. It's very simple and straightforward, yet pretty powerful at the same time. It's object-oriented, high level, and supports GUI and database interaction quite well.

Since you are creating programs for internal use, I would say Python is the language for you.

C# is also useful, Java...well...I don't like it myself, and Perl is a language universal across the nixes (and it works mostly on Windows as well) with support for Tk GUIs and DB interaction.

Any language will probably suit you, but I suggest a high-level scripting one (i.e. Python/Perl) for what you sound like you want.

---

### Post by id1337x on 2009-02-25
C# was created to take market share from Java and the whole language is just another Microsoft rip-off just like VBscript. I would recommend then that you learn Java since the whole C# language was ripped off of it. Learning Java from C# should be easy.

---

### Post by trendyabinash on 2009-02-25
Soltanis Thanks for telling me about python.
But before I give it a try I would like to know some basics like
is it similar to C# coding or different?
does it requires codes for design if it is so then I would prefer JAVA as it's coding is almost same as C#.
If it gives gui like C# then I would like to give python a try or else I am good to go with java

---

### Post by directhex on 2009-02-26
> **id1337x said:**
> C# was created to take market share from Java and the whole language is just another Microsoft rip-off just like VBscript. I would recommend then that you learn Java since the whole C# language was ripped off of it. Learning Java from C# should be easy.

C# was created to offer a Java-like experience, but remove the most braindead crap from Java such as JNI or the worthless generics implementation. Once upon a time Microsoft tried adding those fixes to their own Java implementation, and they were sued for it.

Java is unquestionably "more mature" than C#, but too many people conveniently ignore the reasons for C#'s creation

See [http://www.koushikdutta.com/2009/01/jni-in-android-and-foreword-of-why-jni.html](http://www.koushikdutta.com/2009/01/jni-in-android-and-foreword-of-why-jni.html) for a little piece on .NET's P/Invoke compared to Java's JNI

---


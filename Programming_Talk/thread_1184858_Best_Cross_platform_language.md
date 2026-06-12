---
title: "Best Cross platform language"
date: 2009-06-11
forum: Programming Talk
---

### Post by ultimatebuster on 2009-06-11
Hi!

I want to start to learn a language in the C family (C, C++, C#), which one is easy to learn and can be ported cross platform? 

Can I develop on Visual C++/C# Studio Express and port it over to Linux since there are more resource (tutorial, books etc)? 

Thanks!

---

### Post by smartbei on 2009-06-11
C# is a bit problematic, since while Mono is usable, it isn't up to par with .net.

Either C or C++ are good choices, as long as you stick with cross-platform libraries for GUI, threading, etc. Qt or GTK are two such examples.

Since you are just beginning, it probably doesn't matter much, since you won't be building an application with a GUI as your fist project :-).

BTW - why are you looking at the C family for your first programming language? While they are great tools, I am not sure they are the best starting language. (Go Python! :-))

---

### Post by fr4nko on 2009-06-11
Hi,

I don't have a real knowledge of C# and visual studio but for me a portable language between linux and windows is C/C++. What is also relevant for the portability is also the set of libraries you are using. Typically the most is important is the library/toolkit to develop the user interface because some are portable and some are not. For example the Qt and FOX allows you to compile your code unmodified on linux and windows.

Personally I have developed and I'm maintaining a software which works finely on linux and windows. The software is written in C and C++ and the graphical toolkit is FOX (C++). I'm also using the GNU scintific library and everything works very nicely. I just need to add some preprocessor conditionals for cross-portability but it is limited to a few points, 99% of the code is just the same. The developing tools I'm using on windows are MinGW plus MSYS and I'm very happy with them since it gives me the same environment I'm used to have on linux.
I guess that if you use Visual Studio it will be more difficult to port your code on linux. You should be also aware that most (all) of the Microsoft libraries for the user interface just works on windows, they are not cross platform.

I cannot say you a lot about C#. In linux we have the excellent mono tools but, as far as I know, GUI programs are non-portable because the libraries are system specific (Gtk# for linux and <I don't know what>) for linux.

I hope that helps, but in principle my message is:
Visual C++ can be very nice but it tends to bind you to develop software that can be compiled only with Visual C++ itself and can run only on windows.

Francesco

---

### Post by Sockerdrickan on 2009-06-11
C++.

If all else fails use Python.

---

### Post by froggyswamp on 2009-06-11
There we go again, what is the best cross platform programming language, why not just google first, I'm also sure wikipedia has lots to say.

---

### Post by directhex on 2009-06-11
> **fr4nko said:**
> I cannot say you a lot about C#. In linux we have the excellent mono tools but, as far as I know, GUI programs are non-portable because the libraries are system specific (Gtk# for linux and <I don't know what>) for linux.

GTK# works on Windows, as long as you install the GTK#-for-MS.NET package.

WinForms works on Linux, but looks like crap

The only platform-specific GUI framework for Mono is Cocoa#, for Mac (and the Mac can use both GTK# and WinForms)

---

### Post by Can+~ on 2009-06-11
Who cares if it's portable?

If your just learning to program, go with a high level language (#1 language for starters of the forum: Python 2.x, comes with ubuntu).

If you know other languages and want to learn the C family, start with C and forget about being portable, later you can how to do that properly.

---

### Post by ultimatebuster on 2009-06-11
I started with VB.NET, although Visual Studio has a great IDE, you can't port them. At least i don't know how. If someone know how to port apps over to ubuntu, i can keep develop for VB.Net

---

### Post by directhex on 2009-06-11
> **ultimatebuster said:**
> I started with VB.NET, although Visual Studio has a great IDE, you can't port them. At least i don't know how. If someone know how to port apps over to ubuntu, i can keep develop for VB.Net

Install mono-vbnc. Then run your apps with "mono foo.exe"

Install monodevelop. Then start that GUI, open & compile your csproj files.

---

### Post by ultimatebuster on 2009-06-12
> **directhex said:**
> Install mono-vbnc. Then run your apps with "mono foo.exe"

Install monodevelop. Then start that GUI, open & compile your csproj files.

So i can just compile the Vb.net code in monodevelop?

---

### Post by benj1 on 2009-06-12
what is your rationale for learning one of the Cs ?
yes the syntax is similar but they are 3 different languages, c is the lowest level, while c# is the highest level, just because they have similar names doesn't mean they are the same.
i would advise you to read up on all languages, and decide what to want to achieve with the language.

---

### Post by fr4nko on 2009-06-12
> **benj1 said:**
> 
  the syntax is similar but they are 3 different languages, c is the lowest level, while c# is the highest level, just because they have similar names doesn't mean they are the same.
i would advise you to read up on all languages, and decide what to want to achieve with the language.
I agree, even if the syntax is a little bit similar c# and c are quite different beasts. c is low level and give you all the power but is difficult to program and is hard to build complex application with it. For the other side, a well written and designed C application can be fast, lightweight and rock solid but you need to make it right.

---

### Post by directhex on 2009-06-12
> **ultimatebuster said:**
> So i can just compile the Vb.net code in monodevelop?

```
jms@osc-franzibald:/tmp$ cat example.vb 
Module Example
    Sub Main()
        System.Console.WriteLine("Hello World!")
    End Sub
End Module

jms@osc-franzibald:/tmp$ vbnc example.vb 
Visual Basic.Net Compiler version 0.0.0.5913 (Mono 2.2 - r)
Copyright (C) 2004-2008 Rolf Bjarne Kvinge. All rights reserved.


Assembly 'example, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' saved successfully to '/tmp/example.exe'.
Compilation successful
Compilation took 00:00:01.1390860
jms@osc-franzibald:/tmp$ mono example.exe 
Hello World!
jms@osc-franzibald:/tmp$ 
```

Yes.

---

### Post by Dragonbite on 2009-06-12
> **ultimatebuster said:**
> So i can just compile the Vb.net code in monodevelop?

Yes, you can compile VB.NET code. Monodevelop doesn't have the easy GUI or ASP.NET tools for VB.NET that are included in C# yet but with the MVC(?) ASP.NET should become easier to develop in either language.

There are a couple pages on the [[COLOR="Blue"]Mono [/COLOR]]("http://www.mono-project.com")website that goes over using Visual Studio and/or VS plug-ins for developing Mono on Windows.  They have some new ones coming out that look pretty slick.

Also there is an application that will scan your assembly and spit out how Mono-compatible it is.

---

### Post by fr4nko on 2009-06-12
> **Dragonbite said:**
> Yes, you can compile VB.NET code. Monodevelop doesn't have the easy GUI or ASP.NET tools for VB.NET that are included in C# yet but with the MVC(?) ASP.NET should become easier to develop in either language.

Great, so you can have the best programming language of ever, Visual Basic, on linux ? That's so exciting!!

---

### Post by Dragonbite on 2009-06-12
> **fr4nko said:**
> Great, so you can have the best programming language of ever, Visual Basic, on linux ? That's so exciting!!

YMMV. VB and VB.NET seem to be the LEAST supported language for Linux unfortunately. I know there's Gambas for VB, but that's about it I think.

---

### Post by Vadi on 2009-06-12
Mono is problematic. It's missing things, playing catchup, and etc.

I'm getting into Vala and it's quite nice so far. C#-like syntax, C speed, and no additional stuff for the user to install (really, nothing.). It's great.

---

### Post by pokerbirch on 2009-06-12
Nobody has mentioned Java? It's not a language that i particularly like, but it IS multi platform and the syntax is similar to C++.

---

### Post by Dragonbite on 2009-06-12
> **pokerbirch said:**
> Nobody has mentioned Java? It's not a language that i particularly like, but it IS multi platform and the syntax is similar to C++.

If you're used to the MS Visual Studio type IDE, then for Java you might want to look into [[COLOR="Blue"]NetBeans[/COLOR]]("http://www.netbeans.org/").

---

### Post by Can+~ on 2009-06-12
> **fr4nko said:**
> the best programming language of ever, Visual Basic!

Borrowing from CptPicard

[img]http://ubuntuforums.org/customavatars/avatar148462_5.gif[/img]

---

### Post by benj1 on 2009-06-12
> **fr4nko said:**
> Great, so you can have the best programming language of ever, Visual Basic, on linux ? That's so exciting!!

sorry my sarc-o-meter just exploded, can anyone help fix it ;)

---

### Post by blackxored on 2009-06-12
I'm a user of a lot of languages. And I'd said portability in some cases gets the main topic in the implementation and other times in the code. I'd personally recommend Java, if you like a C-like syntax, a cleaner language than C, C++, and C#, and of course It has been ported even to portable devices. If you need something quicker than Java, then I'd recommend Python over Ruby, Perl and the like, but that's a personal choice most of the time.

---

### Post by hero1900 on 2009-06-12
why you don't try java i think it is the best multi platform programing enviroment

---

### Post by fr4nko on 2009-06-12
> **benj1 said:**
> sorry my sarc-o-meter just exploded, can anyone help fix it ;) I'm glad that  your sarc-o-meter is working again. I was afraid something in the forum could think I was serious!:p

VB the best language of ever - come on... of course I was kidding!!!

At work many people are using VB and I'm amused by the quantity of crap code that they are able to produce. Sometimes I go through the code just to laugh a little bit when I'm tired. I've recently reimplemented with one page of python what was written in several tens of VB pages. The more, since it seems that in VB you don't have the urllib module, they was creating a batch file on the fly to call an external executable (curl.exe for the curious) just to retrieve a file from an URL in https - when I've understood what the code was doing it made me laugh for a moment :D

Francesco

---

### Post by Can+~ on 2009-06-12
My sarc-o-meter was disabled when I posted my original message. Thanks god.

Talking about dumb code, here's one tdwtf that cracked me up the other day:
[http://thedailywtf.com/Articles/The-Int-Divide.aspx](http://thedailywtf.com/Articles/The-Int-Divide.aspx)

It has extra funny points for calling the database to divide.

---

### Post by pokerbirch on 2009-06-12
VB is no worse than Python...it just got a bad name because it is another easy-to-use syntax which means that anybody can become a "programmer" within a few hours. Very few people ever learn to use it *properly*, which results in millions of lines of bad code which then get googled and copy/pasted by the next generation, thus continuing the snowball. I blame Microsoft.
:)

---

### Post by eilios on 2009-06-12
Java is somewhat annoying to make classes for, but it is very cross platform. If you insist on having a c-like language, you can easily develop c++ apps using opengl, which is cross-platform, using code blocks(one of my favourite IDEs). Java isn't a language I like to use, but again, it is a very good option. Except, jar files don't run well with macs. C# is not a good choice because it is very windows-central and people in general do not like having to install several packages just to run a game/program. I love python, it is extremely cross-platform and has a variety of libraries, but it isn't c-like. C itself is used for different operating systems, but it is somewhat of a pain to program.
 
TL;DR
 
Go with c++.
 
[offtopic]
Poker, VB isn't nearly as powerful as python, and python you can't really write bad code with it, due to the fact with python they strongly believe to do everything, there is one obvious approach; as such, most programming tutorials are the same, and most new programmers will get used to the ease of use of python, and since the only way to write python code is a good way, you have no bad code. VB is also not cross platform, and you can't do much with it besides windows applications. Sure, you get the occasional game, but it's always better to just program it in python/java/c++/c/other powerful language.
[/offtopic]

---

### Post by Dragonbite on 2009-06-12
> **eilios said:**
>  C# is not a good choice because it is very windows-central and people in general do not like having to install several packages just to run a game/program. 

Java seems to me to be a bigger download to get things going and I have not found an application that runs at an acceptable speed.

Of course some of it could be the distro including some Mono components already, I'll admit.

---

### Post by Mirge on 2009-06-12
> **eilios said:**
> 
[offtopic]
Poker, VB isn't nearly as powerful as python, and python you can't really write bad code with it, due to the fact with python they strongly believe to do everything, there is one obvious approach; as such, most programming tutorials are the same, and most new programmers will get used to the ease of use of python, and since the only way to write python code is a good way, you have no bad code. VB is also not cross platform, and you can't do much with it besides windows applications. Sure, you get the occasional game, but it's always better to just program it in python/java/c++/c/other powerful language.
[/offtopic]

I have no experience with Python, but I don't really understand how one couldn't write "bad" code with any language...

---

### Post by Vadi on 2009-06-12
Same. Nor do I understand how does Mono produce better programs (and people actually say this).

A computer language is a set of rules and syntaxes, and a person is a person.

---

### Post by benj1 on 2009-06-12
> **Mirge said:**
> I have no experience with Python, but I don't really understand how one couldn't write "bad" code with any language...

```
@P=split//,".URRUU\c8R";@d=split//,"\nrekcah xinU / lreP rehtona tsuJ";sub p{
@p{"r$p","u$p"}=(P,P);pipe"r$p","u$p";++$p;($q*=2)+=$f=!fork;map{$P=$P[$f^ord
($p{$_})&6];$p{$_}=/ ^$P/ix?$P:close$_}keys%p}p;p;p;p;p;map{$p{$_}=~/^[P.]/&&
close$_}%p;wait until$?;map{/^r/&&<$_>}%p;$_=$d[$q];sleep rand(2)if/\S/;print
```

10 points for working this out

---

### Post by Vadi on 2009-06-12
I don't see how obfuscation relates to bad code.

---

### Post by benj1 on 2009-06-12
> **Vadi said:**
> I don't see how obfuscation relates to bad code.

well i suppose it depends on how you define bad code, i would define it as hard to read. there are some languages that tend to be easier to read than others.
yes this is an extreme example and was meant more as a joke, playing on perls reputation

---

### Post by simeon87 on 2009-06-12
> **benj1 said:**
> well i suppose it depends on how you define bad code, i would define it as hard to read. there are some languages that tend to be easier to read than others.
yes this is an extreme example and was meant more as a joke, playing on perls reputation

So clean, concise, elegant, and efficient code becomes bad code after running an obfuscation tool over it?

---

### Post by benj1 on 2009-06-12
> **simeon87 said:**
> So clean, concise, elegant, and efficient code becomes bad code after running an obfuscation tool over it?

well yes, if you can't read it.

how does everyone else define 'bad code'?

---

### Post by Mirge on 2009-06-12
Some would say that "bad code" could be excessive (or any) use of system() calls, losing its portability.

I wouldn't say obfuscation = bad code, given the developer(s) still had access to a non-obfuscated version. Good example: Javascript. It's extremely common for JS developers to keep 2 versions of their code, one obfuscated/compressed, one development, clean, easily-read version.

Viewed the source for [www.google.com](www.google.com) lately? :)

I just think it's incorrect to say a language is incapable of producing "bad" code.

---

### Post by Can+~ on 2009-06-12
> **benj1 said:**
> how does everyone else define 'bad code'?

Bad code could be just anything:

[http://en.wikipedia.org/wiki/Anti-pattern#Programming_anti-patterns](http://en.wikipedia.org/wiki/Anti-pattern#Programming_anti-patterns)

---

### Post by benj1 on 2009-06-12
> **Mirge said:**
> Some would say that "bad code" could be excessive (or any) use of system() calls, losing its portability.

I wouldn't say obfuscation = bad code, given the developer(s) still had access to a non-obfuscated version. Good example: Javascript. It's extremely common for JS developers to keep 2 versions of their code, one obfuscated/compressed, one development, clean, easily-read version.

Viewed the source for [www.google.com](www.google.com) lately? :)

I just think it's incorrect to say a language is incapable of producing "bad" code.

agreed
i would also say code that is more inefficient than it should be is also bad code.
i wasn't trying to make the point that obfuscation = bad code, (although it does), i was trying to make the point that hard to read code is bad code, you can't maintain code that you can't read.

---

### Post by StormDrain on 2009-06-12
Remarking only on the topic title and not on anyone else's personal preferences, I kind of like XBasic, because of its being cross platform compatible and some believe, faster than C.

Regrettably, the information about it on the web is very outdated and the team that continues to develop it work in relative obscurity in a Yahoo members only group. Personally, I think they should be putting copies of their work out on the web for the world to enjoy and maybe even offering it for inclusion in the Ubuntu repoistory list, but thats just me. 

I've just downloaded the latest Linux version of XBasic, (xbasic-6.3.3-src-20090606.tar.gz) and I'll be installing it on the weekend. I've only been using Ubuntu for a little over a month and when I installed a copy of XBasic from sourceforge, it just froze up. Hopefully this time the newer version doesn't.

Have a good day!

K.

---

### Post by blackxored on 2009-06-15
In any language, you write bad code if you want to; or if you're unable to get it right. 
Besides the fact that some languages are trickier than others, for example compare Perl to Python, or take a look at Lisp or Scheme, you will be annoyed with things like:
```
 (+ 5 3)
```
But anyways. Take a look at who is using Python and how. You will see many programs included in Linux distros with a very flexible design, and you'll of course find some ugly scripts, but that's how it works.

---

### Post by Vadi on 2009-06-15
Is that extended notation code?

---

### Post by CptPicard on 2009-06-15
> **blackxored said:**
> 
Besides the fact that some languages are trickier than others, for example compare Perl to Python, or take a look at Lisp or Scheme, you will be annoyed with things like:
```
 (+ 5 3)
```

Uh... how is that tricky, and why would someone be annoyed?

Lisp syntax is actually almost no-syntax; S-expressions are actually quite remarkable in that regard.

---

### Post by Mirge on 2009-06-15
I have no idea what it means lol

---

### Post by simeon87 on 2009-06-15
> **Mirge said:**
> I have no idea what it means lol

Simply put, (+ 5 3) is the equivalent of 5 + 3 in languages like C. But it's more flexible. For example, you can also write (+ 1 2 3) - or with an arbitrary number of arguments - to sum all these values; this would become 1 + 2 + 3 in C. It's also called prefix notation because the operator is mentioned before the arguments.

Note that in the way it is implemented in Lisp (with an arbitrary number of arguments), you only need 1 operator and n arguments to write down a summation yet you need (n - 1) operators and n arguments to write down the same in C (in 1 + 2 + 3 there are 3 arguments and 2 operators).

---

### Post by Mirge on 2009-06-15
> **simeon87 said:**
> Simply put, (+ 5 3) is the equivalent of 5 + 3 in languages like C. But it's more flexible. For example, you can also write (+ 1 2 3) - or with an arbitrary number of arguments - to sum all these values; this would become 1 + 2 + 3 in C. It's also called prefix notation because the operator is mentioned before the arguments.

Note that in the way it is implemented in Lisp (with an arbitrary number of arguments), you only need 1 operator and n arguments to write down a summation yet you need (n - 1) operators and n arguments to write down the same in C (in 1 + 2 + 3 there are 3 arguments and 2 operators).

Ahh ok I get it. That's actually quite handy...

---


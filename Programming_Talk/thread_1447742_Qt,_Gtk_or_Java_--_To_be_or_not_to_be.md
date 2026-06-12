---
title: "Qt, Gtk or Java -- To be or not to be"
date: 2010-04-05
forum: Programming Talk
---

### Post by sheperson on 2010-04-05
Hi,
I have been in the programming world for some time now and have experienced C++, Java, PHP and C# (in the order of appearance).
Now I want to start with something which is more usable on Linux.
I have Qt, Gtk and Java in mind, but I can't see a winner in them.

Qt is very powerful, but it belongs to KDE, which I am not a big fan of (unlike the old days with KDE 3.X which I was a real fan).

Java is even more powerful, but when it comes to speed, it sucks. It has many usages from Application programming to Mobile and Server side programming.

Gtk belongs to my favorite Gnome, but as far as I know, it is more a GUI toolkit than a frame work.

Now I am stuck here and don't know what to choose.

I appreciate any ideas, comments or experiences with these guys or any other rivals.
Thanks in advance.

---

### Post by Simian Man on 2010-04-05
I'd suggest C# with Mono and GTK#.  You get a better language than C, C++ or Java, a very featureful and robust platform with Mono and easy to use bindings to GTK which, as you said, is the most "native" toolkit for Linux.  Win-Freaking-Win :).

---

### Post by CptPicard on 2010-04-05
Qt is actually my favourite platform/framework/toolkit at the moment... it's very nice, and Nokia's mobile development on it makes it nicer. I guess the C++-specificness is a bit of an issue, but really, technically speaking, KDE has a very good technical foundation in it. The Gnome libraries always seemed like such a mess in comparison.

IMO, Java is slow only when you actually run into something where you *know* it's slow, and that it's a fundamental Java issue. Java is actually among the fastest, if not often the fastest of the non-native compiled languages. The bigger problem is the fact that it runs a whole separate abstract platform next to everything else, and doesn't necessarily integrate well. For desktop apps it's a no-no; for enterprise server and back-office stuff, very useful.

---

### Post by weezerBo on 2010-04-05
Qt kicks GTK+ to the ground and dances around when it comes to cross-platform. The documentation is generally more verbose and it's just plain nicer to program in. You can also make your Qt application look like a GTK+/GNOME application (as well as Windows, OS X, ...) but not the other way around.

---

### Post by lumitoro on 2010-04-05
> **sheperson said:**
> Hi,
I have been in the programming world for some time now and have experienced C++, Java, PHP and C# (in the order of appearance).
Now I want to start with something which is more usable on Linux.
I have Qt, Gtk and Java in mind, but I can't see a winner in them.

Qt is very powerful, but it belongs to KDE, which I am not a big fan of (unlike the old days with KDE 3.X which I was a real fan).

Java is even more powerful, but when it comes to speed, it sucks. It has many usages from Application programming to Mobile and Server side programming.

Gtk belongs to my favorite Gnome, but as far as I know, it is more a GUI toolkit than a frame work.

Now I am stuck here and don't know what to choose.

I appreciate any ideas, comments or experiences with these guys or any other rivals.
Thanks in advance.

   QT doesn't belong to KDE, actually KDE is bound to QT, also QT is not a programming language, it is a cross-platform framework written in c++ and has all the goodies c++ can give plus full-time developers working on it since it is a commercial open-source project(most new comers in the open-source community often think of commercial as evil shady companies but the fact is that the open-source nature of the app gives the knowledgeable individuals the security that the code is not evil).
   QT is the best bet for fast HighTech(and by HighTech i mean the core of software and hardware control) development.

   So by my previous explanation java is not more powerful it's just easier because mostly you don't have to think about where your software is going to run(even thought QT is cross-platform you still have to know witch functions don't work with the OS you are aiming for).

   GTK+ was supposed to be a graphical toolkit but it is much, much more than that, and the fact that it's C language means that you have full control of the machine it runs on(of course, only if you have admin privileges). GTK+, has naming conventions that basically turns it into an object oriented framework even thought C language is not.

  C sharp is .NET(Mono), this is great if you use and develop for Microsoft platforms because Mono is behind .NET several versions and i've failed to run .NET webapps using Mono. IMHO Mono is basically just another try from Microsoft to throw dust in the eyes of the open-source community. I say this because Novell as bought Mono and it as business with Microsoft.

Hope this clarifies things for you. Bye

---

### Post by Simian Man on 2010-04-05
> **lumitoro said:**
> GTK+ was supposed to be a graphical toolkit but it is much, much more than that, and the fact that it's C language means that you have full control of the machine it runs on(of course, only if you have admin privileges). GTK+, has naming conventions that basically turns it into an object oriented framework even thought C language is not.
What a load of bunk, C doesn't give you any more "control" of your machine than any other language.  Also programs written in any language can be executed as root, but that's generally not a good idea.  In fact, if you're writing a program that's meant to run under the root account, it's an even **worse** idea than usual to write them in C due to the higher chance of accidentally doing something stupid.

> **lumitoro said:**
> C sharp is .NET(Mono), this is great if you use and develop for Microsoft platforms because Mono is behind .NET several versions and i've failed to run .NET webapps using Mono. IMHO Mono is basically just another try from Microsoft to throw dust in the eyes of the open-source community. I say this because Novell as bought Mono and it as business with Microsoft.
Read BoycottNovell much?  Actually Mono supports .NET features as they are added to the standard, and with .NET 4.0, Mono is actually *ahead of* Microsoft's implementation in terms of implementing the features.  Don't turn this into a brain-dead lie-fest please.

BTW I agree that QT is a great toolkit and, if I had to use C++ it would be my choice.  Thank God that isn't the case however :).

---

### Post by weezerBo on 2010-04-05
> **Simian Man said:**
> 
Read BoycottNovell much?  Actually Mono supports .NET features _***as they are added to the standard***_, and with .NET 4.0, Mono is actually *ahead of* Microsoft's implementation in terms of implementing the features.  Don't turn this into a brain-dead lie-fest please.

The problem is there is so much more to .NET than the C# standard. That's where mono lags behind and will always be playing catch up.

---

### Post by ad_267 on 2010-04-05
> **sheperson said:**
> Qt is very powerful, but it belongs to KDE, which I am not a big fan of (unlike the old days with KDE 3.X which I was a real fan).

I don't think so. Qt applications without KDE dependencies run great under any desktop environment. Most KDE apps also work fine in Gnome, but are harder to get working on Windows or OSX.

I think there's a big difference in a KDE app and a Qt one, the difference in loading time can be quite noticeable. Some pure Qt apps I can think of off the top of my head are VLC, Skype and Mendeley.

Even though I use Gnome I prefer to use Qt for gui development.

---

### Post by Simian Man on 2010-04-05
> **weezerBo said:**
> The problem is there is so much more to .NET than the C# standard. That's where mono lags behind and will always be playing catch up.

No actually, Mono does fantastic keeping up with the all of the parts of .NET that are covered by the ECMA standard.  That includes not just the C# language specification, but also the CLR and all of the supporting class libraries.  As I said they are ahead of Microsoft in some areas.

The only area "lagging" is in Microsoft-specific libraries like WinForms, but those are primarily only useful to people porting existing software.  Nobody developing new software for Linux wants to use Winforms as GTK# is so much better :).

---

### Post by sheperson on 2010-04-06
Hi all,
Thanks for your wonderful ideas.

To Simian Man:
Although I have been programming in .net for a while now, I don't want to be bound to Microsoft. I mean I had to choose C#, I wouldn't and would choose Java instead. Thanks for your comments.

To CptPicard and weezerBo:
I agree with you. Qt is such a nice framework. Ease of use + fast + cross platform.

To lumitoro:
Nice tip. Thank you.

And finally:
I think I will go for Qt.

---

### Post by lumitoro on 2010-04-06
> **Simian Man said:**
> What a load of bunk, C doesn't give you any more "control" of your machine than any other language.  Also programs written in any language can be executed as root, but that's generally not a good idea.  In fact, if you're writing a program that's meant to run under the root account, it's an even **worse** idea than usual to write them in C due to the higher chance of accidentally doing something stupid.

I think i didn't make myself crystal :P, by control i mean that you have to think how everything works, even a simple linked list can trash you down, hehehe, but lots of people like this meddling around and gtk+ already abstracts lots of it so it's a matter of choice.

> **Simian Man said:**
> Read BoycottNovell much?  Actually Mono supports .NET features as they are added to the standard, and with .NET 4.0, Mono is actually *ahead of* Microsoft's implementation in terms of implementing the features.  Don't turn this into a brain-dead lie-fest please.

BTW I agree that QT is a great toolkit and, if I had to use C++ it would be my choice.  Thank God that isn't the case however :).

I'm not one to trash other people's work. Just a few hours ago i installed opensuse to see if it suited my needs, but Microsoft does everything in their power to slow Novell down. Can you blame them??? I don't like it but they are just protecting their interests.

bye.

---

### Post by Reiger on 2010-04-07
It seems nobody has mentioned it; but if you like Qt and you like C# you can use something like Qyoto to combine both.

---


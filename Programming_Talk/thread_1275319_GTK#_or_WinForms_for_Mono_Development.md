---
title: "GTK# or WinForms for Mono Development?"
date: 2009-09-25
forum: Programming Talk
---

### Post by SunSpyda on 2009-09-25
I performed a search before I posted, & I saw no other thread like this - I saw many referring to Mono GUI toolkits as a whole, but I didn't see any discussing these 2 in particular.

I want to use Mono & C# for high-level cross platform development. I already know Java, but I found (in specific areas), C# could be more useful due to unsafe code, easier to do things like console I/O & easy access to C libraries, not to mention the fact it's syntactically better in more areas. I still prefer Java a small range of other areas though.

OK, I'm stalling :) ... 

I want to use a GUI toolkit with it. WinForms seemed the obvious choice, seeing as it works on the three major platforms. But, then again, so does GTK#.

They are both cross platform, GTK# has it's roots, generally speaking, in UNIX/UNIX-like OSes, whilst WinForms is a Windows thing. Where their roots are, is completely irrelevant to me though. Here are the things that I want -

- Out-the-box portability. For example, WinForms will be on any modern Windows machine, whilst I *think* GTK# is present on nearly all Mono implementations.
- Potential portability. Which one has got libraries for the most platforms?
- Widely used with a big following.

That's it. I'm not bothered about it having a 'alien' feel on certain platforms, nor am I that concerned about speed or OO 'pureness'. Just portability, and the peace of mind that it's so popular, it wont just die out.

The problem is, is that WinForms & GTK# both fill my requirements, so I don't know which one to use.

Does Mono come with WinForms these days? Also, is Mono's WinForms implementation open source? How much ahead is GTK# on OS X than WinForms, which apparently is quite bad?

Thanks in advance for the answers :)

---

### Post by hessiess on 2009-09-25
GTK#, scalable, highly theamable, integrates better visually with the environment its running on.

---

### Post by SunSpyda on 2009-09-25
Thanks for the advice. Yeah I was thinking of GTK# also, because it would be easier to port C# apps to C if I did that, since GTK+ is in C. Yes, I know it's very different in C, but even so.

How fast is GTK implementations compared to others? I not actually interested in performance, but it would be interesting to know - especially in comparison to WinForms on non-Windows platforms.

---

### Post by hessiess on 2009-09-25
> **SunSpyda said:**
> Thanks for the advice. Yeah I was thinking of GTK# also, because it would be easier to port C# apps to C if I did that, since GTK+ is in C. Yes, I know it's very different in C, but even so.

How fast is GTK implementations compared to others? I not actually interested in performance, but it would be interesting to know - especially in comparison to WinForms on non-Windows platforms.

Im just guessing, but GTK is probably faster on Linux, though performance of a GUI tool kit is not very impotent as they spend most of theare time in an idle loop.

---

### Post by directhex on 2009-09-25
There are three major questions to ask yourself:

*1) Do I want pixel-based or container-based layout?*

WinForms defines things in pixel terms, meaning buttons, labels, etc, are positioned by specifying X/Y coordinates. GTK is container-based, making it a bit more like using <table> to build a website: you define the layout by making VBox, HBox, and Table objects, and sticking things inside them

*2) Do I care about dependencies?*

WinForms "works everywhere" without anything extra needed (except on Debian/Ubuntu where the WinForms library needs to be installed, but it's still part of Mono). GTK# is no harder to obtain on Linux or Mac, but on Windows it requires use of an extra package, GTK#-for-ms.net (you can embed the .msi in your app's installer, of course)

*3) Do I want to design it in Linux?*

GTK# has a GUI designer in MonoDevelop. WinForms does not - you need to use SharpDevelop or Visual Studio on Windows, or write your GUI by hand in raw C#

Now, in the general case, there are (almost) no apps in most distros using WinForms. It looks like ****, for one thing (like a Wine app, but a bit glitchier). There are a few exceptions here and there, but by and large, Linux apps are written for GTK# first and foremost.

They also say a picture says a thousand words, so here is a 3,000 word essay on the topic of portability:

[img]http://www2.apebox.org/wordpress/wp-content/gallery/00-single/osctool3-gtk-01.png[/img]

[img]http://www2.apebox.org/wordpress/wp-content/gallery/00-single/osctool3-win32-01.png[/img]

[img]http://www2.apebox.org/wordpress/wp-content/gallery/00-single/osctool3-macos-01.png[/img]

(Yes, that's the same set of assemblies on all three platforms)

---

### Post by SunSpyda on 2009-09-26
Thanks a lot the the help - those screenies helped. I will use GTK#, since I'm already familiar with GTK+ with C, and GTK# seems to have a little more potential portability, even if it's out-the-box portability may be less.

I know this sounds like a dumb question, but how do people think GTK# scales up against Java's AWT/Swing? That's what I'm using in Java, so thoughts on how they compare/are different would be great.

Does Mono have libraries to achieve the same affect as Java applets? I was just thinking that I'm learning a GUI toolkit for C#, so I was  wondering about it's capabilities. I never tried it with GTK+, but Mono has more internet support, so I thought it might be possible, even with ActiveX or the Mono equivalent of applets.

---

### Post by directhex on 2009-09-26
> **SunSpyda said:**
> Thanks a lot the the help - those screenies helped. I will use GTK#, since I'm already familiar with GTK+ with C, and GTK# seems to have a little more potential portability, even if it's out-the-box portability may be less.

I know this sounds like a dumb question, but how do people think GTK# scales up against Java's AWT/Swing? That's what I'm using in Java, so thoughts on how they compare/are different would be great.

Swing is ****.

Sorry if that offends anyone, and I did spend three years on a Java-heavy degree coming to that conclusion. It's ugly and slow.

> Does Mono have libraries to achieve the same affect as Java applets? I was just thinking that I'm learning a GUI toolkit for C#, so I was  wondering about it's capabilities. I never tried it with GTK+, but Mono has more internet support, so I thought it might be possible, even with ActiveX or the Mono equivalent of applets.

There's Silverlight, which offers a cut-down version of the framework and a different widget toolkit (XAML). But it's early days for designing SL stuff in Linux

---

### Post by chrisjsmith on 2009-09-29
Nothing wrong with Swing.  It's usually the person applying it that is at fault (i.e doing everything in the UI thread etc).  I've built some huge, high performance things with it.

FYI, you might want to consider separating the presentation layer of the application if you are unsure of the technology to use.  It would make life easier to replace it later if you don't like it.

Search on Google for Model-View-Controller pattern with respect to C#.

---


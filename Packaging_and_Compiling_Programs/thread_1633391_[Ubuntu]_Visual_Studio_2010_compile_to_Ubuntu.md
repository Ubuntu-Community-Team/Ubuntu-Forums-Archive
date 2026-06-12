---
title: "[Ubuntu] Visual Studio 2010 compile to Ubuntu"
date: 2010-11-29
forum: Packaging and Compiling Programs
---

### Post by BlueSpecial on 2010-11-29
I use Visual Studio 2010 to develop my apps.

I want to know if there's a way to compile my apps on Windows environment as a Linux package.

Thanks.

---

### Post by BlueSpecial on 2010-11-30
I was researching a bit about this...

Would this be a way to go?:

[http://mono-tools.com/](http://mono-tools.com/)

---

### Post by SevenMachines on 2010-11-30
I take it you mean 'what language should i use to have my apps run on both windows and linux?'

Probably more detailed answers in the programming forum but mono, python, and java are all choices that, in theory at least, should run on all their respective supported platforms. Although, at least in my previous years ago experience of java its not always as platform independent as it claims :)

But the music player banshee is an example of a fairly large app running on mono in windows/linux, the popular cross platform Eclipse IDE is java, and i can at least think of the bittorrent thingy deluge as an example for python on windows and linux. There are plenty of other examples but in short, all three languages are fine as far as i'm aware.

For natively compiled languages such as c or c++ its still possible but much more tricky :).

---

### Post by SevenMachines on 2010-11-30
Just to add, if you go for mono then you should look at monodevelop (in the repositories), its quite a nice ide, i think designed with visual studio users in mind. itll import your visual studio stuff too

---

### Post by directhex on 2010-11-30
> **BlueSpecial said:**
> I use Visual Studio 2010 to develop my apps.

I want to know if there's a way to compile my apps on Windows environment as a Linux package.

Thanks.

If you develop your apps using C#/VB.Net and WinForms or GTK# (not WPF), and target .NET 3.5 (not 4.0), and you aren't a bad coder (i.e. you use System.IO.Path.Combine to construct paths, and don't crash when reading the registry gives a NullReferenceException), then they'll run unmodified on Ubuntu. Tomboy and gBrainy, installed by default, are .NET apps.

---

### Post by BlueSpecial on 2010-11-30
Thanks I will try and test MonoDevelop.

My main goal is: I have some apps already made on VB.NET and I want to port them to Ubuntu.

Never tried to run them under WINE but my objective is to make a native Linux package...

---

### Post by directhex on 2010-11-30
> **BlueSpecial said:**
> Thanks I will try and test MonoDevelop.

My main goal is: I have some apps already made on VB.NET and I want to port them to Ubuntu.

Never tried to run them under WINE but my objective is to make a native Linux package...

Wine is for Windows apps. .NET apps are not Windows apps... well, not by definition anyway.

In case I wasn't clear: apps compiled with VS.NET will run on Ubuntu, via Mono (i.e. without Wine). You don't need to change IDE unless you want to.

---

### Post by BlueSpecial on 2010-11-30
What I meant was making a Windows setup and try to run it under Wine... sorry for confusion.

So all I need is Mono, compile under it on VS and presto! ;)

Many thanks.

---


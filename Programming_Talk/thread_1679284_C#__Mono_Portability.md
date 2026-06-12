---
title: "C# / Mono Portability"
date: 2011-01-31
forum: Programming Talk
---

### Post by VorpalBunny on 2011-01-31
I just got an assignment to write a C# GUI app for school. I've been kind of anti-mono in the past, but I figure using it now is better than installing Windows just to do the project. My question is, if I develop with mono on Linux using the winforms API instead of GTK#, can that source code just be plugged into Visual Studio and compiled with no problem? Preferably it should not need any tweaking since the students are grading each other's programs as a collaborative exercise, and I doubt most of my peers would be able to get it working if it wasn't handed to them as a ready-to-go Visual Studio project.

I pored through the mono website, but the FAQ's seemed geared to getting programs written on Windows to run in Linux, and I'm going the opposite way. :(

/offtopic /rant
The whole CS department here is heavily MS-centric, and when the professor mentioned we would be using C# people were literally thrusting both arms into the air in celebration. It was disgusting the way they looked at C#/.NET as some sort of programming Holy Grail. :roll:

---

### Post by fct on 2011-02-01
My personal choice would be to use the tools everyone else use in class to avoid problems (did so in college so I didn't spend time solving incompatibilities).

If you are brave, just make sure you're using, apart from the System.Windows.Forms namespace, APIs that are compatible with Windows. According to the FAQ:

[http://www.mono-project.com/FAQ:_Technical](http://www.mono-project.com/FAQ:_Technical)

> Compatibility

[I]Can Mono run applications developed with the Microsoft.NET framework?
[/I]
Yes, Mono can run applications developed with the Microsoft .NET Framework on UNIX. There are a few caveats to keep in mind: Mono has not been completed yet, so a few API calls might be missing; And in some cases the Mono behavior might be incorrect.

Mono today ships with support for the .NET 2.0 API for the supported namespaces; Support for the 3.0 and 3.5 and 4.0 API is not complete.

*I am using Visual Studio 2008 (or 2005), will Mono run my code?*

Visual Studio 2005 and 2008 produces code that targets from .NET 2.x up to 3.5 API. This means that most code will work until you hit an API that has not been implemented in Mono.

This will appear as a TypeLoadException when you try to use a method or a property from one of the assemblies.

To make Visual Studio produce 1.1-based applications see this blog post here. 

Edit: a more related article for your question here:

[http://www.devx.com/dotnet/Article/43857](http://www.devx.com/dotnet/Article/43857)

---

### Post by directhex on 2011-02-01
> **VorpalBunny said:**
> My question is, if I develop with mono on Linux using the winforms API instead of GTK#, can that source code just be plugged into Visual Studio and compiled with no problem?

Yes. MonoDevelop's internal project/solution format these days is Visual Studio 2008 files.

Your BINARY will run unmodified on Windows.

However, please remember that there's no designer for designing WinForms in Mono, so if you want to target that toolkit, you need to do the GUI manually in code, not in a GUI designer.

---

### Post by qrazi on 2011-02-02
I recently needed to write in .net 1.1 and decided to use MonoDevelop for it. Compiled .dll works fine in production. Don't know about interchangeability with Visual Studio though.

---


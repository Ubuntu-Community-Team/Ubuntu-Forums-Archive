---
title: "Question about Mono (as in .NET... not the disease)"
date: 2008-06-02
forum: Programming Talk
---

### Post by dickohead on 2008-06-02
Hi all,

I am currently writing an application with Visual Studio (*ducks*) in C#, as I've not yet got my head around MonoDevelop and Mono (mostly it won't run...).

One of the things I am constantly perplexed about is how a complied application or some source code carries over from one platform to the next.

Can I write my code using both MonoDevelop AND VisualStudio (ignoring gtk# and WindowsForms for a second - just business logic junk / console) and then compile it to run on Windows and then on Linux or MacOSX? Or do I need to have Mono installed in all platforms to run applications written with MonoDevelop?

So... If I write code in one platform will it *Just Work* on the other (again - ignorning interfaces), or do I need source code for Windows, Linux and MacOSX?

---

### Post by irrdev on 2008-06-02
Let me explain .NET. "Compiled .NET applications" are actually files compiled in the MSIL (MicroSoft Intermediate Language). Althought a .NET "executable" may have an .exe ending, it is really an interpreted program which is just like Java's ".class" and ".jar" files. Programs compiled with MSIL require an interpreter to run them. On Windows you can use .NET, on Linux you can use Mono. .NET currently supports MSIL 3.5 and older. Mono, on the other hand, currently supports MSIL 2.0 and older. That means that if your application is compiled with .NET 1.0, 1.1 **or** 2.0, then it should run with no problems with Mono. Mono already includes some support for MSIL 3.5, but it is still incomplete. 

It should be noted that Mono still is missing some often unused methods in System.Windows.Forms, so large and complicated GUI applications may fail to run on Mono. To make sure that this is not the case, you can run the [Mono Migration Analyzer]("http://www.mono-project.com/Moma") on Windows to test your .NET program's compatibility. 

Since Mono solely aims to copy .NET's MSIL support, any application compiled with Mono is guaranteed to work with .NET. Just be careful not to use the GTK# libraries, however, since the GTK# libraries are not included with the .NET interpreter. ;)

[COLOR="Blue"]**_EDIT_: Oops, big oops!** I was completely wrong about Mono still missing certain Windows Forms methods. [Read this announcement to learn more]("http://jpobst.blogspot.com/2008/05/big-finale.html"). Mono is finally 100% .NET 2.0 compliant. Yay! Any application compiled with .NET 2.0 on Windows will run perfectly fine with Mono, and vice versa! :)[/COLOR]

---

### Post by Quikee on 2008-06-02
> **irrdev said:**
> 
It should be noted that Mono still is missing some often unused methods in System.Windows.Forms, so large and complicated GUI applications may fail to run on Mono. To make sure that this is not the case, you can run the [Mono Migration Analyzer]("http://www.mono-project.com/Moma") on Windows to test your .NET program's compatibility. 

Note that Miguel just recently announced that [Winforms 2.0 API is complete]("http://tirania.org/blog/archive/2008/May-13.html").

Edit: OH.. you figured it out yourself. ;)

---

### Post by dickohead on 2008-06-02
So...
To develop on both platforms at once I would install .NET 2.0 in Windows (assuming that MSIL numbers correspond to .NET numbers?), and use the same version for Mono in Linux... when you write that out it's kind of an abvious statement! :)

And...
To build an interface for ALL three platforms, ASP (ugghhh) is the way to go, or do we have a PHP hook in?
But to build a native GUI for each, I would need one per platform? (GTK/Glade, WindowsForms and Cairo[?].)

Finally...
What is the advantage of having  IronPython (when it's ready)? *ducks again*

Sorry for the stupid questions!

---

### Post by kragen on 2008-06-02
> **dickohead said:**
> What is the advantage of having  IronPython (when it's ready)?

My understanding of IronPython is that its simply a python interpreter which has the ability to use any .Net 2.0 libraries in python.

So for example you can make calls to System.Windows (and hence build a windows app in python), or System.Web (and make web applications in python), or reference any of your own .Net assemblies.

---

### Post by pmasiar on 2008-06-02
> **kragen said:**
> My understanding of IronPython is that its simply a python interpreter which has the ability to use any .Net 2.0 libraries in python.

More exactly, it is reimplementation of the (C)Python, using .NET as base libraries instead of C ones.

This is reason why some C-based modules are still missing (and there is effort to make independent Python-based implementation, alongside native .NET based).

Because IronPython sits on top of .NET, you can do cool tricks like issue .NET call in python shell to manipulate GUI, mix and match C# and Python, etc.

There is also completely free reimplementation of IronPython, FePy.

---

### Post by dickohead on 2008-06-03
And we like to have Python in .NET because..?

Sorry to ask these questions, but I've not been able to find any answers after many web and wikipedia searches.

I have used Python, but only while reading a book and doing some tutorials, I've not done anything extensive with it (yet), so if my above question sounds ignorant, it probably is.

---

### Post by irrdev on 2008-06-03
> And we like to have Python in .NET because..?

The single biggest advantage is simply the use of Python over any other of the .NET languages. It is probably more of a personal choice than anything else, since the platform base obviouly remains the same, and the languages themselves offer similar functionability. If you already know Python, but not C#, Visual Basic .NET, etc., then using IronPython would be a natural choice. That said, if you don't any of the above languages, you are probably better off learning one of the .NET languages from the outstart. 

It should be noted that neither the .NET or Mono runtimes come with IronPython support. Your end-users will have to install .NET/Mono-Python-IronPython to simply run your applications. Programs written with C# or Visual Basic only require the .NET/Mono runtimes, thus making deployment much easier, particularly on Windows. Also, using IronPython creates a *second * layer of interpretation, as both the MSIL and Python runtimes execute as separate processes. 

As I said above, if are already a Python user, then IronPython may provide an easy transition to the .NET platfom. Otherwise, I would recommend that you learn one of the .NET languages directly. C# is the most popular of the .NET languages, but Visual Basic also provides an easy-to-use struture aimed at both beginners and intermedaite users. By using a .NET/Mono platform language, you are also able to make use of either Visual Studio or Monodelop, which is a huge advantage. Both are great IDEs, and both sport great integration with their respective platforms. Indeed, .NET on Windows has achieved much of its popularity over Java due to the fabulous features found in Visual Studio. ;)

---

### Post by dickohead on 2008-06-03
Awesome.

You've all been fantastic help!

I'll stick with C# (have done plenty of VB for years.. ughhh) and see what I can come up with, hopefully I'll have my first cross platofmr out before the end of the month eh?

:)

Thanks again to all of you!

---

### Post by kragen on 2008-06-03
> **dickohead said:**
> And we like to have Python in .NET because..?

Sorry to ask these questions, but I've not been able to find any answers after many web and wikipedia searches.

I have used Python, but only while reading a book and doing some tutorials, I've not done anything extensive with it (yet), so if my above question sounds ignorant, it probably is.

.Net allows you to develop against a common set of libraries in your own preferred language, so you can develop in C#, VB or even C++ while all the time referencing the same set of libraries - it means less code to maintain for library developers (one library, rather than one for each language), as well as fewer things for users to install.

IronPython is just another choice on top of the existing languages, but on top of that because its interpreted rather than compiled, it potentially makes it very handy as a scripting language. (The alternative would be to dynamically compile your code just before you run it, which is very easy with .Net and people do do it).

---


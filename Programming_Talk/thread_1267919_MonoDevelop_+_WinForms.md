---
title: "MonoDevelop + WinForms?"
date: 2009-09-16
forum: Programming Talk
---

### Post by dchurch24 on 2009-09-16
Hi all,

I'm a C#/Vb.net developer but have been using Python for my development on Ubuntu.

I haven't needed until recently to have any Gui stuff, but now I do, so I looked at MonoDevelop. I've googled round and I keep coming across something called "MonoDevelop WinForms", but I don't understand what it is.

I would ideally like a forms editor similar to the one in VS; is WinForms my answer?

If so, where do I get it?

---

### Post by gtr32 on 2009-09-16
Mono should be installed by default and it contains WinForms. 

[http://www.mono-project.com/WinForms_Getting_Started_Guide](http://www.mono-project.com/WinForms_Getting_Started_Guide)

With Monodevelop you won't get GUI builder, you have to do it by code or use Visual Studio in Windows to build them. Another option is to use GTK# instead of WinForms.

---

### Post by dchurch24 on 2009-09-16
Ahh - thank you.

So I could, theoretically, make the forms in VS in a VM, then copy the code the forms designer creates into Mono, and I'm up and running?

---

### Post by gtr32 on 2009-09-16
In practice too. You can create the whole binary in VS and run it with Mono in Linux. You just have to pay attention to your code and avoid platform dependent code.

Instead of writing code like this:

string myNewLine = "This is a line ending with newline.\n"

use this:

string myNewLine = "This is a line ending with newline." + Environment.Newline;

Another obvious is the directory separator which is different in Windows and Linux:

[http://msdn.microsoft.com/en-us/library/system.io.path.directoryseparatorchar.aspx](http://msdn.microsoft.com/en-us/library/system.io.path.directoryseparatorchar.aspx)

---

### Post by directhex on 2009-09-16
WinForms is the System.Windows.Forms namespace. MonoDevelop has no integrated support for designing GUIs with WinForms - instead, it has an integrated editor for GTK# GUIs. You can hand-write WinForms GUIs if you want to, though

---

### Post by phrostbyte on 2009-09-16
GTK# is a better option if you are writing apps that will primarily be run on Linux. It is the native widget toolkit of the Gnome desktop (Ubuntu's desktop system).

---

### Post by dchurch24 on 2009-09-17
Thanks guys.

I'm struggling to understand a little though, having come from a Visual Studio background, I have difficulty in understanding how GTK+(#) ties in with the IDE.

e.g. In VS, I would 'draw' a button, then double click it and I'm ready to code for the click_event. Does this work the same way?

Mainly this will be for Ubuntu dev. - I have a huge project that I've been working on over the past year for home (home automation, integrated with MythTV on a Windows Front End - I originally had Xubuntu on the machine and was going to develop it in that, but I just couldn't get the touch-screen serial drivers working quite right - I can explain more if anyone is interested, I am going to release the code under Gnu soon), but I started that in VB.net to get used to the syntax (I would usually have used C# as my preference).

If GTK is the way to go, would it be preferable to stay with Python for my Linux development. I am told that these compliment each other well.

I'm not too bothered about the language - most are very similar IMO, I'm just trying to find the best way to go, with the most amount of support should I get stuck ;-)

---

### Post by dchurch24 on 2009-09-17
> **directhex said:**
> WinForms is the System.Windows.Forms namespace. MonoDevelop has no integrated support for designing GUIs with WinForms - instead, it has an integrated editor for GTK# GUIs. You can hand-write WinForms GUIs if you want to, though

Hi, I've installed GTK# and MonoDevelop, but I can't see anywhere how to instigate the integrated editor.

I'm probably just being daft.

---

### Post by directhex on 2009-09-17
> **dchurch24 said:**
> Hi, I've installed GTK# and MonoDevelop, but I can't see anywhere how to instigate the integrated editor.

I'm probably just being daft.

Create a new GTK# project, and in the solution pane, double-click the interface element you want to edit (the default being MainWindow) from the User Interface section

GTK is container-based rather than pixel-based, so you draw your UI using containers (VBox, HBox, Table, and so on), a bit like drawing a website using <table > rather than with <div style="position:absolute" >

There's no default hooking of events from double-clicking it in the designer, but if you select the button or whatever, take a look in the Signals tab of the Properties pane, and you can double-click on something in the list (i.e. Clicked) to insert the boilerplate code & take you there

---

### Post by dchurch24 on 2009-09-17
I think I must have a different version, or I've cocked something up.

I don't get a 'User Interace' section in the solution pane.

If I double-click on 'main' or 'mywindow', the source code loads, but no integrated designer.

---

### Post by directhex on 2009-09-17
> **dchurch24 said:**
> I think I must have a different version, or I've cocked something up.

I don't get a 'User Interace' section in the solution pane.

If I double-click on 'main' or 'mywindow', the source code loads, but no integrated designer.

Can you post a screenshot?

---

### Post by dchurch24 on 2009-09-17
[[IMG]http://thumbnails18.imagebam.com/4913/41b21649129553.gif[/IMG]](http://www.imagebam.com/image/41b21649129553)

---

### Post by dchurch24 on 2009-09-17
oops!

The designer is only available for C# - I was using VB.

Sorry :oops:

---

### Post by directhex on 2009-09-17
> **dchurch24 said:**
> oops!

The designer is only available for C# - I was using VB.

Sorry :oops:

That'd do it

VB.NET has always been something of a red-headed stepchild within the Mono project - partly because unlike C#, it's not a published standard. I packaged it to be sure people could use it, but it's fairly common for it to be an afterthought in things like IDE support

---

### Post by dchurch24 on 2009-09-17
Hey, no problem.

I prefer to use c# in any case.

The reason I started in VB is because I'd written a big chunk of my project in VB for Windows, it seemed to make sense to do keep it the same if at all possible (despite there being large chunks of Python floating about the same project ;-) )

It's looking good though! The Beta Windows version is a bit slow, but it's looking amazing.

---


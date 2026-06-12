---
title: "Convert Delphi source code to OS-neutral Free-pascal?"
date: 2007-12-25
forum: Programming Talk
---

### Post by saphil on 2007-12-25
So assume I am a beginner and do not really write pascal yet.  I have an EXE that came with source code in  .pas but which starts out with the windows library (that has the entire win32 api in it).  I want to build the program in a platform-agnostic way and then maybe use the freePascal compiler to compile it for my Ubuntu and maybe fedora7.  

I am not entirely sure how the program's windows gui would look, but if I have to, I will go over to a Windows machine to look at it.

I am mostly sure I have the whole pascal compiler on my machine.  I installed the package that contains it and cpp and so on.  I also installed Lazarus IDE for Pascal and something like 29 dependencies.

Would I be better off going into painting with oils, or actually taking a class in programming, or just going over to the win machine to use exe apps than attempting to adjust this source code?

---

### Post by CptPicard on 2007-12-25
It's the Windows-specific GUI stuff that is going to be your worst sticking point, and there really is not much alternative to just rewriting from scratch against some crossplatform (or Linux-specific) GUI toolkit, which in turn will probably force you to switch languages, away from Delphi/Pascal.

If you really need to be using that application, you might try running it under Wine.

---

### Post by saphil on 2007-12-26
so once again, taking the lazy way is more work. :-(
Thanks for the advice.  I am probably going to have to actually learn how to code.  

Wine almost never works how I want it to.  I suspect it is the chair to keyboard interface being buggy..

---

### Post by LaRoza on 2007-12-26
> **saphil said:**
> 
Wine almost never works how I want it to.  I suspect it is the chair to keyboard interface being buggy..

:lol:

Don't blame yourself, Windows software can be difficult in Windows.

---

### Post by saphil on 2007-12-26
Thanks for letting me off the hook, LaRoza

---

### Post by Xealot on 2007-12-27
If you have the time and patience, You can convert the code into using GTK2 or QT, There are quite a few GTK2 tutorials for Free pascal

[http://www.freepascal.org/packages/gtk/tutorial/pgtk-contents.html]("http://www.freepascal.org/packages/gtk/tutorial/pgtk-contents.html")

[http://www.geocities.com/mazen_neifer/GTK_help.html]("http://www.geocities.com/mazen_neifer/GTK_help.html")

Also, you might want to look into Glade, as it will be extremely helpful when you want to create GUI applications "from scratch"

And last but not least, The GTK API documentation
[http://www.gtk.org/api/2.6/gtk/index.html]("http://www.gtk.org/api/2.6/gtk/index.html")


Good luck and have fun, if you are still interested in any of the above,
I can dig out some old code I made using Glade in a Delphi application designed for FPC. 

 - X

---

### Post by Klipt on 2007-12-28
If you already have Lazarus installed, that's probably the easiest way to write cross platform GUI programs in Pascal. Lazarus is meant to be an open source clone of Delphi, which is a RAD (rapid application development) IDE for Pascal. It includes Glade-like form designer functionality but all built into the IDE.

The question is, how was the original program written? If it's in Delphi, there are tools to help convert Delphi projects into Lazarus projects. Try asking on the [Lazarus forums](http://www.lazarus.freepascal.org/modules.php?op=modload&name=PNphpBB2&file=index).

If it's just Pascal code calling the raw Win32 API, I think you'll have to rebuild the GUI from scratch - that will be more difficult.

---

### Post by saphil on 2007-12-29
Thanks Xealot & Klipt

I will woodshed what you have sent.  I am pretty sure it is calling direct to the windows api, and that is where lazarus puked on compiling the main.pas file (which I am assuming is the one to get compiled first...)  I do not have a win32 library.pas to build first.

I am probably going to look at the gtk stuff and glade and see about building from there.  I would like to see the glade code you did, Xealot. I have always done best learning a new thing when I had a strong case to model from.  

Happy New year!
-Wolf

---


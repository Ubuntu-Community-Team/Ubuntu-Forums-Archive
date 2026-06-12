---
title: "Some MonoDevelop questions"
date: 2009-04-13
forum: Programming Talk
---

### Post by lemmof on 2009-04-13
I have some pretty dopey questions about MonoDevelop, and I've searched my fingers off and can't find any help.  I'm using MD 2.0 in Jaunty.

Number one:  How do I set project dependencies?  I have this situation: I have two C++ projects.  One project is a static library, and another project is a small program that uses the library.  The problem is that MonoDevelop doesn't realize that one depends on the other.  If I build the whole solution, it builds the application first!

Two: How on earth do I debug??  I can see that I can set breakpoints, but how do I start the debugger?  I've checked the "Debugger" toolbar in the toolbars context menu, but no toolbar appears.

I've tried Anjuta, Code::Blocks, and KDevelop.  All of them have had one or two problems that prevent me from getting anything done.  I really want MonoDevelop to be the one that works out.

---

### Post by johnl on 2009-04-13
For your first question, right click on your main project.  In that menu you should find something like "References" (I believe it's called).  Click on that. It will let you add a reference to an existing library, an external library, or an existing project.

As for the debugging, I haven't used MD in a while, but when I did the debugger was not finished.  You should check the website or mailing list and see if the debugger is available in the current version.

Hope this helps.

Edit:  Just re-read your post;  MonoDevelop was designed for C# (.NET) projects.  I don't know if there is a 'references' concept for C++ projects in MonoDevelop. Additionally, I doubt that MD has built in GDB support for debugging C++ code.

---

### Post by lemmof on 2009-04-13
> **johnl said:**
> For your first question, right click on your main project.  In that menu you should find something like "References" (I believe it's called).  Click on that. It will let you add a reference to an existing library, an external library, or an existing project.

As for the debugging, I haven't used MD in a while, but when I did the debugger was not finished.  You should check the website or mailing list and see if the debugger is available in the current version.

Hope this helps.

Edit:  Just re-read your post;  MonoDevelop was designed for C# (.NET) projects.  I don't know if there is a 'references' concept for C++ projects in MonoDevelop. Additionally, I doubt that MD has built in GDB support for debugging C++ code.

I didn't realize it until now, but that is what the "Packages" thing under the project is for.  You can add dependencies there.  After I added my library there, it now builds properly.

As far as debugging, the MD 2.0 release notes say that it supports GDB.

I tried debugging a C# program as well, but I couldn't figure that out either.

Another thing is that I tried looking at the help for MD, but the help option in the menu only results in an error "Could not start monodoc :" followed by a lengthy stack trace.  Googling for that phrase only finds the source code that generates the error!  Maybe I need to report a bug for that?

---

### Post by days_of_ruin on 2009-04-13
You need to install monodoc to use help.
EDIT: has anyone figured out how to use the debugger yet?
And is there a way to make MD show application output better?

---

### Post by lemmof on 2009-04-13
Okay.  I figured it out.  You simply have to install the package monodevelop-debugger-gdb for C++ (or monodevelop-debugger-mdb for C#).

It really isn't an obvious solution.  Why isn't that included?  What are you going to do with an IDE if not debugging?

---

### Post by schmendrick on 2009-04-14
> What are you going to do with an IDE if not debugging? 

good question, i always wonder that myself. 

but FYI the mono+monodevelop guys survived without a debugger in monodevelop for maaaany many months (or years? anybody having a number?), so maybe they didnt want to overstrain their community by integrating it by default ;)

---

### Post by directhex on 2009-04-14
monodevelop-debugger-gdb package installed?

---


---
title: "Mono question re: WinForms and Gtk#"
date: 2007-03-29
forum: Programming Talk
---

### Post by samjh on 2007-03-29
Sorry if this has already been asked.  I tried a search but couldn't find a satisfactory answer.

I'm considering a small project to develop an application for multiple users to read and write to a flat database (such as an Access .mdb).  The target platform for this is Windows XP Professional SP1.

But my home computer is Linux-only (specifically Ubuntu).

I am trying to choose between Java and Mono.

Four questions about Mono:

If I write an application using Mono on Linux, will I be able to do a simple copy-paste of the binary to Windows and run it under MS .NET Framework 1.1?

Will I need to install Gtk# on Windows?

Am I able to develop in Linux using WinForms?

What are some pitfalls I need to be aware of?

Thanks in advance for any assistance.

---

### Post by mardawi on 2007-03-29
If you use winForms then you can just copy and paste to run your app on windows (with .net 1.1 installed), but unfortunately, there is not gui designer for winForms in monoDevelop. on the other hand, you can use gtk#, but it requires gtk to be installed on windows as well as you need to copy the gtk# dll from mono libraries, but you can use the gui designer in monoDevelop.

be aware that there is no debugger in monoDevelop (at least i can't use it :( ) and it's not so stable (sometimes it just shutdowns while i'm at the middle of writing something :( )

so, you can program apps that uses winForms in linux and you can run them on windows without installing anything.

Another things that you need to know, when using winForms i noticed that fonts (and maybe borders) are sometimes larger in  linux than windows. so, don't waste your time designing a neat gui in linux, it might not look the same in windows!

---

### Post by samjh on 2007-03-30
Thanks a lot Mardawi! :)

---

### Post by Nxx on 2008-11-24
I cannot run the GTK# designer what am I doing wrong? All plugins are enabled.

---

### Post by directhex on 2008-11-24
> **Nxx said:**
> I cannot run the GTK# designer what am I doing wrong? All plugins are enabled.

Are you looking at the right thing? You started a new GTK# project, Opened the MainWindow.cs file, and clicked the "Designer" button underneath the code window?

---


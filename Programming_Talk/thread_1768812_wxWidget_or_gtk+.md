---
title: "wxWidget or gtk+"
date: 2011-05-27
forum: Programming Talk
---

### Post by Blackbug on 2011-05-27
i am in process to design a new application.
for the ui part, i was wondering which is better to use
wxwdiget or gtk+?

---

### Post by juancarlospaco on 2011-05-27
wx

---

### Post by Simian Man on 2011-05-27
Definitely wxWidgets, *especially* if you have any plans to run it on Windows or Mac.

---

### Post by Blackbug on 2011-05-27
yes i do, i am creating application on linux, but its required on windows as well..

---

### Post by JupiterV2 on 2011-05-27
1. wxWidgets is a native C++ toolkit where GTK+ is a C toolkit. You can use gtkmm language bindings for GTK+.

2. I've never written anything with wxWidgets but from what I've read, it does seem to be more portable. GTK+ is portable, too, but there are a few gotcha's. It takes some wrangling to make a GTK+ app cross-platform.

3. If you're writing a Linux only app, then portability concerns just don't matter.

As said, time and time again, there is no one silver bullet. wxWidgets does appear to be easier to port applications with but if you are writing your app in C, then you're SOL. And there's Qt to consider as well, another C++ native toolkit.

Your language choice makes a big difference. If you're using Java, I recommend Swing. If you're using Python, probably PyGTK (is there a wxWidgets language binding for Python?). The list goes on...

I suppose the point is, we need more specifics to point you in the right direction.

---

### Post by Blackbug on 2011-05-27
well, yes i think wxPython do exists..
and in one of my earlier post, people were advising clearly to use python for UI part.
 
Although, as of now I am stickin with c++ for everything once my application has it basic structure and working, later i will try to replace UI with python ( just to learn and see the difference ) or should really choose python now?

---

### Post by Blackbug on 2011-05-27
but core logic part of the application is in c++

---

### Post by cgroza on 2011-05-27
> **JupiterV2 said:**
> 
Your language choice makes a big difference. If you're using Java, I recommend Swing. If you're using Python, probably PyGTK (is there a wxWidgets language binding for Python?). The list goes on...

Yes, there is. It is called wxPython. If the OP knows python, I would suggest he learns the toolkit in this language because it takes a lot of burden and lets you focus on the toolkit aspects, not the language's.

---


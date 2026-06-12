---
title: "Before Visual Studio ?"
date: 2008-09-18
forum: Programming Talk
---

### Post by Fosfate on 2008-09-18
How were GUI's for applications created before any of the Visual Studios existed?

Or, for that matter, using C++ in a different IDE than Visual Studio, how is it possible to create user interfaces for applications? Were there other plug-ins used? To be more specific, how would Photoshop be coded in C++?

I'm kind of interested in some of the history of programming before drag and dropping for controls existed.

---

### Post by LaRoza on 2008-09-18
> **Fosfate said:**
> How were GUI's for applications created before any of the Visual Studios existed?

Or, for that matter, using C++ in a different IDE than Visual Studio, how is it possible to create user interfaces for applications? Were there other plug-ins used? To be more specific, how would Photoshop be coded in C++?

I'm kind of interested in some of the history of programming before drag and dropping for controls existed.

VS is a RAD tool. Dragging and dropping is good for quick simple apps. Useless for more complex apps.

Don't confuse VS with being a standard. Although GUI designers exist for many toolkits (see sticky under Programming Talk FAQ's), one can always code it manually.

This project (started by me ;)) has two GUI's both coded: [https://code.launchpad.net/sysres](https://code.launchpad.net/sysres)

Photoshop would be built by a large team of people with experts working on the various pieces of it. [http://library.gnome.org/devel/gtk-tutorial/stable/c39.html](http://library.gnome.org/devel/gtk-tutorial/stable/c39.html)

Visual Studio is a Windows only application by the way. Nothing on Linux was built with it, and Linux has much better GUI's than Windows.

Some IDE's have support for designing GUI's (Netbeans I think for Java, and Monodevelop for G#). However, most do not because there is not dictator controlling the languages and toolkits. There are designers for the various toolkits [http://ubuntuforums.org/showthread.php?t=772507](http://ubuntuforums.org/showthread.php?t=772507) but they (and VS) never have the flexibility of hand coding.

---

### Post by Fosfate on 2008-09-18
How would one manually code a GUI? Are there any web links on this?

*edit: nevermind, I see GTK+*

---

### Post by LaRoza on 2008-09-18
> **Fosfate said:**
> How would one manually code a GUI? Are there any web links on this?

*edit: nevermind, I see GTK+*

Keep in mind most hand coded GUI's are abstracted away.

Having all the code in main() is not usually done, but it is the trivial way to demonstrate.

---

### Post by armageddon08 on 2008-09-18
> **LaRoza said:**
> Keep in mind most hand coded GUI's are abstracted away.

Having all the code in main() is not usually done, but it is the trivial way to demonstrate.

Yes.....dividing the program into modules/functions is a really good approach which increases program efficiency as well as makes it easier for debugging.

---

### Post by jespdj on 2008-09-18
Microsoft Visual Studio has existed already for a very long time. When I started my job in 1996 I was writing software for Windows 3.1 and Windows 95 using Microsoft Visual C++.

---

### Post by LaRoza on 2008-09-18
> **jespdj said:**
> Microsoft Visual Studio has existed already for a very long time. When I started my job in 1996 I was writing software for Windows 3.1 and Windows 95 using Microsoft Visual C++.

1996? I was a kid then, but that is not a long time ;)

In terms of editors, Vi and then E**** have been around longer and are the editors of choice, not VS.

---

### Post by Idefix82 on 2008-09-18
Actually, until about 1999 or 2000, I don't remember, VS wasn't that widely used for commercial applications. Borland C++ Builder was generally accepted to be the more powerful IDE. They had their own GUI classes library, called the VCL, as opposed to Microsoft's MFC. Eventually, they stopped developing the C++ Builder but have now released a brand new version again, after some 8 or 9 years' break.

I guess in the old days, one wrote an application, which actually drew pixel by pixel the windows and controls and received interrupts from the mouse controller when, say, a mouse button was clicked.

---

### Post by dwhitney67 on 2008-09-18
In the old days, I developed under Unix systems.  The "IDE" used was vi, and GUIs were developed using a combination of X-Motif and DataViews.

In the mid-90s I had heard of MFC and VS, but never took it seriously; perhaps this was because Windows couldn't run for more than a day without crashing.

---

### Post by LaRoza on 2008-09-18
> **dwhitney67 said:**
> perhaps this was because Windows couldn't run for more than a day without crashing.
Ah the good old days... oh, wait, you can still get that for $150!

---

### Post by tinny on 2008-09-18
Alot of people still code GUI's. I code my Java Swing GUIs because I want full flexibility. I have used GUI editors in the past and have found that at some point they all hit the wall eventually.

---


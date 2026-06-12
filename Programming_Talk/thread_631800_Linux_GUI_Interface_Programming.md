---
title: "Linux GUI Interface Programming"
date: 2007-12-04
forum: Programming Talk
---

### Post by JupiterV2 on 2007-12-04
As an Ubuntu user, I am of course familiar with Gnome. I am currently learning how to ues the GTK+ toolkit to develop a user interface for the program I'm currently writing. I opted to learn how to write the GUI from scratch via GTK rather than via Glade as I've found it better to learn hard way first, before using the easy way.

It has occured to me, however, that while applications created using the GTK+ toolkit can be run on distribution using KDE as their desktop environment (Like Kubuntu) it may not display correctly as not all features will work in KDE.

Is there a more universal toolkit that will display equally well on all X-Windows implementations? Or, is there a list of what specific features of GTK don't work in KDE?

---

### Post by davidgarcin on 2007-12-04
well, there's always Java or Qt....

EDIT:  by Java I mean a toolkit such as NetBeans

---

### Post by bruce89 on 2007-12-04
No.

QT and GTK+ are seperate things, so things in GTK+ look daft of KDE and vice versa.

---

### Post by davidgarcin on 2007-12-04
I realize Qt and GTK+ are different.... but Jupiter is looking for an alternative to GTK+

---

### Post by MicahCarrick on 2007-12-04
> Is there a more universal toolkit that will display equally well on all X-Windows implementations? Or, is there a list of what specific features of GTK don't work in KDE?

GTK+ works fine on KDE (and Windows and OSX for that matter), however, it might not look like applications targeting KDE, however, functionally it will work. The same is true the other way around.

There are a few GLib functions which might not be available in Win32 in which case the API documentation will say as much--but they are relatively rare. 

As far as obtaining a "native" look on each platform, you may want to check out wxWidgets.

---

### Post by JupiterV2 on 2007-12-05
Thanks, that's exactly what I was looking for. 

I was wanting to shy away from Java as I've heard it's notoriously slow in comparison to more native toolkits that don't rely on a runtime environment. It's not that I don't want to use GTK+, I just wanted to make sure it was the best tool for the job. Even though the fork may work with Chili,  the spoon would work better.

I was planning on writing a Windows port using the Win32 API. Is this better, though at lot more work, than simply requiring Windows users install GTK+ support libraries in addition to my program?

---

### Post by Luggy on 2007-12-05
For the love of god and all that is holy use QT.

The job I get paid to do has me writting a cross platform application and for that we use QT.

The first application we wrote used wxWidgets and doing the simiplist things such as laying out widgets on a dialog is a painful task. QT makes that task trivial.

Not only does QT handle GUI with ease it has a boat load of other classes to make your life so much eaiser.

QT also does a pretty good job of obtaining a native look, at least as far as Windows is concerned.

And as far as 'creating a windows port' all that you have to do is compile the same code on windows.

---

### Post by slavik on 2007-12-05
> **Luggy said:**
> For the love of god and all that is holy use QT.

The job I get paid to do has me writting a cross platform application and for that we use QT.

The first application we wrote used wxWidgets and doing the simiplist things such as laying out widgets on a dialog is a painful task. QT makes that task trivial.

Not only does QT handle GUI with ease it has a boat load of other classes to make your life so much eaiser.

QT also does a pretty good job of obtaining a native look, at least as far as Windows is concerned.

And as far as 'creating a windows port' all that you have to do is compile the same code on windows.
Just have to ask ... how is GTK+ difficult?

---

### Post by jespdj on 2007-12-05
> **JupiterV2 said:**
> I was wanting to shy away from Java as I've heard it's notoriously slow in comparison to more native toolkits ...
That was true in 2000 (Java 1.2, 1.3) but not anymore in 2007 (Java 5, 6).

---

### Post by Luggy on 2007-12-05
> **slavik said:**
> Just have to ask ... how is GTK+ difficult?

I haven't really played around with GTK much ( besides the odd hello world ). If you can easily set up your signals and slots and layout your widgets then I don't think it would be too bad.

My comments were more reserved for wxWidgets and how much a pain in the *** it is to do stuff with it.

That and using QT to create a cross platform application is a snap.

---


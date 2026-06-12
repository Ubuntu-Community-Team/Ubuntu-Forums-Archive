---
title: "How do I use MonoDdevelop Stetic Widgets Pallete?"
date: 2006-05-08
forum: Programming Talk
---

### Post by DA_uf on 2006-05-08
I'm new to Mono and MonoDevelop and heard of this "Stetic" GUI designer.

I'm using Ubuntu Dapper Beta 2 on AMD64 with MonoDevelop 0.10.

I click File | New Project...
I create a test project "test1" from the C# Template | Gtk# 2.0 Project and click New.

Happily, it actually builds and runs with Run | Run.  I close this newly built app.

I see a "Widgets Palette" and I am assuming there should be some sort of blank window I can drag and drop widgets onto.  Perhaps even the same size as the window that was displayed when this test app actually ran.

How do I proceed from here?  Left and right clicking on the widgets do nothing, although dragging seems to attempt to drag a widget; but where would I drop it?  I also see the Widget Properties section and Properties tab, but no properties are displayed when I click on any widget.

I cannot find any docs for Stetic on google.

---

### Post by llonesmiz on 2006-05-08
You need to open the file "MainWindow.cs" (double-click it in the left pane under the "Files" or "Solution" tabs). Then, if you look under the code you can find a button labelled "Designer". Click on it and you'll be able to design the interface.
Good luck.

---

### Post by DA_uf on 2006-05-08
Excellent.

It even has the properties and signals grouped according to their inheritance.

Thank you very much.

---


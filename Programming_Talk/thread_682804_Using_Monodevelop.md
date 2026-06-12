---
title: "Using Monodevelop"
date: 2008-01-30
forum: Programming Talk
---

### Post by lsutiger on 2008-01-30
Hi all!

I am migrating from MS Visual Studio 2003. When I start Monodevelop, my toolbox is empty. I go to Tools-->Add-in Manager-->IDE extentions. The GTK# Visual Designer is enabled. But still notta in the toolbox.

So, I go to Install Add-ons--> GTK-->GTK 2.4-->Forward. 
I get dependency errors.
Core 0.17.0 could not be found. GtkCore 0.17.0 could not be found.

Any help would be appreciated.

---

### Post by lsutiger on 2008-01-31
Anybody?

---

### Post by rufius on 2008-01-31
Can't reproduce. Can you go step by step as to what you're doing? I created a new GTK# project and have full access to the toolkit.

---

### Post by lsutiger on 2008-01-31
Ok
I installed Monodevelop through Synaptic package manager.

I start monodevelop.
I see the toolbox, but nothing is there.
Click on start a new project.
Click on Gtk# 2.0 Project. Name it something. Click on forward. States that GTK# 2.0 enabled. Click on ok.
At this point I have an empty toolbox on the left, the classbar, the program, and to the right, properties.

So I click on Tools-->Add-in manager. click on GTK# Visual designer. It is enabled (he enable button is not enabled out and the uninstall button is enabled. Add that to my original post  and that sums it up. I have nothing in the toolbox and do not see a platform in order to do any visual designing.

---

### Post by lsutiger on 2008-01-31
Hmm..I was fooling around and double clicked a method. Then this button shows up at the top "GUI builder". I click on that then default and "designer" shows up at the bottom.....strange.

---

### Post by rufius on 2008-02-01
Ya by default, monodevelop doesn't show you the toolkit unless you're editing an actual frame etc.

---


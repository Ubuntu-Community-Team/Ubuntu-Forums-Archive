---
title: "[GTK#] Are you missing an assembly reference?"
date: 2009-04-27
forum: Programming Talk
---

### Post by skkeeper on 2009-04-27
Hi everybody

When i was back at Windows I always loved .Net framework and all its capabilities, so now that I'm completely migrated over to Linux i heard about the Mono project and the GTK Sharp.

I decided to give it a try, but with a sample code which i copied from the book "Mono Kickstart" it just pops out this error:

[Task:File=Projects/grublst/grublst/MyButton.cs, Line=4, Column=14, Type=Error, Priority=Normal, Description=The type or namespace name `Drawing' does not exist in the namespace `System'. Are you missing an assembly reference?(CS0234)]

I dont know why this happens, maybe im missing some mono package, i dont know, i already installed mono and gtk2-sharp and some others.

EDIT: I just discovered i need to add manually the references i use to the reference folder inside Mono Develop.

Thank you for your time

---


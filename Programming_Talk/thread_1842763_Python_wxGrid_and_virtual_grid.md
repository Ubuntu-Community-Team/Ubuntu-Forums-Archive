---
title: "Python wxGrid and virtual grid"
date: 2011-09-12
forum: Programming Talk
---

### Post by DBQ on 2011-09-12
Hi Everybody,

I have an application written in python which uses wx as a GUI.  It uses wxGrid to display some data in a spreadsheet. Now, the problem is that once there are many rows, and many cells have attributes, the performance becomes so slow, it renders the thing unusable.  

I know that it is possible to rewrite the application to use virtualized grid. Although this will likely speed things up, it will require a great deal of time and effort to rewrite big chunks of the program.

Is there an easy way to override some methods of wxGrid to speed things up? i.e. without changing wxGrid used by the application.  

To put it another way, I want to speed up the grid performance in a way that is transparent (or as much as possible so) to the current code.

---


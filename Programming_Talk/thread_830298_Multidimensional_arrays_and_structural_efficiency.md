---
title: "Multidimensional arrays and structural efficiency"
date: 2008-06-15
forum: Programming Talk
---

### Post by kvk on 2008-06-15
I have a question regarding the most efficient way to construct code relative to the manner in which it is processed.

I've written a multi-species population dynamics model for marine fish as part of my PhD. It's written in a proprietary application that allows for some pre-written complex statistical analyses, but the basic format is C++, although the application has an interpretive function so that it accepts syntax that is not C++ and converts it into C++; I'm using the Borland compiler.

My code runs, but it is the digital equivalent of duct tape and popsicle sticks- a huge conglomeration of multidimensional arrays all subsetted into given equations by endless "if-then" and "for" loops. I want to clean it up and streamline it to reduce run time, but I have no idea how to approach this. The code is conceptually very, very simple, but I'm having problems finding resources that specifically discuss relational arrays and the best way to approach the structure for such a model that allows for the most efficient processing of the code. Is it better to have a smaller number of enormous arrays that are subsetted, or a larger number of smaller arrays that are integrated directly- that's the sort of thing I need to be able to examine.

What might be the best way to approach cleaning up this code?

Thanks so much!!

---

### Post by pedro_orange on 2008-06-16
Hi.

I don't know how your application works and what sort of data structures you are using and the operations you're using on them.
But as a general rule of thumb, you could try using some of the STL. Since these are very common structures and have associated methods which are arguably the most efficient way of doing it.
For some parts of the application a multi-dimension array may be exactly what you need, but I would not like to speculate without seeing the code first.

Hope this useless speculation helps.

---

### Post by kvk on 2008-06-16
HA! It's only useless speculation because I don't know enough to correctly describe the issue in under 2500 characters or more. :)

But it's not useless, and that's a great idea! I didn't even know the STL existed- it looks like a great resource to go through top to bottom.

Thanks so much! I really appreciate it.

---


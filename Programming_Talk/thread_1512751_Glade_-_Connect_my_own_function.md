---
title: "Glade - Connect my own function"
date: 2010-06-18
forum: Programming Talk
---

### Post by metal_merlin on 2010-06-18
Hello.

I am just learning glade. I would like to make my own function (one that is not belonging to the GTK+ available functions) and have it be called by a button. I have one file called "main.c" and another called "main.glade".

I tried keeping the function, let's call it "myFunction()", in the file main.c and calling it in glade in the button properties -> signals in the handler column. This did not work.

Can someone pls advise on how to add my own function to be called when i press the button? I have googled a lot to no avail.

Thanks in advance.

---

### Post by wkulecz on 2010-06-18
The best way I found to get started with Glade and GTK+ programming is:

[http://tadeboro.blogspot.com/2009/09/glade3-tutorial-1-introduction.html](http://tadeboro.blogspot.com/2009/09/glade3-tutorial-1-introduction.html)


The book "Foundations of GTK+ Development" by Krause from Apress (you can get it from Amazon.com) was also a big help at understanding some of the demented ideas behind GTK+ -- instead of using C++ or Objective-C because they wanted an object oriented programming aproach, they chose to re-invent it badly.  We are stuck with it or QT is would seem.  At least QT is based on C++, but it suffers from having too many versions that aren't truely upward compatable.

I'm not a fan of the object-oriented approach and prefer plain old C and good widget libraries -- LabWindows/CVI from National Instruments is my favorite, but its rather expensive, Linux support is poor, and you have to practically know the secret handshake to get them to sell it to you as they push their Labview product hard.

---


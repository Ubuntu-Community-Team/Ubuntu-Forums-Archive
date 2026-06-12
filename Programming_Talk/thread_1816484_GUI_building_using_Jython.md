---
title: "GUI building using Jython"
date: 2011-08-02
forum: Programming Talk
---

### Post by zhaotianwu on 2011-08-02
Hi, I'm building a small application GUI that features "drill-down" views and direct manipulation on personalized calendars. I intend to write this code in Jython (Python 2.7). However I'm just a new learner of Python. I've got 4 questions hoping some advice from senior programmers.  

1. I'm looking for Jython IDE in Windows/Ubuntu. I strongly desire that the IDE would support WYSIWYG GUI building, just like Visual Basic form manipulations.(I've already read the stickies) 
2. To implement "drill-down" feature in my GUI, Which library or libraries are most likely to be useful? wxPython or PyQt? Has anybody tried this before:  page.sourceforge.net 
3. Can I use some Java classes in Jython, even though they don't have a Python binding? (personally I assume this unbelievable, want some tips) 
4. Can I write a single code base and let it run on both Windows and Ubuntu? Without any extra tweak? 

Thanks!

---

### Post by cgroza on 2011-08-02
About the GUI part, wxPython is a CPython binding for wxWidgets, so you can't use it with Jython. I think the same goes for Qt too. There may be a way using JPype, but I am not sure about that.
You could use the Java's Swing to do your work.

About point 4, Yes you can. That is all Java and python is about.

---

### Post by akoskm on 2011-08-02
Or you could just use the Java bindings for Qt.
Available from PPA: [https://launchpad.net/~qtjambi-community/+archive/libqtjambi]("https://launchpad.net/~qtjambi-community/+archive/libqtjambi").

---

### Post by zhaotianwu on 2011-08-03
Thanks for the answers here. Please somebody help answer the rest points?:confused:

---

### Post by DangerOnTheRanger on 2011-08-03
> **zhaotianwu said:**
> Hi, I'm building a small application GUI that features "drill-down" views and direct manipulation on personalized calendars. I intend to write this code in Jython (Python 2.7). However I'm just a new learner of Python. I've got 4 questions hoping some advice from senior programmers.  

1. I'm looking for Jython IDE in Windows/Ubuntu. I strongly desire that the IDE would support WYSIWYG GUI building, just like Visual Basic form manipulations.(I've already read the stickies) 
2. To implement "drill-down" feature in my GUI, Which library or libraries are most likely to be useful? wxPython or PyQt? Has anybody tried this before:  page.sourceforge.net 
3. Can I use some Java classes in Jython, even though they don't have a Python binding? (personally I assume this unbelievable, want some tips) 
4. Can I write a single code base and let it run on both Windows and Ubuntu? Without any extra tweak? 

Thanks!

1. I think Eclipse fits the bill.
2. I think Swing would be best.
3. Yep. Just stick those Java classes in a place Jython can find it.
4. Yes. Assuming, of course, you don't make assumptions about things like file path seperators :p

There you go! :)

---

### Post by zhaotianwu on 2011-08-04
> **DangerOnTheRanger said:**
> 1. I think Eclipse fits the bill.
2. I think Swing would be best.
3. Yep. Just stick those Java classes in a place Jython can find it.
4. Yes. Assuming, of course, you don't make assumptions about things like file path seperators :p

There you go! :)

Thank you DangerOnTheRanger, could you take a quick look at this toolkit:  page.sourceforge.net

Is it something parallel to SWING or subordinate to it? Can I call it a GUI builder or a library?

---


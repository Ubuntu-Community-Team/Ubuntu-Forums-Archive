---
title: "Tkinter inconsistent behaviour"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by bwanamarko on 2012-08-06
I am getting inconsistent behavior with Python's Tk wrapper TKinter on Ubuntu 12.04 LTS (Precise Pangolin). I have the stock, always most recently updated via Ubuntu only, versions of Python, Tcl/Tk and matplotlib.
Python: 2.7.3-0ubuntu2
Tcl/Tk: 8.5.0-2
matplotlib: 1.1.1~rc1+git20120423-0ubuntu1

1) Apparently erratically sized windows each time I execute my application. I know that there could be a bug in my code, but on MS-Windows XP with Python 2.7.3 & Tk/Tcl 8.5.11 I get exactly the same Tk window everytime. The window consists of 5 frames. There are 3 frames in the master, root or top-level window, each uses the pack geometry manager with fill=BOTH (side=TOP is the default, correct?). The bottom frame has 4 button widgets and a message widget. This bottom frame sometimes also gets squashed to about half its height. The middle frame has 2 frames, one with pack(side=LEFT) & the other with pack(side=RIGHT). The right frame has 2 widgets, first FigureCanvasTkAgg, then NavigationToolbar2tkAgg both with pack(fill=BOTH). The left frame uses the grid geometry manager because it has lots of widgets. This is the frame that get's squashed sometimes seemingly at random, and when it get squashed, that's also when the bottom frame gets squished too. Sometimes the window shows up with everything, and sometimes this left frame is squashed and only the right frame with the matplotlib figure shows. If I resize the window, then everything shows up, so it's there, but the geometry manager is ignoring it, instead of just shrinking it to the size of the widgets within it, which is frustrating.

2) Validation is also inconsistent on Ubuntu, but not on MS-Windows. I tested these answers from SO ([http://stackoverflow.com/a/4140988/1020470](http://stackoverflow.com/a/4140988/1020470), [http://stackoverflow.com/a/4372831/1020470](http://stackoverflow.com/a/4372831/1020470) & [http://stackoverflow.com/a/8960839/1020470](http://stackoverflow.com/a/8960839/1020470)) on both machines. On MS-Windows the behavior is consistent and as expected, but on Ubuntu, seemingly at random, if I resize the window, or type too rapidly, it will stop validating. This might provide a clue about this mysterious behavior, as it probably has met an exception setting the validate key to None, which is the only reason it would stop validating. It may be a similar issue with the geometry manager, that causes it to set propagate to False?

So is there some Ubuntu process that is interfering with Tkinter?
Has anyone else ever experienced inconsistent Tkinter behavior on Ubuntu or anywhere else? I have read very few posts, on what seems like inconsistent behavior, but haven't found a good way to solve this yet. Any help would be greatly appreciated. Thanks!

---


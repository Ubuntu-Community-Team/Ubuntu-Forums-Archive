---
title: "Problem with matplotlib.pyplot in Lucid"
date: 2012-10-12
forum: Programming Talk
---

### Post by ncanna1 on 2012-10-12
I've been toying around with Python to work on a project for work, and am catching on pretty well.  I'm using the matplotlib, numpy, and scipy modules for computational data analysis and display stuff.  

I was using the versions in the repos for 10.04, but it turns out that scipy.optimize which has the curve_fit routine is not available through those versions.  I used pip to find and install the latest versions of numpy (1.6.2), scipy (0.11.0), and matplotlib (1.1.1).  However, when I try to interactively plot things in ipython --pylab, I don't get the pop-up plot display.

I've tried manually resetting the backend to use qt4Agg and made sure that I had the libqt4-dev packages installed, but that sadly has not helped me at all.  

No error messages show when I try to show(), but no window opens either.  I can still generate the plot objects and then save them using savefig(), but I can't seem to get the display to work.

Any ideas on what could be going wrong?

---

### Post by MadCow108 on 2012-10-12
have you tried upgrading ipython too?

---


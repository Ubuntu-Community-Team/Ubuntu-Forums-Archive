---
title: "Eclipse PDT 'New Project' Wizard Not Behaving Properly"
date: 2010-01-18
forum: Programming Talk
---

### Post by bkann on 2010-01-18
Hi -

I've used Eclipse PDT several times on-and-off over the years.  I installed it today on my current 9.04 installation and I'm getting some unusual behavior in one a couple of places, for example...

When I go File > New > PHP Project, the "Next" buttons are barely responsive.  That is, I may have to click "Next" about 30 times to get it to move to the next screen.  The button does highlight as you would expect it to do.  I don't know if it's the software responding slowly (CPU utilization does not increase), or if something else is happening, but I'm completely at a loss on this one.

This is also happening, for example, with some of the Window > Preferences buttons, but not all of them.

Has anyone else seen this?  Any guidance would be appreciated.  Thanks!

---

### Post by eewoz on 2010-01-18
> **bkann said:**
> Hi -

I've used Eclipse PDT several times on-and-off over the years.  I installed it today on my current 9.04 installation and I'm getting some unusual behavior in one a couple of places, for example...

When I go File > New > PHP Project, the "Next" buttons are barely responsive.  That is, I may have to click "Next" about 30 times to get it to move to the next screen.  The button does highlight as you would expect it to do.  I don't know if it's the software responding slowly (CPU utilization does not increase), or if something else is happening, but I'm completely at a loss on this one.

This is also happening, for example, with some of the Window > Preferences buttons, but not all of them.

Has anyone else seen this?  Any guidance would be appreciated.  Thanks!

I have had similar problems.  Two things worked for me.  The quick one is to click a button by hovering over the button with the mouse and press Enter.  The second one is to type ```
export GDK_NATIVE_WINDOWS=true
```
before running Eclipse from the command line.

---

### Post by bkann on 2010-01-18
That's great information, eewoz.  Thanks very much for your quick response!

I ended up creating eclipse.sh and putting your line first, then calling Eclipse.  Works perfectly.

Thanks again!

---


---
title: "Foolishly, I uninstalled Firefox"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by underthesun on 2008-06-10
So, yeah, that's what I did. I had a reason, I didn't just do it on a whim, but let's not go into that now...

So, I had Firefox 3.0 Beta 5, uninstalled that, and was unable to reinstall it via the package manager. It kept saying something about xulrunner. 

My query thus is: How might I get back toFirefox 3.0 Beta 5?

Edit:

When I attempt to mark Firefox 3.0 for installation it says:

firefox-3.0:
  Depends: xulrunner-1.9 (<1.9~b6~) but 1.9~rc1+nobinonly-0ubuntu1~8.04.1 is to be installed

---

### Post by kansasnoob on 2008-06-10
I'm not sure this will help, but look in synaptic and be sure the following two packages are installed:

xulrunner-1.9
xulrunner-1.9-gnome-support

No other xulrunner packages should be installed. You can just type xulrunner into synaptics search box to see all xulrunner packages.

Perhaps aftyer installing (or reinstalling) the appropriate xulrunner packages you'll be able to install firefox 3.

---

### Post by Epidemic_HardyBoy on 2008-06-10
Ya, thats the only thing I can think of too, if not try another browser until a solution comes up

---


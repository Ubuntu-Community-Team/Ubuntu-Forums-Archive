---
title: "C++ Accessories"
date: 2005-10-26
forum: Programming Talk
---

### Post by keron on 2005-10-26
I learned basic C++ about 5 years ago, and have since been programming java. Well, I had enough of java for now and want to get back to C++. 

Now to the question: I want to be able to do do GUI and network programming, how to make that happen the Ubuntu way? GTK--? 

Howto make a program reasonably cross-platform? Lots of friends and family uses windows....

I think I know how to do the actual programing, just need som pointers to the practical stuff, like what to use and what not to use....

---

### Post by David Marrs on 2005-10-26
You want [gtkmm](http://www.gtkmm.org/) for GUI development in Ubuntu. I guess you'll probably also want gnomemm from the same site, for the Gnome libraries. You can run gtk apps in Windows and (I think) Mac, but be aware that not all of the Gnome libraries have been ported, so the more you use them, the less chances of success you'll have in porting your apps to Windows.

---


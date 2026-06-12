---
title: "How to compile a driver?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by spookthehamster on 2008-08-15
I'm running Ubuntu on my old Powermac, and I haven't been able to find a PPC driver for my Canon Pixma iP1800 printer, only i386 drivers.

I've found a website that has the source in an .src.rpm file. I've never compiled anything before. How can I compile this to run on my PPC computer?

---

### Post by nicedude on 2008-08-15
An rpm package is a redhat linux package, but never fear someone wrote a program called "alien" and that is what you need to use to convert the rpm to a debian package , its in the repositories.

To install it paste this in a terminal

sudo apt-get install alien


hope you get it going

---

### Post by Crafty Kisses on 2008-08-15
> **spookthehamster said:**
> I'm running Ubuntu on my old Powermac, and I haven't been able to find a PPC driver for my Canon Pixma iP1800 printer, only i386 drivers.

I've found a website that has the source in an .src.rpm file. I've never compiled anything before. How can I compile this to run on my PPC computer?

You are gonna definataley need "buid-essiantals" and with that, you can compile files, there's a good link > [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---


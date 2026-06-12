---
title: "Missing A5 selection from printer properties"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by mdraicch on 2008-11-07
Hi to all,

I have a cannon mp610 and am trying to print duplex A5 pages, but the printer settings does not give me A5 in the drop down list.  Can I add A5 to this list? is it a function of CUPS?

Also how do I run cups admin, it does not seem to be in the menu.

Many thanks
Muzza

---

### Post by mdraicch on 2008-11-07
Hi to all,

I found the MP610_series.ppd and PDF.ppd in /etc/cups/ppd directory.  I copied the A5 lines from PDF.ppd to MP610_series.ppd and A5 now appears.

Also [http://localhost:631/](http://localhost:631/) to access cups admin.

Thanks to all
muzza

---


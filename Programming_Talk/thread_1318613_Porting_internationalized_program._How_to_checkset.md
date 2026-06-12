---
title: "Porting internationalized program. How to check/set locale?"
date: 2009-11-07
forum: Programming Talk
---

### Post by roccivic on 2009-11-07
I am in the process of porting a linux program (written in C) to windogs. The program uses LC_MESSAGES for internationalization. It all works great, except windogs does not set the environment variable LC_ALL. I see a few ways around it and I'm wondering if there is a standard I should follow or at least which would be best way to go about it. So far I can think of:

a): Prompt the user at install time for a language of his choice and let the user override by setting LC_ALL at any time he changes his mind.
b): Try to read LC_ALL at run time, if it returns nothing or an invalid string, somehow try to determine the locale and if that fails, too, fall back to English.
c) Something else?

Help much appreciated and thank you in advance.

Rouslan.

---

### Post by roccivic on 2009-11-08
bump

---

### Post by dwhitney67 on 2009-11-08
Consider using setlocale().  Read the man-page on how you can use this function to query the locale of the system.

Windoze supports a similar function; you can read about that here: [http://msdn.microsoft.com/en-us/library/x99tb11d.aspx](http://msdn.microsoft.com/en-us/library/x99tb11d.aspx)

---


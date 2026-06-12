---
title: "Which source control should I use with Eclipse?"
date: 2010-04-14
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-04-14
I use Eclipse for my Java development and I develop on two different machines, but I am the only author.  I would like to backup all my code on a file server running Ubuntu at home.  Can anyone recommend a source control utility that would be good for this purpose?

---

### Post by myrtle1908 on 2010-04-14
CVS integrates nicely with eclipse.

---

### Post by TheOrangePeanut on 2010-04-14
Look into Git or Mercurial.  Distributed versioning software is fantastic, as opposed to SVN and the like which is centralized.  I like Mercurial because it is easier to use than Git, but both are great choices.

---

### Post by km0r3 on 2010-04-15
I'd say anyone, but would prefer a SCM like Git. There's a good plug-in called [egit.]("http://www.eclipse.org/egit/")

---

### Post by SNYP40A1 on 2010-04-15
> **TheOrangePeanut said:**
> Look into Git or Mercurial.  Distributed versioning software is fantastic, as opposed to SVN and the like which is centralized.

But for what I am trying to do, merge code only with myself across a couple computers, why would distributed be a better option than centralized?

---

### Post by myrtle1908 on 2010-04-15
> **SNYP40A1 said:**
> But for what I am trying to do, merge code only with myself across a couple computers, why would distributed be a better option than centralized?

It wouldn't.  Just use CVS like I suggested earlier.  Eclipse comes with CVS support built in.

---


---
title: "[C++] Rogue Wave SourcePro C++"
date: 2009-08-01
forum: Programming Talk
---

### Post by dwhitney67 on 2009-08-01
Does anyone use the Rogue Wave SourcePro C++ product?  Or is my employer the only one on Earth using it?

If you use it, or have used it, do you have any comments with respect to it?

P.S.  Here is a link to Rogue Wave's [documentation]("http://www2.roguewave.com/support/docs/index.cfm").

---

### Post by ratcheer on 2009-08-02
I used it in the mid-90's at BellSouth Telecommunications. I am sure it was much less advanced then, but I really liked it. I assume we are talking about the same kind of thing. What we used was Rogue Wave tools++.h, at least I am pretty sure that is what it was called.

Anyway, it provided us with a class framework with which we could get real work done in a timely, efficient manner. The alternative was coding everything from the ground up. It made c++ coding almost as much fun as Smalltalk. Well, not really, but at least much better than raw c++.

Tim

---

### Post by dwhitney67 on 2009-08-02
Yes, it is probably the same thing.  RW became popular before C++ STL was "standard".  It is, I suppose, comparable to the Boost Libraries of today, which while offering an extension to C++, Boost does not actually form part of the standard; at least not yet.

Btw, I am familiarizing myself with RW because it is used on a legacy project that I support, which was developed circa 1999, if not a couple of years prior.

---

### Post by ratcheer on 2009-08-02
Sounds about right. So, is Rogue Wave still an active company in the grand scheme of things? We were using it on an HP-UX project. 

In case you couldn't tell, I greatly preferred Smalltalk. We had formerly been using Visual Works on a smaller project. Our small project was subsumed by a larger project and the new project forced us to switch to c++. After a few months of c++, we were all sick of it and moved on to other jobs.

Tim

---

### Post by dwhitney67 on 2009-08-02
The project I support is porting s/w apps from Solaris 2.8 to RHEL 5, with the goal of minimizing s/w changes so as to keep costs down and also preserve as much as possible the working (ie. heavily used/tested) applications.

From what I heard, for my project, runtime licenses for RW run about $225K.  To port/test the 5400+ lines of code that rely on RW would be costlier/riskier, and thus the rationale for sticking with RW came about.  This was not my assessment, but that made by others.  It makes sense though, when one considers that one software engineer alone costs (the employer) anywhere from $150-$200K per year.  Throwing in testers and Q&A personnel would in turn cost even more money.

---

### Post by ratcheer on 2009-08-02
> **dwhitney67 said:**
> 

From what I heard, for my project, runtime licenses for RW run about $225K.  To port/test the 5400+ lines of code that rely on RW would be costlier/riskier, and thus the rationale for sticking with RW came about.  This was not my assessment, but that made by others.  It makes sense though, when one considers that one software engineer alone costs (the employer) anywhere from $150-$200K per year.  Throwing in testers and Q&A personnel would in turn cost even more money.

I would also agree with that assessment. If R W was removed, many (probably most) things would have to be completely re-coded. It would be like a brand new project instead of a port.

But, why couldn't the license be removed from the old system, saving the money to be applied to the new target system?

Tim

---

### Post by dwhitney67 on 2009-08-02
> **ratcheer said:**
> I would also agree with that assessment. If R W was removed, many (probably most) things would have to be completely re-coded. It would be like a brand new project instead of a port.

But, why couldn't the license be removed from the old system, saving the money to be applied to the new target system?

Tim
The project is mission critical (deals w/ commanding and collecting data from a trio of satellites); both the new and the old systems will be running concurrently, at least until the new system proves it is reliable.

---


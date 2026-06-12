---
title: "Mono 2.4"
date: 2009-03-31
forum: Repositories &amp; Backports
---

### Post by jonbuys on 2009-03-31
Hello,

I've got a friend of mine who's really into coding in .Net, and the Mono project is perfect for his background.  Unfortunately, the version of Mono in the repos is seriously behind.  Is there any push to get Mono updated to the latest version?  What would it take to add Mono 2.4 to the repos?

Thanks

---

### Post by directhex on 2009-03-31
Not happening. Mono is a big set of packages, which affects many others. Jaunty ships in 3 weeks, there simply isn't enough time to prepare and fully test 2.4 by then to a standard which will mean it's ready for everybody's desktops. We skipped 2.2 because it showed some serious problems which 2.0 did not - if we packaged a version before testing for those same serious problems, then we'd be up a certain creek.

---

### Post by EmmeDa on 2009-04-01
At the moment my Synaptic says that the mono version is 1.9.3. I have an Intrepid Ibex with all Updates installed. If 2.0 dont have problems, why it is not in the repository?

emmeda

---

### Post by directhex on 2009-04-01
> **EmmeDa said:**
> At the moment my Synaptic says that the mono version is 1.9.3. I have an Intrepid Ibex with all Updates installed. If 2.0 dont have problems, why it is not in the repository?

emmeda

Because it's a core framework, which makes it ineligible for backporting, due to regression risk.

---

### Post by jonbuys on 2009-04-16
OK, that makes sense.  Do you know if there are any plans for including he 2.4 mono in 9.10?

---

### Post by directhex on 2009-04-16
> **jonbuys said:**
> OK, that makes sense.  Do you know if there are any plans for including he 2.4 mono in 9.10?

2.4 or 2.6 depending on timescales and issues. 2.4 contains a significant number of licensing issues we need to resolve before packages can exist

---


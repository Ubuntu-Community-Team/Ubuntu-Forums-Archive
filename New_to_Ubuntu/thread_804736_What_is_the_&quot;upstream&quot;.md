---
title: "What is the &quot;upstream&quot; ?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by KingTermite on 2008-05-23
I keep hearing mention of releasing software/patches to the upstream. What exactly is "the upstream"?

From the connotation it sounds like some common Linux code place where fixes/patches get posted for all distributions. Am I even close?  

What is it?

---

### Post by aeiah on 2008-05-23
from wikipedia:
Upstream in software development refers to a direction toward the original authors or maintainers of software that is distributed as source code, and is a qualification of either a bug or a patch. A patch sent upstream, i.e. offered to the original authors or maintainers of the software the patch applies to, would be targeted at being included in (a future release of) the original software instead of being maintained by a distribution's maintainer of said software. The term also pertains to bugs - responsibility for a bug is said to lie upstream when it is not caused through the distribution's porting efforts. Equally, a generally useful or generic porting patch could be sent upstream so that other distributions may benefit from earlier porting efforts.

---

### Post by fluteflute on 2008-05-23
Kind of. Ubuntu rarely creates new software itself. Ubuntu is a collection of software written by many (thousands?) different people.

Upstream is simply the people who develop the programs (as opposed to those who make minor modifications so it works properly on ubuntu).

---

### Post by KingTermite on 2008-05-23
Does that imply there is some original group who still maintains something? Do distributions modify their own kernel or is the kernel maintained by some core group?

> **aeiah said:**
> from wikipedia:
Upstream in software development refers to a direction toward the original authors or maintainers of software that is distributed as source code, and is a qualification of either a bug or a patch. A patch sent upstream, i.e. offered to the original authors or maintainers of the software the patch applies to, would be targeted at being included in (a future release of) the original software instead of being maintained by a distribution's maintainer of said software. The term also pertains to bugs - responsibility for a bug is said to lie upstream when it is not caused through the distribution's porting efforts. Equally, a generally useful or generic porting patch could be sent upstream so that other distributions may benefit from earlier porting efforts.

---

### Post by markbuntu on 2008-05-23
Distributions are usually just coordinators though some maintain their own kernels. In Ubuntu the current distribution is 8.04 and bugs in it are generally fixed by the 8.04 maintainers and their third party contributors while others work on the new release, 8.10, due in October, the "Upstream". 

Very often the upstream developers will come up with something that fixes some problem in the current and previous releases or provides previously unavailable opprtunities and so it is ported (configured to work with the) downstream and made available as an update. 

Other items and fixes are not so easily portable and require a more extensive replumbing of the entire system and so are identified as to be addressed in the next (upstream) release. This gives the developers a lot more leeway in how they do stuff since extensive changes can be made systemwide to accomodate new implementations.

I hope this is a little clearer than the goobledygook from the wiki.

---


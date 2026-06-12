---
title: "Monodevelop 2.4 - run tests remains disabled"
date: 2010-08-24
forum: Programming Talk
---

### Post by bprins on 2010-08-24
Hi guys,

I'm pretty puzzled here. I've installed monodevelop, which runs quite nice I must say. 

However, the problem is that I can't get the "run tests" button enabled.

I've google-d the issue, but apparently I am the only person with this issue. I also gave the monodevelop-list a try, but no response.

Does anybody has a clue what to do to get this working? 

I have: 
- created a new solution
- created a test project
- added the nunit.Core & nunit.Framework references to the test project
- switched to the unit test view
- wrote Test class skeletons with [TestFixture]'s and [Test]'s.
Result: disabled "run tests" button.

Installed packages:
- monodevelop
- monodevelop-nunit

Hope somebody can get me further.

Thanks in advance.

Bas

---

### Post by bprins on 2010-08-24
Oh god, found this completely by accident.

Apparently, if you right click the test-project and select "Run item", it does something (no clue what) and the "run test" button is magically enabled.

Restarting monodevelop results in a disabled button of course. The "Run item" workaround does the trick again.

I am still very curious about:
- if others have this very same issue
- if there a other solutions for this problem
- if this is a bug, or if this is some misconfiguration

---


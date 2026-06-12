---
title: "Problem with notification-daemon and apport"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Blutkoete on 2012-05-01
Hello!

On every boot-up, I get a crash report from apport (the details tell me notification-daemon had a problem) and I confirm that it should be reported.

Apport collects info for some time then, but it never reports anything (after the collection, it just closes).

Is there a way I can upload that report to launchpad by hand? It's kind of annoying to have a crash report on every start :).

Thank you very much,

Blutkoete

---

### Post by aJacom on 2012-05-03
I am getting this exact same behavior. In every startup, I get a "notification-daemon" crash.

Lubuntu 12.04

Thank you.

---

### Post by Atadam on 2012-05-05
I had the same trouble and you can fix this easily if you install apport-retrace with synaptic.
The package allows reports even if you are not active as admin what would be the most time you use your computer. Since you have the package not installed apport makes trouble and confuses more than it is useful.
Whatsoever, just install the package and apport will do is job.

M.Peters

---

### Post by Guilden_NL on 2012-05-24
Every single Lubuntu 12.04 install has this problem.  Plenty of bug reports, but not a thing mentioned here on the Ubuntu forums.

It's annoying as heck to me, and enough so that if work arounds or a patch is not worked on soon, it will be time for me to leave Lubuntu behind.

---


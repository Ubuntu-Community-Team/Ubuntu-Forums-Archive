---
title: "New LibreOffice 3.4.1 in Oneiric repos"
date: 2011-08-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-23
The new LibreOffice 3.4.1 has found its way into Oneiric repos.

The only problem I noticed immediately was the missing launcher icons.
This is some linking issue, because the icons are there:
/usr/share/icons/hicolor/48x48/apps/

After I edited the launcher files
/usr/share/applications/libreoffice-*.desktop
the icons are now working again.

---

### Post by xebian on 2011-08-23
A lot of 404's on us.archive ATM

---

### Post by rburkartjo on 2011-08-23
tks just noticed it when i updated

---

### Post by Harry33 on 2011-08-23
It looks like 32-bit setups do not suffer this symptom. Icons will stay.
So, only in my two 64-bit setups the launcher icons disappeared.

---

### Post by andrewabc on 2011-08-23
3.4.2 is out, and 3.4.3 already has an RC.

So hopefully it gets updated past 3.4.1 before final release.

---

### Post by carltonh on 2011-08-23
Not to sound too alarmist, but Libreoffice 3.4.1 is a potential major disaster. It destroys all formulas when opening MS Excel .xlsx documents, which is essential for any enterprise working with others.  I filed a bug report and they fixed it in 3.4.2, thank goodness.

BUT if 11.10 stays with 3.4.1, I can't imagine a greater disaster. My employer tried Open Office in 2004, and a bad experience back then has ruled out considering it for the 7 years since then.

---

### Post by Ichtyandr on 2011-08-23
According to libreoffice [release notes for 3.4.2]("http://www.libreoffice.org/download/release-notes/#LO342") this version still has some intolerable bugs. 
But they say 3.4.3 bugfix release will be out end of August and I guess there is no reason to think that it will not make into final oneiric release.

Until that happens I stick to 3.3.4 downloaded from libreoffice website which is rock solid, and added the lo-menubar (extracted from the latest oneiric package to the "/opt/libreoffice/share/extensions") for global menu support. 

No risking my articles and papers.

---

### Post by jbicha on 2011-08-24
Ubuntu will be including 3.4.2 soon. 3.4.1 was already ready so it was pushed first. 3.4.3 is [scheduled]("http://wiki.documentfoundation.org/ReleasePlan") to be released upstream next week.

---

### Post by Harry33 on 2011-08-24
> **jbicha said:**
> Ubuntu will be including 3.4.2 soon. 3.4.1 was already ready so it was pushed first. 3.4.3 is [scheduled]("http://wiki.documentfoundation.org/ReleasePlan") to be released upstream next week.

Thanks for the info.

---


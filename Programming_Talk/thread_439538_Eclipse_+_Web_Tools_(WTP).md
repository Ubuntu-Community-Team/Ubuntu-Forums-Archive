---
title: "Eclipse + Web Tools (WTP)"
date: 2007-05-10
forum: Programming Talk
---

### Post by saracen on 2007-05-10
I've had trouble with the Eclipse that's in the repositories so I downloaded it from the website and untarred it into my home directory.  Then I downloaded the 2 prerequisites for WST (Web Standard Tools) from [here]("http://download.eclipse.org/webtools/downloads/drops/R1.5/R-1.5.4-200705021353/") and unzipped them into the eclipse directory properly.  Then I got the WST package and unzipped that as well.  But when I open Eclipse I don't get any additional options.  And I know the editors aren't working because I can't open an HTML editor to edit HTML files.

Does anyone know how to get this working?

---

### Post by burlaka on 2007-06-10
Try to run Eclipse with helps of this command:
```
eclipse -clean
```

---

### Post by Keffin on 2007-06-10
Somehow I never had much luck installing eclipse plugins manually. Luckily the WTP project offers an "All-in-one" download which is the latest compatible versions of eclipse, WTPs dependencies, and WTP itself. Not a solution as such, but a good workaround.

---


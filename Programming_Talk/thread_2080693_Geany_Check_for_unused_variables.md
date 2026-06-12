---
title: "Geany: Check for unused variables"
date: 2012-11-04
forum: Programming Talk
---

### Post by BobTheZealot on 2012-11-04
Hi all,

Not sure where this went, but this subforum seemed like the closest fit.

People refer to a feature in Geany that allows you to identify unused variables.  How do I enable that?  Maybe I'm being dense, but I can't seem to find this feature (I mostly edit .py files).

Thanks!

---

### Post by MG&amp;TL on 2012-11-05
Not sure if the feature supports python-as I understand it, syntax and programming helpers are done on a per-language basis in Geany.

Can't find anything to do it from the interpreter, either. :(

---

### Post by BobTheZealot on 2012-11-05
Oh well.  Thank you anyway.

---

### Post by r-senior on 2012-11-06
You can set up a build task in Geany to run pylint or similar. Output then appears in the build results window. It doesn't highlight the issues in the code itself but it's useful.

You'll probably want to customise the rules pylint uses but there's documentation in the manual: [http://www.logilab.org/card/pylint_manual](http://www.logilab.org/card/pylint_manual)

Geany's build settings window:

---


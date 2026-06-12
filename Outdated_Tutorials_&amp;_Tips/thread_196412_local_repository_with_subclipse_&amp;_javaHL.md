---
title: "local repository with subclipse &amp; javaHL"
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by aouie on 2006-06-14
If you are using subversion and eclipse (and subclipse), and would like to access a local repository using the file:// protocol then you need to install libsvn-javahl. Then start eclipse with "eclipse -vmargs -Djava.library.path=/usr/lib/jni/".
In the Eclipse menu Windows -> Preferences -> Team -> SVN and select JavaHL.
I am using eclipse 3.1 (custom installation) with subclipse 1.0.2 and libsvn and libsvn-javahl from the Dapper repositories.
Sincerely,
Aouie

---

### Post by ethan@xmlstandards.org on 2006-06-15
Thanks for this information.

Was never sure how to use this method correctly until today.

Many thanks.

---

### Post by korny on 2008-02-03
Thanks for this.  One note:
> **aouie said:**
> then start eclipse with "eclipse -vmargs -Djava.library.path=/usr/lib/jni/".


You can also set this by changing the "eclipse.ini" file in the root eclipse directory.

---


---
title: "What dependencies to include?"
date: 2010-09-07
forum: Packaging and Compiling Programs
---

### Post by hakermania on 2010-09-07
I am developing an app but I really dont now what dependencies to add...
E.g. this app uses **sed** and **echo** which are pre-installed to the ubuntu.
One other program my app uses is mpg321, which is not pre-installed.
So, i cannot understand what to have into the dependencies.
1) only the non-pre-installed apps
2) All other apps used by the app.

---

### Post by B_rebel on 2010-09-07
I dont understand your problem precisely. But you want to install mpg321

you may type in terminal

sudo apt-get install mpg321, that may will be solve dependencies.

---

### Post by Bachstelze on 2010-09-07
Put everything. lintian will tell you if something is unnecessary.

---

### Post by hakermania on 2010-09-07
My problem is that I don't know what to include into the dependencies of the DEB package. Should I include all the terminal-programs used (like sed, echo, awk etc) or only the non-pre-install into the Ubuntu ISO?

---

### Post by Bachstelze on 2010-09-07
Do you actually read answers?

---

### Post by hakermania on 2010-09-07
I can't read xD


I read your answer but I got it as you didn't understand as well.
Ok thx, I'll try it!

---


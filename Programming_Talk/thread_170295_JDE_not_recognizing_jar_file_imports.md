---
title: "JDE not recognizing jar file imports"
date: 2006-05-04
forum: Programming Talk
---

### Post by jaywhy13 on 2006-05-04
I am tryin to compile some code that imports this jar file. The command that the beanshell shows me works ok in konsole, but within emacs the jde reports that it cannot find the classes, hence obviously not importing the jar file. Any suggestions on how 2 correct that?

---

### Post by kunnk on 2006-05-05
You must set correctly classpath. Looks -classpath option for javac.

---


---
title: "qtjambi: problem using juic on .ui files"
date: 2009-02-18
forum: Programming Talk
---

### Post by strattonbrazil on 2009-02-18
I've created a .ui file using Qt Designer, but can't make the corresponding .jui file for Qt Jambi to load.  When I run juic, it gives me an error.  

```

uic: File is not a 'jambi' form
./juic: Failed on input file: '/home/dvn/test.ui'

```

Has anyone gotten juic to work correctly?

---

### Post by gorilla on 2009-02-18
Have you used the version of Designer which came with Jambi? You cannot use the normal Designer.

---

### Post by strattonbrazil on 2009-02-18
> **gorilla said:**
> Have you used the version of Designer which came with Jambi? You cannot use the normal Designer.


Yes, I've tried both.  Using the juic that comes with QtJambi gives the following error:

```

./juic: Skipping 'Ui_Form.java': Not a generated file

```

---


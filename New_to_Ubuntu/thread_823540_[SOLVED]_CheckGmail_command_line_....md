---
title: "[SOLVED] CheckGmail command line ... ???"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-06-09
in the preferences section under External Commands it says:

Command to execute on clicking the icon tray
(use %u to represent the Gmail Web address)

so I entered:

/usr/bin/firefox

that works ok, Firefox opens and goes to the homeoage (in this case, Google)

but I need it to go to gmail, so I tried the following:

/usr/bin/firefox%u

and then tried

/usr/bin/firefox/%u

but the browser doen't open at all, let alone go to gmail.

What command do I need to open Firefox and make it go to gmail when I click on the CheckGmail icon in the task bar? Thanks

---

### Post by Cypher on 2008-06-09
You need a space between the program and the argument.
```

/usr/bin/firefox %u

```

---

### Post by Vadi on 2008-06-09
Try "firefox %u"

---

### Post by Samurai Penguin on 2008-06-09
yup. that did it. Thanks much !!!

---


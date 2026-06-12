---
title: "[SOLVED] java applet problem !!!"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Biggy on 2008-05-31
hi

i try to open ftp hosting control but give this error : An error occurred while loading this applet.

i use Firefox version 2.0.0.14


any idea !!

---

### Post by Hospadar on 2008-05-31
what version of java do you have installed?

In a terminal (Applications->Accessories->Terminal) type "java -version" (I think, if that doesn't work, try "java -v" or "java --version")

Just copy and paste the output of that back up here

---

### Post by Biggy on 2008-05-31
java-version
> java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


---

### Post by Biggy on 2008-05-31
any idea !

---

### Post by dracayr on 2008-05-31
hi,
try using a different jvm by typing

```
sudo update-alternatives --config java
```

if that doesn't work, there is the possibility that the applet is buggy.

dracayr

---

### Post by Biggy on 2008-05-31
> **dracayr said:**
> hi,
try using a different jvm by typing

```
sudo update-alternatives --config java
```

if that doesn't work, there is the possibility that the applet is buggy.

dracayr

i try 5 alternatives but doesn't work !!

---

### Post by dracayr on 2008-05-31
open a java console (I don't know exactly how to do that without the web-developer plugin, If you can't find it, install the plugin, then press Ctrl+Shift+O), and reload the page. Then post the error.

dracayr

---

### Post by Biggy on 2008-05-31
> **dracayr said:**
> open a java console (I don't know exactly how to do that without the web-developer plugin, If you can't find it, install the plugin, then press Ctrl+Shift+O), and reload the page. Then post the error.

dracayr

how to do that !!??

---

### Post by dracayr on 2008-05-31
install this addon:
[https://addons.mozilla.org/de/firefox/addon/141](https://addons.mozilla.org/de/firefox/addon/141)

then, in your tools menu, there should be an option mentioning the java console. click on that. then, reload the page with the applet. An error should occur. Post it.

---

### Post by Biggy on 2008-05-31
ok

---

### Post by dracayr on 2008-05-31
:lolflag:

If you havn't done it yet:
Edit>Preferences>Content>Enable java

dracayr

---

### Post by philinux on 2008-05-31
> **dracayr said:**
> :lolflag:

If you havn't done it yet:
Edit>Preferences>Content>Enable java

dracayr

I think thats the default.

---

### Post by dracayr on 2008-05-31
yes, but apparantly he had it disabled (look at his screenshot)

dracayr

---

### Post by Biggy on 2008-05-31
> **dracayr said:**
> :lolflag:

If you havn't done it yet:
Edit>Preferences>Content>Enable java

dracayr

is checked ..!

---

### Post by Biggy on 2008-05-31
!

---

### Post by dracayr on 2008-05-31
Strange..

where do you actually see that "error loading Applet"? On the statusbar of firefox, on the page, or somewhere else? Can you post the address of the page? And when did you see that window with java is not enabled? when you loaded the page or when you clicked on java console?

dracayr

---

### Post by Biggy on 2008-05-31
when i go to open ftp client from my hosting manager :

---

### Post by dracayr on 2008-05-31
hmm, well looks like either firefox or the applet has a bug.. maybe try opening the java console with this plugin:
[https://addons.mozilla.org/de/firefox/addon/60](https://addons.mozilla.org/de/firefox/addon/60)

If that doesn't work, the only other possibility I see is reinstalling firefox...

dracayr

---

### Post by Biggy on 2008-05-31
doesn't work !

i try to reinstall Firefox..

thank you dracayr for replays !

---


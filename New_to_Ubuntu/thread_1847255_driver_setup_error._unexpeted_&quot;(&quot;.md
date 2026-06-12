---
title: "driver setup error. unexpeted &quot;(&quot;"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by sburgh on 2011-09-20
Hi
First of all i shoud say that my english is not very good so sorry for the misstakes.

I got little Touchpanel PC and installed Ubuntu 8.04.4.. its working.
now i wanted to install the driver for the touch panel from the developers Homepage.
 [http://www.dmp.com.tw/tech/icop_cd/Driver/TouchPanel/linux.zip](http://www.dmp.com.tw/tech/icop_cd/Driver/TouchPanel/linux.zip)

At first I got an error -> uudecode unknown command
or something like that but i googled it and fixed it.

So now it decodes/extracts all files into the TMP folder but when it´s running the setup script a error appears 

```
./setup: 11: Syntax error: "(" unexpected
```

So i looked up the setup file and in Line 11 is:

```
package=(make tcl tk)
```

Is it possible to fix this??

I hope that somebody can help me :/

---

### Post by An Sanct on 2011-09-20
Have you used sudo?

Do you have the packages *tcl* and *tk* installed?

---

### Post by sburgh on 2011-09-20
Yes I used sudo su for the complete installation to have root access but what are tcl and tk ??
how to install this packages???

---

### Post by sburgh on 2011-09-20
Ok
 Thanks to google I installed the two packeges tcl and tk but there´s still the same error :/
I don´t know what to do..

---

### Post by wildmanne39 on 2011-09-20
Hi, I just wanted to let you know that 8.04 is an old release no longer supported so you will not get updates, that includes security updates so your system my be at risk for viruses, where if you used say 10.04 it would not be.
Thank you

---


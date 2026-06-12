---
title: "cups-pdf installed but not detected"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-06-02
Hi, I have installed cups-pdf in 13.04 but it is apparently no virtual printer is detected by the system.  See attached.

Thanks in advance for any help.

---

### Post by newb85 on 2013-06-02
Have you read the readme file?  (You can find it at [http://cups-pdf.de/cups-pdf-CURRENT/README](http://cups-pdf.de/cups-pdf-CURRENT/README).)  Section 2 is the one you need to pay attention to.

The first thing that jumps out at me when skimming it: Have you restarted CUPS since installing cups-pdf?

---

### Post by monkeybrain2012 on 2013-06-02
Does it work for you? 

I don't remember having to go through any hassle in previous Ubuntu releases, just apt-get install and it is good to go.  I am now fairly sure that it is a bug in cups-pdf 2.6.1-8 in raring because a minute ago I uninstalled it and grab a .deb for version 2.6.1-6 from Precise's repository and it works right the way. I am going to file a bug report tomorrow, so it would help if you can tell me if it works for you or not.

Thanks.

---

### Post by monkeybrain2012 on 2013-06-03
Hi, I have filed a bug against cups-pdf 2.6.1-8

[https://bugs.launchpad.net/cups-pdf/+bug/1187138](https://bugs.launchpad.net/cups-pdf/+bug/1187138)

Please visit and add an "affect me too" if you are experiencing the same problem. Thanks.

---

### Post by monkeybrain2012 on 2013-06-05
Anyone who experiences this please add an "affect me too" to the bug report. Thanks.

---


---
title: "Oracle 10g Web Interface - Script Editor"
date: 2009-02-01
forum: Programming Talk
---

### Post by apostate on 2009-02-01
Hello,

I am using the Oracle Express 10g Web interface, and when using the script editor, I notice that the script editor text window is blank. I cannot see or edit scripts in it. Is anyone else havig this issue, and is there any fix?

---

### Post by TommCatt on 2009-03-11
Interesting. I have not installed Oracle Express on Ubuntu but I do have it on Vista Ultimate. However, I have the same problem. Actually that makes sense. The app builder is obviously just a web site running from within XE. That part would not be platform specific.

But the implication of that is that everyone should be having this problem.

[Edit]Quick update. I held my nose and tried IE. Sigh, everything works fine on IE. Chrome also doesn't work. So it looks like there is a workaround for Windows. So my only suggestion in Ubuntu is to keep trying browsers.

---

### Post by TommCatt on 2009-03-11
I just visited the Oracle site and confirmed that the problem is with Firefox. Their "solution": use IE. :(

---

### Post by pedro_magalhaes86 on 2011-03-04
Hi there,

I have the same problem.

I started [this]("http://support.mozilla.com/en-US/questions/787734"). Maybe we can persuade the good people at Mozilla to do something about it.

Take care.

---

### Post by Shpongle on 2011-03-04
You could always try sql developer [http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html](http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html), Its a great tool with lots of features

---

### Post by Waappu on 2011-03-08
Hi,

You can upgare XE Apex
[http://www.oracle.com/technetwork/developer-tools/apex/upgrade-apex-for-xe-154969.html](http://www.oracle.com/technetwork/developer-tools/apex/upgrade-apex-for-xe-154969.html)

Apex version 2.1 that comes with XE is rather old and do not support new browsers.

Please read whole document from link before start upgrade.
You will lose DB admin features. But you can do all those with SQLPlus or SQL Developer

---


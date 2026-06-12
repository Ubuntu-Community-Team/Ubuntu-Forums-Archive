---
title: "Library for POP3 mail access"
date: 2009-12-27
forum: Programming Talk
---

### Post by kulkarniniraj on 2009-12-27
Hello,
     I want to write a 'C' code to read mails from my gmail account and display them on console. So which library should I use to do POP3 access?Its ok if library only provides POP3 access (SMTP  not required)
   Thanx

---

### Post by matsuzine on 2009-12-30
Not sure if this would work for your purposes, but you could try

[http://savannah.nongnu.org/projects/libspopc/](http://savannah.nongnu.org/projects/libspopc/)

I'd be interested to hear what you find!

---

### Post by iharrold on 2010-01-05
poco

Its also cross compatible.

Documentation here:
[http://pocoproject.org/docs/](http://pocoproject.org/docs/)

Poco::Net::POP3ClientSession() class should do what you are talking about I believe.

---

### Post by WitchCraft on 2010-01-05
From [http://www.wxwidgets.org/about/users.htm](http://www.wxwidgets.org/about/users.htm)

Mahogany Project
[http://mahogany.sourceforge.net/](http://mahogany.sourceforge.net/)

Mahogany is an OpenSource(TM) cross-platform mail and news client. It is available for X11/Unix and MS Windows platforms, supporting a wide range of protocols and standards, including POP3, IMAP and full MIME support. Thanks to its built-in Python interpreter it can be extended far beyond its original functionality. Mahogany's wealth of features and ease of use make it one of the most powerful clients available, providing a consistent and intuitive interface across all supported platforms. Contact: Vadim Zeitlin

---


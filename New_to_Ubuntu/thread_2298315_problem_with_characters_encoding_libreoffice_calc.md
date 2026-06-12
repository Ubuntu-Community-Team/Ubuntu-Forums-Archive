---
title: "problem with characters encoding libreoffice calc"
date: 2015-10-10
forum: New to Ubuntu
---

### Post by farid4 on 2015-10-10
Hi guys! Helllllllllllllllllllllllllllllllp me!
Every time I use "Link to External Data..." in calc to insert html tables of every Persian web pages, it cannot encode characters. what should I do?
I use Libreoffice 5
[IMG]http://i60.tinypic.com/2ag9qx.png[/IMG]

---

### Post by ta-bu-shi-da-yu on 2016-01-31
This was reported upstream to the LibreOffice team at [https://bugs.documentfoundation.org/show_bug.cgi?id=95217](https://bugs.documentfoundation.org/show_bug.cgi?id=95217) and has now been resolved. 

The issue was that the content-type header wasn't being detected because a case-sensitive match was being done on the header field. Once this was made into a case-insensitive match the content-encoding header, which specifies the character encoding of the web page, was detected and the text was able to be rendered correctly.

Thank you for your patience whilst we fixed this.

---


---
title: "how to convert files to unicode (/u****)"
date: 2011-10-19
forum: Programming Talk
---

### Post by devish1 on 2011-10-19
hi,
I need to convert some files(in different languages like korean, chinese) to unicode (/u****) so that my parser is able to print them.
can any one direct me to some tool or way by this can be done?

---

### Post by Arndt on 2011-10-19
> **devish1 said:**
> hi,
I need to convert some files(in different languages like korean, chinese) to unicode (/u****) so that my parser is able to print them.
can any one direct me to some tool or way by this can be done?

The program 'iconv' may know about those encodings.

Both Korean and Chinese probably have several different encoding each.

---

### Post by ofnuts on 2011-10-23
> **devish1 said:**
> hi,
I need to convert some files(in different languages like korean, chinese) to unicode (/u****) so that my parser is able to print them.
can any one direct me to some tool or way by this can be done?The Java JDK comes with a "native2ascii" utility to convert file to ISO-8859-1 and Unicode escape sequences for the characters that hav no direct representation in  ISO-8859-1  (typically used ti generate properties file for I18N). see:

[http://download.oracle.com/javase/1.4.2/docs/tooldocs/windows/native2ascii.html](http://download.oracle.com/javase/1.4.2/docs/tooldocs/windows/native2ascii.html)

---


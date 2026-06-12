---
title: "QT QString from a unicode decimal"
date: 2013-10-10
forum: Programming Talk
---

### Post by Woody1987 on 2013-10-10
I have a database which holds a list of unicode characters in decimal format, i.e. The [£ symbol ]("http://www.fileformat.info/info/unicode/char/a3/index.htm") would be stored as '163' in the database. How would I go about converting this into a QString which holds the £ character? In Java I can do:

```
return Character.toString((char)Integer.parseInt("163"));
```

Is there an equivalent in QT C++? 

 Thanks.

---

### Post by Woody1987 on 2013-10-10
Fixed it myself:

```

QChar c((short)163);
return QString(c);
```

---


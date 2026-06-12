---
title: "LibreOffice internal date format"
date: 2014-01-20
forum: Programming Talk
---

### Post by kangaba on 2014-01-20
Hi,
I unzipped an .ods file and the meta.xml file has this:
```

<meta:creation-date>2013-12-18T21:08:47.079646992</meta:creation-date>
<dc:date>2014-01-08T08:40:11.689560849</dc:date>

```

Any idea what the .079646992 and .689560849 stand for?

PS: In case it matters, I'm trying to create a C++ reader/writer of .ods (spreadsheet) files.

---

### Post by ofnuts on 2014-01-20
Nanoseconds, very likely (that makes 47.079646992 and 11.689560849 fractional seconds).

---

### Post by kangaba on 2014-01-20
Wow, you're clever, thanks. It didn't cross my mind cause I thought nanoseconds make no sense in timing a document, apparently they do matter.

---

### Post by Vaphell on 2014-01-20
they don't matter from the user perspective but the internal representation of timestamps in the system has such precision, why bother truncating it if it doesn't matter?

---


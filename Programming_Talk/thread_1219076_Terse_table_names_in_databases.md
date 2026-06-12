---
title: "Terse table names in databases"
date: 2009-07-21
forum: Programming Talk
---

### Post by froggyswamp on 2009-07-21
Folks, are you using short names for tables like "EMP" instead of "Employee"?
If so - why, to save typing? And is it (still) considered a good practice?

---

### Post by Tony Flury on 2009-07-21
I would recommend using long names in your design and DB development, and if you are using a decent RDMS you could create aliases to shorten your table names.

However - just like code which uses short variable names, code which uses shortened table name is likely to be less obvious, and less easy to read.

---

### Post by apoth on 2009-07-21
I tend to write them out in full, to an extent.

At work some muppet's written table names like PACKAGE_CLASS where just CLASS would suffice as unique. Then they have columns like TABLENAME_UID. Drives me mad!

---

### Post by ratcheer on 2009-07-21
I have been a DBA for most of the past 30 years. It is generally recommended to make table names as descriptive as possible, i.e., not terse. This doesn't mean extra long just to be long, but whatever is required to give clear meaning.

Tim

---


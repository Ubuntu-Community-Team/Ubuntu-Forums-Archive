---
title: "parsing file in bash (Solaris)"
date: 2010-09-20
forum: Programming Talk
---

### Post by qmqmqm on 2010-09-20
Hi

I have an xml file that contains the following content:

<abc>whatever</abc>
<id>123</id>
<def>something</def>
&#8230; &#8230;

In bash, how may I get the id number (i.e. "123") out of such a file?

Thanks a lot.

Tom

---

### Post by kurum! on 2010-09-20
```

perl -ne 'print $1 if m/<id>(.*?)<\/id>/' file

```

---

### Post by qmqmqm on 2010-09-21
Thanks so much kurum!

Works like a charm.

Tom

---


---
title: "How to install the document for gcc?"
date: 2007-05-18
forum: Programming Talk
---

### Post by HolyJoe on 2007-05-18
I installed the gcc and gcc-doc, but I get nothing when I type: man fopen, etc.

How can I get the gcc man pages?

---

### Post by WW on 2007-05-18
Install **manpages**, **manpages-dev**, **manpages-posix**, **manpages-posix-dev**.
```

sudo apt-get install manpages manpages-dev manpages-posix manpages-posix-dev

```

---

### Post by HolyJoe on 2007-05-20
Thank you for your reply. But I want to get **C**'s function documents, how can I get it??

---

### Post by WW on 2007-05-23
Install **manpages-dev**. Then the command **man fopen** will give you the C documentation for fopen.

---

### Post by HolyJoe on 2007-05-25
Thank you for your help.

---


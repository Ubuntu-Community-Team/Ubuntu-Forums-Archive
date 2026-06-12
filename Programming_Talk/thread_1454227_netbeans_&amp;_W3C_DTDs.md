---
title: "netbeans &amp; W3C DTDs"
date: 2010-04-14
forum: Programming Talk
---

### Post by .:PiXi²:. on 2010-04-14
Hi

I've been searching for this, but have not found any useful answers yet. The question is simple: is there a way to validate xHTML against public DTDs in NetBeans? For example: validate against [http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd](http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd).
NetBeans doesn't seems to recognize "<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">" like Dreamweaver does.

Thanks in advance!

---

### Post by .:PiXi²:. on 2010-04-14
Is this thread in the wrong place or doesn't someone knows the answer?

---

### Post by Reiger on 2010-04-14
Sort of both. You can validate any type of XML using the context menu, or the tools menu (I think). That said, Netbeans uses the colour code mechanism to highlight errors; and this includes validation errors (not just syntax ones).

---

### Post by .:PiXi²:. on 2010-04-15
Thanks for the reply. NetBeans indeed validates xml instantly while you type, even with public DTDs. I discovered that the problem was something else: NetBeans doesn't validate xHTML 1.1 100% correct.

---


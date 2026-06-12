---
title: "python-notify: problems with ampersand (&amp;) in link URL"
date: 2009-01-18
forum: Programming Talk
---

### Post by bogoliubov on 2009-01-18
Hello. I am writing a simple python script that looks for certain keywords in RSS feeds, and if found the user is notified using python-notify. 

But it seems I can't get the link feature of python-notify to work when there's and ampersand ("&") in the link URL. Anyone else who has experienced this? Any idea how to fix/bypass it?

---

### Post by Krupski on 2009-01-18
> **bogoliubov said:**
> Hello. I am writing a simple python script that looks for certain keywords in RSS feeds, and if found the user is notified using python-notify. 

But it seems I can't get the link feature of python-notify to work when there's and ampersand ("&") in the link URL. Anyone else who has experienced this? Any idea how to fix/bypass it?

Have you tried using \%38 in place of the "&" character?

---

### Post by bogoliubov on 2009-01-18
No, but good idea! Do you know of an easy way of replacing all "&" in the string to "\%38"?

---

### Post by jorgecs10 on 2009-01-19
What about [string.replace]("http://www.python.org/doc/2.5.2/lib/string-methods.html")?

---

### Post by myrtle1908 on 2009-01-19
I don't know python, but surely there is a urlencode function or similar.

---

### Post by bogoliubov on 2009-01-19
string.replace did it very nicely! Thanks for the help!

---


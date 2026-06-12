---
title: "How do I delete SSL certificate?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by KingTermite on 2008-06-23
I created a certuficate using the first part of this web page tutorial:
[http://www.vanemery.com/Linux/Apache/apache-SSL.html](http://www.vanemery.com/Linux/Apache/apache-SSL.html)

Now, I realize, I'm not so sure I need it.

How can I delete it - the correct way?


I'm trying to set up a subversion server, I don't need to create this certificate do I?

---

### Post by furlabs on 2008-07-04
A certificate is just a file, so 
```
rm filename
```
will delete it. It would only be an issue if you have already set up apache to look for this file.

---


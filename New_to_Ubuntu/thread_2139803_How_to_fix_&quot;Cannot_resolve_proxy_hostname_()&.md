---
title: "How to fix &quot;Cannot resolve proxy hostname ()&quot; with Eclipse help files"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-27
I loaded up Eclipse to use as an IDE and when I try to access the help files, I get this:

```
Unable to load page

Problem occurred while loading the URL http://127.0.0.1:37867/help/advanced/help.jsp?topic=%2Forg.eclipse.cdt.doc.user%2Fconcepts%2Fcdt_o_home.htm

Cannot resolve proxy hostname ()
```

---

### Post by stevesy on 2013-04-27
> **alhefner said:**
> I loaded up Eclipse to use as an IDE and when I try to access the help files, I get this:

```
Unable to load page

Problem occurred while loading the URL http://127.0.0.1:37867/help/advanced/help.jsp?topic=%2Forg.eclipse.cdt.doc.user%2Fconcepts%2Fcdt_o_home.htm

Cannot resolve proxy hostname ()
```


[http://help.eclipse.org/juno/index.jsp](http://help.eclipse.org/juno/index.jsp)

---

### Post by alhefner on 2013-04-27
> **stevesy said:**
> [http://help.eclipse.org/juno/index.jsp](http://help.eclipse.org/juno/index.jsp)

Thanks, I'll bookmark the site for online help.

Now, I still need to resolve the actual issue ...

---

### Post by alhefner on 2013-04-28
OK, found how to "fix" the issue...sort of. In the preferences, choose to use an external browser for the help section. That mostly gets you to where you can get to things but you will still get the occasional error.

The real fix, for now, seems to not use Eclipse unless you need extensive documenting in your project. I went to Code::Blocks and that is working very well...

---


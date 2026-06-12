---
title: "SVN help"
date: 2009-01-30
forum: Programming Talk
---

### Post by DFord425 on 2009-01-30
I installed the newest version of eclipse and i have having a problem installing the SVN subclipse so that i can connect to the SVN repository. Is there a way to use the command line downlaod the source code using the SVN.

---

### Post by geirha on 2009-01-30
For the command-line you need the [subversion](apt:subversion) package installed. And to get the source:
```
svn checkout *url-to-the-repository*
# or
svn co *url-to-the-repository*

```

Run "svn help" for more info.

---

### Post by bruce89 on 2009-01-30
I use the Subversive plugin. You also have to install a Subversion connector, perhaps that's what the issue is.

---

### Post by DFord425 on 2009-01-30
That worked, thanks for the help.

---

### Post by DFord425 on 2009-01-30
> **bruce89 said:**
> I use the Subversive plugin. You also have to install a Subversion connector, perhaps that's what the issue is.

I wasnt able to install that, thats what my problem was.

---


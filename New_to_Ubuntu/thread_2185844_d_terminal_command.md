---
title: "\d terminal command"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by EddyNigma on 2013-11-04
Hi folks, hope I have this posted in the right place. I'm new to linux and and file globbing. I'm trying to serch for files containing any digit within the filename by using ls | grep \d, however the results are giving files containing d. It seems the delimiter isn't being recognized. Any ideas how to fix this?

---

### Post by steeldriver on 2013-11-04
Hello and welcome to the forums

The \d digit shorthand is a perl extension - try

```
ls | grep **-P** '\d'
```

See the grep manual pages ('man grep') for an explanation of the different  matcher selections (basic versus extended versus perl)

That being said, parsing the output of the 'ls' command is not a generally recommended way to find files by name

---

### Post by EddyNigma on 2013-11-04
Thanks steeldriver, thats exactly what I was looking for. The ls command was specified in me lab.

---

### Post by steeldriver on 2013-11-04
You're welcome - just for the record '\d' is neither a terminal command nor a glob in this context, it's a *pattern argument* to the grep command

---


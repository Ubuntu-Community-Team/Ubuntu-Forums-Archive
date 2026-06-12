---
title: "Missing XML::Simple"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by alexander21778 on 2012-09-29
Hi, I'm trying to install GCstar and managed to correct all of the missing mandatory components except for XML::Simple. Is there any way that I can tell if this is installed? And if not than what's the best way to install XML::Simple?

I come here as a last resort, I've been googling for at least an hour. Maybe someone can help?

---

### Post by wallaroo on 2012-09-29
The quickest way to check is to run the following on the command.
```
perl -e 'use XML::Simple'
```if you get a 'Cant Locate..' message then it's not installed in any of the places that Perl expects it to be in, if you get no messages, then it has been installed.

To install it yourself, you can either go to the Package Manager and install 'libxml-simple-perl', or alternately you can install it from the CPAN web site using the command-line ..
```
sudo perl -MCPAN -e 'install XML::Simple'
```

---


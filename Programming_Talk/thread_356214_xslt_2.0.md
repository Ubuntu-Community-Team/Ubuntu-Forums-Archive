---
title: "xslt 2.0"
date: 2007-02-08
forum: Programming Talk
---

### Post by waster on 2007-02-08
Hello,

Is there a packaged xslt 2.0 processor for Ubuntu? Saxon 8 isn't in the repos, and I can't seem to find another. What are you using?

---

### Post by runningwithscissors on 2007-02-08
xsltproc?

It may actually be installed on your system already. Try "man xsltproc"

---

### Post by waster on 2007-02-09
Thanks for your reply, but xsltproc is only xslt 1.0, I'm afraid.

---

### Post by Heliix on 2007-03-14
afaik, saxon seems to be the only xslt processor which supports 2.0 version. i have xsltproc which is just fine but.. i would like to split output into several files and only xsl/transformations version 2.0 support <xsl:result-document> tag. 
so, with xsltproc, i have to do it manually.

please, does anybody here use saxon? is it worth installing in my situation? thanks!

---

### Post by shaitan on 2007-06-02
> **Heliix said:**
> 
please, does anybody here use saxon? is it worth installing in my situation? thanks!

why don't you install manually?

[http://saxon.sourceforge.net/](http://saxon.sourceforge.net/)

Saxon-SA 8.9 is a version 30 days evaluation [http://prdownloads.sourceforge.net/saxon/saxonb8-9j.zip](http://prdownloads.sourceforge.net/saxon/saxonb8-9j.zip)

Saxon-B 8.9 is free (as a beer and as a free speech ;)) [http://prdownloads.sourceforge.net/saxon/saxonb8-9j.zip](http://prdownloads.sourceforge.net/saxon/saxonb8-9j.zip)

installation instruction [http://www.saxonica.com/documentation/index/installationjava/installingjava.html](http://www.saxonica.com/documentation/index/installationjava/installingjava.html)

contact me if you have any trouble :)

---

### Post by losomo on 2009-04-20
Currently, it can be installed like this:

```
sudo apt-get install libsaxon-java
```

---

### Post by overdrank on 2009-04-20
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---


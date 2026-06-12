---
title: "Mercurial help"
date: 2010-03-12
forum: Programming Talk
---

### Post by ctult on 2010-03-12
Hi,

I am trying to clone Java's full source, but I don't know how.  I used Mercural, and it just gives me an error.

```

sam@sam-desktop:~/Documents/java_source$ hg clone http://hg.openjdk.java.net/
abort: requirement '<body bgcolor="#f0f0f8"><font color="#f0f0f8" size="-5"> -->' not supported!

```I don't know how to get it all at once, if it is possible.

Thanks in advance, CTuLT.

P.S.  The website is [http://www.sun.com/software/opensource/java/getinvolved.jsp](http://www.sun.com/software/opensource/java/getinvolved.jsp).

---

### Post by Zugzwang on 2010-03-12
Just visit [http://hg.openjdk.java.net/](http://hg.openjdk.java.net/) in your web browser, choose a repository and clone from that URL. You are trying to clone the list of repositories at the moment.

---

### Post by km0r3 on 2010-03-12
Your request link must look somehow like this:
```
hg clone http://hg.openjdk.java.net/jdk7/jdk7/
```

As mentioned earlier you're trying to clone the HTML document.

---


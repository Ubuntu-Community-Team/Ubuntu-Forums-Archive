---
title: "Help: libraries to install for ant &lt;junitreport&gt; with gcj + GNU classpath"
date: 2006-02-04
forum: Programming Talk
---

### Post by as230 on 2006-02-04
Hi,

I'm currently trying to use GNU classpath + gcj + ant for building my Java projects on Ubuntu 5.10.

I've installed these packages (with their dependencies):

classpath
ant
junit
gcj-4.0
libcrimson-java

in addition to several other Java packages which came along during installation.

I then use ant to try build my project on the console. Works fine, the compile and junit steps succeeded; but when I want junit to generate the test report using the <junitreport> task, I got the following error:

```

Could not find a valid processor version implementation from gnu.xml.transform.TransformerFactoryImpl

```

I'm pretty sure I should be missing something. What libraries I didn't install, or any configurations I forgot to make?

Thanks in advance.

---


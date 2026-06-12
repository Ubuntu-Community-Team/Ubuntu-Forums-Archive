---
title: "Problems getting jsp pages to render"
date: 2008-09-17
forum: Programming Talk
---

### Post by devinWhalen on 2008-09-17
Hello,

I am a long time Perl/PHP developer so I figured I should learn a new language, so I am going to give Java a try.

I am trying to create a JSP page and get it running on my Ubuntu machine at home.  I installed java, javac and apache and tomcat, I tried following some docs on how to get it installed but I think I am missing something.  I put a jsp page at my webroot directory /var/www/index.jsp with this in it:
```

<html>
<body>
<%@ page language="java" imports="java.util.*" %>

<H1>Welcome</H1>

</body>
</html> 


```


but it just displays as text when I try to view it in the browser.


Any help would be appreciated, I am just trying to learn java and I can't even seem to get started!

java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)
javac -version
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.

And I have tomcat5.5 installed and running:
sudo /etc/init.d/tomcat5.5 status
 * Tomcat servlet engine is running with pid 11567

---


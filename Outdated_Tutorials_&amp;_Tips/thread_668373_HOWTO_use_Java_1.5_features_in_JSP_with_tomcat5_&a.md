---
title: "HOWTO: use Java 1.5 features in JSP with tomcat5 &amp; sun-java5-jdk, Ubuntu 6.06 LTS"
date: 2008-01-15
forum: Outdated Tutorials &amp; Tips
---

### Post by mdmbkr on 2008-01-15
The most recent version of the Apache Tomcat servlet container in the Ubuntu 6.06 LTS package repository is 5.0 (tomcat5).  Unfornately, Tomcat 5.0 no longer appears to be supported by the Apache community.  In fact, the Tomcat 5.0.x documentation is no longer available at Apache's web site.

Meanwhile, the Sun JDK package is up to version 1.5 (sun-java5-jdk).

If you use 1.5 features (such as autoboxing, or new methods like String.format()) in a JSP page, you may get an unexpected error.  If you compile and test the problem code on the command line with javac/java it will work as expected.

I do not have a complete understanding of the situation, but it appears to me that tomcat is explicity telling the java compiler (perhaps with the -source argument) to behave as though it were an older version.

I found a brief treatment of this issue, as it relates to tomcat 5.5:

[http://blog.taragana.com/index.php/archive/how-to-run-javac-15-or-beyond-compiler-for-jsp-compilation-in-tomcat-55-with-generics-enabled-and-other-15-only-features/]("http://blog.taragana.com/index.php/archive/how-to-run-javac-15-or-beyond-compiler-for-jsp-compilation-in-tomcat-55-with-generics-enabled-and-other-15-only-features/") 

It turns out this approach will also work with tomcat 5.

In short:  Make a backup of /etc/tomcat5/web.xml, and then edit it, adding the following lines to the JSP servlet section:

```

    <servlet>
        <servlet-name>jsp</servlet>
        <servlet-class>org.apache.jasper.servlet.JspServlet</servlet>
        <init-param>
            <param-name>fork</param-name>
            <param-value>false</param-value>
        </init-param>
[B]        <init-param>
            <param-name>compilerSourceVM</param-name>
            <param-value>1.5</param-value>
        </init-param>
        <init-param>
            <param-name>compilerTargetVM</param-name>
            <param-value>1.5</param-value>
        </init-param>
[/B]        <init-param>
            <param-name>xpoweredBy</param-name>
            <param-value>false</param-value>
        </init-param>
        <load-on-startup>3</load-on-startup>
    </servlet>

```


This has been tested on Ubuntu 6.06 LTS AMD64.  It should work on other platforms as well.

---


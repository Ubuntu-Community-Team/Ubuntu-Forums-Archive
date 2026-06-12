---
title: "running Lucene web demo in Ubuntu"
date: 2010-04-14
forum: Programming Talk
---

### Post by huangyingw on 2010-04-14
Hello,
	I have trouble at running Lucene web demo in Ubuntu. And I am a newbie at Java and JSP:(
	Seems that the result.jsp file could not found my lucene-core-3.0.1.jar and lucene-demos-3.0.1.jar files.
	Result of lucene web search [http://192.168.0.25:8080/luceneweb/results.jsp?query=linux&maxresults=100:](http://192.168.0.25:8080/luceneweb/results.jsp?query=linux&maxresults=100:)
	```

	HTTP Status 500 - 

--------------------------------------------------------------------------------

type Exception report

message 

description The server encountered an internal error () that prevented it from fulfilling this request.

exception 

org.apache.jasper.JasperException: An exception occurred processing JSP page /results.jsp at line 38

35:                                                 //less
36: 
37:         try {
38:           IndexReader reader = IndexReader.open(FSDirectory.open(new File(indexName)), true); // only searching, so read-only=true
39:           searcher = new IndexSearcher(reader);         //create an indexSearcher for our page
40:                                                         //NOTE: this operation is slow for large
41:                                                         //indices (much slower than the search itself)


Stacktrace:
	org.apache.jasper.servlet.JspServletWrapper.handleJspException(JspServletWrapper.java:505)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:398)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:342)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:267)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	sun.reflect.GeneratedMethodAccessor21.invoke(Unknown Source)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	java.lang.reflect.Method.invoke(Method.java:616)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:269)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:537)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:301)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:162)


root cause 

javax.servlet.ServletException: java.lang.NoClassDefFoundError: Could not initialize class org.apache.lucene.store.FSDirectory
	org.apache.jasper.runtime.PageContextImpl.doHandlePageException(PageContextImpl.java:862)
	org.apache.jasper.runtime.PageContextImpl.access$1100(PageContextImpl.java:71)
	org.apache.jasper.runtime.PageContextImpl$12.run(PageContextImpl.java:778)
	java.security.AccessController.doPrivileged(Native Method)
	org.apache.jasper.runtime.PageContextImpl.handlePageException(PageContextImpl.java:776)
	org.apache.jsp.results_jsp._jspService(results_jsp.java:332)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:70)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:374)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:342)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:267)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	sun.reflect.GeneratedMethodAccessor21.invoke(Unknown Source)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	java.lang.reflect.Method.invoke(Method.java:616)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:269)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:537)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:301)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:162)


root cause 

java.lang.NoClassDefFoundError: Could not initialize class org.apache.lucene.store.FSDirectory
	org.apache.jsp.results_jsp._jspService(results_jsp.java:163)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:70)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:374)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:342)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:267)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
	sun.reflect.GeneratedMethodAccessor21.invoke(Unknown Source)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	java.lang.reflect.Method.invoke(Method.java:616)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:269)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:537)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:301)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:162)
	
```
	Part of my /etc/profile file:
	```

	root@linux_programming:/media/volgrp/myproject/git/webapps/luceneweb# cat /etc/profile
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).
HERITRIX_HOME=/root/myproject/git/java/heritrix-1.14.3/heritrix-1.14.3/heritrix-1.14.3/
JAVA_OPTS=-Xmx1024M
JAVA_HOME=/usr/lib/jvm/java-6-openjdk/jre/bin/java
CLASSPATH=/media/volgrp/myproject/git/java/lucene/lucene-3.0.1/lucene-core-3.0.1.jar:/media/volgrp/myproject/git/java/lucene/lucene-3.0.1/lucene-demos-3.0.1.jar:/var/lib/tomcat6/webapps/luceneweb/WEB-INF/lib/lucene-core-3.0.1.jar:/var/lib/tomcat6/webapps/luceneweb/WEB-INF/lib/lucene-demos-3.0.1.jar
export CLASSPATHroot@linux_programming:/media/volgrp/myproject/git/webapps/luceneweb# 
	
```
	
	Part of my /var/lib/tomcat6/conf/server.xml file,and indeed that the only part which I have modified:
	```

      <Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true"
            xmlValidation="false" xmlNamespaceAware="false">
				<Context docBase="/media/volgrp/myproject/git/webapps/luceneweb" reloadable="true" path="/luceneweb" />
      </Host>
    </Engine>
  </Service>
</Server>
	
```
	My /media/volgrp/myproject/git/webapps/luceneweb's structure:
	```

	luceneweb
		--WEB-INF
			--lib
				--lucene-core-3.0.1.jar
				--lucene-demos-3.0.1.jar
			--web.xml
		--results.jsp
		--META-INF
			--LICENSE.txt
			--MANIFEST.MF
			--NOTICE.txt
	
```

---

### Post by huangyingw on 2010-04-15
Hello, I see no reply.
Should I simplify my question?
Seems that the JSP could not find the correct *.jar package it need.
I have put the *.jar package under the WEB-INF\lib folder, and update the classpath in /etc/profile. But still I got the fail to initialize the class exception.

---


---
title: "Issue with tomcat not recognizing JARs"
date: 2009-10-23
forum: Programming Talk
---

### Post by billy61 on 2009-10-23
Hello all,

I recently installed tomcat 5.5 on my ubuntu 9.04 server, in order to develop some jsp/servlets webapps.  

My app that I am going to be developing is going to use the jakarta commons HttpClient library.

I downloaded the library from [here]("http://hc.apache.org/downloads.cgi") and unzipped it, and put the jars in my WEB-INF/lib directory.

however, when I go to a simple page i made (you can view it [here]("http://bk.unl.edu:8180/billy/")) I get an error saying that HttpClient cannot be resolved to a type.  I imported the package in my page, can anyone help me figure out what is wrong?

here is the code for my page:
```

<%@ page import="org.apache.commons.httpclient.*" %>
<%@ page import="org.apache.commons.httpclient.methods.*" %>
<%@ page import="org.apache.commons.httpclient.params.HttpMethodParams.*" %>

<html>
<head><title>test</title></head>
<body>
Hello!
<%
HttpClient client = new HttpClient();
%>
</body>
</html>

```

---


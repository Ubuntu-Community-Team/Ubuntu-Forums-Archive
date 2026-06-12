---
title: "Jetty, Apache and HTTP status 302"
date: 2011-03-23
forum: Programming Talk
---

### Post by cavh on 2011-03-23
Having posted on stackoverflow and coderanch without any answers, I'm hoping someone here has an idea :)


I have a webapp running on Jetty 7.2.2. The webapp includes a proxy servlet which forwards requests to a Bugzilla installation running on localhost, port 80 (Apache serves the Bugzilla pages).

When I request a particular URL through the webapp, the Apache access log shows a response as expected; and the jetty request log does the same, but the web page isn't displayed in the browser, and no error message is generated.

_Jetty request log_

[COLOR="Blue"]0:0:0:0:0:0:0:1 - - [22/Mar/2011:12:22:17 +0000] "GET /dash/bugs/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=open&product=&content= HTTP/1.1" 200 0[/COLOR]

_Apache log_

[COLOR="Blue"]127.0.0.1 - - [22/Mar/2011:12:22:17 +0000] "GET /bugzilla/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=open&product=&content= HTTP/1.1" 302 290 "http://localhost:8080/dash/bugs/query.cgi" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.13 (KHTML, like Gecko) Chrome/9.0.597.98 Safari/534.13"

127.0.0.1 - - [22/Mar/2011:12:22:19 +0000] "GET /bugzilla/buglist.cgi?query_format=specific&order=relevance%20desc&bug_status=open&list_id=73 HTTP/1.1" 200 4081 "http://localhost:8080/dash/bugs/query.cgi" "Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/534.13 (KHTML, like Gecko) Chrome/9.0.597.98 Safari/534.13"[/COLOR]

Looking closer at the Apache log, I see that the initial request produces HTTP status 302, i.e. that the resource requested has moved. A second request is then made which returns '200 4081', i.e. the request has succeeded and 4081 bytes of data have been returned. However, the Jetty log indicates a '200 0' response, i.e. a successful fetch but zero bytes returned. If I access Bugzilla through Apache (i.e. not through my webapp on localhost:8080), all works just fine.

How can I configure my webapp to ensure that moved resources are displayed? Is it a Jetty configuration issue, or do I have to adjust my Apache configuration?

Thank you,

---

### Post by Some Penguin on 2011-03-23
You might have to show the source of the webapp's request handler.  Is it a custom job?

---

### Post by cavh on 2011-03-24
Thanks for your reply. No, I'm not using a custom handler; I'm using a vanilla Jetty distribution and starting it as plainly and simply as possible with 'java -jar start.jar'. I'm no servlet expert so assume I'm a total fool in these matters :)

Here is my web.xml:

```
<?xml version="1.0" encoding="UTF-8"?>
<web-app 
   xmlns="http://java.sun.com/xml/ns/javaee" 
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd" 
   version="2.5"> 

  <filter>
    <filter-name>JettyContinuationFilter</filter-name>
    <filter-class>org.eclipse.jetty.continuation.ContinuationFilter</filter-class>
  </filter>
  <filter-mapping>
    <filter-name>JettyContinuationFilter</filter-name>
    <url-pattern>/bugs/*</url-pattern>
  </filter-mapping>
  
   <servlet>
     <servlet-name>BugzillaProxy</servlet-name>
     <servlet-class>org.eclipse.jetty.servlets.ProxyServlet$Transparent</servlet-class>
     <init-param>
       <param-name>Prefix</param-name><param-value>/bugs</param-value>
     </init-param>
     <init-param>
        <param-name>ProxyTo</param-name><param-value>http://localhost/bugzilla/</param-value>
     </init-param>
     <init-param>
      <param-name>HostHeader</param-name><param-value>localhost</param-value>
    </init-param>
     <load-on-startup>1</load-on-startup>
  </servlet>
  <servlet-mapping>
     <servlet-name>BugzillaProxy</servlet-name>
     <url-pattern>/bugs/*</url-pattern>
  </servlet-mapping>  

  <welcome-file-list>
    <welcome-file>Dashboard.html</welcome-file>
  </welcome-file-list>

</web-app>
```

---

### Post by cavh on 2011-03-24
Update: things go wrong when I log in to Bugzilla through my webapp. If I'm not logged in I can search for bugs (but obviously not update them). If I log in, the search page just 'goes nowhere', i.e. zero bytes are fetched. 

Looking closer at the link targets displayed on the various pages within Bugzilla, I can see that when logged in, the link is of type 'http://localhost/bugzilla' when it should be of type 'http://localhost:8080/dash/bugzilla'. When not logged in, the links are correct. The reason zero bytes are returned must be to do with this difference. Very strange .....

---

### Post by cavh on 2011-03-25
Further update - I think the problem is to do with the [FONT="Courier New"]urlbase[/FONT] setting in the Bugzilla Administration Parameters page. Will post further in due course.

---


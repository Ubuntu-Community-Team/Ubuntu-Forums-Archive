---
title: "Apache setup with Tomcat - htaccess redirect"
date: 2008-07-08
forum: Programming Talk
---

### Post by Asham on 2008-07-08
Hello

I have no experience working with Apache so I need help getting a simple htaccess rule to work.

The httpd.conf file has several virtual hosts and for one of them I'd like to redirect ALL REQUESTS to one particular page on that domain. The page will be used for when the site is down due to server maintenance. If the htaccess is activated, all requests are forwarded to this page.

Thing is I have no idea how to setup Apache for this to work.

Would placing the htaccess-file in the root of the virtual domain work?
```

Options +FollowSymLinks
RewriteEngine on
RewriteRule (.*) http://my.domain.com/my/page.jsp$1 [R=301,L] 

```

---

### Post by Asham on 2008-07-08
Actually my first description was not accurate enough

I want all requests to forward to: /my/page.jsp?id=200

So even requests for /my/page.jsp?id=123 should be forwarded to the URL above. Don't know if that makes adds to the complexity.

---


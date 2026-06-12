---
title: "JavaScript To Retrieve Logged In User"
date: 2009-04-08
forum: Programming Talk
---

### Post by xluryan on 2009-04-08
It seems like this should be simple. I have an Apache server with several pages secured via .htaccess/.htpasswd files.

Behind the login prompt is an AJAX page. What I'd like to do is have it behave differently for certain users. How can I get the JavaScript to look up which user logged in?

---

### Post by soltanis on 2009-04-08
If you have some kind of system for sessions (using cookies), then look up the user's session cookie, look up the user using an AJAX request to a server-side application, then change the page behavior.

client -> login -> assign session cookie -> give client copy, retain server copy in DB

client -> page -> lookup session cookie -> send cookie to server

server -> lookup cookie in DB -> return user name

client javascript -> read returned value(s) -> change the page accordingly

---


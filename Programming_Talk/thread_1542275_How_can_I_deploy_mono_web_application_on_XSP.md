---
title: "How can I deploy mono web application on XSP ?"
date: 2010-07-30
forum: Programming Talk
---

### Post by hoboy on 2010-07-30
I have install mono 2 on lucid from the repository.
When I make web project then hit run the XSP server start.
but it doesn't deploy the application on XSP webServer.
I get 
Server Error in '/' Application
The resource cannot be found.
error 404

---

### Post by jmbaria on 2010-09-24
you need to change directory to /usr/share/asp.net2-demos/ and then run xsp2.
i.e
```

user@computer4:~$ cd /usr/share/asp.net2-demos/ 
user@computer4:/usr/share/asp.net2-demos$ xsp2
xsp2
Listening on address: 0.0.0.0
Root directory: /usr/share/asp.net2-demos
Listening on port: 8080 (non-secure)
Hit Return to stop the server.


```

---

### Post by directhex on 2010-09-24
> **hoboy said:**
> I have install mono 2 on lucid from the repository.
When I make web project then hit run the XSP server start.
but it doesn't deploy the application on XSP webServer.
I get 
Server Error in '/' Application
The resource cannot be found.
error 404

Are you definitely connecting to the correct port? When an XSP instance starts, it'll pick a port like 8081. Make sure this is the port you're trying to connect to in your browser.

---


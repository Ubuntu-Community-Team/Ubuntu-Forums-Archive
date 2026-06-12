---
title: "[Python] Simple server Authentication"
date: 2009-06-10
forum: Programming Talk
---

### Post by mzi on 2009-06-10
Hello all,

I am desperately trying to find a way to handle authentication with python BaseHTTPServer. I have created a simple client script following the howto available here:

[http://www.wingware.com/psupport/python-manual/2.6/howto/urllib2.html#id6](http://www.wingware.com/psupport/python-manual/2.6/howto/urllib2.html#id6)

My question is: on the server side, how can I fetch authentication information (username, password) so that I can check them? 

So far, the request handler (BaseHTTPRequestHandler) implements a simple "do_GET" method that should be able to access this information through the methods of the handler. I have tried "self.headers.get("Authorization")" and the like without success, and printing "self.headers.headers" clearly shows that authentication information are not in the headers...

Any idea? Thanks for any help.

---


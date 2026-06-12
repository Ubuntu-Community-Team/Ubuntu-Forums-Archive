---
title: "Http edirects in python"
date: 2014-08-06
forum: Programming Talk
---

### Post by demontager on 2014-08-06
How may i redirect user's webrowser to some url if non-existent file requested ? For example i want all 404 errors(not found) redirect to index.html
I am using basic methods to run webserver, as you see do_HEAD method of CGIHTTPRequestHandler already defined, but there is no 404 redirects.
```

#!/usr/bin/env python3

import http.server
from http.server import CGIHTTPRequestHandler

port = 80
addr = '192.168.150.1'
addrport = (addr, port)

class myHandler(CGIHTTPRequestHandler):
    def do_HEAD(s):
        if not self.path=="/":
            f = open(curdir + sep + self.path) 
            self.send_response(200)
            self.send_header('Content-type','text/html')
            self.end_headers()
            self.wfile.write(f.read())
            f.close()
        return
try:
    serv = http.server.HTTPServer(
        addrport,
        myHandler
    )
    serv.serve_forever()
except KeyboardInterrupt:
    print ('Shutting down the web server')
    serv.socket.close()
EOF


```

---

### Post by ofnuts on 2014-08-06
Send it a [redirection status code](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes#3xx_Redirection) with the new URL (302, usually).

---

### Post by ian-weisser on 2014-08-06
ofnuts is right.

Error and redirection codes exist for a reason. Use them, and let the client decide what they want to do about it.
If a client keep trying to access *foo.html*, but keeps getting *index.html* instead, they may assume your server is broken.

---

### Post by demontager on 2014-08-06
ok, and how practically to code this redirection in python ? If i use apache2 as webserver i simply put in .htaccess
ErrorDocument 404 /index.php

---

### Post by ian-weisser on 2014-08-06
Pretty much the same way you coded the 200 success within your MyHandler class.

---

### Post by demontager on 2014-08-07
I was unable to get it working, could you show any sample code example, please ?

---

### Post by ofnuts on 2014-08-07
What have you done/tried so far?

---

### Post by demontager on 2014-08-08
Tried below code
```

#!/usr/bin/env python3

import http.server
from http.server import CGIHTTPRequestHandler

port = 80
addr = '192.168.150.1'
addrport = (addr, port)

class myHandler(CGIHTTPRequestHandler):
    def do_GET(self):
        if not self.path == '/':
            self.send_response(302)
            self.send_header('Location','/index.html')
            self.end_headers()

try:
    serv = http.server.HTTPServer(
        addrport,
        myHandler
    )
    serv.serve_forever()
except KeyboardInterrupt:
    print ('Shutting down the web server')
    serv.socket.close()



```
When client requesting not root path / it gets redirected to 192.168.150.1/index.html, but index.html not shown, browser reporting "Firefox has detected that the server is redirecting the request for this address in a way that will never complete."
If / requested index.html not shown as well. If i use http.server without my own class CGIHTTPRequestHandler index.html working. Code as below
```

#!/usr/bin/env python3

import http.server

port = 80
addr = '192.168.150.1'
addrport = (addr, port)

try:
    serv = http.server.HTTPServer(
        addrport,
        http.server.CGIHTTPRequestHandler
    )
    serv.serve_forever()
except KeyboardInterrupt:
    print ('Shutting down the web server')
    serv.socket.close()

```

---


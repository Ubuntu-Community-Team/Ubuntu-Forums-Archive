---
title: "Python socket Server Help"
date: 2014-05-29
forum: Programming Talk
---

### Post by sameermw on 2014-05-29
I need a python socket program for my latest project and i found this code.

```
#Copyright Jon Berg , turtlemeat.com


import string,cgi,time
from os import curdir, sep
from BaseHTTPServer import BaseHTTPRequestHandler, HTTPServer


class MyHandler(BaseHTTPRequestHandler):


    def do_GET(self):
        try:
            if self.path.endswith(".html"):
                f = open(curdir + sep + self.path) 
                #self.path has /test.html
                #note that this potentially makes every file on your computer readable by the internet


                self.send_response(200)
                self.send_header('Content-type',    'text/html')
                self.end_headers()
                self.wfile.write(f.read())
                f.close()
                return
            return
                
        except IOError:
            self.send_error(404,'File Not Found: %s' % self.path)
     
def main():
    try:
        server = HTTPServer(('', 8585), MyHandler)
        print 'Hello...started httpserver...'
        server.serve_forever()
    except KeyboardInterrupt:
        print '  shutting down server... Bye...'
        server.socket.close()


if __name__ == '__main__':
    main()



```

I've modified this code and added more advanced feature it according to my requirements. It works well, but what i need is when i run this code, need to automatically open web browser http://localhost:<8585>. How do i do that. Thanks.

---

### Post by ian-weisser on 2014-05-29
import subprocess
subprocess.call(['firefox', 'http://localhost:8585'])

Be careful where you put it. Using subprocess.call will block further execution until after Firefox terminates.
You should really open the server and client using separate processes so they don't block each other.

---

### Post by sameermw on 2014-05-30
i found this code and it's work fine.
[B]
webbrowser.open_new("http://localhost:" + str(portNum))[/B]

By the way I'll try that too. Anyway Thank you for your comment.

---


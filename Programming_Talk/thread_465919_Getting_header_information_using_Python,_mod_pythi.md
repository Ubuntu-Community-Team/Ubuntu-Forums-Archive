---
title: "Getting header information using Python, mod_pythin and Apache"
date: 2007-06-06
forum: Programming Talk
---

### Post by lrhaugen on 2007-06-06
I have some problems getting the information sent in the header from a client to server.

In my scenario I will send a file (http POST) from a client (mobile or stationary) to a server. The server should store the file, and send some kind of 200 OK reply if the file is received properly. 
I will send the filename in the header, so I know what to save it as on the server.

I have searched and found some examples, but they are all sending the file from a web form, and the server gets the filename from there.

So can anyone help get the header info? and the body content?

I use python 2.5, mod_python 3.3.1 and apache 2.2.3

thanks!

---

### Post by pmasiar on 2007-06-06
maybe this [file upload recipe](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/273844) will help?

---

### Post by lrhaugen on 2007-06-07
Thanks for your tip!
The problem here is that the filename is given in a form. I would like to get it from the header of an http post request, so it is hardcoded on the client side.

---

### Post by pmasiar on 2007-06-07
The use cgi module on the server.

```

#!/usr/bin/python
import cgi
import cgitb; cgitb.enable()

FORM = cgi.FieldStorage()
filename= FORM.getfirst('filename')

```

See WebApplication page at wiki in my sig for simple 35-lines example.

---

### Post by lrhaugen on 2007-06-12
Thanks!

Have you tried using mod_pythons util?

from mod_python import util

def index(req):

        form = util.FieldStorage(req)
        fname = form.get("firstname",None)

Should be the same as cgi
FORM = cgi.FieldStorage()
filename= FORM.getfirst('filename')

The problem now is that i can't get only the headers from the request.
req.headers_in.get("content-length")) - give the correct content-length, but
req.read() - will not give anything.

the 'fname' outputs NONE.

I really don't understand this, any ideas?

---


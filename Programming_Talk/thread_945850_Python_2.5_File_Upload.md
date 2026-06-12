---
title: "Python 2.5 File Upload?"
date: 2008-10-12
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-10-12
I have been looking around and found that this is supposed to work, but of course it doesn't. nothing even prints

[PHP]
#!/usr/bin/env python
print "Content-Type: text/html"
print

import cgi, os
form = cgi.FieldStorage()

if form.has_key("file") and form.has_key('name') and form.has_key('key'):# and form['name'].value == 'aidan' and form['key'].value == open('/var/http.key', 'r').read():
        fname = form['file'].value[form['file'].value.rfind('/')+1:]
        f = open('/data/uploads/' + fname, 'w')
        f.write(form['file'].file.read())
        #f.close()
        #print "<html>Upload Successful</html>"
        print fname
else:
        print open('/var/www/fileupload.html', 'r').read()
[/PHP]

but if i comment out "f.write(form['file'].file.read())" then the fname prints??

Does anyone know what is wrong

---


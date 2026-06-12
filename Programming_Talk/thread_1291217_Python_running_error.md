---
title: "Python running error"
date: 2009-10-14
forum: Programming Talk
---

### Post by hoboy on 2009-10-14
I am using eclipse to try to run a small Google app engine tutorial.
witch is created by the googleappengine wizard.
*****************************************************************
from google.appengine.ext import webapp
from google.appengine.ext.webapp.util import run_wsgi_app

class MainPage(webapp.RequestHandler):
    
    
    def get(self):
        self.response.headers['Content-Type'] = 'text/plain'
        self.response.out.write('Hello, webapp World!')


application = webapp.WSGIApplication([('/', MainPage)], debug=True)


def main():
    run_wsgi_app(application)

if __name__ == "__main__":
    main()
****************************************************************
Here is the error when I try to run it insid eclipse


Traceback (most recent call last):
  File "C:\eclipse-jee-galileo-SR1-win32\eclipse\workspace\TesEng02\src\helloworld.py", line 1, in <module>
    from google.appengine.ext import webapp
  File "C:\Program Files\Google\google_appengine\google\appengine\ext\webapp\__init__.py", line 247
    except UnicodeError, e:
                       ^
SyntaxError: invalid syntax

---

### Post by unutbu on 2009-10-14
Please post lines 230--250 of
C:\Program Files\Google\google_appengine\google\appengine\ext \webapp\__init__.py

PS. I can produce the same error with the code-snippet:
[PHP]
#!/usr/bin/env python
except UnicodeError,e:
    print(e)[/PHP]

Here there is an except-block without a try-block first. Perhaps that is what is wrong in 
C:\Program Files\Google\google_appengine\google\appengine\ext \webapp\__init__.py

---

### Post by hoboy on 2009-10-14
> **unutbu said:**
> Please post lines 230--250 of
C:\Program Files\Google\google_appengine\google\appengine\ext \webapp\__init__.py

PS. I can produce the same error with the code-snippet:
[PHP]
#!/usr/bin/env python
except UnicodeError,e:
    print(e)[/PHP]

Here there is an except-block without a try-block first. Perhaps that is what is wrong in 
C:\Program Files\Google\google_appengine\google\appengine\ext \webapp\__init__.py

Thanks.

def clear(self):
    """Clears all data written to the output stream so that it is empty."""
    self.out.seek(0)
    self.out.truncate(0)

  def wsgi_write(self, start_response):
    """Writes this response using WSGI semantics with the given WSGI function.

    Args:
      start_response: the WSGI-compatible start_response function
    """
    body = self.out.getvalue()
    if isinstance(body, unicode):
      body = body.encode('utf-8')
    elif self.headers.get('Content-Type', '').endswith('; charset=utf-8'):
      try:
        body.decode('utf-8')
      except UnicodeError, e:
        logging.warning('Response written is not UTF-8: %s', e)

    if (self.headers.get('Cache-Control') == 'no-cache' and

---

### Post by unutbu on 2009-10-14
Are you using python3? I'm also able to reproduce the SyntaxError using the code snippet
[PHP]
#!/usr/bin/env python3
try:
    ha
except UnicodeError,e:
    print(e)
[/PHP]

PS. I don't see anything wrong in the code you posted. 
The code presumably has the correct indentation. If it did not, you would have gotten an IndentationError, rather than a SyntaxError.

---

### Post by hoboy on 2009-10-14
> **unutbu said:**
> Are you using python3? I'm also able to reproduce the SyntaxError using the code snippet
[PHP]
#!/usr/bin/env python3
try:
    ha
except UnicodeError,e:
    print(e)
[/PHP]

PS. I don't see anything wrong in the code you posted. 
The code presumable has the correct indentation. If it did not, you would have gotten an IndentationError, rather than a SyntaxError.

Thanks I will try it later I have delete some thinks that need to be reinstalled.

---

### Post by engla on 2009-10-14
> **unutbu said:**
> Are you using python3? I'm also able to reproduce the SyntaxError using the code snippet
[PHP]
#!/usr/bin/env python3
try:
    ha
except UnicodeError,e:
    print(e)
[/PHP]

PS. I don't see anything wrong in the code you posted. 
The code presumably has the correct indentation. If it did not, you would have gotten an IndentationError, rather than a SyntaxError.

If it's not Python 3 code, don't run it with Python 3!

A bit OT, but if it really is Python 3, the correct way to catch an exception is like this:
```

try:
    pass
except UnicodeError as e:
    print(e)  
```

With many exception types:
```

try:
    pass
except (AttributeError, KeyError) as e:
    print(e)  
```

---


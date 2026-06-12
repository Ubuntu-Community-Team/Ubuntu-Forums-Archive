---
title: "Turbogears web service connection with SUDS -- connection denied"
date: 2010-08-20
forum: Programming Talk
---

### Post by matmatmat on 2010-08-20
Hi everyone, I'm trying to make a simple web service, described
[here]("http://www.doughellmann.com/articles/pythonmagazine/features/building-soap-service//index.html#prototyping-with-tgwebservices").
I am using turbogears1 installed from the ubuntu repos:
```

#controller.py
from turbogears import controllers, expose, flash
from tgwebservices.controllers import WebServicesRoot, wsexpose, wsvalidate

class EchoService(WebServicesRoot):
    """EchoService web service definition"""

    @wsexpose(str)
    @wsvalidate(value=str)
    def echo(self, value):
        "Echo the input back to the caller."
        return value

class Root(controllers.RootController):
    """The root controller of the application."""

    echo = EchoService('http://localhost:7000/echo/')

```
I can view the WSDL file in my browser, but I want to be able to access it
from a python script, so I downloaded the SUDS module... but this didn't
work:
```

>>> from suds.client import Client
>>> url = 'http://0.0.0.0:8080/echo/soap/api.wsdl'
>>> client = Client(url)
>>> print client

Suds ( https://fedorahosted.org/suds/ )  version: 0.3.9 GA  build:
R659-20100219

Service ( EchoService ) tns="http://localhost:7000/echo/soap/"
   Prefixes (0)
   Ports (1):
      (EchoService_PortType)
         Methods (1):
            echo(xs:string value, )
         Types (0):


>>> resut = client.service.echo("hi")
Traceback (most recent call last):
  File "", line 1, in 
  File
"/usr/local/lib/python2.6/dist-packages/suds-0.3.9-py2.6.egg/suds/client.py",
line 539, in __call__
    return client.invoke(args, kwargs)
  File
"/usr/local/lib/python2.6/dist-packages/suds-0.3.9-py2.6.egg/suds/client.py",
line 598, in invoke
    result = self.send(msg)
  File
"/usr/local/lib/python2.6/dist-packages/suds-0.3.9-py2.6.egg/suds/client.py",
line 623, in send
    reply = transport.send(request)
  File
"/usr/local/lib/python2.6/dist-packages/suds-0.3.9-py2.6.egg/suds/transport/https.py",
line 64, in send
    return  HttpTransport.send(self, request)
  File
"/usr/local/lib/python2.6/dist-packages/suds-0.3.9-py2.6.egg/suds/transport/http.py",
line 77, in send
    fp = self.u2open(u2request)
  File
"/usr/local/lib/python2.6/dist-packages/suds-0.3.9-py2.6.egg/suds/transport/http.py",
line 118, in u2open
    return url.open(u2request, timeout=tm)
  File "/usr/lib/python2.6/urllib2.py", line 391, in open
    response = self._open(req, data)
  File "/usr/lib/python2.6/urllib2.py", line 409, in _open
    '_open', req)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 1161, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.6/urllib2.py", line 1136, in do_open
    raise URLError(err)
urllib2.URLError: 
>>>

```
Is this is problem with the web service or the client?

---


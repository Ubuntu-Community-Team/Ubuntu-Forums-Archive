---
title: "Python Web Service Client"
date: 2007-11-07
forum: Programming Talk
---

### Post by skeeterbug on 2007-11-07
Hey All,
I am working on a Python library to communicate with some .NET web services (some internal ones within the company, and Authorize.NET later on). I found a SOAP library on sourceforge that seems to be updated.

[http://pywebsvcs.sourceforge.net/zsi.html](http://pywebsvcs.sourceforge.net/zsi.html)

However, I am getting an error when attempting to call my web service.
```

from ZSI.client import Binding
b = Binding(url='http://192.168.1.200/WebService/UserService.asmx')
result = b.Login('user','pass')
print result

```

Error:
```
Traceback (most recent call last):
  File "C:\soap.py", line 3, in ?
    result = b.Login('user','pass')
  File "build\bdist.win32\egg\ZSI\client.py", line 42, in __call__
  File "build\bdist.win32\egg\ZSI\client.py", line 171, in RPC
  File "build\bdist.win32\egg\ZSI\client.py", line 503, in Receive
  File "build\bdist.win32\egg\ZSI\client.py", line 431, in Receive
FaultException: Server did not recognize the value of HTTP Header SOAPAction: .

```

Does anyone have experience in this area? Thanks!

---

### Post by skeeterbug on 2007-11-07
Nevermind, I used the wsdl2py script and got it working OK that way.

---


---
title: "SOAPpy"
date: 2009-06-09
forum: Programming Talk
---

### Post by matmatmat on 2009-06-09
Does anyone know of any SOAP tutorials? I have tried a few examples:
```

import SOAPpy as SOAP
  # XMethods.net provides several interesting SOAP
  # services.  See the references below for details.
server = SOAP.SOAPProxy(
  "http://services.xmethods.net/soap/servlet/rpcrouter",
  namespace = "urn:xmethods-Temperature")
  # 47978 is Rensselaer's zip (postal) code.
print server.getTemp("47978")

```
which outputs:
```

Traceback (most recent call last):
  File "soaptest.py", line 8, in <module>
    print server.getTemp("47978")
  File "/var/lib/python-support/python2.6/SOAPpy/Client.py", line 470, in __call__
    return self.__r_call(*args, **kw)
  File "/var/lib/python-support/python2.6/SOAPpy/Client.py", line 492, in __r_call
    self.__hd, self.__ma)
  File "/var/lib/python-support/python2.6/SOAPpy/Client.py", line 363, in __call
    config = self.config)
  File "/var/lib/python-support/python2.6/SOAPpy/Client.py", line 187, in call
    r.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 868, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 740, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 699, in send
    self.connect()
  File "/usr/lib/python2.6/httplib.py", line 683, in connect
    self.timeout)
  File "/usr/lib/python2.6/socket.py", line 498, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
socket.gaierror: [Errno -2] Name or service not known

```
which im guessing means that the service no longer exists and is therefor out of date

---

### Post by matmatmat on 2009-06-10
bump

---


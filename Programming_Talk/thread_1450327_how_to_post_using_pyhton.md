---
title: "how to post using pyhton"
date: 2010-04-08
forum: Programming Talk
---

### Post by mobio.dev on 2010-04-08
hi expert, i'm newbie for python, learning using sample code, now i'm trying send data to server using python,  i.e wireless ssid, so i need to send as follow

http://22.42.13.58:8080/ProcessData?data={"userId":"guest"}

how this can be done

i try as follow

import httplib,urllib
params = urllib.urlencode({'userId':'guest'})
headers = {"Content-type":"application/x-www-form-urlencoded","Accept":"text/plain"}
conn=httplib.HTTPConnection("http://202.45.139.58:8080")
conn.request("POST","ppod-web/ProcessRawData?data=",params,headers)
response = conn.getresponse()
print response.status,response.reason
data = response.read()
conn.close()

but getting error as follow 

  File "http.py", line 6, in <module>
    conn.request("POST","ppod-web/ProcessRawData?data=",params,headers)
  File "/usr/lib/python2.6/httplib.py", line 898, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python2.6/httplib.py", line 935, in _send_request
    self.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 892, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 764, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 723, in send
    self.connect()
  File "/usr/lib/python2.6/httplib.py", line 704, in connect
    self.timeout)
  File "/usr/lib/python2.6/socket.py", line 500, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
socket.gaierror: [Errno -2] Name or service not known

can anyone help me :confused:

thanks in advance

---

### Post by skullmunky on 2010-04-21
I tried your code and I got a timeout, the server's not up.  that could be your problem ... other than that the code looks right to me.

---


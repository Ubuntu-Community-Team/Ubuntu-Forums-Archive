---
title: "Why does the Temporary failure in name resolution error sometimes occur?"
date: 2021-08-19
forum: New to Ubuntu
---

### Post by tipoheri on 2021-08-19
finally there is a tube where you can find porn with big **** beauties absolutely free [https://bigtitstube.xxx/](https://bigtitstube.xxx/)
There is a python script that makes frequent requests to api.telegram.org. (about 40 requests per minute, made with the requests module).
The script runs using nohup and should run continuously for a long time. However once a day or so at any time it may crash with an error
[PHP]Traceback (most recent call last):
  File "/usr/local/lib/python3.9/dist-packages/urllib3/connection.py", line 169, in _new_conn
    conn = connection.create_connection(
  File "/usr/local/lib/python3.9/dist-packages/urllib3/util/connection.py", line 73, in create_connection
    for res in socket.getaddrinfo(host, port, family, socket.SOCK_STREAM):
  File "/usr/lib/python3.9/socket.py", line 953, in getaddrinfo
    for res in _socket.getaddrinfo(host, port, family, type, proto, flags):
socket.gaierror: [Errno -3] Temporary failure in name resolution

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/local/lib/python3.9/dist-packages/urllib3/connectionpool.py", line 699, in urlopen
    httplib_response = self._make_request(
  File "/usr/local/lib/python3.9/dist-packages/urllib3/connectionpool.py", line 382, in _make_request
    self._validate_conn(conn)
  File "/usr/local/lib/python3.9/dist-packages/urllib3/connectionpool.py", line 1010, in _validate_conn
    conn.connect()
  File "/usr/local/lib/python3.9/dist-packages/urllib3/connection.py", line 353, in connect
    conn = self._new_conn()
  File "/usr/local/lib/python3.9/dist-packages/urllib3/connection.py", line 181, in _new_conn
    raise NewConnectionError(
urllib3.exceptions.NewConnectionError: <urllib3.connection.HTTPSConnection object at 0x7f89f832c340>: Failed to establish a new connection: [Errno -3] Temporary failure in name resolution

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/local/lib/python3.9/dist-packages/requests/adapters.py", line 439, in send
    resp = conn.urlopen(
  File "/usr/local/lib/python3.9/dist-packages/urllib3/connectionpool.py", line 755, in urlopen
    retries = retries.increment(
  File "/usr/local/lib/python3.9/dist-packages/urllib3/util/retry.py", line 574, in increment
    raise MaxRetryError(_pool, url, error or ResponseError(cause))
urllib3.exceptions.MaxRetryError: HTTPSConnectionPool(host='api.telegram.org', port=443): Max retries exceeded with url: /bot1885620738:A/sendMessage?chat_id=-10015&text=2F&parse_mode=HTML (Caused by NewConnectionError('<urllib3.connection.HTTPSConnection object at 0x7f89f832c340>: Failed to establish a new connection: [Errno -3] Temporary failure in name resolution'))

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/root/PHa/parse_old.py", line 79, in <module>
    response = requests.get(tgUrl)
  File "/usr/local/lib/python3.9/dist-packages/requests/api.py", line 75, in get
    return request('get', url, params=params, **kwargs)
  File "/usr/local/lib/python3.9/dist-packages/requests/api.py", line 61, in request
    return session.request(method=method, url=url, **kwargs)
  File "/usr/local/lib/python3.9/dist-packages/requests/sessions.py", line 542, in request
    resp = self.send(prep, **send_kwargs)
  File "/usr/local/lib/python3.9/dist-packages/requests/sessions.py", line 655, in send
    r = adapter.send(request, **kwargs)
  File "/usr/local/lib/python3.9/dist-packages/requests/adapters.py", line 516, in send
    raise ConnectionError(e, request=request)
requests.exceptions.ConnectionError: HTTPSConnectionPool(host='api.telegram.org', port=443): Max retries exceeded with url: /bot1885620738:AAGIHn10gB/sendMessage?chat_id=-100154&text=%3Cb%3D0% (Caused by NewConnectionError('<urllib3.connection.HTTPSConnection object at 0x7f89f832c340>: Failed to establish a new connection: [Errno -3] Temporary failure in name resolution'))[/PHP]

---

### Post by ActionParsnip on 2021-08-19
Failure in name resolution is a DNS issue. If you use different DNS servers does it help?

---


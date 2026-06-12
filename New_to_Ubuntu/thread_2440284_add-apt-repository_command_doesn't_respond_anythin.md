---
title: "add-apt-repository command doesn't respond anything"
date: 2020-04-08
forum: New to Ubuntu
---

### Post by staffcondor on 2020-04-08
I can't add any PPA using "add-apt-repository" command on my laptop (HP Elitebook folio 9470m, Kubuntu 18.04 and Windows 10 Dual) every-time when I use it, it doesn't respond anything and when I stop the process by using Ctrl+C, it throws out the following errors;

```
sudo add-apt-repository ppa:kokoye2007/ppa
^CTraceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 136, in <module>
    shortcut = shortcut_handler(line)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 868, in shortcut_handler
    ret = factory(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 398, in shortcut_handler
    return PPAShortcutHandler(shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 355, in __init__
    info = get_ppa_info(self.shortcut)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 326, in get_ppa_info
    ret = get_ppa_info_from_lp(user, ppa)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 101, in get_ppa_info_from_lp
    return get_info_from_lp(lp_url)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 95, in get_info_from_lp
    return get_info_from_https(lp_url, True)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 88, in get_info_from_https
    data = _get_https_content_py3(url, accept_json)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 120, in _get_https_content_py3
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.6/urllib/request.py", line 223, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.6/urllib/request.py", line 526, in open
    response = self._open(req, data)
  File "/usr/lib/python3.6/urllib/request.py", line 544, in _open
    '_open', req)
  File "/usr/lib/python3.6/urllib/request.py", line 504, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.6/urllib/request.py", line 1361, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.6/urllib/request.py", line 1318, in do_open
    encode_chunked=req.has_header('Transfer-encoding'))
  File "/usr/lib/python3.6/http/client.py", line 1254, in request
    self._send_request(method, url, body, headers, encode_chunked)
  File "/usr/lib/python3.6/http/client.py", line 1300, in _send_request
    self.endheaders(body, encode_chunked=encode_chunked)
  File "/usr/lib/python3.6/http/client.py", line 1249, in endheaders
    self._send_output(message_body, encode_chunked=encode_chunked)
  File "/usr/lib/python3.6/http/client.py", line 1036, in _send_output
    self.send(msg)
  File "/usr/lib/python3.6/http/client.py", line 974, in send
    self.connect()
  File "/usr/lib/python3.6/http/client.py", line 1407, in connect
    super().connect()
  File "/usr/lib/python3.6/http/client.py", line 946, in connect
    (self.host,self.port), self.timeout, self.source_address)
  File "/usr/lib/python3.6/socket.py", line 713, in create_connection
    sock.connect(sa)
KeyboardInterrupt
```

Please hep me, I have searched and tried several ways and even reinstalled OS but the problem couldn't be solved still now.

---

### Post by CelticWarrior on 2020-04-08
Have you made any change regarding Python?

---


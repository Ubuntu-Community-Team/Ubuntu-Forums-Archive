---
title: "sudo apt-add-repository does not work"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by Leslie Dorner on 2013-04-29
wellywu@System76:~/Downloads$ sudo add-apt-repository ppa:jonoomph/openshot-edge^CTraceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in get_ppa_info_from_lp
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.3/urllib/request.py", line 160, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.3/urllib/request.py", line 473, in open
    response = self._open(req, data)
  File "/usr/lib/python3.3/urllib/request.py", line 491, in _open
    '_open', req)
  File "/usr/lib/python3.3/urllib/request.py", line 451, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.3/urllib/request.py", line 1287, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.3/urllib/request.py", line 1252, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.3/http/client.py", line 1061, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.3/http/client.py", line 1099, in _send_request
    self.endheaders(body)
  File "/usr/lib/python3.3/http/client.py", line 1057, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python3.3/http/client.py", line 902, in _send_output
    self.send(msg)
  File "/usr/lib/python3.3/http/client.py", line 840, in send
    self.connect()
  File "/usr/lib/python3.3/http/client.py", line 1202, in connect
    server_hostname=server_hostname)
  File "/usr/lib/python3.3/ssl.py", line 210, in wrap_socket
    _context=self)
  File "/usr/lib/python3.3/ssl.py", line 306, in __init__
    self.do_handshake()
  File "/usr/lib/python3.3/ssl.py", line 513, in do_handshake
    self._sslobj.do_handshake()
KeyboardInterrupt

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 129, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 105, in get_ppa_info_from_lp
    import pycurl
ImportError: No module named 'pycurl'
wellywu@System76:~/Downloads$

I tried to add a PPA as listed above, but it keeps pausing and I don't get the PPA added using sudo apt-add-repository command. I remember downgrading from the GNOME3-Team PPA and I don't remember if it removed some Python3, Python3.3, python-software-properties, python3-software-properties, python-pycurl commands, but I checked to make sure that these packages are installed and I did a sudo apt-get install -f and it did not find any broken packages.

I'd like to be able to use sudo apt-add-repository in the future. How do I fix this problem?

I'm using Ubuntu 13.04 64 bit Raring Ringtail.

---

### Post by Leslie Dorner on 2013-04-29
Is there something wrong with Launchpad or Ubuntu Forums right now on April 29th, 2013 at 10:47:12 PM EDT? Could this be the issue causing my problems?

---

### Post by kneedalz on 2013-04-29
i was trying to add one also, just froze, any suggestions?

sudo add-apt-repository ppa:gloobus-dev/gloobus-preview

---

### Post by Leslie Dorner on 2013-04-29
I tried to add your ppa and mine froze too.

It seems that I got all the required packages installed to make add-apt-repository work properly, but it's not connecting to Launchpad to get the PPA information correctly. This is odd.

Is it just you and me or does this affect others currently?

---

### Post by Leslie Dorner on 2013-04-29
wellywu@System76:~/Downloads$ sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
Cannot access PPA ([https://launchpad.net/api/1.0/~gloobus-dev/+archive/gloobus-preview](https://launchpad.net/api/1.0/~gloobus-dev/+archive/gloobus-preview)) to get PPA information, please check your internet connection.
wellywu@System76:~/Downloads$

---

### Post by Leslie Dorner on 2013-04-29
I think that Launchpad or Canonical just went missing in action. My Ubuntu Software Center won't accept my Ubuntu credentials to turn on recommendations right now. It says the authentication failed.

---

### Post by Leslie Dorner on 2013-04-29
[https://twitter.com/launchpadstatus](https://twitter.com/launchpadstatus)

Launchpad is down due to a datacenter failure.

---

### Post by kneedalz on 2013-04-30
ok, that makes sense because I also have a warning sign up in my notification section that my computer is out of date and can't access the repository.

---

### Post by matt_symes on 2013-04-30
There were problems with some of the servers last night/morning/day - depending on which part of the world you live in.

---

### Post by 0N3 on 2013-04-30
I had the same problem too I changed the server for downloading 

Software & Updates under the Ubuntu Software tab change the download server to a different server. My server was the server for Ireland I changed it to the main server and it worked for me.

---


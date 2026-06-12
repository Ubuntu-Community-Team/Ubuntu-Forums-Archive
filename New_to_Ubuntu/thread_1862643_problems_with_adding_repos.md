---
title: "problems with adding repos"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-10-17
HI I am getting following error while adding any repositories......... I am using ubuntu 11.10

amit@amit-R580-R590:~$ sudo add-apt-repository ppa:webupd8team/y-ppa-manager
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 77, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 65, in get_ppa_info_from_lp
    lp_page = urlopen(req).read()
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 394, in open
    response = self._open(req, data)
  File "/usr/lib/python2.7/urllib2.py", line 412, in _open
    '_open', req)
  File "/usr/lib/python2.7/urllib2.py", line 372, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 1209, in https_open
    return self.do_open(httplib.HTTPSConnection, req)
  File "/usr/lib/python2.7/urllib2.py", line 1171, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error [Errno -2] Name or service not known>

---


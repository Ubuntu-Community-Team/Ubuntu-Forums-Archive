---
title: "sources download error"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by xsamurai on 2011-11-23
I have issues when installing certain software through terminal apt get. ubuntu soft centre and synaptic connect well to internet and install but this doesnt work. please help .this is the error message. 

~$ sudo add-apt-repository ppa:tiheum/equinox
[sudo] password for xx: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
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
harsha@hubuntu:~$

---

### Post by neofreud on 2011-11-23
Which version of Ubuntu are you using? and what exactly are you trying to accomplish?? Install a theme I am assuming.

---

### Post by xsamurai on 2011-11-23
I am using 64 bit oneiric ocelot on my compaq laptop. here i was trying to install some icons (faenza). Similar error occurred when I was trying to resolve the white dots on login screen problem as mentioned in this link
[http://joesteiger.com/2011/11/06/remove-white-dots-from-lightdm-login-screen-ubuntu-11-10/](http://joesteiger.com/2011/11/06/remove-white-dots-from-lightdm-login-screen-ubuntu-11-10/)
So i thought it was a generic download problem. but synaptic and softw center works well so also update manager. I dont know where to change the network access settings for this problems and what kind of a problem is this!! 
thanks

---


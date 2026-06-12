---
title: "&quot;sudo apt-add-repository ppa&quot;"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by bonedriven on 2013-01-11
I've set my pc to use proxy for everything as at work I'm behind a proxy of our university.
I've also set up the proxy for apt-get:

gksudo gedit /etc/apt/apt.conf
Add this line to your /etc/apt/apt.conf file (substitute your details for yourproxyaddress and proxyport).

Acquire::http::Proxy "http://yourproxyaddress:proxyport";

Everything seems to work fine, except I find I still failed to connect when trying to use 
sudo apt-add-repository ppa:b-eltzner/qpdfview

I get this:
Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 84, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (7, "couldn't connect to host")

---

### Post by Rocklobster690 on 2013-01-12
Same results with another PPA? ie ppa:webapps/preview

Also use the "Network" application to apply the proxy system wide. I've had to reboot in the past to apply these settings.

---

### Post by NikTh on 2013-01-12
Probably you need further configuration for PPAs . 
See the question and answers here : [http://askubuntu.com/questions/53146/how-do-i-get-add-apt-repository-to-work-through-a-proxy](http://askubuntu.com/questions/53146/how-do-i-get-add-apt-repository-to-work-through-a-proxy)

Tell us if something worked. 
Thanks

---


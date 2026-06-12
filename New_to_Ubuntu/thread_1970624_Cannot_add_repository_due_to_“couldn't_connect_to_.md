---
title: "Cannot add repository due to “couldn't connect to host” error"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by ronsci on 2012-05-01
I am not able to add repository in ubuntu 12.04. My internet connection is working. And I am facing this problem with all the repositories. PLease help. 
I am getting the following msg:

Traceback (most recent call last):   File "/usr/bin/add-apt-repository", line 125, in <module>     ppa_info = get_ppa_info_from_lp(user, ppa_name)   File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp     curl.perform() pycurl.error: (7, "couldn't connect to host")

---


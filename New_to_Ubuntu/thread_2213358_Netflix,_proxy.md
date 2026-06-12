---
title: "Netflix, proxy"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by stevie2 on 2014-03-26
Hello,

 I installed Ubuntu a couple of days ago to start getting better in programming.
One thing i wanted to do first is see if netflix worked on Ubuntu.
So i tried to set it up with some tuts i found on the net.
But too bad i got that error. I used proxys before so i think there might be a problem now 
with my configuration proxy file.
Here is the error i get : 

root@username-K95VJ:~# sudo apt-add-repository ppa:ehoover/compholio
Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 128, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 84, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (56, 'Proxy CONNECT aborted')

How can i fix this error. I don't know what to do please help.

Thanks in advance guys

(Sorry for the bad english)

---


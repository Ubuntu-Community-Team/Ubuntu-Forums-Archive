---
title: "cannot add repository to install cinnamon"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by stonecoldjha on 2012-04-30
since i wanted to give cinnamon a try, i followed the following:
[http://www.noobslab.com/2012/01/install-cinnamon-12-with-new-features.html](http://www.noobslab.com/2012/01/install-cinnamon-12-with-new-features.html)

but i could not add the repo as the terminal output shows:

sonu@sonu-desktop:~$ sudo add-apt-repository ppa:merlwiz79/cinnamon-ppa
[sudo] password for sonu: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (7, "couldn't connect to host")

how do i add this repository?

---

### Post by ammofreak on 2012-04-30
Hi):P: I think Cinnamon is only supported from 11.10 and up... What is your version of Lubuntu?

---

### Post by Curtis6767 on 2012-04-30
Here's an optional way using the Software Center. It's for 11.10 but should work for 12.04

Actually I was playing around with this method and received a couple of errors so I'm going to delete that link.

[]("http://www.linuxbsdos.com/2012/01/05/how-to-install-cinnamon-in-ubuntu-11-10/")

---


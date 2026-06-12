---
title: "cannot add repo"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by stonecoldjha on 2012-04-30
i installed ubuntu 12.04, and then wanted to install myunity. I proceeded as per this link: [http://news.softpedia.com/news/MyUnity-3-0-Supports-Ubuntu-12-04-and-Themes-255220.shtml](http://news.softpedia.com/news/MyUnity-3-0-Supports-Ubuntu-12-04-and-Themes-255220.shtml)
and i typed teh first command, and its output is

sonu@sonu-desktop:~$ sudo add-apt-repository ppa:myunity/ppa
[sudo] password for sonu: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (7, "couldn't connect to host")

I cannot add the repo. Can anyone out here help me please?

---

### Post by Curtis6767 on 2012-04-30
Myunity is in the Software Center

---

### Post by stonecoldjha on 2012-04-30
yes, thank you so much. I could get it installed.

---

### Post by kc1di on 2012-04-30
I'm not sure why you could not add that PPA but you can install MyUnity directly form Ubuntu's Software center. As pointed out by the softpedia page 



> Ubuntu 12.04 LTS (Precise Pangolin) users can easily install MyUnity 3.0 from the Ubuntu Software Center.

---


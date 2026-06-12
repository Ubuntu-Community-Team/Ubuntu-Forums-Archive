---
title: "[SOLVED] medibuntu failing to load"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by eatingganesh on 2008-10-24
Hey friends,

I have been trying to install the medibuntu repository and keep running into the same problem... 

> Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) hardy Release.gpg                          
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) hardy/free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) hardy/non-free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Fetched 841B in 2min0s (7B/s)                             
Reading package lists... Done
W: Failed to fetch [http://packages.freecontrib.org/plf/dists/hardy/Release.gpg](http://packages.freecontrib.org/plf/dists/hardy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/plf/dists/hardy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/hardy/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/plf/dists/hardy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/plf/dists/hardy/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

When I run apt-get update as suggested, the same error occurs. It seems like the error is at freecontrib.org... timing out essentially. I tried to go to their website and see if I could download directly (or get help), but the site is in French. 

Any advice? ideas? Thanks in advance!

---

### Post by jerome1232 on 2008-10-24
[http://packages.freecontrib.org](http://packages.freecontrib.org) doesn't even load for me, either the site is down or your sources.list is just wrong and has a typo in it. What's that repo for?

---

### Post by Coreigh on 2008-10-24
Two things;
1. It looks like your sources.list configuration may be wrong, or out of date. Try this [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu").

2. Medibuntu if often down and you'll just have to try again later.

---

### Post by eatingganesh on 2008-10-24
hi Coreigh!

I originally had followed the instructions on the site you mentioned. So my sources config should be the latest as it was straight from the heron's mouth. Does medibuntu go down often? I hadn't heard.

hi Jerome!

I just don't know what is in that particular repo. As you said, the site itself does not load. But I assume it is part of the medibuntu repo for good reason. Stumped I am.

Guess I'll just keep trying in case the site is just plain down. It does seem that the rest of the medibunutu repo is fine despite this one error. Has anyone else come upon this particular problem with medibuntu?

Thanks for your help!

---

### Post by plucky on 2008-10-24
> Has anyone else come upon this particular problem with medibuntu?


That is not part of the medibuntu repo,so if I were you,I would edit my sources.list file and get rid of it.Better safe than sorry.


Do you know how it got into your sources.list file?

Medibuntu has been quite stable lately,but had problems a couple months back.

---

### Post by eatingganesh on 2008-10-24
Thanks for the info plucky!I did as you suggest and all is well now. :)

---


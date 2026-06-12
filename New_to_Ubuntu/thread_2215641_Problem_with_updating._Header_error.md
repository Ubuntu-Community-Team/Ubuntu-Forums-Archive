---
title: "Problem with updating. Header error?"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by whamola-sam on 2014-04-07
Hey everyone, 

When I tried updating my machine running Ubuntu 13.10 I got an error saying that my headers were unconfigured (or something to that effect). So I open up Synaptic Package Manager and attempt to reinstall "linux-headers-3.11.0-19" and "linux-headers-3.11.0-19-generic" and get the following error message.

E: linux-headers-generic: Package is in a very bad inconsistent state - you should  reinstall it before attempting configuration.
E: linux-generic: dependency problems - leaving unconfigured

So I tried to reinstall those packages and got this error:

E: Internal Error, No file name for linux-generic:amd64

Anyone have any ideas that don't involve a fresh install?
Thanks

---

### Post by whamola-sam on 2014-04-07
Looks like I might have fixed it by running 

sudo apt-get install --reinstall linux-headers-generic
I'll have to see the next time an update is available, but I'm thinking it's all going to be alright.

---


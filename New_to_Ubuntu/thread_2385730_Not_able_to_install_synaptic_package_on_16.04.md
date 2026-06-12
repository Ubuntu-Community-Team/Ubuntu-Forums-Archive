---
title: "Not able to install synaptic package on 16.04"
date: 2018-02-23
forum: New to Ubuntu
---

### Post by alam-284 on 2018-02-23
Hi, i am trying to install synaptic on my 16.04, i am getting an error while doing so,
here is the error i got
sudo apt-get install synaptic
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Anyone how to resolve this error and same error for 
sudo apt-get update

thanks

---

### Post by wildmanne39 on 2018-02-23
Make sure you are not using the terminal, software center, updater at the same time, it should be as simple as closing one of those open or running applications, if not reboot should take care of it. Only one installer application can run at a time.

---

### Post by alam-284 on 2018-02-23
thanks it worked.

one more thing, the download speed in my terminal is very slow and while browsing and downloading from web it is very fast..what could be the issue?

---

### Post by wildmanne39 on 2018-02-23
We only allow one question per thread, please mark this one solved by going to thread tools at the top of the page, then create a new thread for the speed issue.

---


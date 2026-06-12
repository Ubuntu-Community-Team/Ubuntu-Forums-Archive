---
title: "errors occur when mozilla developer edition installation"
date: 2018-03-07
forum: New to Ubuntu
---

### Post by niveshna2018 on 2018-03-07
hi hello everyone,
             i am using UBUNTU 16.04LTS .i want to install mozilla developer edition .But i undergo some errors and i don't know how to solve pls help me.i attached 2 images.pls help me guys.when i try to put in terminal 

this is the code:

umake web firefox-dev
Choose installation path: /home/nivi/.local/share/umake/web/firefox-dev
ERROR: [https://www.mozilla.org/en-US/firefox/developer/all](https://www.mozilla.org/en-US/firefox/developer/all) couldn't finish download: HTTPSConnectionPool(host='www.mozilla.org', port=443): Max retries exceeded with url: /en-US/firefox/developer/all (Caused by NewConnectionError('<requests.packages.urllib3.connection.VerifiedHTTPSConnection object at 0xb18f6fac>: Failed to establish a new connection: [Errno -3] Temporary failure in name resolution',))
ERROR: An error occurred while downloading [https://www.mozilla.org/en-US/firefox/developer/all:](https://www.mozilla.org/en-US/firefox/developer/all:) HTTPSConnectionPool(host='www.mozilla.org', port=443): Max retries exceeded with url: /en-US/firefox/developer/all (Caused by NewConnectionError('<requests.packages.urllib3.connection.VerifiedHTTPSConnection object at 0xb18f6fac>: Failed to establish a new connection: [Errno -3] Temporary failure in name resolution',))

---

### Post by wildmanne39 on 2018-03-07
*Thread moved to **New to Ubuntu, a more appropriate forum**.*

---

### Post by again? on 2018-03-07
Install an updated version of umake and try again.
```
sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
sudo apt update
sudo apt install ubuntu-make

umake web firefox-dev
```

---

### Post by niveshna2018 on 2018-03-07
my error has been solved .thank you very much:):):o:o
thanks for your code

---

### Post by yetimon_64 on 2018-03-07
> **niveshna2018 said:**
> my error has been solved .thank you very much:):):o:o
thanks for your code

Could you please mark your thread solved so it shows in the forum it is posted in please ?

Currently you have only marked your last post which leaves your thread unmarked as [SOLVED] in the New To Ubuntu sub-forum.

If you need a guide for how to do so the blue middle link in my signature has one that is easy to follow.

Regards, yeti.

---


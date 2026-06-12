---
title: "gPodder will not Load"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by yo_pandabear on 2008-06-07
gPodder does not crash.  It will not load.  I have tried broken dependency.  This did not work.  I get the following message after running:

sudo apt-get update

sudo apt-get install -f



W: GPG error: [http://repository.akirad.net](http://repository.akirad.net) akirad-hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB70C672B219D801

W: You may want to run apt-get update to correct these problems

xxxxx@ubuntu:~$ 



What is the problem?   Thanks.

---

### Post by quelx on 2008-06-07
The packages are digitally signed for your protection.

Instructions to install the repositories key:
[http://akiradproject.net/repository](http://akiradproject.net/repository)

```
sudo wget http://repository.akirad.net/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by yo_pandabear on 2008-06-07
Thanks:  
This is my reply from your instructions:

xxxxxx@ubuntu:~$ sudo wget [http://repository.akirad.net/dists/hardy.list](http://repository.akirad.net/dists/hardy.list) -O /etc/apt/sources.list.d/akirad.list
[sudo] password for xxxxxx: 
--13:37:37--  [http://repository.akirad.net/dists/hardy.list](http://repository.akirad.net/dists/hardy.list)
           => `/etc/apt/sources.list.d/akirad.list'
Resolving repository.akirad.net... 66.7.206.3
Connecting to repository.akirad.net|66.7.206.3|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198 [text/plain]

100%[====================================>] 198           --.--K/s             

13:37:37 (14.11 MB/s) - `/etc/apt/sources.list.d/akirad.list' saved [198/198]

xxxxx@ubuntu:~$ 


What should I try next?


I did this, however gPodder tried harder to load this time, well it took more time to try to load.

A great podcast for me is "Going Linux".

---

### Post by quelx on 2008-06-08
```
wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```
Then
```
sudo apt-get install -f
```

---


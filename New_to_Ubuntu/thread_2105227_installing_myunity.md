---
title: "installing myunity"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by quarkhirad on 2013-01-15
I want to install myunity packages i searched on google and found the following procedure 

```

sudo add-apt-repository ppa:myunity/ppa
sudo apt-get update 
sudo apt-get update 

```

However when i enter the second command it gives the following output 

> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en_US
W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


And hence when i type the third command it gives me the following 
> 
khirad@gini:~$ sudo apt-get install myunity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package myunity

Can someone please tell me what is wrong with this method or tell me another way to install myunity.

---

### Post by orange2k on 2013-01-15
I think that myunity isn't available for 12.10 if thats the version of Ubuntu you're running...

---

### Post by haqking on 2013-01-15
Quantal is not there

[https://launchpad.net/ubuntu/quantal/+source/myunity](https://launchpad.net/ubuntu/quantal/+source/myunity)

[http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/)

---

### Post by Cheesemill on 2013-01-15
MyUnity isn't available for Ubuntu 12.10.

You may want to try using [Unsettings]("http://www.florian-diesch.de/software/unsettings/") instead.

```
sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install unsettings
```

---

### Post by quarkhirad on 2013-01-15
> **Cheesemill said:**
> MyUnity isn't available for Ubuntu 12.10.

You may want to try using [Unsettings]("http://www.florian-diesch.de/software/unsettings/") instead.

```
sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install unsettings
```

Hey thanks 

what a shame that myunity is not available .

---

### Post by quarkhirad on 2013-01-15
Hey their is just one more thing. How to install Playdeb in ubuntu 12.10

---

### Post by Cheesemill on 2013-01-15
Playdeb has been down for a while now, I'm not sure if anyone knows whether it will be back again or not.

---


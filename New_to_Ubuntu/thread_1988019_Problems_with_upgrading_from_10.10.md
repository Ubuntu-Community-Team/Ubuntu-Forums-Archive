---
title: "Problems with upgrading from 10.10"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by CarstenA on 2012-05-26
Hi

I am trying to upgrade a Ubuntu 10.10 I have tried to make a sudo apt-get update and sudo apt-get check

But in I dont have the message that there is a new distrubtion avaible in this screen:
[http://www.unixmen.com/wp-content/uploads/2012/02/Update-Manager_003.png](http://www.unixmen.com/wp-content/uploads/2012/02/Update-Manager_003.png)

And I dont have the ugprade screen

I have checked settings and it is marked to check for new releases.

Any ideas why it is not giving the option to upgrade?

Thanks in advance :)

---

### Post by Frogs Hair on 2012-05-26
It used to be you had to upgrade in order so I don't know if 10.10 to 12.04 is possible. You may have to settle for 11.04. 10.10 has reached end of life and that may be a problem as well. You can try from the terminal, but first and back up any valued files.


```
sudo apt-get install update-manager-core
``````
sudo do-release-upgrade
```

---


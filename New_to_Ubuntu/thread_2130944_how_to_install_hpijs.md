---
title: "how to install hpijs?"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by Matrix01 on 2013-03-31
how do u install a driver of HP ink jet printer from Synaptic Package?
i found hpijs.

---

### Post by Rex Bouwense on 2013-03-31
You need to install HPLIP.  First go here:

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

That will determine if your printer is supported in Linux.  It probably is since HP is very Linux friendly.  Then you need to go here to download and install HPLIP.

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

I just downloaded and installed the latest HPLIP.  It is fairly easy.

---

### Post by Matrix01 on 2013-04-01
k@ubuntu:~$ cd Desktop k@ubuntu:~/Desktop$ sh hplip-3.13.3.run sh: 0: Can't open hplip-3.13.3.run k@ubuntu:~/Desktop$   this failed. any helps?   > **Rex Bouwense said:**
> You need to install HPLIP.  First go here:  [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)  That will determine if your printer is supported in Linux.  It probably is since HP is very Linux friendly.  Then you need to go here to download and install HPLIP.  [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)  I just downloaded and installed the latest HPLIP.  It is fairly easy.

---

### Post by Rex Bouwense on 2013-04-01
Did you download HPLIP to your Desktop or to Downloads?  More than likely it is in Downloads if you saved it.  You can check quite easily.  If that is the case, just enter
```
cd Downloads
```
That will get you to where you want to be.  Then just follow the instructions on the site I provided.

---


---
title: "unable to Configure the update manager and sudo apt-get update error"
date: 2020-04-16
forum: New to Ubuntu
---

### Post by aniketiitr on 2020-04-16
Hi,
I have just installed ubuntu bionic 18.04 through usb to my pc, after having multiple BSOD problems with win 10. The system is working well.
The pc configuration is
AMD Ryzen 5 3500
Gigabyte B450M DS3H
Adata Gammix 3200mhz 16GB 
Gigabyte RX570 graphic card
1 Tb WD blue HDD

I am on a proxy  internet having proxy 172.16.24.3 and port 3128, new userid or password  needed. I could configure my wired connection and is using internet  properly.
Going ahead with first step, i tried to Configure the update manager. After clicking on Software and Updates, I am unable to connect to any download server "No suitable download server was found".
I performed this on Terminal
sudo apt-get clean
then
sudo apt-get update
and i got this:
Err:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic InRelease
  Could not resolve 'in.archive.ubuntu.com'
Err:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic-updates InRelease
  Could not resolve 'in.archive.ubuntu.com'
Err:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Could not resolve 'in.archive.ubuntu.com'
Err:4 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic-security InRelease
  Could not resolve 'in.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease)  Could not resolve 'in.archive.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
.
Please help me resolve the errors and also help me Configure the update manager. Please tell me in a little basic way, as i am totally new here.

---

### Post by CatKiller on 2020-04-16
[https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-set-the-proxy-for-apt-for-ubuntu-18-04/](https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-set-the-proxy-for-apt-for-ubuntu-18-04/)

---

### Post by aniketiitr on 2020-04-16
> **CatKiller said:**
> [https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-set-the-proxy-for-apt-for-ubuntu-18-04/](https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-set-the-proxy-for-apt-for-ubuntu-18-04/)

Thanks a lot CatKiller. I followed the steps of the link but the problem remains. Please help..

---

### Post by aniketiitr on 2020-04-16
> **aniketiitr said:**
> Thanks a lot CatKiller. I followed the steps of the link but the problem remains. Please help..

Wow... done... I was not adding http:// again after Proxy :"!!
Anyways thanks a ton..

---


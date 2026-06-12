---
title: "invoke-rc.d: initscript zram-config, action &quot;start&quot; failed."
date: 2013-01-04
forum: New to Ubuntu
---

### Post by kesabussi on 2013-01-04
I am running Ubuntu 12.10 on a virtual server (XFCE as a desktop). I have 1gb of RAM, and I assumed that it might be useful to run zram. I ran the installation command:

sudo add-apt-repository ppa:shnatsel/zram
sudo apt-get update
sudo apt-get install zramswap-enabler 

and got the errors above

I tried to remove the software with:

sudo apt-get remove zramswap-enabler

And tried to reinstall it with 
sudo apt-get install zram-config
However, I got the following error:

Setting up zram-config (0.1) ...
start: Job failed to start
invoke-rc.d: initscript zram-config, action "start" failed.
dpkg: error processing zram-config (--configure):
 subprocess installed post-installation scrip returned error exit status 1
Errors were encountered while processing:
 zram-config
E: Sub-process /usr/bin/dpkg returned an error code (1)

does someone have any ideas what I should do next?

---

### Post by kesabussi on 2013-01-10
bump

---

### Post by Sw1tchx on 2013-02-04
^^ bump*

---

### Post by harayz on 2014-01-24
^^^bump

---


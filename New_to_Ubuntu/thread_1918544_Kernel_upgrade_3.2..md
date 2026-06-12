---
title: "Kernel upgrade 3.2."
date: 2012-02-01
forum: New to Ubuntu
---

### Post by Gforgio on 2012-02-01
Hi everyone, 

I'm currently dual-booting ubuntu 11.10 and w7. 
Yesterday I decided to upgrade my kernel, since I was having troubles shutting down my computer from ubuntu. It would cleanly restart, but will freeze when shutting down. 
So I went on and did this and reboot:

sudo apt-add-repository ppa:francisbrwn9/kernels
sudo apt-get update
sudo apt-get dist-upgrade

Now, when I select ubuntu on the Grub, it goes first to the purple screen for a while and then to a black screen with some processes and it just doesn't turn on. 

I'm pretty new to this, and it's the first time I even attempted to upgrade kernel. And somehow I feel that,it was too uncomplicated to be true :). 
So my questions are: 
Is there something I'm missing from the installation to be properly installed? 
Could this mean that my hardware doesn't support these newest kernels anymore? (I say this because when I was running 10.04/10.10 everything was in perfect working condition)
and lastly if I uninstall with synaptic-PM this last version, will my system go automatically to the last version 3.0.0-15.26? (It is still installed AFAIK from synaptic)


Thanks in advance!

---

### Post by anewguy on 2012-02-01
Don't know what you did, but the page that explains how to update to that kernel also includes instructions on to purge it and go back to where you were:

[http://www.unixmen.com/how-to-upgrade-to-kernel-3-2-in-ubuntu11-10-and-linuxmint12/]("http://www.unixmen.com/how-to-upgrade-to-kernel-3-2-in-ubuntu11-10-and-linuxmint12/")

I suspect you have a driver that needs to be recompiled with the new kernel headers, etc., in order to work.


Dave ;)

---


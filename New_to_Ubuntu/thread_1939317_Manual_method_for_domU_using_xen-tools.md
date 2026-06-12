---
title: "Manual method for domU using xen-tools"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by AleeRaza on 2012-03-11
I have installed Xen hypervisor. Now I dont want to use  virt-manager to create virtual machines. I need to use command line tool  to create guest OS. For this I have read this to create guest OS:


  xen-create-image --hostname=xen1.example.com --size=4Gb --swap=256Mb  --ip=192.168.0.101 --memory=256Mb --arch=i386 --role=udev --scsi --dist  maverick --mirror=http://archive.ubuntu.com/ubuntu


  I am using ubuntu server 11.04. I have downloaded ubuntu 11.04  desktop version. so in above lines how can I include the path of that  iso file. I dont want to install from network.. Thanks

---


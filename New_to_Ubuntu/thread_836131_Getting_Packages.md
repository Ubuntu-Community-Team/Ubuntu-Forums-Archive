---
title: "Getting Packages"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Tharakanuwanpro on 2008-06-21
Without getting packages one by one can't we get ftp acces to packages.ubuntu.com or a package pack or something like that .

I need to get all libraries .

And mp3 decoder means the mp3 codec right ? if not where is the mp3 codec package

---

### Post by hyper_ch on 2008-06-21
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

### Post by syczu on 2008-06-21
mp3 codec is in gstreamer package.

---

### Post by Vivaldi Gloria on 2008-06-21
> **Tharakanuwanpro said:**
> Without getting packages one by one can't we get ftp acces to packages.ubuntu.com or a package pack or something like that .

I don't exactly understand what you mean by that. To install a package use synaptic from your system menu.

> **Tharakanuwanpro said:**
> 
And mp3 decoder means the mp3 codec right ? if not where is the mp3 codec package

Start synaptic from your system menu. Search for the following packages and install them:

```
ubuntu-restricted-extras
lame
```

---

### Post by Tharakanuwanpro on 2008-06-21
The thing is i don't have internet on ubuntu . I am having dual boot for windows xp and ubuntu . I am now in XP . Ubuntu Does not have internet connection . Because my modem does not support linux

---

### Post by hyper_ch on 2008-06-21
install ubuntu in a virtual machine on windows and then you have network access if the windows host has network access ;)

---

### Post by Tharakanuwanpro on 2008-06-21
Thanks . Can you give me a tutorial on installing a virtual machine in windows xp and installing ubuntu on it . But then what about the Ubuntu in my computer

---

### Post by hyper_ch on 2008-06-21
well, download vmware-server ( [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) ) [you have to register yourself - no costs - to get serial number) or virtualbox ( [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI) )

then install the virtualization software... create a virtual machine and then assign the ubuntu cd/image as cd to boot from....

Then it's like a normal installation of ubuntu only that it runs within windows...

You can then "apt-get" or "apt-mirror" all the packages you want... they will be downloaded to /var/cache/apt/archives (when using apt-get, aptitude, adept, synaptic) or some other location that you specify with apt-mirror....

You can then copy them onto a usb key or to a networked drive.... or you could ssh into the virtual OS and download it from there....

---

### Post by the_doc on 2008-06-21
[http://www.psychocats.net/ubuntu/virtualbox]("http://www.psychocats.net/ubuntu/virtualbox")

---

### Post by hyper_ch on 2008-06-21
I rather prefer vmware ;)

---

### Post by the_doc on 2008-06-21
[http://cmsproducer.com/Ubuntu-Linux-Windows-VMware-Server]("http://cmsproducer.com/Ubuntu-Linux-Windows-VMware-Server")

Whatever helps the OP, although I'm not sure this tutorial is as good! :)

---

### Post by hyper_ch on 2008-06-21
:) thx for posting those... the reason I like vmware-server better is because networking into the vm is a lot simpler :)

---

### Post by the_doc on 2008-06-21
I agree about the point on networking, although from my experience I don't think he'll have issues with VB.

---

### Post by Tharakanuwanpro on 2008-06-21
Thanks . I will try it . Without that isn't there a way

---

### Post by the_doc on 2008-06-21
I managed to dig this up.

[http://wubdepends.sourceforge.net/#]("http://wubdepends.sourceforge.net/#")

I don't use it, or endorse it, but it may help with your issue.  It has a Windows .exe so you should be able to download packages and their dependencies on your XP box then transfer to Ubuntu via USB/CD or whatever.

I suggest you read around it first though.

---


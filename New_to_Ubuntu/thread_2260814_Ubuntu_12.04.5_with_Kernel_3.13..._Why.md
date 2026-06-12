---
title: "Ubuntu 12.04.5 with Kernel 3.13... Why?"
date: 2015-01-14
forum: New to Ubuntu
---

### Post by padremayi on 2015-01-14
Hi to all.

Is it normal that when I install Ubuntu 12.04.5 I find that my kernel is 3.13.0-32-generic?

I need 3.2 kernel.

Thanks

---

### Post by slickymaster on 2015-01-14
Ubuntu 12.04.5 ships with an updated kernel 3.13 drawn from 14.04 LTS.

---

### Post by padremayi on 2015-01-14
What is the last version of 12.04 with a kernel 3.2+?

Thanks for your reply

EDIT: Ok, I found the answer, thanks

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support)

---

### Post by deadflowr on 2015-01-14
> **padremayi said:**
> What is the last version of 12.04 with a kernel 3.2+?

Thanks for your reply

12.04.1, or just 12.04
You can get it here
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

You need to scroll down until you find the version marked ubuntu-12.04-desktop..., or ubuntu-12.04.1-desktop...
Replace ... with the arch(amd64 for 64-bit, i386 for 32-bit) and iso.

---

### Post by padremayi on 2015-01-14
Thanks, I just found that page :)

---

### Post by padremayi on 2015-01-14
Just a question: if I do

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
does it change my kernel version?

---

### Post by slickymaster on 2015-01-14
**apt-get upgrade** always install new versions of the packages that are already installed on the system. And yes, kernel updates belong to them.

---

### Post by deadflowr on 2015-01-14
> **padremayi said:**
> Just a question: if I do

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
does it change my kernel version?
dist-upgrade will upgrade the current kernel version of which ever kernel series you are currently using.
So it'll upgrade 3.2.0-29 to 3.2.0-30, but it will not upgrade 3.2.0-29 to 3.13.0-43, for example.
> **slickymaster said:**
> **apt-get upgrade** always install new versions of the packages that are already installed on the system. And yes, kernel updates belong to them.
Sort of.
But something like 3.2.0-74 and 3.2.0-75 are different packages.
But 3.2.0-74.33 and 3.2.0-74.34 would be of the same package so in those cases they would be updated using only apt-get upgrade.
Here are two outputs from the terminal showing apt-get upgrade and dist-upgrade
apt-get upgrade
```
~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic
```
and apt-get dist-upgrade
```
~ $ sudo apt-get dist-upgrade
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-image-3.13.0-44-generic linux-image-extra-3.13.0-44-generic
```
Hope it helps or make sense or whatnot.

---

### Post by slickymaster on 2015-01-14
> **deadflowr said:**
> dist-upgrade will upgrade the current kernel version of which ever kernel series you are currently using.
So it'll upgrade 3.2.0-29 to 3.2.0-30, but it will not upgrade 3.2.0-29 to 3.13.0-43, for example.

Sort of.
But something like 3.2.0-74 and 3.2.0-75 are different packages.
But 3.2.0-74.33 and 3.2.0-74.34 would be of the same package so in those cases they would be updated using only apt-get upgrade.
Here are two outputs from the terminal showing apt-get upgrade and dist-upgrade
apt-get upgrade
```
~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic
```
and apt-get dist-upgrade
```
~ $ sudo apt-get dist-upgrade
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-image-3.13.0-44-generic linux-image-extra-3.13.0-44-generic
```
Hope it helps or make sense or whatnot.

Spot on deadflowr :p

---

### Post by padremayi on 2015-01-15
Ok, so

```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
does update only xx on kernel version like this?

```
3.2.0-xx.xx
```
EDIT: I found the answer from [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

> To remain on the original Precise stack there are a few options:
[LIST]
[*]Install from a previous 12.04.0 or 12.04.1 point release and update. The previous 12.04.0 and 12.04.1 releases are archived at [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
[*]Only those installing from the 12.04.2 or newer point release media will automatically receive a newer enablement stack by default.
[/LIST]

Thanks to all

---

### Post by viceone on 2015-11-06
I'm sorry, I lacked the quote, a moderator can delete it if you want

---

### Post by viceone on 2015-11-06
> 
Originally Posted by **padremayi**

What is the last version of 12.04 with a kernel 3.2+?
Thanks for your reply
EDIT: Ok, I found the answer, thanks[URL="https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support"]
https://wiki.ubuntu.com/Kernel/LTSEn...Kernel_Support[/URL]                 
            
                         
                                       

Thanks for the link

---


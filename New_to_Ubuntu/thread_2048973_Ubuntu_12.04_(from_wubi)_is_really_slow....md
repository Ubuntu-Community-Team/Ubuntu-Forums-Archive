---
title: "Ubuntu 12.04 (from wubi) is really slow..."
date: 2012-08-27
forum: New to Ubuntu
---

### Post by asmith2306 on 2012-08-27
Hi,

can anyone help me?  I have Ubuntu 12.04 installed from a wubi installation (don't know if that makes a difference, gave it 30gb) and at times it hangs for relatively long periods.  I am using Netbeans, glassfish application server and a mysql server which I thought might be eating up the system but I checked the system monitor and its not too bad.  I have 6GB of RAM and an i5 quad core.  Each processor is at about 8% and I'm only using up to 2.5 GB of RAM.   The whole system just seems slow and laggy regardless of these applications.  Package manager and firefox in particular hang regularly.  

I have seen other posts with people updating their nvidia cards which seemed to solve their problem but I don't even know how to check my graphics card on Ubuntu!

Please help me stay away from Windows once and for all!

Thanks,
Alan

---

### Post by MG&amp;TL on 2012-08-28
Wubi is really designed to test out Ubuntu-if you want maximum performance, you'll want to actually do a full disk install.

Anyway, you're probably missing a driver if you have an nvidia card. Open 'additional drivers' and see if anything is available.

---

### Post by mastablasta on 2012-08-28
if you have optimus technology you need to use bumblebee.

---

### Post by blade4 on 2012-08-28
Try using unity 2d ... choose the option from the login screen .

For checking the graphics card follow this : 
[http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/](http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/)

For updating nvidia graphics ( or any graphics for that matter ) , use x-swat ppa 

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates  
sudo apt-get update 
sudo apt-get upgrade
```
Instead of 'upgrade' in the last line you can enter the package name of the driver you need if you know its name .

Cheers

---


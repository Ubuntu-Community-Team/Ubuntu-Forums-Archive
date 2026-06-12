---
title: "How to install firmware"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by nawaz1 on 2012-08-17
plz tell me how to install this firmware 
[http://de.archive.ubuntu.com/ubuntu/...e_1.11_all.deb]("http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb")
any command needed in terminal 
or something else plz tell me

---

### Post by roger_1960 on 2012-08-17
Hi

I suggest first install "GDebi package installer" from the Software Center

Then download the .deb file to your PC

Then right click the file and select "install with gdebi.."

Good luck

---

### Post by NikTh on 2012-08-17
Hi , 
why you want to install specific this non-free-firmware from .deb package ? 

You can install non-free-firmware from terminal(ctrl+alt+t) with this command 
```
sudo apt-get install linux-firmware-nonfree
``` 
If you want to install (for your own reasons) this specific .deb package you can do it from terminal (ctrl+alt+t) with this command 

```
cd Downloads
sudo dpkg -i linux-firmware-nonfree_1.11_all.deb
``` 
I assume you downloaded the .deb file in Downloads (is the default location).
Thanks

---


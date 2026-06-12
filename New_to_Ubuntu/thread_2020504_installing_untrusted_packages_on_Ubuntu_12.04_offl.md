---
title: "installing untrusted packages on Ubuntu 12.04 offline (64bit)"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by jovalec on 2012-07-08
Hi all

I have some problems with installing *wvdial*, but not with it directly. The thing is, currently my only way to connect to the Internet is by my GSM provider. Now on Win7.

I am trying to make a connection on Ubuntu 12.04. Firstly, I must install *wvdial *but, because I'm offline there, I must have standalone .deb packages. The problem is - I can't install them - Software Center tells me to install them 'normally' because they don't come from a trusted source. How can I avoid it?

Thanks in advance

---

### Post by NikTh on 2012-07-08
If you are sure about trust for packages then you can use dpkg from terminal to install. 
e.g ```
sudo dpkg -i /path/to/package/.deb
``` 

If this not solve your problem you can do a force install with dpkg. [COLOR=Red]WARNING[/COLOR] : This is dangerous for your system , doing it an your own risk.
```
sudo dpkg --force-all -i /path/to/packagee/.deb
``` 
I repeat that you are doing in this with you own risk.

---

### Post by jovalec on 2012-07-08
Thanks a lot, *dpkg* was what I've been looking for. Now writing from Ubuntu :>

---


---
title: "Installing Freeradius"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by cway00 on 2012-10-01
hello 

I meet a problem while trying to install freeradius..want to use it for a hotspot ..but i met this error after installation. 
 ```

ubuntu 12.04 /var/run/freeradius/freeradius.pid not found

```Using Ubuntu 12.04

---

### Post by HermanAB on 2012-10-01
Howdy,

See this guide:
[http://www.aeronetworks.ca/howtos/radius.html](http://www.aeronetworks.ca/howtos/radius.html)

and scroll down to Maintenance Configuration.

---

### Post by cway00 on 2012-10-02
> **HermanAB said:**
> Howdy,

See this guide:
[http://www.aeronetworks.ca/howtos/radius.html](http://www.aeronetworks.ca/howtos/radius.html)

and scroll down to Maintenance Configuration.

I went through the site you gave me extensively ..but still lurking on dat issue, which file will I edit based on the maintenance option from

---

### Post by HermanAB on 2012-10-02
You need to create a directory where radiusd can store the pid file when it starts up.

Your error message said:
ubuntu 12.04 /var/run/freeradius/freeradius.pid not found

So try this:
# sudo mkdir /var/run/freeradius

Then restart it and see what it says this time.

This is very obscure stuff.  There are only a handful of people in world that play with Radius.

---

### Post by cway00 on 2012-10-02
Thanks for this advice  

```
you need to create a directory where radiusd can store the pid file when it starts up.

Your error message said:
ubuntu 12.04 /var/run/freeradius/freeradius.pid not found

So try this:
# sudo mkdir /var/run/freeradius

Then restart it and see what it says this time.

This is very obscure stuff.  There are only a handful of people in world that play with Radius.     
```I have been able to make it work by performing the following actions 
Removing all config files and directory of freeradius 

Then I have to reboot in recovery mode and tried to perom a system like reapir and when I had to do a normal boot, I now installed freradius using the following 

```

sudo su  

``````
apt-get install freeradius freeradius-mysql freeradius-utils 
```now it works perfectly 

anyway I want to setup a hotspot captive portal ..using Ubuntu, Freeradius, coovachiili ..any hotspot script like daloradius, easyhotspot ..yfi hotspot ..

---


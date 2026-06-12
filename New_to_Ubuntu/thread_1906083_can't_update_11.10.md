---
title: "can't update 11.10"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by Watts2012 on 2012-01-08
I just did a clean install of 11.10.  
I'm trying to install updates but I get this message after I click install

REQUIRES INSTALLATION OF UNTRUSTED PACKAGES
THIS ACTION WOULD REQUIRE THE INSTALLATION OF PACKAGES FROM NOT AUTHENTICATED SOURCES.

Whats up with that?  Can anyone help?  Thanks  :confused:

---

### Post by tersogar on 2012-01-08
When that happen to me I use the terminal and was able to update.

---

### Post by Frogs Hair on 2012-01-08
Hello and Welcome 

From the update manager , select the check again to update the package information and then try to install the updates again . The terminal equivalent to this would be .```
sudo apt-get update
```  ```
sudo apt-get upgrade
```

---

### Post by hansdown on 2012-01-08
Welcome to the forum, Watts2012.

That's just a generic warning.

As long as you're downloading from an official ubuntu site, you have no worries.

---

### Post by Watts2012 on 2012-01-08
tried that too, that fails also

---

### Post by Watts2012 on 2012-01-08
the sudo apt-get upgrade seems to be working now.  

regarding the reply that it is a generic notification, when I get it the process exits so I get none of the updates.  
Do you think there is some preference setup wrong?

---

### Post by goofey24 on 2012-01-08
> **Watts2012 said:**
> I just did a clean install of 11.10.  
I'm trying to install updates but I get this message after I click install

REQUIRES INSTALLATION OF UNTRUSTED PACKAGES
THIS ACTION WOULD REQUIRE THE INSTALLATION OF PACKAGES FROM NOT AUTHENTICATED SOURCES.

Whats up with that?  Can anyone help?  Thanks  :confused:
Just my way of update proccess

```
I always update using:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo apt-get autoclean
sudo dpkg --configure -a

```
and if there was a kernel upgrade:
```
sudo update-grub2
```

---


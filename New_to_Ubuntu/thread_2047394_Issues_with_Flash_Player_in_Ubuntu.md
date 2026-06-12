---
title: "Issues with Flash Player in Ubuntu"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by PumaMania on 2012-08-24
I have a Dell Inspiron N4110 With Intel HD 2000 Graphics and a Core i5 processor. In Windows, I can play flash smoothly. In Ubuntu, flash stutters and the computer's vents get really hot. I have Ubuntu 12.04 32bit version. Is there anything I can fix?

---

### Post by NikTh on 2012-08-24
Hi , 
are you sure that you have installed flash player ? (no offense but you didn't say if you are a newbie in Ubuntu(Linux) 

If you are not sure , open a terminal (ctrl+alt+t) and post the results of these commands
```
apt-cache policy adobe-flashplugin
apt-cache policy flashplugin-installer
```you can copy from here one at time , the commands and paste them to terminal . 

Put the results inside ```
 tags so can be readable
[noparse][code]the results here
```[/noparse]
Thank you.

---

### Post by PumaMania on 2012-08-30
After typing in 
```
 apt-cache policy adobe-flashplugin 
```
I got 
```
adobe-flashplugin:
  Installed: (none)
  Candidate: 11.2.202.238-0precise1
  Version table:
     11.2.202.238-0precise1 0
        500 http://archive.canonical.com/ubuntu/ precise/partner i386 Packages
```

After typing in 
```
 apt-cache policy flashplugin-installer 
``` 
I get
```
flashplugin-installer:
  Installed: 11.2.202.238ubuntu0.12.04.1
  Candidate: 11.2.202.238ubuntu0.12.04.1
  Version table:
 *** 11.2.202.238ubuntu0.12.04.1 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/multiverse i386 Packages
        500 http://archive.ubuntu.com/ubuntu/ precise-security/multiverse i386 Packages
        100 /var/lib/dpkg/status
     11.2.202.233ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages

```

---

### Post by NikTh on 2012-08-30
Hi , 
I don't know if this makes any difference but you can try this 

```
sudo apt-get remove flashplugin-installer
sudo apt-get install ubuntu-restricted-extras
``` 

reboot.

Thanks

---

### Post by MadmanRB on 2012-08-30
Install google chrome, flash support for linux is dead and the only way to actually get a working version now without insane command line is to install google chrome.

---


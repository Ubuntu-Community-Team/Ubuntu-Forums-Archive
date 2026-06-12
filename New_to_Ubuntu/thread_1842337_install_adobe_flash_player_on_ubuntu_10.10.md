---
title: "install adobe flash player on ubuntu 10.10"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by nosmas on 2011-09-11
Hello fellas Its my first day to use ubuntu, I'm a newbie, Ijust wanted to install adobe flash player I downloaded it and the ubuntu software center automatically opened, when I click the "use this source " button nothing happens.  I'm using ubuntu 10.10

---

### Post by fooman on 2011-09-11
are you using firefox? ...if so,  try the "flash-aid" add on.  

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

that will install the proper version of flash for you.

---

### Post by gandaran on 2011-09-11
> **nosmas said:**
> Hello fellas Its my first day to use ubuntu, I'm a newbie, Ijust wanted to install adobe flash player I downloaded it and the ubuntu software center automatically opened, when I click the "use this source " button nothing happens.  I'm using ubuntu 10.10
you have to enable the archive canonical repository in software sources for that package, but forget that one and install the ubuntu official flash package, find the "flashplugin-installer" in sofware center to install or use the command line to install
```
sudo apt-get install flashplugin-installer
```
if you are on ubuntu 64-bits post back for instructions for 64-bits flash.

---

### Post by haqking on 2011-09-11
> **fooman said:**
> are you using firefox? ...if so,  try the "flash-aid" add on.  

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

that will install the proper version of flash for you.

+1

Flash

I suggest using [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/") for firefox aswell, it will download the best version for your system and can use across browsers once installed.

usually solves about 99.9%of Flash issues posted on this forum, it was created by one of the community members (lovinglinux)

hope this helps

regards

haqking

---

### Post by donpeter06 on 2011-09-11
You can alternately install the same from synaptic or ubuntu software center.type "flash plugin" choose and install.

---


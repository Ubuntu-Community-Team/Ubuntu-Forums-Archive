---
title: "errors in ftp installation"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by jerryheavyarms on 2008-09-09
Hello!

Could you tell me what's the meaning of this error?

E:Could not get lock /var/cache/apt/archives/lock - open (11 Resource Temporarily Unavailable)

E: Unable to lock the downloade directory


Prior to this i install proftpd then after a few minutes i uninstall it. I did these using the terminal.

And then i decided to install it again and this error comes out. I tried installing pure-ftpd but it has the same errors.

Any help? Thank you very much in advance!
Jerry

---

### Post by iaculallad on 2008-09-09
You could try removing the lock file:

```
sudo rm /var/cache/apt/archives/lock
```

Then:

```
sudo apt-get update && sudo apt-get upgrade
```

and install proftpd

---

### Post by jemate18 on 2008-09-09
> **jerryheavyarms said:**
> Hello!

Could you tell me what's the meaning of this error?

E:Could not get lock /var/cache/apt/archives/lock - open (11 Resource Temporarily Unavailable)

E: Unable to lock the downloade directory


Prior to this i install proftpd then after a few minutes i uninstall it. I did these using the terminal.

And then i decided to install it again and this error comes out. I tried installing pure-ftpd but it has the same errors.

Any help? Thank you very much in advance!
Jerry

are you using 
```
apt-get install whateverpackage
``` ?

it should be run as a Super user.. type
```
sudo apt-get install whateverpackage
```
and then type your password after hitting the enter key

---


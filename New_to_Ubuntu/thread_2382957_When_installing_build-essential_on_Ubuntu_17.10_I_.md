---
title: "When installing build-essential on Ubuntu 17.10 I encounterrd a problem"
date: 2018-01-19
forum: New to Ubuntu
---

### Post by sakuraro on 2018-01-19
I used the command "sudo apt-get install build-essential", I got an error in the installation process
The error is below:
```
Err:2 http://us.archive.ubuntu.com/ubuntu artful-updates/main amd64 libc6 amd64 2.26-0ubuntu2.1
```
how do I reinstall the failed packages?

---

### Post by cruzer001 on 2018-01-19
Hello

I'm not finding this package (the 2.1).

[https://packages.ubuntu.com/artful/libc6-amd64](https://packages.ubuntu.com/artful/libc6-amd64)

What is currently installed?

```
apt-cache policy libc6
```

What about build-essential?

```
apt-cache policy build-essential
```

Have you open up the pre-release (proposed) updates?  Or maybe added a PPA or some third party app?

May help to have a look at your sources; please post the output of:

```
inxi -r
```

---

### Post by oldos2er on 2018-01-19
sakuraro, try running ```
sudo apt update
``` first.

---


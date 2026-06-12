---
title: "Can't install package"
date: 2015-05-19
forum: New to Ubuntu
---

### Post by Arpan_Bag on 2015-05-19
Trying to setup environment for android ROM development, but the libgl1-mesa-glx:i386 package is not installing. I'm on Ubuntu 14.04.2. Need help...
Update: Meanwhile I installed libglapi-mesa-lts-saucy:i386    Is it fine now?

---

### Post by SeijiSensei on 2015-05-19
Did you run "sudo apt-get update" before trying to install?

---

### Post by Arpan_Bag on 2015-05-19
yeah. sudo apt-get update as well as sudo apt-get upgrade

---

### Post by dino99 on 2015-05-19
[https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

---

### Post by Arpan_Bag on 2015-05-19
> **dino99 said:**
> [https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)
I can't get u

---

### Post by deadflowr on 2015-05-19
14.04.2 you say?
You don't happen to already have the upgraded lts-utopic version installed, by chance.
what does
```
dpkg -l | grep libgl1-mesa-glx
```
say?

More here on reference about what I meant about lts-utopic version
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Arpan_Bag on 2015-05-20
[COLOR=#111111][FONT=Ubuntu]Meanwhile, I installed libglapi-mesa-lts-saucy:i386

Command:
[/FONT][/COLOR]dpkg -l | grep libgl1-mesa-glx

[COLOR=#111111][FONT=Ubuntu]Output:
[/FONT][/COLOR]ii  libgl1-mesa-glx-lts-utopic:amd64                      10.3.2-0ubuntu1~trusty2                             amd64        free implementation of the OpenGL API -- GLX runtime

---


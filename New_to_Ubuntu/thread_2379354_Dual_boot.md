---
title: "Dual boot"
date: 2017-12-04
forum: New to Ubuntu
---

### Post by physwizz2 on 2017-12-04
I have just got a Toshiba Satellite L650D and I have managed to install Ubuntu 12 as dual boot by adding the following to grub.
nomodeset
pcie_aspm=off
This is not working with any Ubuntu 13 or greater.
Is there anything else I can try?

---

### Post by RobGoss on 2017-12-04
Hello and welcome to the forum, I would suggest using a supported version of Ubuntu, the one you installed is not supported. Try 16.04 LTS

---

### Post by yancek on 2017-12-04
How old is this computer?  You might post some details on the hardware you are using.

---

### Post by mastablasta on 2017-12-07
you likely need non pae kernel. i think lubuntu or lxle have it.

---

### Post by leunam12 on 2017-12-07
try using the 'forcepae' flag.

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by leunam12 on 2017-12-07
Satellite L650D?? That looks a lot like my laptop, I'll check when I get home, I have to install Ubuntu on it anyway.

---


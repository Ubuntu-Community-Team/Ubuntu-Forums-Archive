---
title: "how to setup server to conduct penetration test"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by john rosswrock on 2013-05-09
I am using ubuntu 12.04LST and want to setup a server on the same os so as conduct penetration tests on it ....
can anyone guide me to how to setup a server...
thanx in advance

---

### Post by LutraMan on 2013-05-09
I would think in a direction of setting up a virtual machine.
Try oracle Vbox as a start: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
You can also try using KVM using:
```
sudo apt-get install kvm
```
however I've found that it is just as efficient and much simpler with vbox.

After installing, create a new machine and tell it to mount your .iso file as start. boot from it and install ubuntu 12.04 (or any other OS for that matter)
remember to remove the iso afterwards. and since you will be using it for penetration testing, I would highly recommend to take a snapshot at that point.

good luck.

---

### Post by john rosswrock on 2013-05-09
> **LutraMan said:**
> I would think in a direction of setting up a virtual machine.
Try oracle Vbox as a start: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
You can also try using KVM using:
```
sudo apt-get install kvm
```
however I've found that it is just as efficient and much simpler with vbox.

After installing, create a new machine and tell it to mount your .iso file as start. boot from it and install ubuntu 12.04 (or any other OS for that matter)
remember to remove the iso afterwards. and since you will be using it for penetration testing, I would highly recommend to take a snapshot at that point.

good luck.

thanx for the reply..:smile: 		
but are there other ways to do it rather than using Vbox

---

### Post by lisati on 2013-05-09
To install Ubuntu Server, download the ISO image, burn it to CD or DVD, and boot the server machine from the disk. *Don't forget to make backups of important data first, including recovery partitions etc.*

---


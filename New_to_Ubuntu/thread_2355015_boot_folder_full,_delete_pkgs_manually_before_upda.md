---
title: "boot folder full, delete pkgs manually before update, how to set limit for the folder"
date: 2017-03-08
forum: New to Ubuntu
---

### Post by ockac23 on 2017-03-08
Hi folks,

I have the Ubuntu 14.04. LTS on a 64 bit machine.
My question is how to set a limited number of **initrd.img-x.x.x.-generic **packages, that are saved automatically in the /boot folder after every kernel update?
The reason for my question is, that after every automatically done Ubuntu update, that includes the kernel files, the old versions are automatically stored in the /boot folder. 
But after several updates, there is no more free space in the folder, so an automatic update cannot start. So I have to delete them manually via terminal command every time this happens. 
Can I choose some setting on my system, so that only a limited number of old kernel files are saved into this folder autocratically, for example the last five or something like this...

Many thanks!

---

### Post by DuckHook on 2017-03-08
Xenial will delete your old kernels except the latest two by using:```
sudo apt autoremove
```…but this was not yet introduced in Trusty. There is a nifty script called "purge-old-kernels" available from the package: *byobu*, which is, itself, a very useful enhancement to the command line. Do:```
sudo apt-get update
``````
sudo apt-get install byobu
``````
sudo purge-old-kernels
```This will purge all kernels except your most recent two.

Kernel upkeep and cleanup is just a chore of using Ubuntu. Until Xenial, the developers appeared to shy away from autopurging of old kernels, preferring to err on the side of caution rather than saving disk space.

Another area where old kernels hang around is the actual kernel package itself. Note: I am referring to the kernel *package* and not the kernel proper, which is what you are wrestling with in /boot. The old packages can be found be doing:```
dpkg --get-selections | grep linux
```All the ones labelled "deinstall" can be safely purged.

---

### Post by ockac23 on 2017-03-08
Thank you very much!

---

### Post by DuckHook on 2017-03-09
You are welcome.

Good Luck & Happy Ubuntu-ing!

---


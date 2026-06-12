---
title: "Can't find make"
date: 2005-10-28
forum: Packaging and Compiling Programs
---

### Post by maclaren_sg on 2005-10-28
I'm new to Ubuntu. I try to install a package which consist of a few steps.
./configure
make
make install


the problem is there is no make in Ubuntu.
What so I do then?

---

### Post by manicka on 2005-10-28
make does exist in ubuntu. Have you installed the build-essential package?

sudo apt-get update
sudo apt-get install build-essential

---

### Post by yogiudo on 2007-03-28
I need make to compile rp-pppoe so I can get internet, and obviously sudo apt-get update
sudo apt-get install build-essential wont work without internet

please advise

---

### Post by maclarensg on 2007-04-01
U have to at least download the deb  packages
try to download from
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) 
to on machine and bring it over...to the machine w/o internet 

However, I recommend u to connect the machine w/o internet to internet....
less pain and fuss with apt-get

---


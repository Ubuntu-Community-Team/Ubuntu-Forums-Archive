---
title: "Trying to install Firefox on Raspberry Pi 3"
date: 2017-08-16
forum: New to Ubuntu
---

### Post by warrenc51 on 2017-08-16
Trying to install Firefox on Raspberry Pi 3 but can not get past 
ssh <Ubuntu SSO user name>@<device IP address>
I input my user name(warrenc51) & the IP address of my device

I input my user name(warrenc51@gmail.com) & the IP address of my device

Inboth cases I get an error message of:  Creating user failed   no ssh keys found

Please help

---

### Post by cariboo on 2017-08-16
You need to create and install the ssh key pair on the computer you are using and on the Raspberry Pi, for an ssh howto have a look here:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

You don't say what O/S you are running on the Raspberry PI, but most of the operating system's I've tried don't install openssh by default.

---


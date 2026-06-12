---
title: "Error when trying to upgrade."
date: 2008-05-03
forum: New to Ubuntu
---

### Post by L Campbell on 2008-05-03
I get this message in Update Manager when checking to see if my system is up to date.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Should I/can I do anything about this?

When I 'close' it Update Manger then tells me that my system is up to date and seems to indicate that I can begin the upgrade procedure. 

Am I being concerned unnecessarily here?

TIA.

---

### Post by frup on 2008-05-03
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

try that

otherwise maybe this will work better

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

that is from
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by rajaram_s on 2008-05-03
Please donot try upgrading your ubuntu. Its always better to install a clean copy of 8.04, backing up all your data in a seperate partition for home folder. I am having a lot of problems since I upgraded from 7.10 to 8.04 tough my friends, who made a clean install report that its working great.....

---

### Post by mattkf4aej on 2008-06-02
i did the following below today it worked and updated with no problems. mine is working now. 

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---


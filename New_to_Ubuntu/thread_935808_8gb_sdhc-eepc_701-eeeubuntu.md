---
title: "8gb sdhc-eepc 701-eeeubuntu"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by bujulock on 2008-10-02
Hello all,

i gues it's a Ubuntu problem...?

Ubuntu/my eee pc sees my 8gb card, but comes with the "can't mount" message, superuser issue....

i like to use my 8gb card constantly....but since ubuntu(yesterday) i can't, then again I LUUUUUUUUUUV UBUNTU! up till now ;-) i think it's great.

the main question: is there a way to get Ubuntu/eee pc to mount the card.

thnx in advance

Sherlock....as in Holmes, but since it's fiction, i didn't find the answer :confused:

---

### Post by rybaxs on 2008-10-02
what is your problem? installation problem?

---

### Post by bujulock on 2008-10-02
if i stick a usb stick in, it recognizes the usb stick, when i put a sd or sdhc card in it doesn't open the card...it doesn't mount it.

it sees(recognizes) the sdhc card, but you can't do anything with it.

---

### Post by RAMDrive on 2008-10-14
Same problem on the asus eee 901 running Ubuntu eee 8.04

---

### Post by t0p on 2008-10-14
Running ubuntu 8.04.1 on an eeepc?  [Here's a guide]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly") to tweaking hardy for the eeepc, and scripts to automate the tweaking.  It includes a fix so your sdhc will mount.  I use a 4gb sdhc constantly, I keep it in the card reader and ubuntu auto-mounts it.

---

### Post by RAMDrive on 2008-10-15
> **RAMDrive said:**
> Same problem on the asus eee 901 running Ubuntu eee 8.04

Solved:
[http://ubuntuforums.org/showpost.php?p=5920180&postcount=2](http://ubuntuforums.org/showpost.php?p=5920180&postcount=2)

---

### Post by edrizo on 2009-04-10
I have the same problem!!!!

Any help????

---

### Post by edrizo on 2009-04-10
> **RAMDrive said:**
> Solved:
[http://ubuntuforums.org/showpost.php?p=5920180&postcount=2](http://ubuntuforums.org/showpost.php?p=5920180&postcount=2)

This didn't work for me.

My SDHC card didn't mount on the EEE PC with ubuntu 8.04!

Please, help!

---

### Post by edrizo on 2009-04-13
I still have this issue to solve. Does any one know how can I use my SDHC on Ubuntu 8.04???

---

### Post by edrizo on 2009-05-14
Anyone???

---

### Post by edrizo on 2009-05-17
I did it!!!!  It's Alive!!!!

Here is what I did:

1) mkfs.ext2 /dev/sdb

This command format SD card in ext2. "/dev/sdb" is where my SD is.


2) mkdos - I /dev/sdb


Now I can see the SD Card in Linux and Windows.

It works fine for me.

---


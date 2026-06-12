---
title: "[SOLVED] Help with reinstallation"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-09-03
I decided to move Ubuntu to another partition on another disc.

The previous partitioning scheme was:

/dev/sda1  ext3 /media/disk

/dev/sdb1 swap
/dev/sdb2 ext3  /
/dev/sdb3 ext3 /home

The new scheme is:

/dev/sda1 swap
/dev/sda2 ext3 /
/dev/sda3 ext3 /backup

/dev/sdb1 ext3 /virtual
/dev/sdb3 ext3 /home

I wanted to get a list of all installed applications before making the change. The irc channel bot provided me with the following instructions:

> To replicate your packages selection on another machine (or restore it if re-installing), you can type 

dpkg --get-selections > ~/my-packages 

move the file "my-packages" to the other machine then type

sudo dpkg --set-selections < my-packages && apt-get dselect-upgrade

So I did as instructed, formated /dev/sda1,  /dev/sda2,  /dev/sda3 and  /dev/sdb1, installed Ubuntu accordingly and yadayadayada

After installation, when I typed "sudo dpkg --set-selections < my-packages && apt-get dselect-upgrade" I received a message that I was not root. So I typed "sudo su" and the previous command again.

All applications were installed accordingly and everything seems to be working properly. 

I want to know if the fact that I used "sudo su" could mess something with the installed applications?

---

### Post by Peter09 on 2008-09-03
sudo means that the command following is executed as root. In Ubuntu it is normal just to do

sudo <command line>

Doing sudo su just means that you are permanently in the root user until you exit. This is not really recommended as it is a security risk (some debate this).

Other than that there is no difference (as far as I am aware) between the two actions.

---

